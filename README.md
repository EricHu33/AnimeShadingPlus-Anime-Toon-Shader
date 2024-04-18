# About Anime Shading Plus

---

Anime Shading Plus (+), or ASP for short, is a Unity plugin specially designed for rendering anime-style characters. It helps game developers render 3D characters in the Unity engine with a style close to traditional cel-shading or even more stylized anime character.

# Why Anime Shading Plus

---

Toon shaders are one of the most widely used shader types in Unity, and there are countless discussion and articles about toon shader on the Internet. However, over the years, I feel that there is no plugin on the Unity Asset Store or Github that meets all of the following conditions at the same time:

- Shader dedicated to rendering JRPG, anime-style characters
- ShadowMap specially drawn for cel-shaded characters to prevent ugly self shadowing.
- Good inner and outer outline effects (Screen Space Outline and Mesh-based Outline for characters)
- Post-processing effects for JRPG, anime-style characters (e.g. Tonemapping)
- Special handling of multiple light sources and ambient lighting (indirect light sources) for cel-shaded characters
- Option to mix standard PBR and toon shading.
- Additional tools to improve workflow such as face shadow map baking tool and smoothed normal baking tool for mesh-based outline.

However, I believe that each of these feature is indispensable for achieving high-quality JRPG-like, anime-style character rendering. Therefore, I decided to integrate the above functions into a single plugin on the URP pipeline of Unity.

I believe that this plugin has the stability/performance/completeness to be a production-ready product for PC platforms. At the same time, it can also be used as a based shader to extend upon, for projects that require anime style characters.

# Feature Highlights

---

## 1. A shader that is specifically designed to render anime-style characters.

- The shader includes a variety of features, such as cartoon lighting, stylized PBR lighting parameters, rim light, MatCap reflection, subsurface scattering, and FOV correction…and may more.
- ASP also provides a baking tool for SDF-based face shadow maps, which are commonly used to render anime character faces in games.
- A shader specifically for rendering anime character eyes.

![Untitled](About%20Anime%20Shading%20Plus%20f339786e15584d20855bdefec9e35bfe/Untitled.png)

![Untitled](About%20Anime%20Shading%20Plus%20f339786e15584d20855bdefec9e35bfe/Untitled%201.png)

## 2. **Character-Only Shadow Maps and Depth-Offset Shadows**

To solve the problem of low-quality self-shadowing on characters in toon rendering, ASP supports rendering characters separately to a separated shadow map. This means that two shadow maps are used in the scene: one built-in Unity shadow map that does not include characters, and another shadow map that only includes characters.

To increase character detail, ASP also supports specifying Renderers to render shadows based on offseted depth buffer.

![Untitled](About%20Anime%20Shading%20Plus%20f339786e15584d20855bdefec9e35bfe/Untitled%202.png)

![Untitled](About%20Anime%20Shading%20Plus%20f339786e15584d20855bdefec9e35bfe/Untitled%203.png)

## 3. **Tone Mapping Shader Designed For Anime Characters**

Traditional full-screen tone mapping can reduce saturation, which is not ideal for anime characters. To address this, ASP provides a tone mapping that can adjust the strength of the effect based on the pixels occupied by the characters on the screen. This allows anime characters to retain their origin colors even in a PBR environemt scene that required tone mapping.

![Untitled](About%20Anime%20Shading%20Plus%20f339786e15584d20855bdefec9e35bfe/Untitled%204.png)

## 4. **Screen Space and Mesh-based Outlines**

ASP provides comprehensive outlining features for characters, both in screen-space and model-space. Screen-space outlines can be drawn based on multiple factors such as depth/normal/color..etc.
The screen space outline has it’s own FXAA as well.
ASP also provide extra control over the outline via vertex color and fading effect based on distance to the camera.

<aside>
💡 ASP also provides tools for baking smooth normals for model-space outlines.

</aside>

![Untitled](About%20Anime%20Shading%20Plus%20f339786e15584d20855bdefec9e35bfe/Untitled%205.png)

## 5. **Cel-Shaded Multi-Light and Ambient Light (Indirect Light) Handling**

To render high quality cel-shaded characters, ASP provides an option to flatten the non-indirect light from ambient light and additional lighting result.
This can eliminate the 3D-ish feel of the characters and achieve a rendering result that is closer to the 2D, cel-shaded style.

![Untitled](About%20Anime%20Shading%20Plus%20f339786e15584d20855bdefec9e35bfe/Untitled%206.png)



