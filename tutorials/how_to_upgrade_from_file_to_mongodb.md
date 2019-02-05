# File to MongoDB

### This feature is part of MyPet-Premium!

If you want to use a MongoDB database to store your pets please download the premium version of MyPet [here](https://www.spigotmc.org/resources/mypet-premium.17566/).

## Setup

First of all thank your for purchasing MyPet-Premium!

1. Put the plugin file into you plugin folder and restart the server so that the plugin can generate the new config options.
2. download this jar file \([mongo-java-driver-3.2.1.jar](https://search.maven.org/remotecontent?filepath=org/mongodb/mongo-java-driver/3.2.1/mongo-java-driver-3.2.1.jar)\) and put it into the MyPet folder.
3. Set the `Type` option under `Repository` to `MongoDB`.
4. If you have an old `My.Pet` file you want to import set `ConvertFrom` option under `Repository` to `NBT`.
5. replace the credentials under `MongoDB` with your own.
6. restart the server once again. It should create the tables and convert the old `My.Pets` file to database .entires.
7. You can run your server like normal but all servers you use can now access the pets from one database!

