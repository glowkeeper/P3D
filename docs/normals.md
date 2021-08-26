# Surface Normals and Anti-aliasing

[Normals](https://en.wikipedia.org/wiki/Normal_(geometry)) are rays that are perpendicular to an object. In three dimensions, the figure below shows that a surface normal at point P is a [vector](#vectors) perpendicular to the tangent plane of the surface at point P. A normal is used in 3D graphics for shading, as it determines a surface's orientation towards a light source.

![](./images/normal.png)

## Vectors

You are not required to have any prior maths to complete this module. However, if you are interested in that maths, or have some mathematical background, [Ray Tracing in One Weekend](https://raytracing.github.io/books/RayTracingInOneWeekend.html) gives more detail, and in the [useful links](#useful-links) section, there is a link to a lecture from a previous year of P3D, which gives an overview of vector operations. Additionally, the _Reading List_, on Canvas, includes a reference to _Essential mathematics for games and interactive applications: a programmer's guide_, which is available in the library.

## Surface Normals

For a sphere, the [outward normal](https://raytracing.github.io/books/RayTracingInOneWeekend.html#surfacenormalsandmultipleobjects/shadingwithsurfacenormals) is in the direction of the intersection point, minus the centre.

![](./images/sphereNormal.jpg)

The ability to determine the surface face is important for objects that are rendered differently on each side; for example, a glass ball has an inside and an outside - [Ray Tracing in One Weekend](https://raytracing.github.io/books/RayTracingInOneWeekend.html) gives more detail.

![](./images/sphereWithSurfaceNormal.png)

## Anti-aliasing

[Anti-aliasing](https://helpx.adobe.com/photoshop/key-concepts/aliasing-anti-aliasing.html) of digital images is the smoothing of the jagged edges that are the result of high-contrast borders between pixels.

![](./images/antiAliasedSphere.png)

When you take a picture with a real camera, there are usually no jagged edges because [the edge pixels blend the foreground with the background](https://raytracing.github.io/books/RayTracingInOneWeekend.html#antialiasing). Anti-aliasing algorithms might achieve a similar effect by averaging the colours of the boundary pixels. However, there are more advanced approaches - if you are interested in those, the [useful links](#useful-links) section contains a link to the user manual of [Pixar Studios'](https://www.pixar.com/) [Renderman](https://renderman.pixar.com/) product, which describes other anti-aliasing techniques. It also contains a link to a thorough examination of anti-aliasing for the [OpenGL API](https://www.opengl.org/).

## Useful Links

+ [Ray Tracing in One Weekend](https://raytracing.github.io/books/RayTracingInOneWeekend.html)
+ [Vectors](../vectors.pdf)
+ [Basic Antialiasing in RSL](https://renderman.pixar.com/resources/RenderMan_20/basicAntialiasing.html)
+ [Anti Aliasing using OpenGL](https://learnopengl.com/Advanced-OpenGL/Anti-Aliasing)
