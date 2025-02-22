# Face Shadow Map- Creation and Baking Workflow

# Introduction to Face Shadow Textures

When rendering cartoon characters, it is common to see broken light and shadow changes on the face. This is mainly because the normal of the character's face tends to be more complex than other parts of the body, but for simplified lighting logic (e.g Cel Shading), it will resulting a undesired visual appearance.

Common solutions include usingええroxy normal or manually modifying the model normal in third-party DCC, and using SDF-based face shadow map.

Face shadow map is the most efficient method in my opinion. It has high controllability for artists and does not take as much time as modifying normals manually . Therefore, the **Face** mode of **ASP/Characte**r shader supports the use of face shadow map, and provides a tool to bake individiual hand-painted maps into SDF-based face shadow map.

### Before applying face shadow map

![Untitled video - Made with Clipchamp (1).gif](Face%20Shadow%20Map-%20Creation%20and%20Baking%20Workflow%20d3b8769021e04683a2f2ae4cf16ac810/Untitled_video_-_Made_with_Clipchamp_(1).gif)

### After applying face shadow map

![Untitled video - Made with Clipchamp.gif](Face%20Shadow%20Map-%20Creation%20and%20Baking%20Workflow%20d3b8769021e04683a2f2ae4cf16ac810/Untitled_video_-_Made_with_Clipchamp.gif)

# **Create a Face Shadow Map**

## 1. Hand paint the map

---

First, according to the uv unwrapped face, draw 9 textures. In the **Face** mode o**f ASP/Character** shader, there is an option to select the UV channel used by the texture (UV0~UV3). Therefore, you can choose to use the existing UV channel in DCC or do uv unwrap in the new UV channel based on the face shadow texture.

![Untitled](Face%20Shadow%20Map-%20Creation%20and%20Baking%20Workflow%20d3b8769021e04683a2f2ae4cf16ac810/Untitled.png)

Divide the light angle of 0~180 into 9 angles, and draw 9 textures according to the change of the light angle on the single side face.

![Untitled](Face%20Shadow%20Map-%20Creation%20and%20Baking%20Workflow%20d3b8769021e04683a2f2ae4cf16ac810/Untitled%201.png)

Finally, import the 9 drawn pictures into the Unity project.

<aside>
💡 It is not restrict to 9 textures (as long as total texture is more than 2). The more textures, the more detailed can be control under different angles of light. The less pictures, the lower the controling, and there will be a larger jump of light and shaded area change when the light angle changes. (From the previous texture to the next texture)

</aside>

## 2.Baking and Merging SDF Textures with ASP SDF Generator

---

### Use the SDF Generator

In the unity project, select **ASP**→**SDFGenerator** in the upper window bar to open the sdf generator window.

![Untitled](Face%20Shadow%20Map-%20Creation%20and%20Baking%20Workflow%20d3b8769021e04683a2f2ae4cf16ac810/Untitled%202.png)

Drag the 9 textures into the source textures array. These 9 textures will be used as the source texture for generating SDF.

Then set the GroupName (the naming header of the generated texture) and specify the path where you want to generate the texture.

Then click **Create SDFs & Merge**, it will merge the SDFs calculated from the 9 textures into a single one, which is our SDF-based face shadow map.

![Untitled](Face%20Shadow%20Map-%20Creation%20and%20Baking%20Workflow%20d3b8769021e04683a2f2ae4cf16ac810/Untitled%203.png)

In the example above, I only need UnityChanFace_merged. The other generated texture are for reference only and can be delete.

### **Assign the Face Shadow Map**

Back to the material inspector of the face materia and set [Toon Shading Style](Shader%20Properties%20References%20b6d95870279e49bba2e94933508053bb/Toon%20Shading%20Style%20baac54f6e9154bf19d3146e001e72061.md) **to Face**

![Untitled](Face%20Shadow%20Map-%20Creation%20and%20Baking%20Workflow%20d3b8769021e04683a2f2ae4cf16ac810/Untitled%204.png)

Assign the generated SDF-based face shadow map into the **Face Shadow Map** texture field and we are done.

<aside>
⏭️ Go to next page → [Color of The Received Shadow](Color%20of%20The%20Received%20Shadow%2088d9ff8c09a6499c97c50e7c9a5a8364.md)

</aside>