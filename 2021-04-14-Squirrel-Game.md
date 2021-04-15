## Squirrel Game - Generating Background and random Objects within 

I was tasked the job too generate the background and randomnly place environmental objects (Grass, Flowers) on the background.

Before going into the implementions I wanted to talk about the challenges of randomly placing things. When you use the random function, your objects tend to cluster together and to avoid that I tweaked how my random values would work. I implemented two methods for placing grass and flowers.

For placing the grass I divided the canvas into four quadrants like a cartesian plane. Then using a while loop I made sure that there were only two peices/objects of grass in each quadrant of the canvas. I accomplished that with the help of a while loop which kept track of how many peices of grass were in each quadrant usinf if statements. 
I chose this method because naturally grass sometimes looks good clustered but it doesn't look good when there is too much clustering. So in each quadrant the grass may randomly cluster or not but there will be a limit to how much it will which in this case is two grass peices per quadrant.

Pseudocode:
	
    q1,q2,q3,q4: represent the four quadrants
	while (q1 + q2 + q3 + q4 < 8) {
     randX = random(width);
     randY = random(height);
     if (randX > 0 && randX < width / 2 && randY > 0 && randY < height / 2 && q1 < 2) {
      q1++;
      g[gCount] = new Grass(randX, randY)
      gCount++;
     }
     if (randX > width / 2 && randX < width && randY > 0 && randY < height / 2 && q2 < 2) {
      q2++;
      g[gCount] = new Grass(randX, randY)
      gCount++;
     }
     if (randX > 0 && randX < width / 2 && randY > height / 2 && randY < height && q3 < 2) {
      q3++;
      g[gCount] = new Grass(randX, randY)
      gCount++;
     }
     if (randX > width / 2 && randX < width && randY > height / 2 && randY < height && q4 < 2) {
      q4++;
      g[gCount] = new Grass(randX, randY)
      gCount++;
     }
    }


