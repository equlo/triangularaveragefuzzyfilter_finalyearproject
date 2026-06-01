# Low Light Image Enhancement Using Triangular Fuzzy Filter

## Overview

Low-light images often suffer from poor brightness, low contrast, hidden details, and noise, making visual interpretation difficult. This project presents a low-light image enhancement framework based on a Triangular Fuzzy Filter. The proposed method uses fuzzy logic to adaptively enhance image brightness while preserving important visual information.

To further improve image quality, CLAHE (Contrast Limited Adaptive Histogram Equalization) is used for contrast enhancement and a sharpening filter is applied to highlight image details and edges.

---

## Objectives

- Improve visibility of low-light images.
- Enhance image brightness and contrast.
- Preserve important image details.
- Increase image information content.
- Compare performance with traditional enhancement methods.

---

## Methodology

### 1. Image Acquisition

The input low-light image is loaded into the system.

### 2. HSV Color Space Conversion

The image is converted from RGB/BGR to HSV color space.

- H → Hue
- S → Saturation
- V → Value (Brightness)

Enhancement is performed on the V channel to preserve color information.

### 3. Triangular Fuzzy Filtering

A triangular membership function is applied to classify pixel brightness levels.

```text
Membership

1
       /\
      /  \
     /    \
____/______\____

a     b     c
```

Where:

- a = Starting point
- b = Peak point
- c = Ending point

The membership value determines how strongly a pixel should be enhanced.

### 4. Brightness Enhancement

Dark pixels receive stronger enhancement while brighter pixels are preserved to avoid overexposure.

### 5. Contrast Enhancement

CLAHE is applied to improve local contrast and reveal hidden details.

### 6. Sharpening

A sharpening kernel is applied to enhance edges and fine image details.

### 7. Output Generation

The enhanced image is generated and displayed alongside the original image.

---

## System Workflow

```text
Input Image
      │
      ▼
Triangular Fuzzy Filtering
      │
      ▼
Brightness Enhancement
      │
      ▼
Contrast Enhancement (CLAHE)
      │
      ▼
Sharpening Filter
      │
      ▼
Enhanced Output Image
```

---

## Technologies Used

- Python
- OpenCV
- NumPy
- Matplotlib

---

## Features

- Triangular fuzzy membership based enhancement
- Adaptive brightness correction
- Contrast enhancement using CLAHE
- Edge sharpening
- Entropy-based performance evaluation
- Simple and computationally efficient implementation

---

## Parameter Settings

The performance of the proposed method can be adjusted according to the darkness level of the input image.

### Very Dark Images

```python
b = 0.35
k = 0.9

clahe = cv2.createCLAHE(
    clipLimit=3.5,
    tileGridSize=(8,8)
)
```

**Characteristics:**

- Strong brightness enhancement
- High contrast improvement
- Suitable for extremely dark and night-time images

---

### Moderate Low-Light Images

```python
b = 0.40
k = 0.8

clahe = cv2.createCLAHE(
    clipLimit=3.0,
    tileGridSize=(8,8)
)
```

**Characteristics:**

- Balanced enhancement
- Natural appearance
- Recommended for most low-light images

---

### Slightly Dark Images

```python
b = 0.50
k = 0.6

clahe = cv2.createCLAHE(
    clipLimit=2.0,
    tileGridSize=(8,8)
)
```

**Characteristics:**

- Mild enhancement
- Preserves natural brightness
- Prevents over-enhancement

---

## Parameter Description

| Parameter | Description |
|------------|------------|
| b | Peak point of the triangular membership function |
| k | Fuzzy enhancement strength factor |
| clipLimit | CLAHE contrast enhancement limit |

---

## Parameter Selection Guide

| Image Type | b | k | clipLimit |
|------------|------|------|-----------|
| Very Dark | 0.35 | 0.9 | 3.5 |
| Moderate Low-Light | 0.40 | 0.8 | 3.0 |
| Slightly Dark | 0.50 | 0.6 | 2.0 |

---

## Datasets

The project can be tested using publicly available low-light image datasets:

### LOL Dataset

A paired low-light image dataset widely used for image enhancement research.

### ExDark Dataset

A collection of real-world low-light images captured under various lighting conditions.

### SID Dataset (See-in-the-Dark)

A dataset specifically designed for low-light image enhancement and analysis.

Custom low-light images can also be used for testing.

---

## Performance Evaluation

The proposed method is evaluated using image entropy.

### Entropy

Entropy measures the amount of information present in an image.

Higher entropy generally indicates:

- Better visibility
- More image details
- Richer information content

### Entropy Formula

H = -Σ p(i) log₂ p(i)

Where:

- H = Entropy
- p(i) = Probability of pixel intensity i

---

## Comparison with Existing Methods

| Method | Limitation |
|----------|------------|
| Histogram Equalization | Over-enhancement and noise amplification |
| CLAHE | Parameter sensitivity |
| Retinex | Halo effects and color distortion |
| Deep Learning Methods | Requires training data and high computational resources |
| Proposed Triangular Fuzzy Filter | Simple, adaptive, and computationally efficient |

---

## Applications

- Surveillance Systems
- Security Cameras
- Medical Imaging
- Satellite Imaging
- Mobile Photography
- Computer Vision Applications
- Autonomous Vehicles

---

## Results

The proposed framework successfully improves:

- Image brightness
- Local contrast
- Edge visibility
- Information content

The combination of Triangular Fuzzy Enhancement, CLAHE, and Sharpening produces visually clearer and more informative images compared to traditional enhancement techniques.

---

## Conclusion

This project presents a low-light image enhancement framework based on a Triangular Fuzzy Filter. The method adaptively enhances dark regions using fuzzy logic while preserving brighter areas. CLAHE improves local contrast and a sharpening filter enhances image details. Experimental results demonstrate improved visual quality and increased information content, making the proposed approach suitable for various image processing and computer vision applications.
