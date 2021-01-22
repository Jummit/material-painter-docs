Effect Layers
=============

Effects are json-based layers that specify a shader and expose its parameters. Material Painter ships with some useful effects by default, for example blur, hsv adjust and invert.

Creating a Custom Effect
------------------------

This is the structure of the ``Scalar`` layer:
::

	{
		"name": "Scalar",
		"properties" : [
			{
				"name": "value",
				"type": "float",
				"range": [0, 1],
				"default": 0.5
			}
		],
		"blends": true,
		"in_context_menu": true,
		"shader": "return vec4({value}, {value}, {value}, 1.0);"
	}

The name is how the effect will be called in Material Painter. The ``properties`` array holds the properties that can be used in the shader and are exposed in the editor. If ``in_context_menu`` is true, the effect will appear when right clicking in the :ref:`Layer Stack <doc_layer_stack>`.

The Shader
----------

The ``shader`` property holds the shader that is used to compose the final material. It should return a ``vec4``.

Information about Godot's shader language can be found in the `Godot Shader Reference`_.

.. _Godot Shader Reference: https://docs.godotengine.org/en/latest/tutorials/shaders/shader_reference/index.html

Properties
----------

There are properties for each shader uniform type. The type of a property is specified in the `type` value.

Here are the available types and their unique settings:

**color**

**float** and **int**

:range: An array with two numbers, for example ``[0.0, 5.5]``.
:default: The default value, for example ``1.0``.

**enum**

:options: An array of values, for example ``["r", "g", "b"]``.
:default: An element of the ``options`` array that is the default value.

Using Properties in the Shader
------------------------------

By default, every property will be added to the shader as a uniform and can be used in the shader with ``{property_name}``. If ``shader_param`` is set to false, the property will not be added as a uniform, and can be used in the shader directly. This is used in the ``Isolate Channel`` layer to specify if the red, green or blue channel should be isolated.

Blending and modifying
----------------------

Layers can either return a value that is blended with the previous layer, like a ``Scalar`` or a ``Color`` layer. This can be enabled by setting ``blends`` to true.
By default they modify the previous layer, like ``Blur`` or ``HSVAdjust``. You can use ``{previous}(uv)`` to refer to the previous result; ``{previous}`` is the function of the previous layer, so you can pass any uv coordinates you want. This is used in the ``Blur`` layer.

Using the Effect
----------------

Like any asset, you can add it to your global library by dropping the effect file into the :ref:`Asset Browser <doc_asset_library>`. It will be stored in ``user://assets/effects``. To add an effect to your project library, you can put it in the ``asset/effects`` folder alongside your project file.
