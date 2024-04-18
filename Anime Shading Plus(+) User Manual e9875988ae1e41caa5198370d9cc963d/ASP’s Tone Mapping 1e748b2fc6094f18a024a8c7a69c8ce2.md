# ASP’s Tone Mapping

![Untitled](ASP%E2%80%99s%20Tone%20Mapping%201e748b2fc6094f18a024a8c7a69c8ce2/Untitled.png)

With the tone mapping effect in ASP, you can control settings to make sure your cartoon characters keep their bold, saturated colors

# 1. **Adding the ToneMapping Renderer Feature and Volume Override**(click to expand)

• In the Universal Renderer Data asset used by your project, add **ASP ToneMapping.**

![Untitled](ASP%E2%80%99s%20Tone%20Mapping%201e748b2fc6094f18a024a8c7a69c8ce2/Untitled%201.png)

- In the scene, add a new **Volume** (or use an existing one) and set it to **Global Mode**.
- In the Volume's inspector, select **Add Override**, search for **ASP ToneMapping**, and add it.
- Your Volume should now look like the screenshot below, with **ASP ToneMapping** now visible.

### **What does all those toggles on the left mean?**

- Unity's Volume uses a framework called [Volume Override](https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@14.0/manual/VolumeOverrides.html).
- To make the toggle options on the right take effect, you must first check the **override toggle** on the left. Otherwise, the **default values** of the post-processing effect will be used.

![Untitled](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0/Untitled%204.png)

Use above figure as example, the default value of **Enable Outline** for screen space outline feature is true. Therefore, when this outline's renderer feature is enabled in the renderer data, the outline is already turned on.

# 2. **Set the project's Grading Mode to High Dynamic Range (HDR)** (click to expand)

In order to correctly apply a custom Tone Mapping, the Unity project must set the **Grading Mode** of the URP Asset to **HDR**. 

The reason is:

- If it is set to LDR, Unity will perform an internal color LUT in the middle of Post Processing stage, resulting in an incorrect coloring for custom Tone Mapping shader.
- If it is set to HDR, Unity will perform the color LUT after Tone Mapping is applied.
1. Set the Tone Mapping parameters

![Untitled](ASP%E2%80%99s%20Tone%20Mapping%201e748b2fc6094f18a024a8c7a69c8ce2/Untitled%202.png)

# 3. Tune the Tone Mapping parameters

![Untitled](ASP%E2%80%99s%20Tone%20Mapping%201e748b2fc6094f18a024a8c7a69c8ce2/Untitled%203.png)

| Parameter name | Description |
| --- | --- |
| Tone Map Type | The selected Tone Mapping model (currently only Filmic is available) |
| Filmic Exposure | The exposure of Filmic Tone Mapping |
| Ignore Character Pixels | Whether to skip(or tune down) the tone mapping effect for pixle occupied by ASP/Character and ASP/Eye materials. |
| Character Pixel Tone Map Strength | If Ignore Character Pixels is set to true, the impact of the Tone Mapping effect on the ASP/Character and ASP/Eye materials. |
1. Set the toggle to the left of **Tone Mapping Type** to **true** to enable tone mapping.
2. Set all the **Ignore Character Pixels toggles** to true, you will see the tone mapping effect didn’y apply on pixels occupied by **ASP/Character** and **ASP/Eye materials**.
3. Adjust the **Character Pixel Tone Map Strength** parameter at the bottom to control the impact of Tone Mapping on the character pixels.
    
    <aside>
    💡 0 means that tone mapping will not have any effect on the character pixels at all, and 1 means that there will be no restrictions.
    
    </aside>
    
4. Generally speaking, set **Character Pixel Tone Map Strength**  to range between 0.25 and 0.7 can give ideal result.

<aside>
💡 The curve model used by ASP Tone Mapping is **Filmic tone mapping.** The advantage of using filmic is that this model can use the **exposure** parameter to control the overall exposure.

</aside>