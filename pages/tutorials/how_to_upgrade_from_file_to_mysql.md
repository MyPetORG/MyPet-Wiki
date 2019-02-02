# NBT to MySQL

### This feature is part of MyPet-Premium!

If you want to use a MySQL database to store your pets please download the premium version of MyPet [here](https://www.spigotmc.org/resources/mypet-premium.17566/).

## Setup

First of all thank your for purchasing MyPet-Premium!

1. Put the plugin file into you plugin folder and restart the server so that the plugin can generate the new config settings.
2. Set the `Type` setting under `Repository` to `MySQL`
3. If you have an old `My.Pet` file you want to import set `ConvertFrom` setting under `Repository` to `SQLite`\(or what `Type` was before\).
4. create a new database \(collation: `utf8_general_ci`\) on your MySQL server \(default: `mypet`\).
5. replace the credentials under `MySQL` with your own.
6. restart the server once again. It should create the tables and import the local file to the database.
7. **OPTIONAL:** _If you want to merge multiple_ `My.Pets` _files into one database you can use the script at the bottom of this page._
8. You can run your server like normal but all servers you use can now access the pets from one database!

### MySQL Merge Script

If you want to merge two MyPet databases, they need to be on the same server and have different names. Just download the file in the spoiler and fill in the correct credentials and database names and the PHP script will merge them together. Different \(MyPet\) owner UUIDs are no problem as long as the player name or the Mojang UUID are the same.

Please make backups of your databases before you try to merge them!

```text
<?php

$database_1 = "mypet";
$database_2 = "mypet_2";
$user = "root";
$password = "";
$server = "localhost";
$port = 3306;

//----------------------------------------------------------------------------------------------------------------------
// Do not change anything after this
//----------------------------------------------------------------------------------------------------------------------


$mysqli = new mysqli($server, $user, $password, "", $port);

/* check connection */
if ($mysqli->connect_errno) {
    printf("Connect failed: %s\n", $mysqli->connect_error);
    exit();
}

$version_1 = 0;
$version_2 = 0;

if ($result_info = $mysqli->query("SELECT version FROM $database_1.info")) {
    while ($row = $result_info->fetch_assoc()) {
        $version_1 = $row["version"];
    }
} else {
    echo "Version in $database_1.info table not found!";
    exit();
}
if ($result_info = $mysqli->query("SELECT version FROM $database_2.info")) {
    while ($row = $result_info->fetch_assoc()) {
        $version_2 = $row["version"];
    }
} else {
    echo "Version in $database_2.info table not found!";
    exit();
}

if($version_1 != $version_2) {
    echo "Database versions not equal -> $version_1 != $version_2";
    exit();
}


$uuid_map = [];

$updated_mypets = 0;

if ($result_players_1 = $mysqli->query("SELECT * FROM $database_1.players")) {
    //printf("Select returned %d rows.`<br>`", $result_players_1->num_rows);


    while ($row_players_1 = $result_players_1->fetch_assoc()) {

        // find duplicates
        //printf("find duplicates --------------------------------------------------------------`<br>`");
        $query = "SELECT * FROM $database_2.players WHERE ";
        $online_uuid = $row_players_1["mojang_uuid"];
        if($online_uuid != null) {
            $query .= "mojang_uuid LIKE \"" . $online_uuid . "\"";
        }
        $name = $row_players_1["name"];
        if($name != null) {
            if($online_uuid != null) {
                $query .= " OR ";
            }
            $query .= "name LIKE \"" . $name . "\"";
        }
        $query .= ";";

        //printf("Query: " . $query . "`<br>`");

        if ($result_players_2 = $mysqli->query($query)) {

            if($result_players_2->num_rows > 0) {
                //printf("Select returned %d rows.`<br>`", $result_players_2->num_rows);
            }


            while ($row_players_2 = $result_players_2->fetch_assoc()) {
                $uuid_map[$row_players_1["internal_uuid"]] = $row_players_2["internal_uuid"];

                $qq = "UPDATE $database_2.pets SET owner_uuid=\"" . $row_players_1["internal_uuid"] . "\" WHERE owner_uuid=\"" . $row_players_2["internal_uuid"] . "\"";
                //printf("Query: %s`<br>`", $qq);
                $mysqli->query($qq);

                if($mysqli->affected_rows > 0) {
                    //printf("Updated %d pets.`<br>`", $mysqli->affected_rows);
                    $updated_mypets += $mysqli->affected_rows;
                }
            }
            $result_players_2->close();
        }

        // delete duplicates
        //printf("delete duplicates --------------------------------------------------------------`<br>`");

        $query = "DELETE FROM $database_2.players WHERE ";
        $online_uuid = $row_players_1["mojang_uuid"];
        if($online_uuid != null) {
            $query .= "mojang_uuid LIKE \"" . $online_uuid . "\"";
        }
        $name = $row_players_1["name"];
        if($name != null) {
            if($online_uuid != null) {
                $query .= " OR ";
            }
            $query .= "name LIKE \"" . $name . "\"";
        }
        $query .= ";";

        //printf("Query: " . $query . "`<br>`");
        $mysqli->query($query);
        if($mysqli->affected_rows > 0) {
            //printf("Deleted %d duplicate players.`<br>`", $mysqli->affected_rows);
        }

        // copy non duplicates

    }
    $result_players_1->close();
}


foreach ($uuid_map as $key => $value) {
    echo "$value -> $key`<br>`";
}

printf("Deleted %d duplicate players.`<br>`", count($uuid_map));
printf("Updated %d pets.`<br>`", $updated_mypets);

$query = "INSERT INTO $database_1.players SELECT * from $database_2.players";

$mysqli->query($query);

if($mysqli->affected_rows > 0) {
    printf("Inserted %d players.`<br>`", $mysqli->affected_rows);
}

$query = "INSERT INTO $database_1.pets SELECT * from $database_2.pets";
$mysqli->query($query);

if($mysqli->affected_rows > 0) {
    printf("Inserted %d pets.`<br>`", $mysqli->affected_rows);
}
```

