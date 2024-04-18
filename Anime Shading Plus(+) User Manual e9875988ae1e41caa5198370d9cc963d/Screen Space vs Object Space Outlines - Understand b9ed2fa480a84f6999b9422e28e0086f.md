# Screen Space vs. Object Space Outlines - Understand the Differences

ASP offers both screen space and object space outlines as optional features, 

allowing users to enable one of them or both, depending on their needs. This page will explain the pros and cons of each method.

## Screen Space Outlines

---

**Pros:**

- **Better inner outlines:** 
This method provide a more detailed outline on inner parts of the character like clothing, accessories, and other attached objects.
- **Precise and consistent outler lines:** It produces an accurate outlines around the character.
- **Performance is fixed(based on resolution):** The required processing power is directly proportional to the game's resolution, remaining constant for a given resolution regardless of the number of characters on screen.

**Cons:**

- **Thickness issues at distance:** Since the calculation is based on individual pixels on the screen during post-processing, the outline thickness remains constant regardless of the character's distance from the camera. This can lead to overly thick outlines for distant characters. (ASP provides distance-based color and weight fading to mitigate this issue.)
- **Complex setup and parameters:** Similar to the previous point, being a full-screen post-processing effect, it does require extensive experimentation to achieve desired results for different characters, as ideal parameter setup may vary. The parameter settings can also be quite intricate.
- **Limited control per vertex/character:** Fine-tuning outline thickness for individual vertices or characters is challenging. ASP provide vertex color-based mask to reduce outline weight.

## Object Space Outlines

---

**Pros:**

- **Independent control:** Thickness and color adjustments are independent for each character and mesh.
- **Vertex-level customization:** The outline thickness can be adjusted for each vertex individually.
- **Simple setup:** The configuration process is straightforward and user-friendly.

**Cons:**

- **Increased draw calls:** This method utilizes back-face and normal extrusion (the inverted-hull method), leading to an increase in draw calls for each mesh that need object space outline. This can significantly impact performance when the skinned mesh character count increases.
- **Requirement for smooth normals:** Using the model's own normals may result in inconsistent outline thickness or breaks in the outline. Baking smooth normals into the mesh is necessary for achieving optimal results. (ASP provides a tool for baking smooth normals into UV4.)