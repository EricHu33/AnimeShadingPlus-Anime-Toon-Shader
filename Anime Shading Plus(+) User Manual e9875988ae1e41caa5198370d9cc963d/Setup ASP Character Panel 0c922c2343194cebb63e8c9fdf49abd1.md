# Setup ASP Character Panel

# **1. Adding the ASP Character Panel to Current Character's Root GameObject**

---

Aside from the renderer feature, the only component in the ASP plugin that needs to be manually configured is the ASP Character Panel. Before you start configuring the shader and material, you must first add the ASPCharacterPanel component to the root game object of the character you want to render. This component will automatically pass some per-character information required by the shader(such as MaterialID, facing direction..etc) at edit/runtime. Without the component the rendering effect will be incorrect.

At the same time, you can also inspect/setup the character’s shadow/mesh outline/surface parameter through ASP Character Panel’s editor UI. Which give the developer some QoL improvement over individually inspect/setup each material/renderer of the character.

Usually, the root game object of a humanoid character in Unity is the the one that has the animator. After adding the ASP character panel to the root game object of the character, you should see something similar to the following screenshot:

![Untitled](Setup%20ASP%20Character%20Panel%200c922c2343194cebb63e8c9fdf49abd1/Untitled.png)

# 2. **Confirming the Character's Facing Direction**

---

<aside>
💡  Please note that after opening the gizmo, you will see a light blue arrow. This is the Forward direction of the character as determined by the ASP Character Panel. Please make sure that the forward direction of the character object is facing the same direction as the arrow. Otherwise, the effect in the shader will be incorrect.

</aside>

![Untitled](Setup%20ASP%20Character%20Panel%200c922c2343194cebb63e8c9fdf49abd1/Untitled%201.png)

<aside>
⏭️ Go to next page [ASP Character Panel Feature Guide](ASP%20Character%20Panel%20Feature%20Guide%20d7b39661c1f245e79b230fbfd60e3108.md)

</aside>