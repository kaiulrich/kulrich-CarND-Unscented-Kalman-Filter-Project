[//]: # (Image References)
[flowchart]: ./img/flowchart.png

# Unscented Kalman Filter Project

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
* NIS plots show the NIS is mostly below 95% line, which shows the filter is very consistent. The parameters are set properly so that we correctly estimate the uncertainty of the system.

|  | Dataset 1                     | Dataset 2                 |
|-----|---------------------------|---------------------------|
| RMSE | px: 0.0752735, py: 0.0826372, vx: 0.388804, vy: 0.235533 | px: 0.0744176, py: 0.0740475, vx: 0.383008, vy: 0.227252 |
| Track (klick to watch) | [![E](https://img.youtube.com/vi/NAC67y9UfU0/0.jpg)](https://youtu.be/NAC67y9UfU0 "Dataset 1")| [![E](https://img.youtube.com/vi/losWfdkJ2Cc/0.jpg)](https://youtu.be/losWfdkJ2Cc "Dataset 2") |
| Analyse (klick for details) | [![E](img/plot_1.png)](https://plot.ly/~kulrich/5.embed "Dataset 1") | [![E](img/plot_2.png)](https://plot.ly/~kulrich/11.embed "Dataset 2") |
| NIS Radar (klick for details) | [![E](img/nis_radar_1.png)](https://plot.ly/~kulrich/23.embed "Dataset 1") | [![E](img/nis_radar_2.png)](https://plot.ly/~kulrich/27.embed "Dataset 2") |
| NIS Laser (klick for details) | [![E](img/nis_laser_1.png)](https://plot.ly/~kulrich/25.embed "Dataset 1") | [![E](img/nis_laser_2.png)](https://plot.ly/~kulrich/29.embed "Dataset 2") | 