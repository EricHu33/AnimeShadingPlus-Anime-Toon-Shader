# Character Rendering Example - Cel Shading

In this page, I will showcasing how to use the ASP/Character shader to render a cel-shaded character model.

Here's a quick render comparison between using the built-in unlit shader and ASP's shader.

![Untitled](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled.png)

---

### About the model used in this page’s demo

> **Disclaimer :** 
I did not made the character model, I only use the model to demo functions of the shader.
I also did some modification of the model’s uv/material in order to show casing some features in this page.
 
**model source :**
> 
> 
> [【オリジナル3Dモデル】早川葵](https://booth.pm/en/items/5405703)
> 
> **model creator :** 
> 
> [WARPSTAR@3DCG (@WARPSTAR15) on X](https://twitter.com/warpstar15?lang=en)
> 

### 0. Replace Shader

---

First, replace all materials’s target shader to ASP/Character (we will handle eyes on other page). After replaced, select **CelShading** mode under the **Toon Shading Style** at the top, and select **Face** mode for the face material.

<aside>
💡 **If the material is metal or leather (such as metal zippers and accessories on the backpack), you can choose to use StylizePBR and apply the corresponding metallic map, and turn on Specular lighting.**

**For more information on PBR map channels, see** [Albedo/Normal/Emission/OSM Textures](Shader%20Properties%20References%20b6d95870279e49bba2e94933508053bb/Albedo%20Normal%20Emission%20OSM%20Textures%20197cc4c450bc4016a8cc4c2e89dfb6fb.md).

</aside>

### 1. Set up ASP Character Panel Component and configure Shadows

---

Follow the [Setup ASP Character Panel ](Setup%20ASP%20Character%20Panel%200c922c2343194cebb63e8c9fdf49abd1.md) and [**Character Shadow Setup Guide**](Character%20Shadow%20Setup%20Guide%201ebc2c7bb7324ff78f3bc2ca70bc8940.md)  to set up the ASP Character Panel and turn off shadow casting of the current character model to the built-in shadow map. Avoid unnecessary self-shadowing during the process.

![Untitled](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%201.png)

### 2. **Default value of Ramp Map**

---

In the material editor, the **Ramp Lighting Map** under the **Diffuse/Lighting Behaviour** category will use a black-to-white gradient map by default. Resulting a regular lambert lighting.

![Untitled](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%202.png)

### 3. Create a new Ramp Map

---

Click the "**+**" button on the **Ramp Lighting Map** editor to add a new ramp map to the current material. Traditional Cel-shaded style is more suitable for using Fixed mode to create a 2D-ish style with obvious boundaries betwen light/shaded area. After adjusting the ramp map, apply the same ramp map to other materials used by the character (in practice, different materials may apply different ramp maps according to different needs).

<aside>
💡 **What is ramp lighting?**
Using a texture ( ramp map ) to define how surfaces respond to the angles between the incoming light and the normal.

</aside>

We now have a basic 2-step celshading.

![Untitled](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%203.png)

<aside>
💡 **When editing Ramp map, using Fixed mode will automatically change the import settings of ramp map to point sampling, while non-FIXED mode will automatically change to linear sampling.

For more info about the difference of point and linear sampling, see :**

[Unity - Manual:  Using sampler states](https://docs.unity3d.com/Manual/SL-SamplerStates.html)

</aside>

### 4. Subsurface scattering for anime style skin

---

Next, for the materials of the character's skin (e.g - legs, hands, neck, face), in **CelShading** mode, you can set an additional layer of subsurface scattering effect under the **Diffuse/Lighting Behaviour** category. Enable the **SSS Ramp Layer** and add a **SSS ramp map**. The shader will sample the **SSS ramp map** based on the object's normal information and view angle, which will give the material a red translucent feel caused by indirect light passing through the skin and then scattering back into the eyes from the blood vessels. In general, the color of this ramp map should be very light (as shown in the figure below).

![Untitled](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%204.png)

![Untitled](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%205.png)

Without SS

![Untitled](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%206.png)

With SSS

### 5. Flattening the Global Illumination

---

For a cel-shading character, you may consider flattening the indirect light from the environment as well. In the Diffuse category, setting Indirect GI Source to SampleSH_Flatten can turn the ambient light that would otherwise create a 3D sense of the geomotry into a single color.

![Untitled](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%207.png)

![**Regular PBR global illumination color (the base color of the receiving material) enhances the 3D-feel of the model. the gi color is especially noticeable when lowering the main light intensity.**](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%208.png)

**Regular PBR global illumination color (the base color of the receiving material) enhances the 3D-feel of the model. the gi color is especially noticeable when lowering the main light intensity.**

![Flattened global illumination](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%209.png)

Flattened global illumination

<aside>
💡  **Flattened global illumination is also applied to the light from light probes.**

</aside>

### 6. Flattening lighting from additional lights

---

For light sources other than the main light source in the scene (point lights and spot lights), ramp lighting is not applied. This is because ramp lighting usually produce unsatisfactory lighting results and it is too expensive to perform texture sampling of the ramp map for each additonal lights. ASP provides an option to change the lighting model from built-in Lambert lighting to flattened lighting for the additonal lights.

In the **Diffuse** category, toggle **Flatten Additional Lighting** to **true**

![By default, the lighting from multiple light sources will result in a strong 3D-ish feel on the nose of the face.](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%2010.png)

By default, the lighting from multiple light sources will result in a strong 3D-ish feel on the nose of the face.

![After flattening, the 3d-ish feel disappears, and the 2D style is preserved.](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%2011.png)

After flattening, the 3d-ish feel disappears, and the 2D style is preserved.

<aside>
💡 When calculating flattened lighting for additonal lights, only the distance to the light source and the light source intensity are considered. Normal information is no longer effective, so light sources from behind will also illuminate the surface as long as they are within the distance.

This is a method specially designed for anime-style characters, and is not applicable to other non-cel/anime rendering styles.

</aside>

### **7. Rim Lighting**

---

Depending on the needs of your project, some materials may be suitable for rim lighting. In this case, you can choose to use either Fresnel-based rim lighting or depth buffer-based rim lighting.

![Untitled](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%2012.png)

<aside>
💡 For more information on rim lighting, please refer to  [Rim Lighting](Shader%20Properties%20References%20b6d95870279e49bba2e94933508053bb/Rim%20Lighting%205c27a8ad7e9245489f4a19e6c8ca18da.md)

</aside>

### 8. Enable/Disable Specular Lighting

---

Specular lighting is enabled by default. However, if you are not using a specular mask, the area where specular light appear might be too large. Adjust the property accordingly.

<aside>
💡 For more information on rim lighting, please refer to [Specular Highlight](Shader%20Properties%20References%20b6d95870279e49bba2e94933508053bb/Specular%20Highlight%20d239d7fcda504b7ba4570f14ceca40db.md)

</aside>

### 9. Create/Use a Face Shadow Map

---

By using Face Shadow Map, we can prevent the undesired toon lighting on complex face geomety.

![Untitled](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%2013.png)

The setup of a face shadow map deserves a dedicated page for a proper explanation. Please refer to the Face Shadow Map guide - [Face Shadow Map- Creation & Baking Workflow](Face%20Shadow%20Map-%20Creation%20&%20Baking%20Workflow%20d3b8769021e04683a2f2ae4cf16ac810.md) to learn how to create and apply a face shadow map to the character's face material. “

<aside>
💡 **When using Face Mode, the character will only use the leftmost end of the ramp map as the shadow color. The ramp map itself does not create ramp lighting (The lighting will control by the face shadow map).**

</aside>

![Untitled](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%2014.png)

### 10. **Using Depth Offset Shadow to Create Hair Shadows on the Forehead**

1. Follow the depth-offset shadow tutorial in the [**Character Shadow Setup Guide**](Character%20Shadow%20Setup%20Guide%201ebc2c7bb7324ff78f3bc2ca70bc8940.md)  **(section 2-4)** to set up the rendering layer mask for depth offset shadow and hair renderer of the character.

1. In the ASP Character Panel’s **Shadow Behaviours** section, under **ASP Extra Shadow Behaviours**, enable the **Depth Offset Shadow**’s Receive toggle like below figure so the face material can received depth offset shadow.

![Untitled](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%2015.png)

![Untitled](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%2016.png)

After completing the above steps, hair shadows based on depth offset will appear on the character's face.

![Untitled](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%2017.png)

### 11. **Adjusting Screen Space Outline and Using Vertex Color to Control the Outline Weight Mask**

---

1. Follow the Screen Space Outline (Outline) Instructions to set the outline parameters and paint the vertex color mask into the mesh in DCC.
2. Use the debug mode in the screen space outline override to observe the outline of the character and the outline mask(shown as yellow parts in below figure).

![Untitled](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%2018.png)

### 12. Tone Mapping/P

---

Follow the [ASP’s Tone Mapping](ASP%E2%80%99s%20Tone%20Mapping%201e748b2fc6094f18a024a8c7a69c8ce2.md)’s Instructions to adjust the post-processing effect accordingly.

# Final Render Result

---

![Untitled](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%2019.png)

![Untitled](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%2020.png)

![Untitled](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168/Untitled%2021.png)

<aside>
⏭️ Go to next page → [Character Rendering Example - Stylize CelShading/PBR](Character%20Rendering%20Example%20-%20Stylize%20CelShading%20P%20e32b26f68a5f4332b5271e547152fb8d.md)

</aside>