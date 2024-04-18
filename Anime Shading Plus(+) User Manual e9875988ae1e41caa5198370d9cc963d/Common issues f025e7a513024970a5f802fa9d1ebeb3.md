# Common issues

# Q: After building the executable, the outline/tonemapping effect disappears

---

A : 

The outline/tone mapping shader is most likely not packaged into th executable file. Please refer to [**Building and Packaging Shaders - Important**](Building%20and%20Packaging%20Shaders%20-%20Important%20d5138d321fbd4daa8b36568893073651.md)。

# Q: **In the editor, characters using ASP/Character shader do not have outline and tonemapping effects**

---

A : 

Please check in the GUI of the [Setup ASP Character Panel ](Setup%20ASP%20Character%20Panel%200c922c2343194cebb63e8c9fdf49abd1.md) that the screen space outline renderer feature is set up correctly and enabled. You can also refer to [Screen Space Outline Setup Guide](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0.md).

# Q: **When static objects (buildings, props) in the environment use ASP/Character, GI is not baked into the lightmap.**

---

A : 

The ASP shader is only for anime style characters and does not support baking GI into lightmap. Please do not use asp/character for static objects.

# Q: **Clicking the Bake Smooth Normals button does not respond/Using UV4 as Mesh-Based Outline normal source gives incorrect results.**

---

A :

Please check if **com.unity.collections 1.5.1** or later is installed correctly in the Package Manager.

# Q: I can't select any existing ramp textures when I open the ramp lighting map editor.

---

A : 

The ramp map editor searches for textures specifically within the **Assets/ASP/** folder and it’s sub folders. Textures in other locations won't show up in the editor. This limitation is designed to improve performance.  In larger projects with many textures, searching everywhere would significantly increase the time it takes for the ramp map editor to display results.