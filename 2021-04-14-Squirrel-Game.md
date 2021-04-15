## Squirrel Game - Generating Background and random Objects within 

//LINK TO FINAL PROJECT

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
  
Example:

![sg1.JPG]({{site.baseurl}}/sg1.JPG)

Now For the flowers I did something different. Since my grass would appear a bit clustered I wanted my flowers to not cluster. So I made sure that each flower was atleast 100 pixels apart from each other. TO implement that I made a while loop that would stop until 10 flowers had been created and inside the while loop I had another loop that made sure that the current flowers position was atleast 100 pixels from other flowers and if it was not it choose another set of random positions and repeat the process.

Pseudocode:

	fl[0] = new Flower(randX, randY);
    fCount = 1;
    while (fCount < 10) {
     randX = random(width);
     randY = random(height);
     for (let i = 0; i < fl.length; i++) {
      if (dist(fl[i].x, fl[i].y, randX, randY) < 100) {
       check = false;
      }
     }
     if (check == true) {
      fl[fCount] = new Flower(randX, randY)
      fCount++;
     }
    check = true;
 	}
   
Example:

![sg2.JPG]({{site.baseurl}}/sg2.JPG)

Now I combined these two components and made a semi-random background.

Combined Example:

![sg3.JPG]({{site.baseurl}}/sg3.JPG)
