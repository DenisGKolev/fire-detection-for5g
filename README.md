# FOR5G Fire detection dataset

Rinisoft presents a synthetic image dataset generated using the mask-guided diffusion framework introduced in “FLAME Diffuser: Wildfire Image Synthesis using Mask Guided Diffusion”. This framework leverages pre-trained latent diffusion models (e.g., the Stable Diffusion backbone) and a mask generation module to insert controlled wildfire flame regions into arbitrary background imagery.

In our work, we utilised this open-source technology to construct a dataset comprising 51 synthetic images. Each sample in the dataset consists of a high-resolution RGB frame derived from aerial drone footage, into which a photorealistic flame region has been synthetically composited using a mask-guided diffusion model, ensuring controlled placement and realistic integration with the surrounding scene.

The dataset is intended to support downstream computer-vision tasks such as flame detection, segmentation, and localisation in wildfire-relevant imagery. Because the synthesis process allows precise control over flame placement, size, and background context, the dataset aims to mitigate the paucity of annotated real-world fire imagery and to increase model generalisability across diverse scenes.

We produced mask shapes (rectangles, circles, free-form) and applied Perlin-noise perturbation or other noise-based augmentation to introduce realistic irregular flame boundaries. This follows the methodology described for FLAME in the original paper ( https://arxiv.org/pdf/2403.03463).

Using the pre-trained latent diffusion model, the input comprises the background image, plus the mask indicating where flame should appear, and a text prompt describing the fire scene (e.g., “wildfire flame in forest, high-resolution, photo realistic”). The diffusion model then generates the flame-augmented image while preserving the style of the background.

To ensure the realism and relevance of the synthetic images, we applied a filtering step (e.g., using a CLIP-based confidence score) to discard low-quality or inconsistent samples, akin to the approach in the original work.

