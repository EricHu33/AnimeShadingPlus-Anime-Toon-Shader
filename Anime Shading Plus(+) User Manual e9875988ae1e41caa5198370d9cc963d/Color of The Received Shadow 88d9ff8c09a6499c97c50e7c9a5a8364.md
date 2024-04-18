# Color of The Received Shadow

This page will explain how different **Received Shadow Behaviour** impact  the shadow color.

In the ASP character rendering shader, under the [Diffuse/Lighting Behaviour (Ramp Shading)](Shader%20Properties%20References%20b6d95870279e49bba2e94933508053bb/Diffuse%20Lighting%20Behaviour%20(Ramp%20Shading)%20d8c5222e277543d7b499df3e5213db3e.md)  category, you can use different Received Shadow Behaviour to control the way the received shadow color is displayed.

| Received Shadow Behaviour | 說明 |
| --- | --- |
| - Use Ramp End | Use the color at the leftmost end of the Ramp Lighting Map as the shadow color. |
| - Color | Use the Received Shadow Color as the shadow color. |
| - DarkenRampLightByColor | Preserve the current pixel color and blend it with the Received Shadow Color to darken it. |

# 1. Use Ramp End

---

All ASP characters use Ramp lighting Map to represent the changes of light/shadowed. Therefore, the default **Received Shadow Behaviour** is to use **Use Ramp End** - for the received shadow color, use the color at the leftmost end of the Ramp lighting Map to ensure consistency with the object's lighting result.

In the figure below, you can observe that the received shadow color is the same as the color at the far left of the Ramp Map.

![Untitled](Color%20of%20The%20Received%20Shadow%2088d9ff8c09a6499c97c50e7c9a5a8364/Untitled.gif)

![Untitled](Color%20of%20The%20Received%20Shadow%2088d9ff8c09a6499c97c50e7c9a5a8364/Untitled.png)

# 2. Color

---

When Received Shadow Behaviour is set to Color, you can force the received shadow to be a specified color.

![Untitled video - Made with Clipchamp (3).gif](Color%20of%20The%20Received%20Shadow%2088d9ff8c09a6499c97c50e7c9a5a8364/Untitled_video_-_Made_with_Clipchamp_(3).gif)

![Untitled](Color%20of%20The%20Received%20Shadow%2088d9ff8c09a6499c97c50e7c9a5a8364/Untitled%201.png)

You can notice that in this example, there are jagged shadows on the left side of the sphere. This is because the color of the self-shadow does not match the color of the ramp lighting map. According to the instructions in [**Character Shadow Setup Guide**](Character%20Shadow%20Setup%20Guide%201ebc2c7bb7324ff78f3bc2ca70bc8940.md) **(2-1)**, you can avoid self-shadow by disabling the built-in shadow caster of the current renderer.

![Disable the shadow casting to the built-in shadow map can avoid self-shadow.](Color%20of%20The%20Received%20Shadow%2088d9ff8c09a6499c97c50e7c9a5a8364/Untitled%202.png)

Disable the shadow casting to the built-in shadow map can avoid self-shadow.

# 3.DarkenRampLightByColor

---

When using this mode, the received shadow color will be mixed with the specified Color to create a darkening effect. This is a solution that can show the received shadow while retaining the ramp lighting map’s lighting result.

![Untitled video - Made with Clipchamp (4).gif](Color%20of%20The%20Received%20Shadow%2088d9ff8c09a6499c97c50e7c9a5a8364/Untitled_video_-_Made_with_Clipchamp_(4).gif)

![Untitled](Color%20of%20The%20Received%20Shadow%2088d9ff8c09a6499c97c50e7c9a5a8364/Untitled%203.png)

In the **DarkenRampLightByColor** mode, there will be self-shadow problems just like the **Color** mode. The solution is the same, just disable the shadow cast for the built-in shadow map.

![Untitled](Color%20of%20The%20Received%20Shadow%2088d9ff8c09a6499c97c50e7c9a5a8364/Untitled%204.png)

<aside>
💡  DarkenRampLightByColor is a mode that is very suitable for cel-shaded characters. It can preserve the ligting changes of light/shadowed area on the character.

</aside>

![Untitled](Color%20of%20The%20Received%20Shadow%2088d9ff8c09a6499c97c50e7c9a5a8364/Untitled%205.png)

<aside>
⏭️ Go to next page →  [Eyes(Anime-like) Setup Guide](Eyes(Anime-like)%20Setup%20Guide%20ea4ccf4c535e4f33a189b3b670eff28e.md)

</aside>