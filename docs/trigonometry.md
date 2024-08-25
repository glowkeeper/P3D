# Trigonometry

Trigonometry is the mathematics of triangles. However, it's much more than that besides, as it forms the basis of many behaviours of 3D objects, including the description of shapes, motion, angular velocity, rotations and transformations. At the basis of trigonometry are angles.

## Angles

An angle is formed by the space between two intersecting lines that join at a point.

![angle](./images/angle.png)

One unit of measurement of angles is _degrees_, which describes circularity, or rotation.

![Circular Angle](./images/circularAngle.png)

A full rotation, which would bring you back to face in the same direction, is 360°. A half-circle is 180°. A quarter-circle, or right angle, is 90°. Below shows a square rotated 45°, using it's centre as its pivot point.

![Square Rotated](./images/docs/images/square45.webp)

Radians are another unit of trigonometric measurement. They are defined by the ratio of the length of the arc of a circle (a segment of the circle’s circumference) to the radius of that circle. One radian is the length at which that ratio equals 1.

![Radian](./images/docs/images/radian.png)

Radians have a strong relationship to Pi (π), which is an irrational number that is defined as the ratio of a circle’s circumference (the distance around the outside of the circle) to its diameter (a straight line that passes through the circle’s center). A full circle (360°) is equivalent to 2π radians. Hence, 180° is π radians, and 90° is π/2 radians. The formula to convert from degrees to radians is as follows:

radians = (2π x degrees) / 360

Although radians are not as familiar to many as degrees, they are often useful as they can make some calculations much easier because they associate angle and length. For example, to find the speed of a vehicle in metres per second you can just multiply the radius of one of its wheels by the number of radians it turns per second. So if the wheel has a radius of two metres and turns at six radians per second the speed is 12 metres per second. Additionally, their association with Pi (π) makes radians a somewhat more intuitive unit for graphing, performing calculus and modelling some spherical geometry. Hence, Radians are a useful concept to grasp!

## Trigonometric Functions



## Rotation

Rotation, or angular motion, is movement about an angle with respect to time, and just as linear motion uses velcotiy to show the rate at which an object’s position changes over time, angular motion uses angular velocity to show the rate at which an object’s angle changes over time. By extension, angular acceleration describes changes in an object’s angular velocity.

For linear motion, we have acceleration -> velocity -> position, hence:

velocity = velocity + acceleration, and
position = position + velocity

Similarly, for angular motion, we have:

angular velocity = angular velocity + angular acceloration
angle = angle + angular velocity

Angular velocity is a three dimensional vector ω (the lowercase Greek letter omega). It has a direction along the axis of rotation and a magnitude equal to the radians per per unit of time spun by the body.

So given the position vector r of a moving body in three-dimensional space, its angular velocity is a vector whose magnitude is the rate at which r rotates about an angle, and whose direction is perpendicular to the plane in which r rotates about an angle at velocity v. However, as there are two directions perpendicular to any plane, the convention is that the unit vector ω is perpendicular to the plane spanned by r and v, so that the right-hand rule is satisfied and the instantaneous direction of angular displacement is counter-clockwise when looking down on ω:

![Angular Velocity](./images/angularVelocity.png)

Using the cross product, we have:

ω = r x v

Negating the angular velocity is equivalent to changing the direction of rotation about the axis.


