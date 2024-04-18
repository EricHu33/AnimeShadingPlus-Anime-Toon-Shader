# ASP Character Panel Feature Guide

This page explains the additional features provided on the ASP Character Panel. Theoretically, these features can be set directly through code or inspector individually for each character's material. However, for the sake of convenience (a character may have multiple materials), the ASP Character Panel allows you to set the corresponding parameters for all material at once.

---

![Untitled](ASP%20Character%20Panel%20Feature%20Guide%20d7b39661c1f245e79b230fbfd60e3108/Untitled.png)

# ASP Renderer Feature Check List

In order to render ASP characters correctly, the following three renderer features need to be added to the URP rendering data:

---

- ASP Material Pass
- ASP ShadowMap
- ASP Depth-Offset Shadow

The status of these renderer features will be displayed under the ASP Renderer Feature Check List category. If any are missing or disabled, "missing" or "inactive" will be displayed.

# Shadow Behaviours

---

You can uniformly view and set the Layer/Rendering Layer Mask and the shadow receiving and casting states of all material/renderer of the current character.

<aside>
💡 For detail setup, please refer to [**Setup Character Shadow - ASP’s Shadow Solution**](Setup%20Character%20Shadow%20-%20ASP%E2%80%99s%20Shadow%20Solution%20a0426bfd61cd49a58c877e54d27fc317.md) and [**Character Shadow Setup Guide**](Character%20Shadow%20Setup%20Guide%201ebc2c7bb7324ff78f3bc2ca70bc8940.md)

</aside>

# Light Direction Param

---

![Untitled](ASP%20Character%20Panel%20Feature%20Guide%20d7b39661c1f245e79b230fbfd60e3108/Untitled%201.png)

| Mode | Description |
| --- | --- |
| NO_OVERRIDE | Do not override light direction information, use the directional light in the scene as the main light source |
| OVERRIDE_WITH_EULER | Use Override Light Euler Angle as the main light source direction |

The Light Direction Param provides the ability to override the main light source direction for the current character. This feature is suitable for when the main light source direction for the character needs to be separate from the light source direction in the scene (e.g., when the character is more suitable for a higher angle, top-down light source, and the scene uses a light source closer to the horizon...).

> A unity chan that use OVERRIDE_WITH_EULER mode
> 
> 
> [2024-03-17 11-07-12.mp4](ASP%20Character%20Panel%20Feature%20Guide%20d7b39661c1f245e79b230fbfd60e3108/2024-03-17_11-07-12.mp4)
> 

# Mesh Outline Param

---

This section has the parameter to controls the color, thickness, extrusion mode, and smooth normal baking tool to bake smooth normal into model’s UV4 channel.

<aside>
💡 For detailed instructions on how to use these parameters, please refer to [**Object Space Outline Setup / Smooth Normal Bake Flow**](Object%20Space%20Outline%20Setup%20Smooth%20Normal%20Bake%20Flow%209d066f2426a644ed99fb32649bb5404d.md)

</aside>

# Surface Options

---

![Untitled](ASP%20Character%20Panel%20Feature%20Guide%20d7b39661c1f245e79b230fbfd60e3108/Untitled%202.png)

The Surface Options section displays the surface information for each ASP/Character and ASP/Eye material used by the current character.

You can also adjust the dithering and perspective FOV correction effects for each material individually or globally.

<aside>
💡 To see the effects of dithering and FOV correction, please refer to [Surface Options- FOV Correction and Dithering](Surface%20Options-%20FOV%20Correction%20and%20Dithering%20476e51d40c3c42298dda77a6faea1357.md)

</aside>