# Vectors

A Euclidean vector (named after the Greek mathematician Euclid) can be represented as an arrow that describes a movement from one point to another.

![vector](./images/vector.png)

The beauty of such a representation is that it imparts much information because it shows how to travel between points. The size of the arrow shows the vector's magnitude (or how far you have to travel), and where the arrow points shows the vector's direction (or the path the traveller must take).

Vectors are useful for programming motion as they can represent the difference between two points. Imagine every frame of a running program (a single cycle through a [render loop](https://gameprogrammingpatterns.com/game-loop.html)) during which, an object must be repositioned. The instructions to do so will have a magnitude (how far to travel) and a direction (which way to go); in other words, it will be a vector that represents the object's velocity (defined as the rate of change of the object's position with respect to time). For every frame, this velocity vector determines the object's new position according to a basic algorithm for motion, whereby the new position of the object is equal to the result of applying the velocity vector to the object's current position.

However, Vectors are not limited to simply representing motion. They can also describe absolute positions, adding to their versatility because a vector can define a path from a point of origin (the absolute origin in a 3D space is defined as the vector (0, 0, 0)) to any other point.

The ability of vectors to describe motion and position makes them a fantastic tool for programming a 3D space.

Below describes some vector operations.

## Vector Addition and Subtraction

You can add or subtract any two vectors by adding or subtracting their corresponding components:

If 𝐴=(𝑥,𝑦,𝑧) and 𝐵=(𝑥,𝑦,𝑧), then 𝐴 + 𝐵 = (𝑥+𝑥,𝑦+𝑦,𝑧+𝑧)

And

If 𝐴=(𝑥,𝑦,𝑧) and 𝐵=(𝑥,𝑦,𝑧), then 𝐴 - 𝐵 = (𝑥−𝑥,𝑦−𝑦,𝑧−𝑧)

## Magnitude of a Vector

The magnitude of a vector tells us its length. It is denoted by |𝐴|:

If 𝐴=(𝑥,𝑦,𝑧),then |𝐴| =√(x^2+y^2+z^z)

## Unit Vectors

A unit vector is a vector with a magnitude equal to 1.

## Normalising Vectors

Normalisation is the process of making something standard (or normal). The convention is that a normalised vector has a length of 1, and any vector with a magnitude of 1 is considered a unit vector. Therefore, to normalise a vector, you take a vector of any magnitude and change its length to 1. Its direction remains unchanged, so a unit vector describes a vector's direction without regard to its magnitude.

You normalise by dividing the x and y and z components of a vector by its magnitude.  

## Multiplying a Vector

To multiply any vector by a scalar, multiply each vector component by that scalar. Hence:

If 𝐴=(𝑥,𝑦,𝑧), then 𝑘𝐴=(𝑘𝑥,𝑘𝑦,𝑘𝑧) for all real constants 𝑘.

## Dot Product

The dot product takes two vectors and returns a scalar:

If 𝐴=(𝑥,𝑦,𝑧) and 𝐵=(𝑥,𝑦,𝑧), then 𝐴.𝐵 = 𝐴.x*𝐵.x + 𝐴.y*𝐵.y + 𝐴.z*𝐵.z

Furthermore, the Dot Product is commutable, so 𝐴.𝐵 = 𝐵.𝐴

## Cross Product

The cross product takes two vectors and returns a vector. The result is a vector that is perpendicular to the plane containing 𝐴 and 𝐵.

The direction of the vector given by the cross product is shown using the right hand thumb rule. This is achieved by curling the fingers of the right hand in the direction in which 𝐴 would be rotated to meet 𝐵. The thumb then points in the direction of 𝐴 × 𝐵.

![Right Hand Rul]e(./images/rightHandRule.jpg)

Formally:

C = 𝐴x𝐵  = |𝐴| × |𝐵| × sin θ × n,

Where:

C – New vector resulting from doing the cross product
𝐴 – First vector
𝐵 – Second vector
θ – Angle between 𝐴 and 𝐵
n – Unit vector perpendicular to 𝐴 and 𝐵

The cross product is _not* commutative, since:

Bx𝐴 = -𝐴x𝐵

## The Application of Vector Operations

The image below shows multiplication (by a scalar), addition, subtraction, the dot product and the cross product.

![Vector Operations](./images/vectorOperations.png)

Applications of those operations may be useful as they can help determine how objects move or behave in a 3D space. For example, suppose you have 𝐴 and 𝐵 (where 𝐴 and 𝐵 are the motions of the player and the enemy, respectively), and you want player 𝐵 to move away from the enemy 𝐴. Then 𝐵 = 𝐵 - 𝐴 will do the trick. Dot products are useful because, for any two vectors, 𝐴 and 𝐵, the operation will return a scalar, whereby, if the number is greater than zero, both vectors are in the same direction. However, if the number is less than zero, both vectors are in opposite directions. And if the number is zero, the vectors are perpendicular. So, dot products between two vectors ,ight help you ascertain if any two entities are looking towards the same side, opposite sides, or just looking 90 degrees away from each other.
