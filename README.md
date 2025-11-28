# PixelFX

**Professional Bitmap Processing for UltraCanvas**

PixelFX is UltraCanvas's comprehensive bitmap manipulation and analytics engine, delivering industrial-strength image processing with minimal memory footprint. Built on libvips and wrapped in an intuitive C++20 API.

---

## Performance

- **Demand-driven processing** — Only compute what's needed, when it's needed
- **Multi-threaded by design** — Automatic CPU utilization across all cores
- **Memory efficient** — Process 10GB images on machines with 2GB RAM
- **Hardware accelerated** — SIMD instructions (SSE, AVX, NEON)
- **2-3× faster** than traditional libraries for typical operations

---

## Architecture

```
PixelFX/
├── include/
│   ├── PixelFX.h                    # Main API header
│   ├── PixelFXTypes.h               # Image data structures
│   ├── PixelFXArithmetic.h          # Math operations
│   ├── PixelFXColor.h               # Color space operations
│   ├── PixelFXConvolution.h         # Filter operations
│   ├── PixelFXHistogram.h           # Histogram operations
│   └── PixelFXIO.h                  # File I/O operations
├── core/
│   ├── PixelFX.cpp                  # Core implementation
│   └── PixelFXEngine.cpp            # libvips wrapper
└── Plugins/
    ├── JPEG/                        # libjpeg-turbo
    ├── PNG/                         # libpng/libspng
    ├── WebP/                        # libwebp
    └── AVIF/                        # libavif
```

---

## Usage Example

```cpp
#include "PixelFX.h"

// Simple yet powerful
PixelFX::ImageData image;
PixelFX::Load("photo.jpg", image);

// Transform
PixelFX::Resize(image, 800, 600, PixelFX::Quality::High);
PixelFX::Rotate(image, 90);

// Enhance
PixelFX::Sharpen(image, 1.5);
PixelFX::ColorBalance(image, 1.1, 1.0, 0.95);
PixelFX::AutoContrast(image);

// Save in any format
PixelFX::Save("enhanced.webp", image, 85);
```

---

## Operation Categories

### Arithmetic & Mathematical
Pixel-perfect calculations including add, subtract, multiply, divide, trigonometric functions, statistical analysis (min, max, mean, deviation), and complex number operations.

### Color Space
Seamless conversions between RGB, sRGB, scRGB, HSV, HSL, Lab, LCh, CMYK, XYZ, Yxy, and specialized color spaces. ICC profile support included.

### Convolution & Filtering
Gaussian blur, sharpen, edge detection (Sobel, Canny, Prewitt), custom kernel convolution, and separable filters for optimized performance.

### Histogram Processing
Analysis, cumulative histograms, equalization, matching, local contrast enhancement, and entropy calculation.

### Geometric Transforms
High-quality resize with multiple interpolation methods, rotation, affine transforms, perspective correction, and smart cropping.

### Drawing Operations
Anti-aliased shapes, lines, circles, rectangles, flood fill, image compositing, and text rendering.

---

## Use Cases

- **Photo Editing** — Complete toolkit for filters, adjustments, and enhancements
- **Medical Imaging** — Precision processing with floating-point accuracy
- **Web Services** — Fast thumbnail generation and format conversion
- **Scientific Analysis** — Statistical tools and frequency domain processing
- **Machine Learning** — Image preprocessing and augmentation pipelines
- **Game Development** — Texture processing and dynamic asset generation

---

## Technical Foundation

PixelFX leverages battle-tested libraries:

| Library | Purpose | License |
|---------|---------|---------|
| libvips | Core processing engine | LGPL-2.1 |
| libjpeg-turbo | JPEG codec | BSD-3 |
| libpng | PNG codec | libpng |
| libwebp | WebP codec | BSD-3 |
| libavif | AVIF codec | BSD-2 |
| libtiff | TIFF codec | libtiff |

---

## Integration with UltraCanvas

PixelFX integrates seamlessly with the UltraCanvas ecosystem:

- Direct rendering to UltraCanvas surfaces
- Unified color management with vector graphics
- Consistent plugin architecture across all media types
- Single API for bitmap, vector, and text operations

---

## License

Open Source — Part of the UltraCanvas Framework

---

*Developed by Cloverleaf UG*
