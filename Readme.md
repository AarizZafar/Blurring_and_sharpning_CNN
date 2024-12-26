# Image Blurring and Sharpness Enhancement

## Overview

This notebook demonstrates various techniques for **image blurring** and **sharpness enhancement** using convolution operations. The primary goal is to understand how different kernels affect the brightness and contrast of an image while preserving the color information.

## Key Concepts

- **Convolution**: A mathematical operation used to apply filters to images, enhancing or blurring specific features.
- **RGB Color Space**: Represents images using Red, Green, and Blue channels.
- **YUV Color Space**: Separates luminance (Y) from chrominance (U and V), allowing for brightness adjustments without affecting color.

## Steps and Techniques

2. **Convolution Function**:
    - `multi_convolver(image, kernel, iterations)`: Applies a kernel to an image multiple times to achieve the desired effect.

3. **Color Space Conversion**:
    - Convert RGB images to YUV to separate brightness from color.
    - Apply convolutions to the Y channel to adjust brightness and contrast.
    - Convert the modified YUV image back to RGB.

4. **Blurring and Sharpening**:
    - **Blurring**: Reduces noise and detail in an image.
    - **Sharpening**: Enhances edges and details in an image.

### Convolution Function

```python
def multi_convolver(image, kernel, iterations):
    for i in range(iterations):
        image = convolve2d(image, kernel, 'same', boundary='fill', fillvalue=0)
    return image