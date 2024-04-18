# Character Shadow Setup Guide

This page will demonstrate how to use the ASP Character Panel to configure shadow casting and receiving for characters.

---

# 1. **Preparation**

1. First, following the steps in [Setup ASP Character Panel ](Setup%20ASP%20Character%20Panel%200c922c2343194cebb63e8c9fdf49abd1.md),  add the **ASPCharacterPanel** component to the character's root game object,

![Untitled](Character%20Shadow%20Setup%20Guide%201ebc2c7bb7324ff78f3bc2ca70bc8940/Untitled.png)

1. Next, make sure that all required passes in the **ASP Render Feature Check List** are Active**.** If any are displayed as inactive or missing, it means that the corresponding renderer feature is not enabled in the current URP renderer data. Please follow the instructions in [**Installation Instructions and Prerequisites**](Installation%20Instructions%20and%20Prerequisites%205f0a72aeff00486d9b204b62c99a8035.md)  to configure URP rendering data.

![Untitled](Character%20Shadow%20Setup%20Guide%201ebc2c7bb7324ff78f3bc2ca70bc8940/Untitled%201.png)

1. Then, confirm that all materials on the character have been changed to use **ASP/Character**(or **ASP/Eye** if needed) as material’s target Shader.

![Untitled](Character%20Shadow%20Setup%20Guide%201ebc2c7bb7324ff78f3bc2ca70bc8940/Untitled%202.png)

# 2. **Configuring Shadows**

At this point, we are ready to start configuring character shadows. Back to the ASP Character Panel’s inspector for the current character and scroll down to the Shadow Behaviors category. This category contains four expandable items:

| Item Name | Description |
| --- | --- |
| Rendering Layer Information | Inspect and set the layer and rendering layer mask for each renderer under the current character. |
| Built-In Shadow Casting Behaviour | Inspect and set whether each renderer under the current character casts shadows to the Unity built-in shadow map. |
| Built-In Shadow Receive Behaviour | Inspect and set whether each material under the current character receives shadows from the Unity built-in shadow map. |
| ASP Extra Shadow Behaviour | Inspect and set whether each material under the current character receives shadows from the ASP character shadow map and depth offset shadows. |

## 2-1 Exclude character from built-in shadow map.

First, go to the **Built-In Shadow Casting Behaviour** category. Here, we can check whether all the renderers under the character are currently rendering to the built-in shadow map
To control the behaviour individually, you can click on each toggle. Or select **Apply All** at the bottom to turn on or off all shadow casters. Here, we set all the built-in shadow cast behaviors to **OFF**.
This exclude the character from being rendered into the built-in shadow map.

![Untitled](Character%20Shadow%20Setup%20Guide%201ebc2c7bb7324ff78f3bc2ca70bc8940/Untitled%203.png)

## 2-2 Make **other static objects in the scene to display character shadows**

As long as the material uses the ASP/Character or ASP/Eye as target shader, it will be rendered into the ASP's Character-Only Shadow Map. In order to allow other non-ASP materials to receive character shadows (such as the standard PBR material used in the scene), we need to change the original ***Universal Render Pipeline/Lit*** to ***ASP/UniversalPBRLit***. ***ASP/UniversalPBRLit*** is exactly the same as the built-in PBR in terms of functionality. The only difference is that in the code, it will additionally sample the ASP's Character-Only Shadow Map.

<aside>
💡 **ASP/UniversalPBRLit uses the exact same forward rendering code as Universal Render Pipeline/Lit, with the only difference being the additional sampling of the ASP ShadowMap.

This is exactly what you need to do if your other custom shader needs to sample ASP Shadow Map.**

</aside>

![Untitled](Character%20Shadow%20Setup%20Guide%201ebc2c7bb7324ff78f3bc2ca70bc8940/Untitled%204.png)

## 2-3 **Control specific material to receive character shadows**

In ASP Extra Shadow Behaviours, toggles under Character-Only Shadow Map category on the left side of the panel allows us to enable a selected parts that can receive character self-shadows without degrade the visual appearance, according to our needs. For example, legs and clothes. In most cases, they can all be set to **Not received**.

![Untitled](Character%20Shadow%20Setup%20Guide%201ebc2c7bb7324ff78f3bc2ca70bc8940/Untitled%205.png)

## 2-4 **Specify Parts of The Body to Cast and Receive Depth-Offset Shadow**

首先，先確認專案的rendering layer mask設定與Depth Offset Shadow renderer feature。

### 1. **Configure the Project's Rendering Layer Mask and Depth Offset Shadow Renderer Feature**

---

![Untitled](Character%20Shadow%20Setup%20Guide%201ebc2c7bb7324ff78f3bc2ca70bc8940/Untitled%206.png)

1. In the URP Global Setting, set up the Rendering Layer Mask.
    - In **Edit** > **Project Settings** > **URP Global Setting**, add a new Rendering Layer Mask (**Rendering Layers(3D)**). name it a accordingly , such as: DepthOffsetShadowCaster.
2. Set up the ASP Depth-Offset Shadow.
    - In the Project window, find the URP Renderer Data that stores all Renderer Features.
    - Expand the **Renderer Features** list and find **ASP Depth-Offset Shadow**.
    - In the panel, setup the layer and rendering layer mask for the detph-offset shadow.

<aside>
💡 **Please note that a Layer can only have a single Layer setting and cannot be multi-selected. However, Rendering Layer Masks can be multi-selected.**

</aside>

![Untitled](Character%20Shadow%20Setup%20Guide%201ebc2c7bb7324ff78f3bc2ca70bc8940/Untitled%207.png)

---

When you expand the **Rendering Layer Information** item in the **ASP Character Panel**, you will see the following information.

![Untitled](Character%20Shadow%20Setup%20Guide%201ebc2c7bb7324ff78f3bc2ca70bc8940/Untitled%208.png)

| Item Name | Description |
| --- | --- |
| Layer | Can be set in the Editor for each game object. Each game object can only have one layer, and layers are shared with the physics system. This makes layers inflexible |
| Rendering Layer Mask | Can be set independently for each renderer. Rendering Layer Masks can be multi-selected, which makes them more flexible. |
1. First, confirm the target layer and rendering layer mask of the **Depth Offset Shadow** above.
2. Then, set the layer value and rendering layer mask value for each renderer.
3. If the layer **matches** and the combination of the renderer's own rendering layer mask **contains** the value set by **Depth Offset Shadow**, then the renderer will cast a depth offset shadow.

![Untitled](Character%20Shadow%20Setup%20Guide%201ebc2c7bb7324ff78f3bc2ca70bc8940/Untitled%209.png)

<aside>
⏭️ Go to next page →  [Character Rendering Example - Cel Shading](Character%20Rendering%20Example%20-%20Cel%20Shading%20ef046dcd65f148d0a02c54fd35937168.md)

</aside>