# PID Controller Project

Self-Driving Car Engineer Nanodegree Program

---

## Dependencies

* cmake >= 3.5
 * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1(mac, linux), 3.81(Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools]((https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)
* [uWebSockets](https://github.com/uWebSockets/uWebSockets)
  * Run either `./install-mac.sh` or `./install-ubuntu.sh`.
  * If you install from source, checkout to commit `e94b6e1`, i.e.
    ```
    git clone https://github.com/uWebSockets/uWebSockets 
    cd uWebSockets
    git checkout e94b6e1
    ```
    Some function signatures have changed in v0.14.x. See [this PR](https://github.com/udacity/CarND-MPC-Project/pull/3) for more details.
* Simulator. You can download these from the [project intro page](https://github.com/udacity/self-driving-car-sim/releases) in the classroom.

There's an experimental patch for windows in this [PR](https://github.com/udacity/CarND-PID-Control-Project/pull/3)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./pid`. 

Tips for setting up your environment can be found [here](https://classroom.udacity.com/nanodegrees/nd013/parts/40f38239-66b6-46ec-ae68-03afd8a601c8/modules/0949fca6-b379-42af-a919-ee50aa304e6a/lessons/f758c44c-5e40-4e01-93b5-1a82aa4e044f/concepts/23d376c7-0195-4276-bdf0-e02f1f3c665d)

## Reflexion

First of all, synthetizing how each controller influence on the PID controller, P-Controller gives a proportional feedback for the system (in this case the car). A correction on steering angle is applied and it is proportional to the difference between
desired value and measured value.
For a PD-Controller, the D part of the controller damp the response and make the controller smoothier. Mathematically, it's proportional to rate of change of the control error.
For a PID-Controller, the I part accumulate over time the difference between desired value and measured value to eliminate the residual error.

I applied a manual tuning and I started the tuning process by the P-Controller. To calculate the controller error, I used the squared of the difference between the measured and desired values (squared of the CTE). 

|   Kp   	|  Ki 	|  Kd  	| cte_error 	|
|:------:	|:---:	|:----:	|:---------:	|
| -0.250 	| 0.0 	| -1.0 	| 0.315487  	|
| -0.235 	| 0.0 	| -1.0 	| 0.299376  	|
| -0.220 	| 0.0 	| -1.0 	| 0.22905   	|
| -0.205 	| 0.0 	| -1.0 	| 0.256276  	|
| -0.190 	| 0.0 	| -1.0 	| 0.279779  	|
| -0.125 	| 0.0 	| -1.0 	| 0.397308  	|
