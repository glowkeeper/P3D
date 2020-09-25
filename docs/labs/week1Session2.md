# Lab for Week 1, Session 2 - Visualising a Simple Object

This lab focusses on programmatically creating a circle, using C++. It introduces you to rendering 3D objects, and lays the foundations for your understanding of ray tracing.

## Overview

[Ray tracing](https://www.khanacademy.org/computing/pixar/rendering/rendering1/v/rendering-1) is a graphics rendering technique for lighting objects. It is an algorithm that traces the path of light and simulates the way that the light interacts with objects in a virtual world.

Ray tracing is a staple in films - indeed, in the [reading material](#reading-material), below, you will see a link to the excellent [Pixar in a Box](https://www.khanacademy.org/computing/pixar) on [Khan Academy](https://www.khanacademy.org/), which takes a behind-the-scenes look at how [Pixar](https://www.pixar.com/) artists do their jobs. The [Rendering 101](https://www.khanacademy.org/computing/pixar/rendering/rendering1/a/start-here-rendering) suite of videos there give an overview of rendering and ray tracing.

## Creating a Simple Object

Implicit in that explanation of ray tracing, above, was the idea that we need an object with which light can interact.  Below, we will use C++ to create that object. All the code you create comes via the fantastic [Ray Tracing in One Weekend](https://raytracing.github.io/books/RayTracingInOneWeekend.html), so you can read more about what you're doing and why there.

You are going to create a program that outputs a [portable pixmap format](https://en.wikipedia.org/wiki/Netpbm#File_formats) (PPM) graphic. PPM is a text format for describing the [RGB](https://en.wikipedia.org/wiki/RGB_color_model) properties of a graphic.

### Outputting a Simple Graphic

First, create a program that outputs a simple graphic:

```
#include <iostream>

int main() {

    // Image

    const int image_width = 256;
    const int image_height = 256;

    // Render

    std::cout << "P3\n" << image_width << ' ' << image_height << "\n255\n";

    for (int j = image_height-1; j >= 0; --j) {
        for (int i = 0; i < image_width; ++i) {
            auto r = double(i) / (image_width-1);
            auto g = double(j) / (image_height-1);
            auto b = 0.25;

            int ir = static_cast<int>(255.999 * r);
            int ig = static_cast<int>(255.999 * g);
            int ib = static_cast<int>(255.999 * b);

            std::cout << ir << ' ' << ig << ' ' << ib << '\n';
        }
    }
}
```

Save that to a file called `main.cpp`. Now compile and run the program:

```
# g++ -o imageCreator main.cpp && ./imageCreator > image.ppm
```

If you open `image.ppm` via your file browser, you should see your first RGB-inspired graphic, like so:

![](./images/image.png)

### Vectors

You are not required to have any prior maths to complete this module. However, below, you will create a C++ class, `vec3.h`, which implements some of the vector maths needed to visualise an object. If you are interested in that maths, or have some mathematical background, [Ray Tracing in One Weekend](https://raytracing.github.io/books/RayTracingInOneWeekend.html) gives more detail. Additionally, the _Reading List_, on Canvas, includes a reference to _Essential mathematics for games and interactive applications: a programmer's guide_, which is available in the library.

Create `vec3.h`:

```
#ifndef VEC3_H
#define VEC3_H

#include <cmath>
#include <iostream>

using std::sqrt;

class vec3 {
    public:
        vec3() : e{0,0,0} {}
        vec3(double e0, double e1, double e2) : e{e0, e1, e2} {}

        double x() const { return e[0]; }
        double y() const { return e[1]; }
        double z() const { return e[2]; }

        vec3 operator-() const { return vec3(-e[0], -e[1], -e[2]); }
        double operator[](int i) const { return e[i]; }
        double& operator[](int i) { return e[i]; }

        vec3& operator+=(const vec3 &v) {
            e[0] += v.e[0];
            e[1] += v.e[1];
            e[2] += v.e[2];
            return *this;
        }

        vec3& operator*=(const double t) {
            e[0] *= t;
            e[1] *= t;
            e[2] *= t;
            return *this;
        }

        vec3& operator/=(const double t) {
            return *this *= 1/t;
        }

        double length() const {
            return sqrt(length_squared());
        }

        double length_squared() const {
            return e[0]*e[0] + e[1]*e[1] + e[2]*e[2];
        }

    public:
        double e[3];
};

// Type aliases for vec3
using point3 = vec3;   // 3D point
using color = vec3;    // RGB color

// vec3 Utility Functions

inline std::ostream& operator<<(std::ostream &out, const vec3 &v) {
return out << v.e[0] << ' ' << v.e[1] << ' ' << v.e[2];
}

inline vec3 operator+(const vec3 &u, const vec3 &v) {
return vec3(u.e[0] + v.e[0], u.e[1] + v.e[1], u.e[2] + v.e[2]);
}

inline vec3 operator-(const vec3 &u, const vec3 &v) {
return vec3(u.e[0] - v.e[0], u.e[1] - v.e[1], u.e[2] - v.e[2]);
}

inline vec3 operator*(const vec3 &u, const vec3 &v) {
return vec3(u.e[0] * v.e[0], u.e[1] * v.e[1], u.e[2] * v.e[2]);
}

inline vec3 operator*(double t, const vec3 &v) {
return vec3(t*v.e[0], t*v.e[1], t*v.e[2]);
}

inline vec3 operator*(const vec3 &v, double t) {
return t * v;
}

inline vec3 operator/(vec3 v, double t) {
return (1/t) * v;
}

inline double dot(const vec3 &u, const vec3 &v) {
return u.e[0] * v.e[0]
     + u.e[1] * v.e[1]
     + u.e[2] * v.e[2];
}

inline vec3 cross(const vec3 &u, const vec3 &v) {
return vec3(u.e[1] * v.e[2] - u.e[2] * v.e[1],
            u.e[2] * v.e[0] - u.e[0] * v.e[2],
            u.e[0] * v.e[1] - u.e[1] * v.e[0]);
}

inline vec3 unit_vector(vec3 v) {
return v / v.length();
}

#endif
```

### Colour

Later on, you will also need a utility function that changes a single pixel's colour:

```
#ifndef COLOR_H
#define COLOR_H

#include "vec3.h"

#include <iostream>

void write_color(std::ostream &out, color pixel_color) {
    // Write the translated [0,255] value of each color component.
    out << static_cast<int>(255.999 * pixel_color.x()) << ' '
        << static_cast<int>(255.999 * pixel_color.y()) << ' '
        << static_cast<int>(255.999 * pixel_color.z()) << '\n';
}

#endif
```

Save that file as `color.h`.

### Ray Tracing

A ray tracing algorithm computes what colour is seen at a 3D position along a line (or ray). Hence, the basic steps to create a ray tracer are:

1. Calculate the ray from the eye to the pixel
2. Determine which objects the ray intersects
3. Compute a colour for that object at that intersection point

The file `ray.h`, shown below, uses _linear interpolation_ to calculate a position along a line (there is more about linear interpolation in the _Introduction to Animation_ [Pixar in a Box](https://www.khanacademy.org/computing/pixar) suite of videos, which are linked to in the_[reading material](#reading-material) section):

```
#ifndef RAY_H
#define RAY_H

#include "vec3.h"

class ray {
    public:
        ray() {}
        ray(const point3& origin, const vec3& direction)
            : orig(origin), dir(direction)
        {}

        point3 origin() const  { return orig; }
        vec3 direction() const { return dir; }

        point3 at(double t) const {
            return orig + t*dir;
        }

    public:
        point3 orig;
        vec3 dir;
};

#endif
```

You will also need to create a _virtual viewport_ through which to pass rays for the image scene. The viewport's aspect ratio should be the same as the image you are rendering. Below, you'll use a viewport that is two units in height, and the distance between the projection plane and the projection point (the _focal length_) is set to one unit. The camera for viewing the scene will use a [right-handed coordinate system](https://en.wikipedia.org/wiki/Right-hand_rule), where the y-axis goes up, the x-axis goes to the right and the negative z-axis goes into the screen. The camera will be centred at (0,0,0). Again, [Ray Tracing in One Weekend](https://raytracing.github.io/books/RayTracingInOneWeekend.html) gives more detail about the maths being used.

Amend `main.cpp` so that the ray _r_ approximates to the centre of the rendered pixels:

```
#include "color.h"
#include "ray.h"
#include "vec3.h"

#include <iostream>

color ray_color(const ray& r) {
    vec3 unit_direction = unit_vector(r.direction());
    auto t = 0.5*(unit_direction.y() + 1.0);
    return (1.0-t)*color(1.0, 1.0, 1.0) + t*color(0.5, 0.7, 1.0);
}

int main() {

    // Image
    const auto aspect_ratio = 16.0 / 9.0;
    const int image_width = 400;
    const int image_height = static_cast<int>(image_width / aspect_ratio);

    // Camera

    auto viewport_height = 2.0;
    auto viewport_width = aspect_ratio * viewport_height;
    auto focal_length = 1.0;

    auto origin = point3(0, 0, 0);
    auto horizontal = vec3(viewport_width, 0, 0);
    auto vertical = vec3(0, viewport_height, 0);
    auto lower_left_corner = origin - horizontal/2 - vertical/2 - vec3(0, 0, focal_length);

    // Render

    std::cout << "P3\n" << image_width << " " << image_height << "\n255\n";

    for (int j = image_height-1; j >= 0; --j) {
        for (int i = 0; i < image_width; ++i) {
            auto u = double(i) / (image_width-1);
            auto v = double(j) / (image_height-1);
            ray r(origin, lower_left_corner + u*horizontal + v*vertical - origin);
            color pixel_color = ray_color(r);
            write_color(std::cout, pixel_color);
        }
    }
}
```

#### Creating a Ray-traced Circle

Finally, you are in a position to create an object that the ray, _r_, intersects.

Use the `vec3` and `ray` classes to hard code a sphere in `main.cpp`, simply by colouring red any pixel that hits a small sphere we place at −1 on the z-axis:

```
#include "color.h"
#include "ray.h"
#include "vec3.h"

#include <iostream>

bool hit_sphere(const point3& center, double radius, const ray& r) {
    vec3 oc = r.origin() - center;
    auto a = dot(r.direction(), r.direction());
    auto b = 2.0 * dot(oc, r.direction());
    auto c = dot(oc, oc) - radius*radius;
    auto discriminant = b*b - 4*a*c;
    return (discriminant > 0);
}

color ray_color(const ray& r) {
    if (hit_sphere(point3(0,0,-1), 0.5, r))
        return color(1, 0, 0);
    vec3 unit_direction = unit_vector(r.direction());
    auto t = 0.5*(unit_direction.y() + 1.0);
    return (1.0-t)*color(1.0, 1.0, 1.0) + t*color(0.5, 0.7, 1.0);
}

int main() {

    // Image
    const auto aspect_ratio = 16.0 / 9.0;
    const int image_width = 400;
    const int image_height = static_cast<int>(image_width / aspect_ratio);

    // Camera

    auto viewport_height = 2.0;
    auto viewport_width = aspect_ratio * viewport_height;
    auto focal_length = 1.0;

    auto origin = point3(0, 0, 0);
    auto horizontal = vec3(viewport_width, 0, 0);
    auto vertical = vec3(0, viewport_height, 0);
    auto lower_left_corner = origin - horizontal/2 - vertical/2 - vec3(0, 0, focal_length);

    // Render

    std::cout << "P3\n" << image_width << " " << image_height << "\n255\n";

    for (int j = image_height-1; j >= 0; --j) {
        for (int i = 0; i < image_width; ++i) {
            auto u = double(i) / (image_width-1);
            auto v = double(j) / (image_height-1);
            ray r(origin, lower_left_corner + u*horizontal + v*vertical - origin);
            color pixel_color = ray_color(r);
            write_color(std::cout, pixel_color);
        }
    }
}
```

Now compile and run the program:

```
# g++ -o imageCreator main.cpp && ./imageCreator > circle.ppm
```

If you open `circle.ppm` via your file browser, you should see your first RGB-inspired graphic, like so:

![](./images/circle.png)

Congratulations! You have created your first ray-traced image! Even though you've covered a lot of material here, your image is somewhat rudimentary - don't worry - in the [next lab](./week2Session1.md), you will begin turning the object into a much better-looking 3D sphere.

## Reading Material

+ [Ray Tracing in One Weekend](https://raytracing.github.io/books/RayTracingInOneWeekend.html)
+ [Rendering 101](https://www.khanacademy.org/computing/pixar/rendering/rendering1/a/start-here-rendering)
+ [Introduction to Animation](https://www.khanacademy.org/computing/pixar/animate/ball/a/start-here-animation)
+ [What is ray tracing? The games, the graphics cards and everything else you need to know](https://www.techradar.com/uk/news/ray-tracing)
