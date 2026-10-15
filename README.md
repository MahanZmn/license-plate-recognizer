# License Plate Recognition Using Signal Processing

## Overview

This project implements a basic License Plate Recognition (LPR) system using Python and digital image processing techniques. Developed as a Signals & Systems course project, it investigates how image degradation, motion blur, noise, and spatial downsampling affect license plate character recognition.

The system segments individual characters from license plate images and recognizes them by comparing them with reference templates using Pearson correlation. For degraded images, it applies frequency-domain deblurring techniques to improve recognition performance.

### Key Techniques
- Image preprocessing, thresholding, and character segmentation
- Pearson correlation for template-based character recognition
- Spatial downsampling and resolution analysis
- Motion-blur modeling and image restoration
- Wiener filtering and noise analysis in the frequency domain

## Repository Structure

```text
license-plate-recognizer-master/
├── code/
│   └── Project.ipynb
├── ideal/
│   ├── p1.jpg
│   ├── p2.jpg
│   ├── p3.jpg
│   └── p4.jpg
├── realistic/
│   ├── p1.jpg
│   ├── p2.jpg
│   ├── p3.jpg
│   └── p4.jpg
├── noisy/
│   ├── n1.jpg
│   └── n2.jpg
├── letters/
│   ├── A.jpg
│   ├── B.jpg
│   ├── C.jpg
│   └── D.jpg
├── numbers/
│   ├── 0.jpg ... 9.jpg
├── outputs/
│   ├── recRealImg1.jpg
│   ├── recRealImg2.jpg
│   ├── recRealImg3.jpg
│   └── recRealImg4.jpg
└── Report.pdf
```

### Folders and Files

- **`code/Project.ipynb`** — Main Jupyter Notebook containing theoretical explanations, implementation, experiments, visualizations, and recognition results.
- **`ideal/`** — Four relatively clean license plate images used to evaluate character segmentation and recognition under controlled conditions.
- **`realistic/`** — Four degraded license plate images used to investigate motion-blur removal and recognition under more challenging conditions.
- **`noisy/`** — Two noisy license plate images used to compare noise characteristics, particularly high-frequency noise.
- **`letters/`** — Reference templates for the letters A, B, C, and D.
- **`numbers/`** — Reference templates for the digits 0–9.
- **`outputs/`** — Saved deblurred versions of the four realistic license plate images, used for subsequent character recognition.
- **`Report.pdf`** — Project report documenting the theoretical background, methodology, and experimental work.

## Implementation

The notebook follows two main experimental stages:

1. **Ideal conditions:** License plate images are segmented into individual characters and recognized by selecting the reference template with the highest Pearson correlation. The effect of reducing image resolution is also investigated.
2. **Realistic conditions:** Motion-blurred images are restored using an inverse-filtering approach in the frequency domain. The restored images are then segmented and recognized. Additional experiments examine resolution loss and compare the noise content of two images.

The implementation uses Python, OpenCV, NumPy, SciPy, and Matplotlib.

## Results and Conclusions

- **Ideal images:** The correlation-based recognition method successfully recognizes the four license plates at their original resolution. Experiments indicate that recognition remains reliable at approximately one-quarter of the original spatial sampling rate, although some characters become ambiguous.
- **Realistic images:** Direct recognition fails on the degraded images. After deblurring, the system successfully recognizes the four plates as `98C7445`, `56A7495`, `79B1208`, and `93D4328`, with generally lower correlation scores than in the ideal case.
- **Downsampling:** Recognition performance deteriorates as image resolution decreases. For realistic images, the system generally performs well at the original and half-resolution scales, while more aggressive downsampling causes substantial recognition errors.
- **Noise analysis:** Comparison using Wiener filtering and high-frequency filtering indicates that `n1.jpg` contains more high-frequency noise than `n2.jpg`.

Overall, the project demonstrates how signal-processing concepts can be applied to license plate recognition and highlights the importance of image quality, resolution, and preprocessing. The implemented system works well on the provided examples but remains sensitive to severe degradation and relies on a limited set of reference character templates.
