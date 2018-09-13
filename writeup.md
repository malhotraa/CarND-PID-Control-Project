# Writeup

## Compilation

### Your code should compile.

Code compiles fine using cmake/make without any warnings or errors.

## Implementation

### The PID procedure follows what was taught in the lessons.

The PID implementation is in [PID.cpp](./src/PID.cpp). The [PID::UpdateError](./src/PID.cpp#L24) method calculates proportional, integral and derivative errors and the [PID::TotalError](./src/PID.cpp#L31) calculates the total error using Kp, Ki, Kd coefficients.

## Reflection

### Describe the effect each of the P, I, D components had in your implementation.

- The proportional portion of the controller tries to steer the car toward the center line (against the cross-track error). If used alone, the car overshoots the centre line and goes off road or keeps wobbling around the center line. Example video using only proportianl component [p-only.avi](./vids/p-only-.avi).

- The integral portion helps to eliminate a possible steering bias in the controlled system that could prevent the error from settling to zero. If used alone, it makes the car to go in circles. In the case of the simulator, no bias is present. Example video using only integral component [i-only.avi](./vids/i-only.avi).

- The differential portion helps to counteract the proportional trend to overshoot the center line by smoothing the approach to it. Example video using only differential component [d-only.avi](./vids/d-only.avi).

### Describe how the final hyperparameters were chosen.

The parameters were chosen manually by trial and error. First, I checked to ensure the car can drive straight with all parameters set to zero. Then I added only proportional component and the car start following the road but it would overshoot the center line and eventually wobble off the road. Then I added the differential component to try to fix the overshooting. Then I added a tiny integral part to remove any steering bias. Finally these params were manually tuned so that the car would travel smoothly around the lap without too much wobbling. Final parameters were [Kp: 0.15, Ki: 0.001, Kd: 2.5].

## Simulation

### The vehicle must successfully drive a lap around the track.

Video with the final parameters [all-params.avi](./vids/all-params.avi).
