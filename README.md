# Julia Set Renderer

A real-time Julia set fractal renderer implemented using OpenGL and fragment shaders in Visual Studio 2019.

## Overview

This project renders the Julia set fractal using GPU acceleration through OpenGL fragment shaders. The Julia set is a fascinating mathematical fractal that creates intricate, self-similar patterns at different scales. By leveraging the parallel processing power of graphics cards, this implementation achieves real-time rendering with smooth zooming and parameter adjustment capabilities.

### Demo
![Real-Time Julia set rendering](https://github.com/user-attachments/assets/3ce8f69b-471d-4590-bbc8-32c4920390c8)






## Mathematical Background

### The Julia Set

The Julia set is defined for a complex function of the form:

```
f(z) = z² + c
```

Where:
- `z` is a complex number representing a point in the complex plane
- `c` is a complex constant parameter that determines the shape of the Julia set

For each point `z₀` in the complex plane, we iterate the function:
```
z₁ = z₀² + c
z₂ = z₁² + c
z₃ = z₂² + c
...
zₙ₊₁ = zₙ² + c
```

### Mathematical Definition

A point `z₀` belongs to the Julia set if the sequence `{zₙ}` remains bounded as `n → ∞`. In practice, we:

1. **Iterate** the function up to a maximum number of iterations
2. **Test boundedness** by checking if `|zₙ| > 2` (escape radius)
3. **Color mapping** based on the number of iterations before escape

The escape radius of 2 is mathematically significant because if `|zₙ| > 2` at any point, the sequence is guaranteed to diverge to infinity.

### Complex Number Arithmetic

In the fragment shader, complex numbers are represented as 2D vectors:
- `z = (x, y)` represents `z = x + yi`
- **Complex multiplication**: `(a + bi)(c + di) = (ac - bd) + (ad + bc)i`
- **Complex magnitude**: `|z| = √(x² + y²)`

### Parameter Space

Different values of the complex parameter `c` produce dramatically different Julia sets:
- `c = -0.7 + 0.27015i` - Classic spiral pattern
- `c = -0.8 + 0.156i` - Dendrite-like structure  
- `c = -0.123 + 0.745i` - Disconnected dust-like set
- `c = 0.285 + 0.01i` - Connected set with intricate details

## Features

- **Real-time rendering** using OpenGL fragment shaders
- **Interactive parameter adjustment** for exploring different Julia sets
- **Smooth zooming** and panning capabilities
- **Customizable color schemes** for visualization
- **High precision** calculations for deep zoom levels
- **Optimized GPU performance** for smooth frame rates



## Requirements

### Development Environment
- **Visual Studio 2019** or later
- **Windows 10/11** (for VS2019 compatibility)
- **OpenGL 3.3** or higher capable graphics card

### Dependencies
- **OpenGL** (system library)
- **GLFW** - Window management and input handling
- **GLEW** - OpenGL extension loading
- **GLM** - OpenGL mathematics library (optional, for matrix operations)

## Building and Running

### Setup Instructions

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd julia-set-renderer
   ```

2. **Open in Visual Studio 2019**:
   - Open `JuliaSetRenderer.sln`
   - Ensure the project is set to x64 configuration

3. **Install dependencies**:
   - Download GLFW and GLEW libraries
   - Place headers in `include/` directory
   - Place libraries in `lib/` directory

4. **Build configuration**:
   - Set to Release mode for optimal performance
   - Ensure OpenGL libraries are linked: `opengl32.lib`, `glfw3.lib`, `glew32.lib`

5. **Run the application**:
   - Press F5 to build and run

