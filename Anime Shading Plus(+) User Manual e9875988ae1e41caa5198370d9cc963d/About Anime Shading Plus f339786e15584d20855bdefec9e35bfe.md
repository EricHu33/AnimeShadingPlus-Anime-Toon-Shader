# About Anime Shading Plus

![StyleSheet.png](About%20Anime%20Shading%20Plus%20f339786e15584d20855bdefec9e35bfe/StyleSheet.png)

# Intro

---

Anime Shading Plus (+), or ASP for short, is a Unity plugin specially designed for rendering anime-style characters. It helps game developers render 3D characters in the Unity engine with a style close to traditional cel-shading or even more stylized anime character.

# Why Anime Shading Plus

---

Toon shaders are one of the most widely used shader types in Unity, and there are countless discussion and articles about toon shader on the Internet. However, over the years, I feel that there is no plugin on the Unity Asset Store that meets all of the following conditions at the same time:

- Shader dedicated to rendering JRPG, anime-style characters
- ShadowMap specially drawn for cel-shaded characters
- Good inner and outer outline effects (Screen Space Outline and Mesh-based Outline for characters)
- Post-processing effects for JRPG, anime-style characters (e.g. Tonemapping)
- Handling of multiple light sources and ambient lighting (indirect light sources) for cel-shaded characters
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