# GPU Fractal Explorer (WebGL Deep Zoom)

An interactive, real-time 60 FPS fractal renderer powered by a custom GLSL Fragment Shader in WebGL. Built for the **Fractal Card** and **Shader Card**.

🔗 **Live Demo:** [Try it here on Render](YOUR_RENDER_LINK_HERE)

![Fractal Deep Zoom Screenshot](fractal-deep-zoom.png)

## ✨ Features & Fractals Included

1. **Mandelbrot Set** ($z_{n+1} = z_n^2 + c$): Explore infinite self-similar structures along the boundary of the complex plane.
2. **Interactive Julia Sets**: Real-time sliders let you morph the complex constant $c = c_{re} + c_{im}i$ at 60 FPS.
3. **Burning Ship Fractal**: Uses absolute components $(\vert{}\text{Re}(z_n)\vert{} + i\vert{}\text{Im}(z_n)\vert{})^2 + c$ to generate ship-like flame structures.
4. **Tricorn (Mandelbar) Fractal**: Iterates using the complex conjugate $\bar{z}_n^2 + c$.

## 🧠 How It Works

### 1. Parallel GPU Computation (GLSL Fragment Shader)
Instead of calculating pixels sequentially on the CPU, this project offloads the entire complex plane iteration to the GPU using a WebGL fragment shader. Every pixel on the screen is evaluated in parallel, achieving a smooth 60 FPS during zooming and panning.

### 2. Smooth Coloring (Normalized Iteration Count)
Counting raw integer escape steps creates harsh color bands. To achieve smooth gradients, this shader implements the **Normalized Iteration Count** algorithm with a large escape radius ($\vert{}z\vert{}^2 > 256$):

$$\nu = \text{iter} + 1 - \frac{\ln(\ln(\vert{}z\vert{}))}{\ln(2)}$$

The continuous value $\nu$ is then mapped into Inigo Quilez's cosine palette function for smooth procedural coloring.

## 📍 Best Spots to Visit

Use the built-in **"Best Spots to Visit"** buttons in the UI or navigate to these coordinates manually:
- **Seahorse Valley:** `Center: -0.7436438, +0.1318259i` | `Zoom: 4,500x`
- **Elephant Valley:** `Center: +0.2817179, +0.5771052i` | `Zoom: 3,200x`
- **Double Spiral:** `Center: -0.7480000, +0.1000000i` | `Zoom: 900x`
- **Burning Armada (Burning Ship):** `Center: -1.7550000, -0.0300000i` | `Zoom: 35x`
- **Electric Julia:** `c = -0.8 + 0.156i` | `Zoom: 1.2x`

## 🚀 How to Run / Rebuild Locally (Under 1 Minute)

This project has zero external dependencies and runs in any modern browser.

1. Clone this repository:
   ```bash
   git clone [https://github.com/YOUR_USERNAME/fractal-explorer.git](https://github.com/YOUR_USERNAME/fractal-explorer.git)
   cd fractal-explorer
# GPU-Fractal-Explorer
