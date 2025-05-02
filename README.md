# Panorama Generation with Region-Based Control

This repository presents our final project for the Carnegie Mellon University course **16-726: Learning-Based Image Synthesis (Spring 2025)**. We propose a novel pipeline for generating panoramic images with **region-based semantic control**, improving upon the MultiDiffusion framework by addressing its limitations in coherence and region consistency.

## Authors

- **Yinghao Zhang** – yinghaoz@andrew.cmu.edu  
- **Keling Yao** – kennyy@andrew.cmu.edu  
- **Silong Yong** – silongy@andrew.cmu.edu  
- *Carnegie Mellon University*

## Abstract

We introduce a method that enables diffusion-based models to generate panorama images with precise region-level control. While existing techniques such as MultiDiffusion can generate either panoramic structures or region-conditioned images, they fail to combine both capabilities effectively. Specifically, MultiDiffusion often violates region boundaries and lacks global consistency.

To overcome these challenges, our method introduces:
1. **Center-outward panorama generation** to preserve global spatial structure.
2. **Dependent denoising across patches** in early timesteps to reduce inconsistencies.

Our results show significant improvements in image coherence and adherence to semantic masks.

## Methodology

### Motivation

Diffusion models have shown strong capabilities in image synthesis, including panoramic and region-based generation. However, when tasked with both objectives simultaneously, conventional methods exhibit weaknesses such as inconsistent textures and semantic bleeding across regions.

### Key Improvements

- **Dependent Denoising**: Patches are denoised jointly in the early stages to maintain visual coherence across regions. This is particularly useful in ensuring consistent skies, lighting, and object shapes.
  
- **Structured Patch Generation**: Instead of generating sequentially across the horizontal axis, we generate panoramas by expanding outward from the center. This strategy preserves continuity better than edge-first expansion.

- **Mask-aware Composition**: We blend foreground and background using region masks and distinct prompts. Unlike MultiDiffusion, we enhance the integration process to respect boundaries and maintain prompt relevance.

## Comparison with MultiDiffusion

| Feature                      | MultiDiffusion          | Our Method                         |
|-----------------------------|--------------------------|-------------------------------------|
| Panorama support            | Yes                      | Yes                                 |
| Region-based control        | Yes                      | Yes                                 |
| Combined effectiveness      | Poor                     | Strong                              |
| Denoising strategy          | Independent              | Dependent (early steps)             |
| Panorama generation order   | Sequential (left to right) | Center-outward                     |

## Results

A representative result is shown below, where the background consists of Manhattan’s skyline and the foreground shows a forest park. The generation respects the provided masks and text prompts for each region.

![Teaser](./assets/teaser.png)

## File Structure

```bash
├── assets/                     # Visual examples and figures
├── configs/                   # Configuration files for generation
├── scripts/                   # Code for image generation
├── models/                    # Optional pre-trained models
├── results/                   # Generated samples
└── README.md                  # Documentation
```

## Citation

If you find our project useful, please cite it as:

```bibtex
@misc{panorama2025regioncontrol,
  title={Panorama Generation with Region-Based Control},
  author={Zhang, Yinghao and Yao, Keling and Yong, Silong},
  year={2025},
  institution={Carnegie Mellon University},
  note={16-726 Final Project}
}
```

## Project Links

- Project page: [CMU 16-726 Website](https://www.andrew.cmu.edu/course/16-726-sp25/projects/kennyy/project/)
- GitHub repository: [GitHub](https://github.com/KennyYao2001/panorama_generation_with_region-based_mask)

## Contact

For questions, please contact any of the authors via email.
