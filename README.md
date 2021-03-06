rgx
===

*A mid-level 2D graphics library for rust*

Introduction
------------
**rgx** is a 2D graphics library built on top of [wgpu] and [Vulkan]/[Metal]. This
library aims to be "mid-level" in that it provides an API that is higher level
than Vulkan/Metal, but lower level than most 2D graphics libraries in the wild, by
exposing the user to concepts such as *pipelines*, *buffers* and *swap chains*.
The goal of **rgx** is to provide as simple an API as possible without
sacrificing performance or control over the rendering pipeline.  See the
`examples` directory to get a feel.

At this stage, the focus is on 2D *bitmap* graphics and *sprite rendering*. Basic
shape rendering is also supported, but not the core strength of this library.
In the future, text rendering and more complex vector rasterization may be
supported - however, these are incredibly difficult to do correctly, and I would
recommend looking at Mozilla's *pathfinder* project for these needs. **rgx**
aims to do one thing really well, and that is bitmap rendering.

[wgpu]: https://crates.io/crates/wgpu
[WebGPU]: https://www.w3.org/community/gpu/
[Vulkan]: https://www.khronos.org/vulkan/
[Metal]: https://developer.apple.com/metal/

Overview
--------
The library is split into two modules, `kit`, and `core`. The latter provides
**rgx**'s core API with no assumption on what kind of 2D graphics will be
rendered, while the former exposes some useful building blocks for various use-cases,
such as a shape-oriented pipeline and a sprite oriented pipeline. Users can construct
their own pipelines and use them with **rgx**.

### Pipelines included in the `kit`

* **shape2d**: for batched 2D shape rendering
* **sprite2d**: for batched 2D sprite rendering

### Features

* Batched texture rendering
* Batched shape rendering
* Basic primitives for sprite animation
* Off-screen rendering support
* Custom shader support
* Custom pipeline support
* Built-in depth testing

Usage
-----
See [examples/helloworld.rs](examples/helloworld.rs) for a simple usage example.


Rebuilding the shaders
----------------------
To rebuild the shaders run the following:

    glslc -c -Werror --target-env=vulkan ./examples/data/framebuffer.vert -o ./examples/data/framebuffer.vert.spv
    glslc -c -Werror --target-env=vulkan ./examples/data/framebuffer.frag -o ./examples/data/framebuffer.frag.spv
    glslc -c -Werror --target-env=vulkan ./src/kit/data/shape.frag        -o ./src/kit/data/shape.frag.spv
    glslc -c -Werror --target-env=vulkan ./src/kit/data/sprite.frag       -o ./src/kit/data/sprite.frag.spv
    glslc -c -Werror --target-env=vulkan ./src/kit/data/shape.vert        -o ./src/kit/data/shape.vert.spv
    glslc -c -Werror --target-env=vulkan ./src/kit/data/sprite.vert       -o ./src/kit/data/sprite.vert.spv

Support
-------
If you find this project useful, consider supporting it by sending ₿ (Bitcoin) to
`1HMfp9QFXmVUarNPmHxa1rhecZXyAPiPZd`. <3

Copyright
---------
(c) 2019 Alexis Sellier\
Licensed under the MIT license.
