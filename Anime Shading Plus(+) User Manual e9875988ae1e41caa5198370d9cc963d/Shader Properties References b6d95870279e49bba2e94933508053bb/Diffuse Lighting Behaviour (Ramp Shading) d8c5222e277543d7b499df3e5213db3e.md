# Diffuse/Lighting Behaviour (Ramp Shading)

此分類的屬性控制主要的光照效果。

此分類下，使用不同的 [Toon Shading Style](Toon%20Shading%20Style%20baac54f6e9154bf19d3146e001e72061.md)，能夠設定不同的貼圖與參數。

## CelShading Properties

---

| Property Name | Description |
| --- | --- |
| Workflow Space | Determines whether to use gamma workflow or linear workflow when calculating ramp lighting. For non-StylizePBR materials, either workflow can be used. |
| Ramp Lighting Map | A gradient map that controls the brightness and color of the main light source on the material. |
| SSSRamp Layer | Controls whether to sample an additional gradient map and overlay a layer of subsurface scattering effects. |
| SSS Ramp Map | A gradient map used for subsurface scattering, the sampling logic is independent of lighting and uses the normal and view direction of the object. |
| Received Shadow Behaviour | Controls how the shadow color is behave when receiving shadows from the ShadowMap. |
|      - Use Ramp End | Use the color at the leftmost end of the Ramp Lighting Map as the shadow color. |
|      - Color | Use the Received Shadow Color as the shadow color. |
|      - DarkenRampLightByColor | Preserve the current pixel color and blend it with the Received Shadow Color to darken it. |
| Indirect GI Source | Controls the environment indirect lighting received by the current pixel. If the scene lighting is baked, the source of indirect GI will be the spherical harmonic lighting information stored in the light probe. If there is no baking, the source of this spherical harmonic lighting will be the skybox. |
| - SampleSH | Use the indirect GI obtained by sampling the spherical harmonic information. |
| - SampleSH_Flatten | Flatten the sampled spherical harmonic lighting, the indirect GI obtained by sampling the entire material will be a single color. |
| - Color | Do not sample environment lighting, use Override GI Color instead. |
| Override GI Color | A specified color to replace environment lighting. |
| Flatten Additional Lighting | Whether to flatten the lighting results from additional lights |

![Untitled](Diffuse%20Lighting%20Behaviour%20(Ramp%20Shading)%20d8c5222e277543d7b499df3e5213db3e/Untitled.png)

<aside>
💡 For Face Mode, the parameters in this section are same as CelShading mode.

</aside>

## StylizePBR Properties

---

<aside>
💡 In the Diffuse / Lighting Behavior category, most of the parameters in StylizePBR mode are the same as those in CelShading mode. The exceptions are as follows:

</aside>

| Property Name | Description |
| --- | --- |
| SSSRamp Layer (Unsupported) | There is no second layer subsurface scattering effect in StylizePBR mode. |
| PBR Influence On Direct Lighting | Controls the blend between Ramp Lighting and direct diffuse from the standard PBR model, with a range of 0 to 1.

Set to 0 - Direct lighting is calculated entirely based on the result of sampling the Ramp Lighting Map.

Set to 1 - Direct lighting is calculated entirely based on direct diffuse under the standard PBR model.
 |
| Environment Reflection | Whether or not to include indirect specular lighting from the PBR model in indirect GI. (In Unity, the reflection source will be the result of sampling a nearby reflection probe or the skybox if no reflection probe present) |

## **About texture locations of Ramp Lighting Map**

---

Currently, The ramp map editor track **every** textures under **Assets/ASP/** folder and it’s ****subfolders, textures located in other folder won’t be query during the searching process. 
This restriction is solely for reduce the query time. Without this rule the ramp map query time might become very long for a larger project that contains thousands of textures.