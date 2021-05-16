# Randomly Generated Dungeon

I created a minigame which is basically a randomly generated dungeon. The goal is to find a set amount of coins in the dungeon and then find a portal to escape the dungeon.

## How is the dungeon created?

There are two things happening when the map of the dungeon is being created:

	-Rooms are generated with random walls.
    
    -There exista a path between the start and the end and all the coins lie on that path.

### Generating Rooms

Before going into how a map is created I am going to talk about what a room consists
