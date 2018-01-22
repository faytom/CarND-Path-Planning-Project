# CarND-Path-Planning-Project Writeup report
Self-Driving Car Engineer Nanodegree Program
### Model
Most of the code was adopted from Project Walkthrough, Q&A video and [pabloelizalde](https://github.com/pabloelizalde/CarND-Path-Planning-Project). From the current sensor fusion and current car physical status. It is able to predict car's future position in 30, 60 and 90 meters ahead. Based on theres predicted waypoints, the future car trajectory can be calculated by spline function. The car's speed will be reduced if it is getting too close to the car ahead, which in my case is 30 meters.

### Path generation
The path is generating by projecting car's future waypoints 30m 60m and 90m ahead in Frenet coordinate, and converting back to x y coordinate. Then the smooth trajectory is calculated by spline algorithm. The control setpoints will be evenly chosen by interpolating the spline equation in order to meet speed and acceleration constraint.

### Lane change
The lane changing algorithm is based on state machine algorithm. There are totaly three states: Keep Lane, Lane Change Left and Lane Change Right. Each time the possible states and the associated cost will be calculated accordingly. The cost will consider the car's speed, distance to the closest car ahead and behind and lane changing penalty. This algorithm will run effectively for the most of the cases, however, for some complicated situation where multiple cars in parallel it will fail to take the optimal lane.

### Result
The result is shown the following:
[result](./result.png)