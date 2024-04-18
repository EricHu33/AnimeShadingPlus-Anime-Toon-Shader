# Character Rendering Example - Stylize CelShading/PBR

This page will demonstrate how to use the shader in ASP to render the character, getting the result on the right side of below screenshot.

![Untitled](Character%20Rendering%20Example%20-%20Stylize%20CelShading%20P%20e32b26f68a5f4332b5271e547152fb8d/Untitled.png)

---

### About the model used in this page’s demo

> **Disclaimer :** 
I did not made the character model, I only use the model to demo functions of the shader.
I also did some modification of the models uv/material in order to show casing some features in this page.
 
**model source :**
> 
> 
> [[３Dモデル]RUNA QUEST POTATO DRONE[アバター] [VRC]](https://tori-nyan.booth.pm/items/5048032)
> 
> **model creator :** 
> 
> [🍉とりにゃん (@torinyannyan1) on X](https://twitter.com/torinyannyan1)
> 
> concept artist :
> 
> [Радиоволна (@nradiowave) on X](https://twitter.com/nradiowave)
> 

<aside>
💡 Please refer to [](Shader%20Properties%20References%20b6d95870279e49bba2e94933508053bb.md) as well when using the shader

</aside>

## 0. Replace Shader

---

First, setup all material’s target shader to ASP/Character.

## 1. Set up ASP Character Panel Component and configure Shadows

---

Follow the [Setup ASP Character Panel ](Setup%20ASP%20Character%20Panel%200c922c2343194cebb63e8c9fdf49abd1.md) and [**Character Shadow Setup Guide**](Character%20Shadow%20Setup%20Guide%201ebc2c7bb7324ff78f3bc2ca70bc8940.md)  to set up the ASP Character Panel and turn off shadow casting of the current character model to the built-in shadow map. Avoid unnecessary self-shadowing during the process.

![Untitled](Character%20Rendering%20Example%20-%20Stylize%20CelShading%20P%20e32b26f68a5f4332b5271e547152fb8d/Untitled%201.png)

## 2. **Default value of Ramp Map**

---

In the material editor, the **Ramp Lighting Map** under the **Diffuse/Lighting Behaviour** category will use a black-to-white gradient map by default. Resulting a regular lambert lighting.

![Untitled](Character%20Rendering%20Example%20-%20Stylize%20CelShading%20P%20e32b26f68a5f4332b5271e547152fb8d/Untitled%202.png)

## 3. **Create a Ramp Map for Stylize Cel Shading Character**

---

Click the "**+**" button on the **Ramp Lighting Map** editor to add a new **ramp map** to the current material . Compared to the traditional cel-shaded style that is suitable for using FIXED MODE with distinct light and dark boundaries, the ramp map used for stylize cel shading characters can use a smoother gradient.

<aside>
💡 **What is ramp lighting?**
Using a texture ( ramp map ) to define how surfaces respond to the angles between the incoming light and the normal.

</aside>

### 3-1 Ramp Map for Non-Metallic Materials

---

This character model body is divided into metallic and non-metallic parts.
Let's first handle the non-metallic parts - 

1. Open the **Gradient Editor** by click on the ramp light map (or create a new one).
2. Set the **Mode** of the gradient to **Blend(Classic)** mode**.**
3. **Create a multi-color ramp.** Add several color keys to your gradient map. This will provide more colors for the transition.

This gives more smooth color transition on the body parts when lighting it. Compare to the traditional cel shading.

![Untitled](Character%20Rendering%20Example%20-%20Stylize%20CelShading%20P%20e32b26f68a5f4332b5271e547152fb8d/Untitled%203.png)

### 3-2 Ramp Map for Metallic Materials and Stylized PBR Parameters

---

PBR is well suited for metals and leathers materials, and here I will demonstrate how to use **StylizePBR** mode to create a hybrid effect of toon rendering and standard PBR.

1. Switch the **Toon Shading Style** to **StylizePBR** at the top of the material panel.
2. For the metal parts, I use the ramp map in FIXED Mode (personal preference).
3. set the relevant PBR parameters - metallic and Smoothness.

| Property Name | Description |
| --- | --- |
| Metallic | control the metalness  |
| Smoothness | Smoothness, i.e. (1 - roughness) in PBR of other non-Unity renderers |

![Untitled](Character%20Rendering%20Example%20-%20Stylize%20CelShading%20P%20e32b26f68a5f4332b5271e547152fb8d/Untitled%204.png)

**PBR Influence On Direct Lighting -** 

The PBR Influence On Direct Lighting parameter controls the blending ratio between ramp lighting and standard PBR direct diffuse lighting.

For example, setting it to 1 will completely ignore the ramp map's lighting result and use the standard PBR diffuse lighting as result. Here it is set to 0.35 - so the result will be a mix of 65% ramp map lighting and 35% standard PBR diffuse lighting.

![under the current settings, the material’s diffuse lighting will have a stronger ambient reflection compare to pure ramp ligthing.](Character%20Rendering%20Example%20-%20Stylize%20CelShading%20P%20e32b26f68a5f4332b5271e547152fb8d/Untitled%205.png)

under the current settings, the material’s diffuse lighting will have a stronger ambient reflection compare to pure ramp ligthing.

<aside>
💡 You can also use PBR Texture(**Occlusion/Smoothness/Metallic**) to directly control occlusion, smoothness, and metallicness. The difference from Unity's built-in PBR is that ASP treat the value sampled from R channel as the occlusion, in order to reduce the number of texture sampling.

</aside>

**Specular highlight**

An important element of PBR metallic materials is BRDF specular lighting. In the material inspector, turn on specular highlight and use **specular falloff** to control the softness of the highlight edges.

![Untitled](Character%20Rendering%20Example%20-%20Stylize%20CelShading%20P%20e32b26f68a5f4332b5271e547152fb8d/Untitled%206.png)

At this point, we already have a stylized metal material based on standard PBR.

Finally, to add a layer of customized environment reflection effect, apply a MatCap texture under the MatCap Reflection category.

![Untitled](Character%20Rendering%20Example%20-%20Stylize%20CelShading%20P%20e32b26f68a5f4332b5271e547152fb8d/Untitled%207.png)

<aside>
✨ In CelShading Mode, you can still create cartoon-style metal ref;lection with a appropriate MatCap texture.

</aside>

## 4. **Configure Subsurface Scattering for the Body (Non-Metallic Material)**

---

On the body's non-metallic material, you can set an additional layer of subsurface scattering effect under the **Diffuse/Lighting Behaviour** category. Enable the **SSS Ramp Layer** and add a **SSS ramp map**. The shader will sample the **SSS ramp map** based on the object's normal information and view angle, which will give the material a red translucent feel caused by indirect light passing through the skin and then scattering back into the eyes from the blood vessels. In general, the color of this ramp map should be very light (as shown in the figure below).。

![Untitled](Character%20Rendering%20Example%20-%20Stylize%20CelShading%20P%20e32b26f68a5f4332b5271e547152fb8d/Untitled%208.png)

## 5. Rim Lighting

---

Rim lighting is often used in photography when the subject is backlit. To achieve this effect, select the hair material and enable **Enable Fresnel Rim Lighting** under the **Rim Lighting** category. Then, adjust the parameters accordingly. In this example, I set **Fresnel Rim Lighting Align** to -1. This will cause the rim light to only appear at the edges of the object when it is backlit by the main light.

![Untitled](Character%20Rendering%20Example%20-%20Stylize%20CelShading%20P%20e32b26f68a5f4332b5271e547152fb8d/Untitled%209.png)

## 6. **Using Depth Offset Shadow to Create Hair Shadows on the Forehead**

---

Follow the depth-offset shadow tutorial in the [**Character Shadow Setup Guide**](Character%20Shadow%20Setup%20Guide%201ebc2c7bb7324ff78f3bc2ca70bc8940.md)  **(section 2-4)** to set up the rendering layer mask for depth offset shadow and hair renderer of the character.

![Untitled](Character%20Rendering%20Example%20-%20Stylize%20CelShading%20P%20e32b26f68a5f4332b5271e547152fb8d/Untitled%2010.png)

## 7. Screen Space Outline & Post-Processing (Tone Mapping, Bloom)

---

1. Follow the instruction of  [Screen Space Outline Setup Guide](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0.md) to setup screen space outline, 
2. Follow the instruction of  [ASP’s Tone Mapping](ASP%E2%80%99s%20Tone%20Mapping%201e748b2fc6094f18a024a8c7a69c8ce2.md)  to setup ASP Tone Mapping, 
Then, adjust the Bloom(anime character usually has higher scattering for the bloom effect).

![Untitled](Character%20Rendering%20Example%20-%20Stylize%20CelShading%20P%20e32b26f68a5f4332b5271e547152fb8d/Untitled%2011.png)

## 8. Render Result

---

[Untitled video - Made with Clipchamp (19).mp4](Character%20Rendering%20Example%20-%20Stylize%20CelShading%20P%20e32b26f68a5f4332b5271e547152fb8d/Untitled_video_-_Made_with_Clipchamp_(19).mp4)

![Untitled](Character%20Rendering%20Example%20-%20Stylize%20CelShading%20P%20e32b26f68a5f4332b5271e547152fb8d/Untitled%2012.png)

<aside>
💡 Go to next page → [Face Shadow Map- Creation & Baking Workflow](Face%20Shadow%20Map-%20Creation%20&%20Baking%20Workflow%20d3b8769021e04683a2f2ae4cf16ac810.md)

</aside>