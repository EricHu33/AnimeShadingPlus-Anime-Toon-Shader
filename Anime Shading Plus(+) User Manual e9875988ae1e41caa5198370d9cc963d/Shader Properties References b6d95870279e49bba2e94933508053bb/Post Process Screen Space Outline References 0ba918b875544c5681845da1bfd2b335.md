# Post Process Screen Space Outline References

The ASP Screen Space Outline component can be added to a Volume to configure the parameters of screen-space outlines. This page lists the parameters in each category according to the categories on the UI.

---

![Untitled](Post%20Process%20Screen%20Space%20Outline%20References%200ba918b875544c5681845da1bfd2b335/Untitled.png)

# General

---

| Parameter Name | Description |
| --- | --- |
| Enable Outline | Whether to enable screen-space outline |
| Apply FXAA | Whether to apply an additional FXAA anti-aliasing to the outline |
| OutlineWidth | Outline width |
| OutlineColor | Outline color |

# Different Types of Edge

---

| Parameter Name | Description |
| --- | --- |
| Enable Outerline | Whether to enable outlines based on the object's outer contour |
|  |  |
| Enable Material Edge | Whether to enable outlines based on the Material ID |
| Material Edge Threshold | The threshold for detecting Material Edge |
| Material Edge Weight | The weight for calculating Material Edge |
| Material Edge Bias  | Controls the offset for determining Material Edge. A larger bias reduces noise but results in less detail overall. |
|  |  |
| Enable Albedo Edge | Whether to enable outlines based on the Albedo color. This edge  type determines the outline pixels by using the color of the object's albedo texture. |
| Material Albedo Threshold | The threshold for detecting Albedo Edge |
| Material Albedo Weight | The weight for calculating Albedo Edge |
| Material Albedo Bias  | Controls the offset for determining Albedo Edge. A larger bias reduces noise but results in less detail overall. |
|  |  |
| Enable Depth Edge | Whether to enable outlines based on the camera depth. This edge type determines the outline pixels by using the current camera depth. |
| Depth Edge Threshold | The threshold for detecting Depth Edge |
| Depth Edge Weight | The weight for calculating Depth Edge |
| Depth Edge Bias | Controls the offset for determining Material Edge. A larger bias reduces noise but results in less detail overall. 
For Depth Edge, it is recommended to not set the bias lower than 2. |
|  |  |
| Enable Normals Edge | Whether to enable outlines based on the world space normal. This edge type determines the outline pixels by using the current _CameraNormalsTexture. 

Please note that the character shader in ASP shader’s DepthNormal Pass has been modified, So the _cameraNoramlTexture did not contains normal mapped normal for those character (only geometry normal). The reason is normal mapped normal usually create too much unwanted edge. |
| Normals Edge Threshold | The threshold for detecting Normals Edge |
| Normals Edge Weight | The weight for calculating Normals Edge |
| Normals Edge Bias | Controls the offset for determining Material Edge. A larger bias reduces noise but results in less detail overall. 
For Normals Edge, It is recommended to not set the bias lower than 2 or 3. |

> The parameters of different types of edge detection algorithms usually include Threshold, Weight, and Bias. In the simplest sense, edge detection is performed using the following equation. Therefore, lowering the threshold or increasing the weight will make it more likely that a pixel will be classified as an edge.
> 
> 
> ![Untitled](Post%20Process%20Screen%20Space%20Outline%20References%200ba918b875544c5681845da1bfd2b335/Untitled%201.png)
> 

<aside>
💡 Users can using the B channel of the model's vertex color as an additional mask for further control the weight of the current pixel. When the value of vertex color.b is 0, the outline will not be displayed at all. When the value is 1, no mask will be applied.

For example, for areas where you don't want the outline to appear (such as the eyeballs and around the nose), you can directly set the vertex color.b of these vertex to 0 in a your DCC (such as Blender or Substance Painter).

</aside>

# Fade out the color, weight, and width of the outline base on distance

---

![Untitled](Post%20Process%20Screen%20Space%20Outline%20References%200ba918b875544c5681845da1bfd2b335/Untitled%202.png)

| Parameter Name | Description |
| --- | --- |
| Fading Weight By Distance | wheather enable distance fade for weight |
| Fading Color By Distance | wheather enable distance fade for color |
| Color Weight Fading StartEnd Distance | The Start/End distance of the distance-based color/weight fading effect. |
| Fading Width By Distance | wheather enable distance fade for outline width  |
| Width Fading StartEnd Distance | The Start/End distance of the distance-based width fading effect. |