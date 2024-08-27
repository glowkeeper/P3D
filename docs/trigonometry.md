# Trigonometry

Trigonometry is the mathematics of triangles. It forms the mathematical basis of many behaviours of objects, including the description of shapes, motion, angular velocity, rotations and transformations; hence, a basic understanding of trigonometry is essential if you want to work with circles, arcs, or lines and figure out the relationship between objects in a 3D space, perhaps calculating the distances between them. At the heart of trigonometry are angles.

## Angles

An angle (θ - the Greek symbol theta) is formed by the space between two intersecting lines that join at a point.

![angle](./images/angle.png)

A unit of measurement of angles is _degrees_. The amount of degrees formed by an angle describes circularity, or rotation, about the point of origin.

![Circular Angle](./images/circularAngle.png)

A full rotation is 360°. A half-circle is 180°. A quarter-circle, or right angle, is 90°. Below is a square rotated 45°, using its centre as its pivot point.

![Square Rotated](./images/docs/images/square45.webp)

Radians are another unit of trigonometric measurement. They are defined by the ratio of the length of the arc of a circle (a segment of the circle's circumference) to the radius of that circle. One radian is the length at which that ratio equals 1.

![Radian](./images/docs/images/radian.png)

Radians have a strong relationship to Pi (π), which is an irrational number defined as the ratio of a circle's circumference (the distance around the outside of the circle) to its diameter (a straight line that passes through the circle's centre). A full circle (360°) is equivalent to 2π radians. Hence, 180° is π radians, and 90° is π/2 radians. The formula to convert from degrees to radians is as follows:

radians = (2π x degrees) / 360

Although to many (at least in the UK), radians may not be as familiar as degrees. However, radians are often useful as they relate angle to length, making some calculations much more straightforward. For example, to find the speed of a vehicle in metres per second, you can multiply the radius of one of its wheels by the number of radians it turns per second. So if the wheel has a radius of two metres and turns at six radians per second, the speed is 12 metres per second. Additionally, their association with Pi (π) makes radians a somewhat more intuitive unit for graphing, performing calculus and modelling some spherical geometry.

## Trigonometric Functions

Trigonometry is based on the unit circle, a circle with the centre at the origin (0,0 in a 2D space and 0,0,0 in 3D) with a radius equal to 1.

![Trigonometric functions](./images/trigFunctions.png)

Since any triangle can be split into right-angled triangles whose opposite and adjacent sides form the axis of a graph, we can then use the functions found in trigonometry to understand ratios, symmetry, transformations, rotations and much more besides.

The three main trigonometric functions are Sine, Cosine and Tangent, which are used to find an unknown side or angle of a triangle when two pieces of information are known (such as the length of two sides or the length of one side and an angle). Sine, Cosine and Tangent are described by the mnemonic **SohCahToa** - take one of the non-right angles in the triangle - the adjacent side is the one touching that angle, the opposite side is the one not touching that angle, and the hypotenuse is the side opposite the right angle.

- **Soh**: sine(θ) = opposite/hypotenuse
- **Cah**: cosine(θ) = adjacent/hypotenuse
- **Toa**: tangent(θ) = opposite/adjacent

If **Soh** is used, take the sine of the unknown angle set equal to the opposite side divided by the hypotenuse.

- **Soh**: when the opposite side and the hypotenuse are known
- **Cah**: when the adjacent side and the hypotenuse are known
- **Toa**: when the opposite side and adjacent sides are known

For example, given the right-angled triangle below, how can we work out the length of the side labelled _x_?

![Sine example](./images/sinExample.png)

Since _x_ is opposite the hypotenuse, we need the Sine function, and we have:

sin(40) = x/8, giving:

8 * sin(40°) = _x_. Plugging sin(40°) into a calculator, we get ~0.6428, so:

8 * 0.6428 = 5.1424.

So the length of _x_ is ~5.1424. Similarly, we could work out the remaining side's length. That is left as an exercise.

Sometimes, it is the angle that is unknown. In such situations, the inverse functions are useful - we have the inverse tangent (or arctangent (arctan or atan)), the inverse sine (or arcsine (arcsin or asin)) and inverse cosine (or arccos (arccos or acos)).

Using the example above, we have:

sin(θ) = ~5.1424 / 8 = ~0.6428, so:

θ = arcsin(0.64278760968) = 40°, as expected.

## Vectors and Trigonometry

The following describes a right-angled triangle in terms of a vector, v.

![Vectors and Trigonometry](docs/images/vectorsAndTrigonometry.webp)

The vector, v is the hypotenuse, and the components of the vector (x and y) are the opposite and adjacent sides of the triangle. Hence, the angle is another way to specify the vector's direction because you move x steps right and y steps up. Therefore, the trigonometric functions establish a relationship between the components of a vector and its direction and magnitude.

