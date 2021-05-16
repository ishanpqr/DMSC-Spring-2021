# Randomly Generated Dungeon

I created a minigame which is basically a randomly generated dungeon. The goal is to find a set amount of coins in the dungeon and then find a portal to escape the dungeon.

## How is the dungeon created?

There are two things happening when the map of the dungeon is being created:

   -Rooms are generated with random walls.
    
   -There exists a path between the start and the end and all the coins lie on that path.

### **Generating Rooms**

Before going into how a map is created we need to go into how each room in the map is created.

A room consists of:

   -**Walls**: This is done with 4 T/F variables corresponding to each side of a room. For example if the          North side variable is marked as True then there will be a wall on the the North side of the room.
   
   //wall
   
   -**Background Tile**: I have three images that serve as background tiles. Each time a room is created          one of those images is randomly chosen to be the background tile. This tile represents the terrain          of the dungeon room.
   
   -**Objects**: I have a small pool of objects: 3 types of trees, 3 types of flowers, boulder. Each time a        room is created these objects are randomly placed on the tile making sure that they are not too            close to each other. One extra feature I added is that if the background tile is a "Desert type"            then only boulders are generated and nothing else.
   
   -**Coin**: I have T/F variable that if True then a coin exists in the Room and if False then no coin          exists. If a coin exists then I display that coin. The decision whether I put a coin or not in aroom        or how many coins I should put is handled outside the class.
   
   //combined pic
   
   -**Debug Information**: This info is added to a room has no visual impact on the room. It solely used        for debugging. I call this information the "Tag" of a room. I will explain this in detail in the            "Generating Map" section. Another peice of information stored is how many total rows and columns we        have in our map. All this information is provided to the class with the help of the constructor.

These are the five main peices that make up my Room class. Since most of the things are randomly generated the only information needed to instantiate a Room object is: "Tag" of the room and the "Total number of rows and columns in the dungeon". The reason we need this information will be described in the next section "Generating Map".

### **Generating Map**

The map generation is handled in the "setup" part since I only want to create the map once. I start by creating an empty 2-dimensional array. Then I proceed to fill each space in that array with a Room object.

-**_Tag_**: I wanted a way to keep track of my room objects other than by just looking it up in the array so I gave each object in the Room class a specific tag that can be used to differentiate them between each other. The image below will give an idea on how I chose the tags.

//Image

Now while I am creating a new object and putting the Room object in the array, at the same time I run my createRoom() method int the Room class which creates the room.... more specifically it creates the walls of the room.

-**_createRoom()_**: This method randomly chooses the number of the sides it wants to put walls on and then it puts those many walls on random sides. This is the method that chooses which of the 4 T/F variables I mentioned in the "Generating Rooms" section should be True. Another thing this method needs to take care of is if the room is a border room / edge room of the map then it must have walls such that the player cannot get out of the room. This is where our "Debug Information" comes into play and helps us with that. The image below will help in understanding the idea behind this.

//Image

-**_Checking Neighbors_**: After the map has been generated I run through the Map/Array again to make sure that neigbouring rooms have the appropriate walls against each other. This means that, for example if Room 'A' is a neighbor with Room 'B' and Room 'B' is to the right of Room 'A'. If Room 'A' has a right wall then Room 'B' must have a left wall and vice versa. This is the idea behind what "checking neighbors" means.

Now we have a map with rooms with proper walls. But there is one more thing we need to do, we need to make sure that when we randomly choose our 'Start' and 'End' rooms we need to makes sure A path exists between both of them and this was the most challenging part of the project.

-**_Creating a path_**: In this part the code starts at the 'Start room' then it looks at each of its possible neighbors/Rooms (4 neigbors max) and randomly chooses one of them to include in its path and it keeps doing that until it reaches the 'End room'. This process is very taxing and makes the initiallization of the game very slow. To improve its speed I made sure that the path doesnt backtrack too much. While the code is making its own path it also randomly chooses to put a coin in a room in the path which makes sure that all the coins are reachable.

//Image

After these three steps the map is created, rooms are filled and decorated, coins are placed and the dungeon is ready to be explored. Wait we forgot an important key aspect "The Player".

### The Player

The Player only needs to do two things:

-**_Move_**: The player uses basic code to move. If the "W" key is pressed then the player goes up and so on. But there is another thing attached to this Move method in the Player class and that is the Player character display. I approached this in a very rudimentary way. I took 5 images Player walking up,down,left,right and Player rest then I attached those images with the respective key. So for example if the "W" key is pressed then the 'Player walking up image' is displayed or if no key is pressed the the Player rest image' is displayed.

Now that the player can move and it also looks good moving we need to make sure that the player does not go where its not supposed and vice versa.


   
  
