# v0.6.0

commit 1f5e52bf2751be680fef6949604dfa5563cbb84c

    Add `Origin` parameter to `kit::ortho`

# v0.5.0

commit c3de863cb8e6e8d925be5418f85adb3d1009ae6b

    Implement `TransformBuffer`

    This replaces the old `Model`, and implements a transform
    buffer for use with dynamic uniform buffers.

commit 4a585ec89cd5a2a12f7f13d0f762ce3ef5b883e3

    Implement `Geometry` trait

    * `Geometry` trait for things that can be transformed
    * Change `Line` to use `Point2`
    * Implement a few extra methods in `math` module

    This enables transforming `Line` and `Rect` with a `Matrix4`.

# v0.4.1

commit d3021ba684d4fc7f131c82645cc8416212dbbc1c

    Use `Bgra8` for pixel data in `Renderer::read`

# v0.4.0

commit 14947b71417973e620d9ba027b96c174b91e19ec

    Derive `Debug` on core types

commit f152c18b831d827393838834e510d2257a8ce363

    Clear depth buffer on `Op::Clear`

commit eddbfef19bc372001227bb901a915c14146abbcc

    Use a linear color pipeline

    This change moves our pipelines to the sRGB color space, properly
    accounting for gamma correction. This means colors passed in
    need to be manually linearized. For textures, this happens automatically
    by specifying the correct format.

commit 95e6ff64791da4d4fba547c9fa97a220a27929ef

    Rename `TextureView` trait to `RenderTarget`

commit 8eb1eb0b3fccdb081a48739f5c73430b8291f078

    Add z-depth rendering functionality

    This implements depth testing and writing for all pipelines, along with
    an additional `ZDepth` parameter for shapes and sprites.

    Depth testing can significantly improve performance by minimizing
    overdraw.

commit 7edd02cd757228ff7db635130aa36cfcd7c31e00

    Make `Renderer::new` return a `Result`

    In preparation for wgpu not panicking when it doesn't
    find a suitable adapter...

commit 95d5a433a16922f5a3dc651da5b16561cb7e7b26

    Move `Rect` type to its own module
