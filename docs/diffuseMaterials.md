# Diffuse Materials

Light is invisible to us until it hits an object, when some of its energy is absorbed, and some is reflected. Hence, our perception of a material's colour and texture is based on the manner light rays reflect its surface. [Diffuse materials](https://raytracing.github.io/books/RayTracingInOneWeekend.html#diffusematerials) are matt surfaces that absorb much of the light they receive - the darker they are, the more light they absorb.

![](./images/mattSpheres.jpg)

A diffuse surface [reflects light in random directions](https://viclw17.github.io/2018/07/20/raytracing-diffuse-materials/). Thus, diffuse reflection is when light is reflected from a surface and scattered at many angles (as opposed to specular reflection, when light is reflected at just one angle).

![](./images/randomReflection.png)

The [useful links](#useful-links) section contains some links giving more detail about diffuse materials.

## Simulating Diffuse Materials with Ray Tracing

A simple algorithm for generating a diffuse material considers two unit radius spheres that are tangent to the point _P_ of a surface ([a unit sphere](https://en.wikipedia.org/wiki/Unit_sphere) is a sphere whose surfaces are of distance 1 from a fixed central point). These two spheres have a centre of 1) _P + n_ and 2) _P - n_ (where _n_ is the normal to the surface) - sphere 1) is the outside surface, and sphere 2) is inside. Select the unit radius sphere that is on the same side as the ray origin and its tangent surface. Then pick a random point _S_ inside that sphere and send a ray from the hit point _P_ to the random point _S_. To generate that random point, a _rejection algorithm_ is used, which rejects all points generated inside a random point within a cube until it finds a point on the inside of the tangent sphere.

![](./images/diffuseSphere.png)

### Gamma Correction

The sphere above is dark because it has not been [gamma corrected](https://en.wikipedia.org/wiki/Gamma_correction). Gamma correction is a process by which the [bits](https://en.wikipedia.org/wiki/Bit) that make up an image are transformed to take advantage of how we perceive light and colour. Human perception of brightness approximates a power function with greater sensitivity to relative differences between darker tones than the differences between lighter tones. The [useful links](#useful-links) section contains a link to a lecture from a previous year of P3D, which gives an overview of light and colour.

![](./images/gammaCorrectedSphere.png)

### Lambertian Reflection

[Lambertian reflectance](https://en.wikipedia.org/wiki/Lambertian_reflectance), is an ideal which defines a diffusely reflecting surface where the perceived brightness of the surface is the same regardless of the observer's angle of view (unfinished wood exhibits Lambertian reflectance).

For example, the rejection algorithm, described above, produces random points in the unit sphere that are offset along the surface normal. That produces a probability function that favoures rays whose directions are close to the normal. The outcome is that light which arrives at shallow angles and which spreads over a larger area contributes less to the final colour. However, [true Lambertian reflection](https://raytracing.github.io/books/RayTracingInOneWeekend.html#diffusematerials/truelambertianreflection) maintains a uniform distribution for high probability rays that are scattered close to the normal. Hence, true Lambertian reflection is achieved by normalising points inside a diffuse material.

![](./images/lambertianSphere.png)

## Useful Links

+ [Ray Tracing in One Weekend](https://raytracing.github.io/books/RayTracingInOneWeekend.html)
+ [Advanced Ray Tracing](../advancedRayTracing.pdf)
+ [Light, Colour, Colour Spaces and Images](../lightAndColourPerception.pdf)
+ [Materials - Diffuse, Reflection, Transparency](https://www.suplugins.com/podium/help/materials-drt.php)
+ [Ray Tracing - Diffuse Materials](https://viclw17.github.io/2018/07/20/raytracing-diffuse-materials/)
