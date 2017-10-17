[//]: # (Image References)
[flowchart]: ./img/flowchart.png

# Unscented Kalman Filter (Self-Driving Car Engineer Nanodegree Program)

In this project utilize an Unscented Kalman Filter to estimate the state of a moving object of interest with noisy lidar and radar measurements. Passing the project requires obtaining RMSE values that are lower that the tolerance outlined in the project reburic. 

This project involves the Term 2 Simulator which can be downloaded [here](https://github.com/udacity/self-driving-car-sim/releases)

This repository includes two files that can be used to set up and intall [uWebSocketIO](https://github.com/uWebSockets/uWebSockets) for either Linux or Mac systems. For windows you can use either Docker, VMware, or even [Windows 10 Bash on Ubuntu](https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/) to install uWebSocketIO. Please see [this concept in the classroom](https://classroom.udacity.com/nanodegrees/nd013/parts/40f38239-66b6-46ec-ae68-03afd8a601c8/modules/0949fca6-b379-42af-a919-ee50aa304e6a/lessons/f758c44c-5e40-4e01-93b5-1a82aa4e044f/concepts/16cf4a78-4fc7-49e1-8621-3450ca938b77) for the required version and installation scripts.

Once the install for uWebSocketIO is complete, the main program can be built and ran by doing the following from the project top directory.

1. mkdir build
2. cd build
3. cmake ..
4. make
5. ./UnscentedKF

Tips for setting up your environment can be found [here](https://classroom.udacity.com/nanodegrees/nd013/parts/40f38239-66b6-46ec-ae68-03afd8a601c8/modules/0949fca6-b379-42af-a919-ee50aa304e6a/lessons/f758c44c-5e40-4e01-93b5-1a82aa4e044f/concepts/23d376c7-0195-4276-bdf0-e02f1f3c665d)



## Other Important Dependencies
* cmake >= 3.5
  * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1 (Linux, Mac), 3.81 (Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools](https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./UnscentedKF` Previous versions use i/o from text files.  The current state uses i/o
from the simulator.

---

## 1. Unscented Kalman Filter Algorithmus

![alt Unscented Kalman Filter Algorithmus][flowchart]

---
## 2. Project Implementation

I mostly followed the instructions from the UKF class materials. The only special cases are process noise and covariance parameters and initializations.

### Noise parameters

|    Noise   |    Value      | 
|:----------:|:-------------:| 
|  std_a     |      3.0      | 
| std_yawd   |      0.5      | 

---
## 3. Results

####   px, py, vx, vy output coordinates must have an RMSE<= [.09, .10, .40, .30] when using the file: "obj_pose-laser-radar-synthetic-input.txt"
* I ran my algorithm against two data sets. On Data set 1 I have recorded values and analyzed them using python script from `CarND-Mercedes-SF-Utilities`. There is a very powerfull tool to visalize the data [plot.ly](https://plot.ly). Feel free too test it.

|  | Dataset 1                     | Dataset 2                 |
|-----|---------------------------|---------------------------|
| RMSE | px: 0.0964425, py: 0.0852905, vx: 0.415426, vy: 0.431636 | px: 0.0725678, py: 0.0964738, vx: 0.421634, vy: 0.493199 |
| Track (klick to watch) | [![E](https://img.youtube.com/vi/LqPwKTU3QyY/0.jpg)](https://youtu.be/LqPwKTU3QyY "Dataset 1")| [![E](https://img.youtube.com/vi/NxXlZ3zOjZs/0.jpg)](https://youtu.be/NxXlZ3zOjZs "Dataset 2") |
| Analyse (klick for details) | [![E](data_1.png)](https://plot.ly/~kulrich/1.embed "Dataset 1") | [![E](data_2.png)](https://plot.ly/~kulrich/3.embed "Dataset 2") |