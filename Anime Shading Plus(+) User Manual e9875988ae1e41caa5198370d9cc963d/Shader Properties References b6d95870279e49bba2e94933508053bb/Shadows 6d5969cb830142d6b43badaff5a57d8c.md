# Shadows

<aside>
💡 For detailed explanations and settings for Built-In, ASP ShadowMap, and Depth Offset Shadow, please refer to [**Setup Character Shadow - ASP’s Shadow Solution**](../Setup%20Character%20Shadow%20-%20ASP%E2%80%99s%20Shadow%20Solution%20a0426bfd61cd49a58c877e54d27fc317.md)

</aside>

| Property Name | Description |
| --- | --- |
| Receive Built-In Shadows | Whether to receive shadows from the Unity default ShadowMap. |
| Receive Extra Shadow From ASP ShadowMap | Whether to receive shadow from ASP character shadow. |
| Receive Extra Shadow From Offsetted Depth Map | Whether to receive depth offset shadow from ASP material. |
| Depth Offset Shadow Pixel Distance | The offset distance of the depth offset shadow. |

![Untitled](Shadows%206d5969cb830142d6b43badaff5a57d8c/Untitled.png)

<aside>
💡  The three shadow toggles above can be set individually for each material, but for the sake of convenient management of material parameters, It is recommand to uniformly set/manage all material’s shadow behaviour of the current characte on the ASP Character Panel’s component GUI.

</aside>