# SpriteLoadingEffect Shader (Unity Shader Graph)

A customizable loading-progress shader for **2D sprites**, built entirely with **Unity Shader Graph**.  
The effect gradually reveals a sprite using segmented progress steps and features a dynamic **shining head** for a polished loading animation.

---

## 🌟 Preview

![Loading Preview](https://raw.githubusercontent.com/ali-butt/Loading-Sprite/main/GIF/Loadingeffect.gif)

---

## 🎨 Features

- ✔️ Smooth sprite reveal based on a **\_Progress** value (0 → 1)
- ✔️ Customizable number of steps/segments
- ✔️ Animated **shining leading head**
- ✔️ Fully procedural (no extra textures needed)
- ✔️ Works on SpriteRenderer & UI Image
- ✔️ Mobile-friendly, lightweight Shader Graph
- ✔️ Perfect for loading screens, XP bars, animated UI reveals

---

## ⚙️ Shader Properties

| Property     | Type        | Description                        |
| ------------ | ----------- | ---------------------------------- |
| `_Progress`  | Float (0–1) | How much of the sprite is revealed |
| `_Steps`     | Integer     | Number of loading segments         |
| `_HeadWidth` | Float       | Controls shining head thickness    |
| `_MainTex`   | Texture2D   | The sprite texture                 |

---

## 🚀 How It Works

The shader uses a combination of:

- UV manipulation
- Step thresholds
- Smooth transitional highlights
- Segment slicing
- Progressive dissolve masking

### Internal Process:

1. Splits the sprite into **\_Steps** slices.
2. Calculates which slice is visible based on **\_Progress**.
3. Moves a shining head along the boundary using `Time` offset.
4. Blends everything together to create a soft, dynamic loading effect.

---

## 🧩 How to Use

### 1️⃣ Import the Shader

Add `SpriteLoadingEffect.shadergraph` into your Unity project.

### 2️⃣ Create a Material

Right-click → **Create → Material**  
Select **SpriteLoadingEffect** shader.

### 3️⃣ Apply to Sprite

Assign the material to any:

- SpriteRenderer
- UI Image (material override)

### 4️⃣ Drive the Progress via Script

```csharp
public class Loader : MonoBehaviour
{
    public Material mat;
    private float p;

    void Update()
    {
        p += Time.deltaTime * 0.25f; // slow fill
        p = Mathf.Clamp01(p);

        mat.SetFloat("_Progress", p);
    }
}
```

## 📸 Graph Screenshot

![Loading Preview](https://raw.githubusercontent.com/ali-butt/Loading-Sprite/main/Images/Preview.PNG)

## 🛠 Built With
Unity 2022+

Shader Graph

URP / Built-in compatible

## 📄 License
You may use this shader for commercial and non-commercial projects.
Credit is appreciated.

## 👤 Author
Created by Ali Butt.
If you use it, feel free to star the repo or share it!
