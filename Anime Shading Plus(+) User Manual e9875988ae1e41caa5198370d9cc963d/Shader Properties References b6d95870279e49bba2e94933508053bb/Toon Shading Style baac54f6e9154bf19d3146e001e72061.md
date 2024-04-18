# Toon Shading Style

![Untitled](Toon%20Shading%20Style%20baac54f6e9154bf19d3146e001e72061/Untitled.png)

In the material editor for ASP/Character, there are 3 Toon Shading Style modes to choose from at the top - CelShading, StylizePBR, and Face. The material editor will display different Shader property parameters based on the selected mode. Use different textures and parameters to adjust the effect for different material needs.

### **CelShading**

---

Suitable for traditional Japanese cel-shaded characters and portrait art characters commonly seen in JRPGs, using Ramp Lighting.

### StylizePBR

---

This mode can mix the lighting results calculated from the Ramp Shading and the Smoothness/Metallic workflow in the standard PBR, and provides parameters for stylized BRDF Specular. It is suitable for situations where you want to emphasize materials such as metal and leather while retaining the cartoon rendering effect.

### Face

---

When directly applied toon shading to the face model of a 3D characte, It often leads to unsightly shadows. The common practice is to manually modify the normal or use a face shadow map. This mode provides parameters for setting the face shadow map.

<aside>
💡 The plugin also includes an editor tool for generating face shadow SDF maps.

</aside>

<aside>
💡 The functional categories and detailed parameters displayed in the three modes are slightly different. For example, under the Specular category, CelShading provides a second color for falloff, while StylizePBR does not.

</aside>