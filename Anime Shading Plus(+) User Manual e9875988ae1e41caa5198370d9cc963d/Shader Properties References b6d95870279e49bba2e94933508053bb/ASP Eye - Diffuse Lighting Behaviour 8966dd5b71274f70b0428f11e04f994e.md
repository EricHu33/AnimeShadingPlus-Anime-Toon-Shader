# ASP/Eye - Diffuse/Lighting Behaviour

## Properties

---

| Property Name | Description |
| --- | --- |
| Eye Lighting Mode | Determines the eye lighting model. There are two modes: Lambert and Flat. |
|      - Lambert Lighting | Regular Lambert Diffuse lighting. |
|      - Flat Lighting | Flattened lighting, each pixel of the object will change uniformly based on the direction of the light source. |
| Darkest Flat Color | 當啟用Flat Lighing時可選擇，控制Flat lighting時背光時的顏色。 |
| Received Shadow Behavior | Controls how the shadow color is behave when receiving shadows from the ShadowMap. |
|      - Unity Default | Can be selected in Lambert Lighting mode, uses the default Unity shadow color as the shadow color. |
|      - Use Darkest Flat Color | Can be selected in Flat Lighting mode, uses Darkest Flat Color as the shadow color. |
|      - Custom Color | Uses Custom Received Shadow Color as the shadow color. |
| Indirect GI Source | Controls the environment indirect lighting received by the current pixel. If the scene lighting is baked, the source of indirect GI will be the spherical harmonic lighting information stored in the light probe. If there is no baking, the source of this spherical harmonic lighting will be the skybox. |
|      - SampleSH | Use the indirect GI obtained by sampling the spherical harmonic information. |
|      - SampleSH_Flatten | Flatten the sampled spherical harmonic lighting, the indirect GI obtained by sampling the entire material will be a single color. |
|      - Color | Do not sample environment lighting, use Override GI Color instead. |
| Override GI Color | A specified color to replace environment lighting. |
| Flatten Additional Lighting | Whether to flatten the lighting results from additional lights |
| Environment Reflections | Whether or not to include indirect specular lighting from the PBR model in indirect GI. (In Unity, the reflection source will be the result of sampling a nearby reflection probe or the skybox if no reflection probe present) |

![Untitled](ASP%20Eye%20-%20Diffuse%20Lighting%20Behaviour%208966dd5b71274f70b0428f11e04f994e/Untitled.png)