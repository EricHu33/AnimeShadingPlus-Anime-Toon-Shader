# About ASP’s Render Passes

---

At the end of the [**Installation Instructions and Prerequisites (Important)**](Installation%20Instructions%20and%20Prerequisites%20(Impor%205f0a72aeff00486d9b204b62c99a8035.md), it is mentioned that : 

> There are a total of 3 basic renderer features required by ASP. Please be sure to add and enable the following renderer features in the renderer data:
ASP Material Pass, ASP ShadowMap, and ASP Depth-Offset Shadow.
> 

---

These 3 renderer features are 3 independent passes. This page will explain the purpose of these passes in detail.

# Material Pass

---

Whenever a material of the character renderer uses ASP/Character or ASP/Eye as its target shader, that renderer will be rendered into the Material Pass. 

The Material Pass’s render result is a RGBA32 texture:

| Channel | Data | Description |
| --- | --- | --- |
| R | Material ID | For all ASP material of the character, the ASP Character Panel will assign an independent per-material ID. |
| G | Color Luminance | The color brightness of the renderer's albedo (including albedo map), which is a grayscale of color from 0 to 1. |
| B | Outline Weight | B channel value of Vertex Color, if set to 0, the outline will be forced to not be displayed. |
| A | None | Reserved for self-expansion. |

Material ID is very important. For example, screen-space outlines and other post-processing effects (such as tone mapping) rely on material IDs to correctly identify pixels belonging to ASP-rendered characters. This allows for the application of specific effects to those pixels, or optimizations by skipping pixels that don't require those effects.

In addition, the Material Pass also writes a separate depth map for the renderer. This is necessary because screen space shaders, like screen space outline, need depth information to determine if there are other objects (using non-ASP materials) in front of the character. Only then can they correctly apply the occlusion logic.  This is also why screen space outline cannot be applied to translucent objects – they simply don't provide the depth data that these operation require.

# ASP Shadow Map

---

When a character renderer's material uses the **ASP/Character** or **ASP/Eye Shader**, the shadows of these renderers will be written into the **ASP Shadow Map**. In other words, this is a shadow map that only contains characters, and does not contain shadows of dynamic or static objects that use other shaders.

![Untitled](About%20ASP%E2%80%99s%20Render%20Passes%20dc4c24e96e204d8e826296e185fc0c71/Untitled.png)

The **ASP Shadow Map** Renderer Feature provides some parameters for users to customize

| Parameter Name | Description |
| --- | --- |
| Character Shadow Map Resolution | The size of the ASP Shadow Map, with three sizes to choose from: 1024x1048, 2048x2048, and 4096x4096 |
| Clip Distance | The farthest rendering distance of the ASP Shadow Map |
| Cascade Count | The number of cascade of the Cascade Shadow Map, with support for up to 4 cascades. |
| Shaodw Fade Ratio | The fade out level of the ASP Shadow Map, if set to 0 there will be no fade out at all, and when the distance from the camera exceeds the clip distance, you will see the shadow being clipped directly, the recommended setting is 0.5~1 |

# ASP Depth Offset Shadow

---

The forehead part of the character rendering in anime character usually has more detailed hair shadows, which is difficult to reproduce with traditional shadow maps.
At the same time, because ASP rendered characters usually do not have self-shadowing (especially on the face), we render the depth of hair that meet the set Layer and rendering layer mask to an RT, and sample this depth after offsetting it. By doing so, we get hair shadows on the face. The Depth Offset Shadow can be use to give character extra detail such as hair shadow, cloth shadow on the thigh..etc.

![Untitled](About%20ASP%E2%80%99s%20Render%20Passes%20dc4c24e96e204d8e826296e185fc0c71/Untitled%201.png)

<aside>
💡 If the same material is both the caster and receiver of a depth offset shadow, the ASP shader will use the material ID to avoid self-shadowing. Therefore, the same material will not receive the depth offset shadow cast by itself.

</aside>