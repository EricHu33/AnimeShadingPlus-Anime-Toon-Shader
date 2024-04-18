# Environment and Limitations (Must Read)

Please read the limitations of this plugin carefully before purchasing.

## **Target Users**

---

- This plugin is designed for developers who need to render anime characters in Unity. It is recommended that users have the ability to independently operate third-party DCC such as adjust the vertex color or UV of the model.
- Studios/teams that need this type of Shader (or use it as a base for their own needs) for 3D character projects with a target style of Japanese cartoon rendering.
- Developers who want to learn how to write Custom Shaders/Passes in Unity's URP pipeline.

## **Project Environment**

---

The Scripts/Shader code used in this plugin is compatible with the following versions of Unity:

- Unity 2021.3.16f1+
- Unity 2022.3.20f1+
- Unity 2023.2.5f1~Unity 2023.2.15f1

 Please note that Unity 2023 has not yet entered the LTS phase(stable release of 2023.3), so versions newer than 2023.2.15f1 may have unexpected bugs.

- **Not work with** Unity 6(original Unity 2023.3 beta) and **URP 17** yet. There’s some breaking changes introduced in URP 17. An update that resolve those errors and make ASP work in Unity 6 under compatible mode(Non-RenderGraph powered project) will come out later.
- This plugin **does not yet support** the **RenderGraph** introduced in Unity 6(Unity 2023.3). It is planned & on my roadmap to support RenderGraph **in the future.**

<aside>
💡 **Please note that the minor version number is still very important**(e.g → 2021.3.**16**). Unity makes a lot of changes between minor versions, including breaking changes of APIs and bug fixes. If you use a minor version older than the ones listed above, there is a good chance that the plugin will not work properly. If your project cannot be upgraded to the same or newer minor version as the ones listed above, please do not purchase this plugin.

</aside>

## **Rendering Environment**

---

- Render Pipeline - Only supports Universal Render Pipeline (12 (**Unity 2021.3.16f1+**), 14 (**Unity 2022.3.20f1+**), 16 (**Unity 2023.2.5f1~Unity 2023.2.15f1**) ), and will only support URP in the future.
- **Only supports Forward/Forward+ Rendering Path.**

## **Target Platform**

---

- PC/Mac/iOS are the primary target platforms. This plugin has not been optimized for Android/Low-end devices (it is theoretically possible. When creating the various features of this plugin, I considered performance as much as possible, but in some cases I chose flexibility at the expense of performance. For more information, please see the section on performance).
- VR/XR is not yet supported because I have not done any testing on Stereo Rendering/Foveat Rendering. Future updates may add support for VR.
- Consoles (PS5/PS4/Xbox/Switch) have not been tested. If you want to use the provided shader/script on console, make sure you have the resource to resolve potential issue.

## Others

---

- The shader in this plugin is only applicable for rendering anime-style characters. During baking process of the scene lighting , this Shader does not contribute to light maps and light probes, so it is not applicable to use it on static scene objects.
- Some effects are not applicable to Transparent materials.
- GPU Instancing is not supported, but SRP batcher is supported.

<aside>
💡 Although the characters rendered with this plugin will not contribute GI to light maps and light probes as a light source, the shader supports **receive** indirect lighting (baked lighting / APV) through light probes,

</aside>