# Trigonometry

Trigonometry is the mathematics of triangles. It forms the mathematical basis of many behaviours of objects, including the description of shapes, motion, angular velocity, rotations and transformations; hence, a basic understanding of trigonometry is essential if you want to work with circles, arcs, or lines and figure out the relationship between objects in a 3D spac, perhaps calculating the distances between them. At the heart of trigonometry are angles.

## Angles

An angle is formed by the space between two intersecting lines that join at a point.

![angle](./images/angle.png)

A unit of measurement of angles is _degrees_. The amount of degrees formed by an angle describes circularity, or rotation about the point of origin.

![Circular Angle](./images/circularAngle.png)

A full rotation is 360°. A half-circle is 180°. A quarter-circle, or right angle, is 90°. Below shows a square rotated 45°, using it's centre as its pivot point.

![Square Rotated](./images/docs/images/square45.webp)

Radians are another unit of trigonometric measurement. They are defined by the ratio of the length of the arc of a circle (a segment of the circle’s circumference) to the radius of that circle. One radian is the length at which that ratio equals 1.

![Radian](./images/docs/images/radian.png)

Radians have a strong relationship to Pi (π), which is an irrational number that is defined as the ratio of a circle’s circumference (the distance around the outside of the circle) to its diameter (a straight line that passes through the circle’s center). A full circle (360°) is equivalent to 2π radians. Hence, 180° is π radians, and 90° is π/2 radians. The formula to convert from degrees to radians is as follows:

radians = (2π x degrees) / 360

Although to many (at least in the UK) radians may not be as familiar as degrees, they are often useful as they relate angle to length, which can make some calculations much easier. For example, to find the speed of a vehicle in metres per second you can just multiply the radius of one of its wheels by the number of radians it turns per second. So if the wheel has a radius of two metres and turns at six radians per second the speed is 12 metres per second. Additionally, their association with Pi (π) makes radians a somewhat more intuitive unit for graphing, performing calculus and modelling some spherical geometry. 

## Trigonometric Functions

Trigonometry is based on the unit circle, which is a circle with the center at the origin (0,0 in a 2D space, and 0,0,0 in 3D) with the radius equal to 1.

![Trigonometric functions](./images/trigFunctions.png)

Since any triangle can be split into right-angled triangles whose opposite and adjacent sides form the axis of a graph, we can then use the functions found in trigonometry to allow us to better understand ratios, symmetry, transformations and rotations and much more besides.

The three main trigonometric functions are Sine, Cosine and Tangent, which are used to find an unknown side or angle of a triangle when two pieces of information are known (such as the length of two sides or the length of one side and an angle).  Sine, Cosine and Tangent are described by the mnemonic **SohCahToa** - take one of the non-right angles in the triangle - the adjacent side is the one touching that angle, the opposite side is the one not touching that angle, and the hypotenuse is the side opposite the right angle.

- **Soh**: sine(angle) = opposite/hypotenuse
- **Cah**: cosine(angle) = adjacent/hypotenuse
- **Toa**: tangent(angle) = opposite/adjacent

If **Soh** is used, then take sine of the unknown angle set equal to the opposite side divided by the hypotenuse.

- **Soh**: when the opposite side and the hypotenuse are known
- **Cah**: when the adjacent side and the hypotenuse are known
- **Toa**: when the opposite side and adjacent sides are known

For example, given the right-angled triangle below, how can we work out the length of the side labelled _x_?

![Sine example](./images/sinExample.png)

Since _x_ is opposite the hypotenuse, we need the Sine function, and we have:

sin(40) = x/8, giving:

8 * sin(40°) = x. Plugging sin(40°) into a calculator, we get ~0.6428, so:

8 * 0.6428 = 5.1424.

So the length of _x_ is ~5.1424. Similarly, we could work out the length of the remaining side - that is left as an exercise.

## Vectors and Trigonometry

Below describes a right-angled triangle in terms of a vector, v.

![Vectors and Trigonometry](docs/images/vectorsAndTrigonometry.webp)

The vector, v is the hypotenuse, and the components of the vector (x and y) are the opposite and adjacent sides of the triangle. Hence, the angle is an additional means for specifying the vector’s direction, because you move x steps right and y steps up. Viewed in this way, the trigonometric functions establish a relationship between the components of a vector and its direction and magnitude.

## Rotation

Rotation, or angular motion, is movement about an angle with respect to time, and just as linear motion uses velocity to show the rate at which an object’s position changes over time, angular motion uses angular velocity to show the rate at which an object’s angle changes over time. By extension, angular acceleration describes changes in an object’s angular velocity.

For linear motion, we have acceleration -> velocity -> position:

velocity = velocity + acceleration, and
position = position + velocity

Similarly, for angular motion, we have:

angular velocity = angular velocity + angular acceloration
angle = angle + angular velocity

Angular velocity is a three dimensional vector ω (the lowercase Greek letter omega). It has a direction along the axis of rotation and a magnitude equal to the radians per  unit of time spun by the body.

So given the position vector r of a moving body in three-dimensional space, its angular velocity is a vector whose magnitude is the rate at which r rotates about an angle, and whose direction is perpendicular to the plane in which r rotates about an angle at velocity v. However, as there are two directions perpendicular to any plane, the convention is that the unit vector ω is perpendicular to the plane spanned by r and v, so that the right-hand rule is satisfied and the instantaneous direction of angular displacement is counter-clockwise when looking down on ω:

![Angular Velocity](./images/angularVelocity.png)

Using the cross product, we have:

ω = r x v

Negating the angular velocity is equivalent to changing the direction of rotation about the axis.