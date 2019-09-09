**University of Pennsylvania, CIS 565: GPU Programming and Architecture,
Project 1 - Flocking**

 ![FLOCKUP](/images/flockup.PNG)
 ![Flocking Boiiiiiids](/images/flocking.gif)


* Davis Polito
  *  [https://github.com/davispolito/Project0-Getting-Started/blob/master]()
* Tested on: Windows 10, i7-8750H @ 2.20GHz 16GB, GTX 1060

 **For each implementation, how does changing the number of boids affect performance? Why do you think this is?**

 ![Graph of Num Boid vs. fps (visualize)](/images/boidgraph.PNG)
 ![Graph of Num Boid vs. fps (no-visual)](/images/novisual.PNG)

For the Naive implementation low boid counts outperform the more efficient implementations due to reduced overhead for cell checking and array management. Scattered implementation performs significantly better as the boids increase. Coherent implementation performs even better than scattered due to the contiguous memory accesses.o

**For each implementation, how does changing the block count and block size affect performance? Why do you think this is?**

 ![Graphing Block Size vs. fps](/images/blockgraph.PNG)
Block count has little affect on the algorithms. Due to warp size of 32 that is used I kept all of the blocks on multiples of 32 when i did testing such that we didn't have any unused threads.Performance improvements were not of note. 

**For the coherent uniform grid: did you experience any performance improvements with the more coherent uniform grid? Was this the outcome you expected? Why or why not?**
There were massive improvements at higher boid counts as expected. I expected this becuase the contiguous accesses are much better and quicker due to "cache coherency".


**Did changing cell width and checking 27 vs 8 neighboring cells affect performance? Why or why not? Be careful: it is insufficient (and possibly incorrect) to say that 27-cell is slower simply because there are more cells to check!**

The larger the cell width the higher the chance that checked boids are not within the neighborhood distance of the current boid. This causes slowdown as we get to more cells.

