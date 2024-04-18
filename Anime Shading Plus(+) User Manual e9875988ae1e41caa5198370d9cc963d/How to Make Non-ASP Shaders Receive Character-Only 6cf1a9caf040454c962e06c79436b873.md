# How to Make Non-ASP Shaders Receive Character-Only Shadows

# 1. The Scene uses the built-in Lit for static objects/environenment, but needs to display character shadows from the ASP Shadow Map.

After character shadows are rendered separately to an additional ASP Shadow Map, materials that use other shaders must sample this shadow map in order to receive and display character shadows.

ASP/UniversalPBRLit is exactly the same as the built-in PBR (I directly copied the entire code), the only difference is that it will also sample the ASP Shadow Map when rendering shadows. In other words, when you need to allow static objects to receive and display character shadows, you can safely replace the built-in Lit Shader with **ASP/UniversalPBRLit.**

![Untitled](How%20to%20Make%20Non-ASP%20Shaders%20Receive%20Character-Only%206cf1a9caf040454c962e06c79436b873/Untitled.png)

<aside>
💡 **Please note that ASP currently only works correctly in forward rendering and forward rendering + projects. This is because ASP needs to sample additional shadow maps, which is not supported in deferred rendering.**

</aside>

# 2. Scene uses a custom code shader and needs to display character shadows from the ASP Shadow Map

 the following code can be added to sample the ASP Shadow Map:

```glsl
#include "YourPathToASP/Shaders/ShaderLibrary/ASPShadows.hlsl"

//inside your fragment shader 
{
  
    float aspShadowMapAttenuation = SampleASPShadowMap(positionWS);
    
    //assuming your shader use GetMainLight() or similar to retrieve urp main light.

    //now your shader can display both main light shadow map shadow and asp shadow map shadow.
    mainLight.shadowAttenuation *= SampleASPShadowMap;
}
```

# 3. Can Custom Shader Graph Shader receive character shadow from ASP Shadow Map ?

Technically, yes, you can use the code from section 2 in a custom function node to sample the ASP Shadow Map. The challenge is that there's no simple way to override the shadow attenuation of the main light after sampling another shadow map **inside the shader graph**, which will affect the shadow color.

So the shadow color will be incorrect. This is the reason I created **ASP/UniversalPBRLit** as an alternative solution.