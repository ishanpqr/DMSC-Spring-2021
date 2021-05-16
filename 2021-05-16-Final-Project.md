# Randomly Generated Dungeon

I created a minigame which is basically a randomly generated dungeon. The goal is to find a set amount of coins in the dungeon and then find a portal to escape the dungeon.

## How is the dungeon created?

There are two things happening when the map of the dungeon is being created:

   -Rooms are generated with random walls.
    
   -There exists a path between the start and the end and all the coins lie on that path.

### _Generating Rooms_

Before going into how a map is created we need to go into how each room in the map is created.

A room consists of:

   -**Walls**: This is done with 4 T/F variables corresponding to each side of a room. For example if the          North side variable is marked as True then there will be a wall on the the North side of the room.
   
   -**Background Tile**: I have three images that serve as background tiles. Each time a room is created          one of those images is randomly chosen to be the background tile. This tile represents the terrain          of the dungeon room.
