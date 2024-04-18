# Building and Packaging Shaders(Important)

![Untitled](Building%20and%20Packaging%20Shaders(Important)%20d5138d321fbd4daa8b36568893073651/Untitled.png)

1. Before building the entire project, please make sure that the quality setting in [**Installation Instructions and Prerequisites (Important)**](Installation%20Instructions%20and%20Prerequisites%20(Impor%205f0a72aeff00486d9b204b62c99a8035.md)  points to the correct URP asset, and that the renderer data in the asset contains all the ASP-provided renderer features that are used.
2. In the Project Settings->Graphics category, add the following 2 Shaders to **always include**:
- Hidden/ASP/PostProcessing/Outline
- Hidden/ASP/PostProcessing/ToneMapping

<aside>
💡 If your version is 2021 or 2022, you need to include the following shader. For Unity 2023, it will use Unity's built-in screen space lens flare.

</aside>

- Hidden/URP/BackPort/LensFlaresScreenSpace