## Polar Coordinates

When talking about the position of an object in a programming environment, you are _probably_ (if you are from the UK) more familiar with referring to that position in terms of its x, y and z coordinates. These are Cartesian coordinates, named after René Descartes, the French mathematician who developed the ideas behind Cartesian space.

However, polar coordinates are another system for referring to points in space, e.g. (r,θ). The polar coordinate system refers to those points using distances and angles. And in fact, you probably use them more often than you realise. For instance, the author of this piece on polar coordinates lives near Brighton, in England, about 60 miles south of London. In other words, they've given an origin (London), a distance (60 miles), and an angle (south)· In short, polar coordinates often arise because people naturally think about locations in terms of distance and direction. Therefore, the polar coordinate system is useful whenever we need to think in terms of distance and angle.

When working in two dimensions, polar coordinates take the form (r,θ), where, by convention, r (for radius - the value is referred to as the radial line) represents the distance, and θ gives the polar angle from the origin.

![2D Polar Coordinates](./images/2dPolar.png)

With three dimensions, there are two choices for polar coordinate systems. The first is cylindrical coordinates, denoted by (r,θ,z), where z is a third axis perpendicular to the 2D plane created by (r,θ). To locate the point described by the cylindrical coordinates (r,θ,z), you start by finding the point (r,θ) in the 2D polar coordinate space and then move up or down according to the sign of the z coordinate.

![Cylindrical coordinates](./images/cylindricalCoordinates.png)

The second choice of polar coordinate system in three dimensions is the spherical coordinate system. The third value in the system is denoted φ, which is the angle of rotation about the meridian plane, which is the axis perpendicular to the 2D plane created by (r,θ). Hence, spherical polar coordinates take the form (r,θ,φ).

![Spherical Coordinates](./images/sphericalCoordinates.png)

Sometimes, you may see spherical coordinates referred to using the more intuitive (r,h,p), where h refers to heading (similar to compass heading (north, south, etc.), borrowed from an aviation context), and p refers to pitch, which measures how much something is looking up or down.

Finally, to convert a point from Cartesian coordinates to spherical coordinates, use the following:

x=rsinφcosθ
y=rsinφsinθ
z=rcosφ

## Rotation

Rotation, or angular motion, is a movement about an angle with respect to time, and just as linear motion uses velocity to show the rate at which an object's position changes over time, angular motion uses angular velocity to show the rate at which an object's angle changes over time. By extension, angular acceleration describes changes in an object's angular velocity.

For linear motion, we have acceleration -> velocity -> position:

velocity = velocity + acceleration, and
position = position + velocity

Similarly, for angular motion, we have:

angular velocity = angular velocity + angular acceloration
angle = angle + angular velocity

Angular velocity is a three-dimensional vector ω (the lowercase Greek letter omega). It has a direction along the axis of rotation and a magnitude equal to the radians spun by the body per unit of time.

So, given the position vector r of a moving body in three-dimensional space, its angular velocity is a vector whose magnitude is the rate at which r rotates about an angle and whose direction is perpendicular to the plane in which r rotates about an angle at velocity v. However, as there are two directions perpendicular to any plane, the convention is that the unit vector ω is perpendicular to the plane spanned by r and v so that the right-hand rule is satisfied and the instantaneous direction of angular displacement is counter-clockwise when looking down on ω:

![Angular Velocity](./images/angularVelocity.png)

Using the cross product, we have:

ω = r x v

Negating the angular velocity is equivalent to changing the direction of rotation about the axis.

## Simple Harmonic Motion

Below is the graph of a sine wave. The graph shows the relationship of the sine wave to the radians discussed above, where 2π radians represent a circle or a complete revolution of the sine cycle.

![Sine Wave](./images/sinewave.png)

The sine wave exhibits simple harmonic motion, a periodic oscillation between points on the graph. Anything cyclic demonstrates examples of oscillating motion that can be modelled using the sine function. The different notes or chords played on the guitar are examples of such harmonics because the guitar generates sinusoidal sound waves.

Simple harmonic motion is expressed as a function of time, with the following properties elements:

1. Amplitude is the height on the y-axis the sine wave reaches from the x-axis
2. Period is the seconds per (2π) cycle.
3. Frequency is related to period as it represents the number of cycles per second
4. Wavelength is inversely proportional to the frequency of the sine wave as waves with higher frequencies have shorter wavelengths and lower frequencies have longer wavelengths

On guitar, the greater the amplitude, the louder the sound waves. And middle A has a frequency of 440 hertz (cycles per second).

Simple harmonic motion can be graphed in a number of ways, including using a slowly incrementing value of angular velocity as the input to the sine function so that the object's motion oscillates smoothly every time the value of angular velocity goes beyond a multiple of 2π and completes a cycle (whereby _period = 2π / angular velocity_).