---

[**Environment and Limitations - MUST READ**](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/Environment%20and%20Limitations%20-%20MUST%20READ%208b90c36f999d4135b32f86e8e3603d9f.md)

# **Instructions and Usage Examples**

---

[**Installation Instructions and Prerequisites**](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/Installation%20Instructions%20and%20Prerequisites%205f0a72aeff00486d9b204b62c99a8035.md)

[Setup ASP Character Panel ](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/Setup%20ASP%20Character%20Panel%200c922c2343194cebb63e8c9fdf49abd1.md)

[Character Rendering Example - Cel Shading](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168.md)

[Character Rendering Example - Stylize CelShading/PBR](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/Character%20Rendering%20Example%20-%20Stylize%20CelShading%20P%20e32b26f68a5f4332b5271e547152fb8d.md)

[ASP Character Panel Feature Guide](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/ASP%20Character%20Panel%20Feature%20Guide%20d7b39661c1f245e79b230fbfd60e3108.md)

[**Setup Character Shadow - ASP’s Shadow Solution**](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/Setup%20Character%20Shadow%20-%20ASP%E2%80%99s%20Shadow%20Solution%20a0426bfd61cd49a58c877e54d27fc317.md)

[**Character Shadow Setup Guide**](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/Character%20Shadow%20Setup%20Guide%201ebc2c7bb7324ff78f3bc2ca70bc8940.md)

[Surface Options- FOV Correction and Dithering](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/Surface%20Options-%20FOV%20Correction%20and%20Dithering%20476e51d40c3c42298dda77a6faea1357.md)

[Face Shadow Map- Creation & Baking Workflow](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/Face%20Shadow%20Map-%20Creation%20&%20Baking%20Workflow%20d3b8769021e04683a2f2ae4cf16ac810.md)

[Color of The Received Shadow](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/Color%20of%20The%20Received%20Shadow%2088d9ff8c09a6499c97c50e7c9a5a8364.md)

[Eyes(Anime-like) Setup Guide](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/Eyes(Anime-like)%20Setup%20Guide%20ea4ccf4c535e4f33a189b3b670eff28e.md)

[
**How to Make Non-ASP Shaders Receive Character-Only Shadows**](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/How%20to%20Make%20Non-ASP%20Shaders%20Receive%20Character-Only%206cf1a9caf040454c962e06c79436b873.md)

[Screen Space Outline Setup Guide](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0.md)

[**Object Space Outline Setup / Smooth Normal Bake Flow**](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/Object%20Space%20Outline%20Setup%20Smooth%20Normal%20Bake%20Flow%209d066f2426a644ed99fb32649bb5404d.md)

[Screen Space vs. **Object** Space Outlines - Understand the Differences](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/Screen%20Space%20vs%20Object%20Space%20Outlines%20-%20Understand%20b9ed2fa480a84f6999b9422e28e0086f.md)

[ASP’s Tone Mapping](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/ASP%E2%80%99s%20Tone%20Mapping%201e748b2fc6094f18a024a8c7a69c8ce2.md)

[Screen Space Lens Flare (Experimental) ported to Unity 2021/2022](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/Screen%20Space%20Lens%20Flare%20(Experimental)%20ported%20to%20U%206ebca12a1cb94c97822877b2341b5e80.md)

[**Building and Packaging Shaders - Important**](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/Building%20and%20Packaging%20Shaders%20-%20Important%20d5138d321fbd4daa8b36568893073651.md)

[About Character Models Featured in the User Manual](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/About%20Character%20Models%20Featured%20in%20the%20User%20Manual%206d41e2d5b80a440e82eb9ed497aeefd4.md)

# Troubleshooting

---
[Common issues](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/Common%20issues%20f025e7a513024970a5f802fa9d1ebeb3.md)

# Others

---

[Optimizing Skinned Mesh Renderer Performance in Unity](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/Optimizing%20Skinned%20Mesh%20Renderer%20Performance%20in%20Un%200614fd760ef64a6696f17baccb89745d.md)

[**Performance of Different Shaders in ASP**](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/Performance%20of%20Different%20Shaders%20in%20ASP%202d040665d6374f17a36f0f6de71ce626.md)

[About ASP’s Render Passes ](Anime%20Shading%20Plus(+)%20User%20Manual%20e9875988ae1e41caa5198370d9cc963d/About%20ASP%E2%80%99s%20Render%20Passes%20dc4c24e96e204d8e826296e185fc0c71.md)