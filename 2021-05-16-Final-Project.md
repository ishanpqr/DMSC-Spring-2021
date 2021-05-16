# Randomly Generated Dungeon

I created a minigame which is basically a randomly generated dungeon. The goal is to find a set amount of coins in the dungeon and then find a portal to escape the dungeon.

## How is the dungeon created?

There are two things happening when the map of the dungeon is being created:

   -Rooms are generated with random walls.
    
   -There exists a path between the start and the end and all the coins lie on that path.

### _**Generating Rooms**_

Before going into how a map is created we need to go into how each room in the map is created.

A room consists of:

   -**Walls**: This is done with 4 T/F variables corresponding to each side of a room. For example if the          North side variable is marked as True then there will be a wall on the the North side of the room.
   
   //wall
   
   -**Background Tile**: I have three images that serve as background tiles. Each time a room is created          one of those images is randomly chosen to be the background tile. This tile represents the terrain          of the dungeon room.
   
   -**Objects**: I have a small pool of objects: 3 types of trees, 3 types of flowers, boulder. Each time a        room is created these objects are randomly placed on the tile making sure that they are not too            close to each other. One extra feature I added is that if the background tile is a "Desert type"            then only boulders are generated and nothing else.
   
   -**Coin**: I have T/F variable that if True then a coin exists in the Room and if False then no coin          exists. If a coin exists then I display that coin. The decision whether I put a coin or not in aroom        or how many coins I should put is handled outside the class.
   
   //combined pic
   
   -**Debug Information**: This info is added to a room has no visual impact on the room. It solely used        for debugging. I call this information the "Tag" of a room. I will explain this in detail in the            "Generating Map" section. Another peice of information stored is how many total rows and columns we        have in our map. All this information is provided to the class with the help of the constructor.

These are the four main peices that make up my Room class. Since most of the things are randomly generated the only information needed to instantiate a Room object is: "Tag" of the room and the "Total number of rows and columns in the dungeon". The reason we need this information will be described in the next section "Generating Map".

### _**Generating Map**_


   
  
