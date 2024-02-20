# YOLOv8_Explainer
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
<!-- [![Downloads](https://static.pepy.tech/personalized-badge/grad-cam?period=month&units=international_system&left_color=black&right_color=brightgreen&left_text=Monthly%20Downloads)](https://pepy.tech/project/YOLOv8-Explainer)
[![Downloads](https://static.pepy.tech/personalized-badge/grad-cam?period=total&units=international_system&left_color=black&right_color=blue&left_text=Total%20Downloads)](https://pepy.tech/project/YOLOv8-Explainer) -->
## Simplify your understanding of YOLOv8 Results


### Install Environment & Dependencies

`YOLOv8-Explainer` can be seamlessly integrated into your projects with a straightforward installation process:

#### Installation as a Package

To incorporate `YOLOv8-Explainer` into your project as a dependency, execute the following command in your terminal:

```bash
pip install YOLOv8-Explainer
```

## Features and Functionality

`YOLOv8-Explainer`  can be used to deploy various different CAM models for cutting-edge XAI methodologies in `YOLOv8` for images:

- GradCAM : Weight the 2D activations by the average gradient
- GradCAM + + : Like GradCAM but uses second order gradients
- XGradCAM : Like GradCAM but scale the gradients by the normalized activations
- EigenCAM : Takes the first principle component of the 2D Activations (no class discrimination, but seems to give great results)
- HiResCAM : Like GradCAM but element-wise multiply the activations with the gradients; provably guaranteed faithfulness for certain models
- LayerCAM : Spatially weight the activations by positive gradients. Works better especially in lower layers
- EigenGradCAM : Like EigenCAM but with class discrimination: First principle component of Activations*Grad. Looks like GradCAM, but cleaner


# Using from code as a library

```python

from YOLOv8_Explainer import yolov8_heatmap, display_images

model = yolov8_heatmap(
    weight="/location/model.pt", conf_threshold=0.4, renormalize=False,
)

imagelist = model(
    img_path="/location/image.jpg", 
    )

display_images(imagelist)

```

You can choose between the following CAM Models for version 0.0.2:

`GradCAM` , `HiResCAM`, `GradCAMPlusPlus`, `XGradCAM` , `LayerCAM`, `EigenGradCAM` and `EigenCAM`.