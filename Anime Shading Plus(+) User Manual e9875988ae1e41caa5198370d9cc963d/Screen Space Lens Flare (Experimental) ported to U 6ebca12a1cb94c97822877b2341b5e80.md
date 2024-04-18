# Screen Space Lens Flare (Experimental) ported to Unity 2021/2022

# **About Screen Space Lens Flare**

---

Starting with Unity 2023, Screen Space Lens Flare is a built-in post-processing effect in SRP.

[https://youtu.be/-6zbFTBMDmU?t=128](https://youtu.be/-6zbFTBMDmU?t=128)

I personally like this effect very much, so I decided to port this feature to earlier versions of Unity, so that even Unity 2021/2022 users can use this feature. Screen Space Lens Flare relies on the final RT output of **Bloom**, so you must turn on **Bloom** for it to take effect.

Because it is ported backward in a bit of a hacky way, this feature is regard as experimental. At this point, I cannot guarantee that this feature will not have bugs in the editor/buit player of 2021/2022.

<aside>
💡 In some cases, when the **streak threshold** in the screen space lens flare volume is too low, there may be flickering when moving the mouse in the editor.

</aside>

# **Setting Up the Screen Space Lens Flare Renderer Feature**

---

<aside>
💡 **If you are using Unity 2023/Unity 6, please ignore this page and follow the [official Unity documentation](https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@17.0/manual/shared/lens-flare/post-processing-screen-space-lens-flare.html) to set up the official Screen Space Lens Flare in the Volume.**

</aside>

1. Add the screen space lens flare feature to the current URP Renderer Data.

![Untitled](Screen%20Space%20Lens%20Flare%20(Experimental)%20ported%20to%20U%206ebca12a1cb94c97822877b2341b5e80/Untitled.png)

1. Then, make sure the Inject Point is set to After Rendering Post Processing.

![Untitled](Screen%20Space%20Lens%20Flare%20(Experimental)%20ported%20to%20U%206ebca12a1cb94c97822877b2341b5e80/Untitled%201.png)

1. Then, in the current volume, click the Add Override button and select ASP Screen Space Lens Flare.

![Untitled](Screen%20Space%20Lens%20Flare%20(Experimental)%20ported%20to%20U%206ebca12a1cb94c97822877b2341b5e80/Untitled%202.png)

1. Turn on bloom and adjust the relevant parameters to get screen space lens flare.

![Untitled](Screen%20Space%20Lens%20Flare%20(Experimental)%20ported%20to%20U%206ebca12a1cb94c97822877b2341b5e80/Untitled%203.png)