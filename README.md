**University of Pennsylvania, CIS 565: GPU Programming and Architecture,
Project 1 - Flocking**

* SOMANSHU AGARWAL
  * [LinkedIn](www.linkedin.com/in/somanshu25)
* Tested on: (TODO) Windows 22, i7-2222 @ 2.22GHz 22GB, GTX 222 222MB (Moore 2222 Lab)

### OBJECTIVE

The main motive of the project is to visualize Boids flocking and do the performance analysis on three implementation ways of flocking: naive, scattered and coherent search. The search was to find the relevant neigbours of each boid and its position and velocity is updates with respect to its neighbours thorugh the three rules: adhesion, dodging and cohesion. The brief implemetation details of these 3 ways and the performance analysis is given below.

## 1. Naive Implementation

In the naive implementation, got a particluar boid, we are searching all the other boids and then selecting the relevant neighbours for the position and velocity update of the boid. This for every boid, we are checking other N-1 boids, which is time consuming and inefficient when N is large. 

For the rest of the 2 implementation, we are creating a grid system in which we are enclosing the whole space in a cube with grid cell width setting by the user according to the requirements. With changing the gird cell width, the grid resoltion and the grid cell count will vary and its impact on the performance is also studies in this project. By using the grid system, we are labelling each boid to a grid cell index.

## 2. Scattered 

In this implementation, we are limiting our search for the boids which are labelled in the cells of the neighbourhood distance we need to check. Thus, we are checking those grid cells which could be enclosed in the sphere inside the cube with the radius as the neighbouring distance. The number of cells enclosed would differ with the length of the grid cells. Having grid width of twice the maximum neighbourhood distance will take 8 cells while the length equal to maximum neighbouring dustance will take 27 cells. For making sure we are selecting those cells which are enclised in the grid cells, we are sorting the array of boid indexes with respect to the grid indexes labelled and then when we select the particular cell index, we get the range of boids we need to check.

## 3. Coherent

In this implememntation, we do further optimization in our code by reshuffling the position and velocity boid data with the sorted nboid particluar array indexes so that the memory access of the boid data is also contgous and there will be more cache hits and less misses, which would save the runtime. Thus, we only need the start and end indexes of the boids which are present in the cell to access the boid data rather than the boid array indexes we require in our scattered implementation.

# Performance Analysis:

Here are ther graphs showing the frame rate per second of the three implementations when we change the number of boids in the siimulation:




