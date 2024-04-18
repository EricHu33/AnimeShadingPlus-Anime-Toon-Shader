# Albedo/Normal/Emission/OSM Textures

Under this category, using different [Toon Shading Style](Toon%20Shading%20Style%20baac54f6e9154bf19d3146e001e72061.md) will display different textures and parameters.

## CelShading Mode Properties

---

| Property Name | Description |
| --- | --- |
| Albedo | Albedo map |
| Normal Map | Normal map |
| Normal Map Scale | Controls the strength of the normal map, with a range of 0 to 1 |
| Ramp Occlusion Map | The effect is the same as a reocclusion map, but the occlusion color will be the leftmost color of the ramp map |
| Ramp Occlusion Strength | Controls the strength when sampling the R channel of the ramp occlusion map, with a range of 0 to 1 |
| Enable Emission | Whether to enable the emission |
| Emission | Emission color/map |

![Untitled](Albedo%20Normal%20Emission%20OSM%20Textures%20197cc4c450bc4016a8cc4c2e89dfb6fb/Untitled.png)

<aside>
💡 When the material style is set to Face mode, the parameters are the same as CelShading mode, with the exception of the Normal Map. This is because the shading of the face are controlled by the Face Shadow Map entirely.

</aside>

## StylizePBR Mode Properties

---

| Property Name | Description |
| --- | --- |
| Albedo | Albedo map |
| Normal Map | Normal map |
| Normal Map Scale | Controls the strength of the normal map, with a range of 0 to 1 |
| Occlusion/Smoothness/Metallic Map | PBR Map,
R Channel - Occlusion
G Channel - Smoothness (1 - Roughness)
B Channel - Metallic

 |
| Metallic | control the metalness  |
| Smoothness | Smoothness, i.e. (1 - roughness) in PBR of other non-Unity renderers |
| Occlusion Strength | Controls the strength when sampling the R channel of the OSM map, with a range of 0 to 1 |
| Enable Emission | Whether to enable the emission |
| Emission | Emission color/map |

![parameters displayed without OSM texture.](Albedo%20Normal%20Emission%20OSM%20Textures%20197cc4c450bc4016a8cc4c2e89dfb6fb/StylizePBR1.png)

parameters displayed without OSM texture.

![parameters displayed with OSM texture.](Albedo%20Normal%20Emission%20OSM%20Textures%20197cc4c450bc4016a8cc4c2e89dfb6fb/StylizePBR2.png)

parameters displayed with OSM texture.