Layers
======

Materials are made up of textures, which are created by combining different types of layers. This is an overview of the types of layers that exist in Material Painter by default. To create custom layers, see :ref:`doc_creating_effects`.

There are two types of layers: Blending layers and Effects. Blending layers supply a texture which is then blended with the previous layer using a blend mode and an opacity. Effects modify the previous layer using a shader, which opens up a wide range of possibilities.

Blending Layers
---------------

**File Layer**

File layers can be created by dragging images from the :ref:`Asset Library <doc_asset_library>` into the layer stack. They provide the texture by loading an image from the file system.

**Bitmap Layer**

Bitmap layers use a texture that can be modified inside Material Painter using multiple tools. See :ref:`Painting <doc_painting>`.

**Color Layer** provide a uniform color.

**Scalar Layer** provide a uniform grayscale value.

Effect Layers
-------------

**Brightness Contrast** can be used to modify the brightness and contrast.

**HSV Adjust** can be used to modify the hue, saturation and value.

**Isolate Color** makes all instances of the specified color white, and everything else black. This is useful for ID maps.

**Isolate Channel** uses the value of the specified channel as red, green and blue values.

**Blur** blurs the output by the specified amount. This is a expensive operation.

**Invert** inverts all channels except alpha.

**Dust**

When the previous layer is the world normal texture, colors the surfaces that match the specified normal white and everything else black.
