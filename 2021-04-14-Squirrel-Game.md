## Squirrel Game - Generating Background and random Objects within 

I was tasked the job too generate the background and randomnly place environmental objects (Grass, Flowers) on the background.

Before going into the implementions I wanted to talk about the challenges of randomly placing things. When you use the random function, your objects tend to cluster together and to avoid that I tweaked how my random values would work. I implemented two methods for placing grass and flowers.

For placing the grass I divided the canvas into four quadrants like a cartesian plane. Then using a while loop I made sure that there were only two peices/objects of grass in each quadrant of the canvas. I accomplished that with the help of a while loop which kept track of how many peices of grass were in each quadrant usinf if statements. 
I chose this method because naturally grass sometimes looks good clustered but it doesn't look good when there is too much clustering. So in each quadrant the grass may randomly cluster or not but there will be a limit to how much it will which in this case is two grass peices per quadrant.


