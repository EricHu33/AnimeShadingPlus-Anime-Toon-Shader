# Screen Space Outline Setup Guide

![The image above shows the debug mode, which only displays the outline and the mask (yellow pixels) that give futther weight control of the outline.
](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0/Untitled.png)

The image above shows the debug mode, which only displays the outline and the mask (yellow pixels) that give futther weight control of the outline.

# 1. **Adding the Outline Renderer Feature and Volume Override**(click to expand)

• In the Universal Renderer Data asset used by your project, add **ASP Screen Space Outline**.

![Untitled](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0/Untitled%201.png)

• In the scene, add a new **Volume** (or use an existing one) and set it to **Global Mode**.
• In the Volume's inspector, select **Add Override**, search for **ASP Screen Space Outline**, and add it.
• Your Volume should now look like the screenshot below, with **Screen Space Character Outline** now visible.

![Untitled](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0/Untitled%202.png)

• Expanding **Screen Space Character Outline** in the Volume reveals various parameters for the outline.

![Untitled](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0/Untitled%203.png)

### **What is all these parameters about?**

ASP's screen space outline can be composed of five edge detection results:

- Outer Edge
- Material Edge
- Albedo Edge
- Depth Edge
- Normal Edge

 Depending on the project's needs, these five edge detection results can be combined to render character outlines in screen space.

- ASP screen space outline also supports using the mesh’s vertex color as a mask to control the outline weight of each pixel(see **section 4**).
- To avoid the problem of screen space outlines being too thick when objects are far away from the camera, it also provides options to fade out the color, weight, and thickness through parameters. (see **section 3**)

### **What does all those toggles on the left mean?**

- Unity's Volume uses a framework called [Volume Override](https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@14.0/manual/VolumeOverrides.html).
- To make the toggle options on the right take effect, you must first check the **override toggle** on the left. Otherwise, the **default values** of the post-processing effect will be used.

![Untitled](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0/Untitled%204.png)

Use above figure as example, the default value of **Enable Outline** for screen space outline feature is true. Therefore, when this outline's renderer feature is enabled in the renderer data, the outline is already turned on.

# 2. **Adjust the Edge Detection Parameters of Screen Space Character Outline** (click to expand)

---

Next, I will use character model below as an example for setting up the outline.

![Untitled](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0/Untitled%205.png)

1. First, make sure the outline is turned on in the volume. For convenience, click the **ALL** option in the upper left corner to set all override toggles to true. 
This will make our custom parameters override the default value.

![Untitled](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0/Untitled%206.png)

1. Find the **Debug** category at the bottom of the panel and set **Enable Debug Mode** to **true**.

![Untitled](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0/Untitled%207.png)

This will turn on the debug mode for the outline, and the camera’s final output will now display the d**ebug background color** and the current outline (in **outline color**).

![Untitled](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0/Untitled%208.png)

1. Now, under Debug Category, use the **Sreen Space Outline Debug Mode** dropdown menu to display the selected type of edge and adjust the corresponding parameters until you are satisfied with the result.

![Untitled](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0/Untitled%209.png)

1. After adjusting each type of edge individually using the debug options, set **Screen Space Outline Debug Mode** to C**ombined Resul**t to see the combined result of all currently enabled types of edges.

![Untitled](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0/Untitled%2010.png)

And finally, turn off **Enable Debug Mode** to view the final rendering result.

![Untitled](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0/Untitled%2011.png)

# 3. **Adjust Fade-out Effect**

![Untitled](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0/Untitled%2012.png)

One of the biggest challenges of screen-space outlines is that it is difficult to scale the thickness/detailed of the outline according to distance. 
This can lead to outlines being too thick for characters when the character away from the camera.

In order to maintain visual consistency, ASP provides a function to fade out the **color**, **thickness**, and **detection weight** of the outline based on the geometry’s distance from the camera.

**Color & Weight Distance Fade**

- **Fading Weight by Distance
-** When toggle to true,  the weight to detect the outline will gradually decrease as the distance from the camera increases. Resulting less detail as geometry away from camera.
- **Fading Color by Distance
-**  When toggle to true, the color of the outline will gradually fade out as the distance from the camera increases.

**Outline Width Distance Fade (Optional, Not recommend by default)**

- **Fading Width By Distance**
When toggle to true, the width of the outline will gradually decrease as the distance from the camera increases. The width of screen space outline is difficult to control, enable this function with caution.

![Untitled](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0/Untitled%2013.png)

<aside>
💡 To use width distance fade, I recommend setting the 
- **Start** of width fading distance be **+2** of the **Start** of Color & Weight fading distance. 
- **End** of width fading distance same as the **End** of Color & Weight fading distance. 
This has worked well in my experiments.

![Untitled](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0/Untitled%2014.png)

</aside>

# 4. **Adjust Outline Weight Using Vertex Color**

![Untitled](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0/Untitled%2015.png)

In addition to adjusting the global outline weight through the volume, ASP provides a way to further adjust the weight through the B channel of the vertex color.

1. Set the debug mode in the screen space outline volume to **Combine Result And Vertex Color Mask**.
2. In the DCC (e.g. Blender, Substance Painter), modify the value of the vertex color B channel in the places where you want to reduce the outline weight.
3. Go back to Unity and check in the same debug mode.

![Untitled](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0/Untitled%2016.png)

![Untitled](Screen%20Space%20Outline%20Setup%20Guide%20a28de729338444678125dc3a1af2e2c0/Untitled%2017.png)

<aside>
💡 The vertex color mask does not affect the weight of the **outerline**. It only affects the weight of the normal edge, material edge, albedo edge, and depth edge.

</aside>

<aside>
⏭️ Go to next page[**Object Space Outline Settings**](Object%20Space%20Outline%20Settings%209d066f2426a644ed99fb32649bb5404d.md)

</aside>