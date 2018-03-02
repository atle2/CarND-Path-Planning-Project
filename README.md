# CarND-Path-Planning-Project
Self-Driving Car Engineer Nanodegree Program

![Driving](images/driving.png)

### Goals
In this project your goal is to safely navigate around a virtual highway with other traffic that is driving +-10 MPH of the 50 MPH speed limit. You will be provided the car's localization and sensor fusion data, there is also a sparse map list of waypoints around the highway. The car should try to go as close as possible to the 50 MPH speed limit, which means passing slower traffic when possible, note that other cars will try to change lanes too. The car should avoid hitting other cars at all cost as well as driving inside of the marked road lanes at all times, unless going from one lane to another. The car should be able to make one complete loop around the 6946m highway. Since the car is trying to go 50 MPH, it should take a little over 5 minutes to complete 1 loop. Also the car should not experience total acceleration over 10 m/s^2 and jerk that is greater than 10 m/s^3.

#### The map of the highway is in data/highway_map.txt
Each waypoint in the list contains  [x,y,s,dx,dy] values. x and y are the waypoint's map coordinate position, the s value is the distance along the road to get to that waypoint in meters, the dx and dy values define the unit normal vector pointing outward of the highway loop.

The highway's waypoints loop around so the frenet s value, distance along the road, goes from 0 to 6945.554.

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./path_planning`.

### Compilation

![Compiled](images/make.png)

The code compiles without errors without any changes to CMakeLists.txt

## Valid Trajectories
### The car is able to drive at least 4.32 miles without incident.

![Limit](images/432.png)

### The car drives according to the speed limit.

The car drives under the posted speed limit.

### Max Acceleration and Jerk are not Exceeded.

The max acceleration and jerk are under control.

### Car does not have collisions.

There are no collisions after 4.32 miles. 

### The car stays in its lane, except for the time between changing lanes.

The car never leaves its lane except to change lanes in a quick and smooth motion.

### The car is able to change lanes

The car changes lanes when there is a slower vehicle in front of it detected and there are no cars to its sides.

## Reflection

The first thing the code does to begin the path-planning is to determine where the other cars are. Lines 261-277 in /src/main.cpp determine which lanes the other vehicles are in. Afterwards, whether or not they are within 30 meters of our vehicle is determined. If a vehicle is going slowly in front of our car, it will check whether or not a car is in the adjacent lanes. It will then either change lanes to an open lane or slow down.

In lines 374-384 of main.cpp it creates waypoints 30 meters in front of the vehicle based on the current lane. In order to smoothly drive the car, a spline is created using the points generated from getXY. To make the spline calculations easier, the coordinates are shifted and transformed beforehand to local car coordinates. 

## Dependencies

* cmake >= 3.5
 * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools]((https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)
* [uWebSockets](https://github.com/uWebSockets/uWebSockets)
  * Run either `install-mac.sh` or `install-ubuntu.sh`.
  * If you install from source, checkout to commit `e94b6e1`, i.e.
    ```
    git clone https://github.com/uWebSockets/uWebSockets 
    cd uWebSockets
    git checkout e94b6e1
    ```
