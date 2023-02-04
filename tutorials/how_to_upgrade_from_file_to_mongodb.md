# File to MongoDB

## Setup

1. Put the plugin file into you plugin folder and restart the server so that the plugin can generate the new config options.
2. download this jar file \([mongo-java-driver-3.12.11.jar](https://search.maven.org/remotecontent?filepath=org/mongodb/mongo-java-driver/3.12.11/mongo-java-driver-3.12.11.jar)\) and put it into the MyPet folder.
3. Set the `Type` option under `Repository` to `MongoDB`.
4. If you have an old `My.Pet` file you want to import set `ConvertFrom` option under `Repository` to `NBT`.
5. replace the credentials under `MongoDB` with your own.
6. restart the server once again. It should create the tables and convert the old `My.Pets` file to database .entires.
7. You can run your server like normal but all servers you use can now access the pets from one database!

