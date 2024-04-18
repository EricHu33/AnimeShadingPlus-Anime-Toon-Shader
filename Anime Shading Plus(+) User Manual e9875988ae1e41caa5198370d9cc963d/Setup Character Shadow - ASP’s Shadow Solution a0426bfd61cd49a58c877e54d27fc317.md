# Setup Character Shadow - ASP’s Shadow Solution

Before setting up shadows, this page will explain why ASP uses at least one additional shadow map.

---

# **Self-shadowing problems of cel-shading characters**

---

In general, when using the built-in shadow map, the self-shadowing effect on the character is not ideal. This is because the size of the shadow map is limited - the same shadow map must be able to contain the entire scene, and the characters in the scene usually only occupy a very small part of the shadow map (even with Unity's built-in 4-layer Cascaded Shadow Map, it is still not enough).

![Untitled](Setup%20Character%20Shadow%20-%20ASP%E2%80%99s%20Shadow%20Solution%20a0426bfd61cd49a58c877e54d27fc317/Untitled.png)

In the image above, the shadows cast by the hair and face mesh will produce undesirable self-shadowing on themselves because the shadow map is not large enough.

Simply changing the ShadowCaster of the hair and face mesh to Off can avoid the self-shadowing from the face and hair, but the character's shadow on the ground will also be missing the face and hair.

![Untitled](Setup%20Character%20Shadow%20-%20ASP%E2%80%99s%20Shadow%20Solution%20a0426bfd61cd49a58c877e54d27fc317/Untitled%201.png)

# Solution to self-shadowing - Character-Only Shadow Map

---

ASP chooses to use a method that can effectively solve self-shadowing - render the character to a separate shadow map. The character itself only receives shadows from Unity's built-in shadow map, which does not include the character. The general scene objects receive shadows from the shadow map containing the character and the built-in shadow map - a total of two shadow maps. This is not applicable to all types of games, but for anime style character it can already achieve sufficiently convincing results.

![Untitled](Setup%20Character%20Shadow%20-%20ASP%E2%80%99s%20Shadow%20Solution%20a0426bfd61cd49a58c877e54d27fc317/Untitled%202.png)

The character itself can still receive shadows from Unity's built-in shadow map.

![Untitled](Setup%20Character%20Shadow%20-%20ASP%E2%80%99s%20Shadow%20Solution%20a0426bfd61cd49a58c877e54d27fc317/Untitled%203.png)

Or, you can selectively enable specific materials to receive character shadows, such as making the leg material to be able to receive character shadows.

![Untitled](Setup%20Character%20Shadow%20-%20ASP%E2%80%99s%20Shadow%20Solution%20a0426bfd61cd49a58c877e54d27fc317/Untitled%204.png)

# Screen-Space Depth-Offset Shadows

---

Although using two shadow maps can avoid self-shadowing of resolution-limited shadow map, it also loses the shadow details of the character itself. ASP provides an additional pass that relies on the offset depth buffer to create shadows similar to those that appear on the face and body of characters in animation. This can be used to make up for shadow details such as hair shadow on the face.

![Untitled](Setup%20Character%20Shadow%20-%20ASP%E2%80%99s%20Shadow%20Solution%20a0426bfd61cd49a58c877e54d27fc317/Untitled%205.png)

On the next page, I will demonstrate how to use the **ASP Character Panel** to quickly setup shadows for character in the Unity editor.

<aside>
⏭️ Go to next page → [**Character Shadow Setup Guide**](Character%20Shadow%20Setup%20Guide%201ebc2c7bb7324ff78f3bc2ca70bc8940.md)

</aside>