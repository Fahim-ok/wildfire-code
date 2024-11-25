# Image Dehazing Using Dark Channel Prior

This script implements an **image dehazing algorithm** based on **Dark Channel Prior (DCP)** and atmospheric light estimation. The goal is to recover clear images from hazy or foggy scenes by estimating and removing the haze effects.

## Features

### 1. **Dark Channel Calculation**
- Identifies the hazy regions in an image by computing the minimum intensity across color channels for each pixel in a local neighborhood.
- Used to estimate the density of haze in an image.

### 2. **Atmospheric Light Estimation**
- Finds the brightest regions in the dark channel to determine the global atmospheric light.
- Supports both:
  - **Single-pixel light estimation**: Based on the brightest pixel.
  - **Mean-based light estimation**: Uses the average of multiple bright pixels.

### 3. **Transmission Map Estimation**
- Calculates the proportion of light that penetrates the haze and reaches the camera.
- Ensures a minimum transmission threshold to prevent excessive darkening.
- Offers **refinement options** using guided filtering for smoother results.

### 4. **Scene Radiance Recovery**
- Removes haze and reconstructs the original image using the following formula:
  \[
  R(x) = \frac{I(x) - A}{t(x)} + A
  \]
  Where:
  - \( R(x) \): Recovered radiance (dehazed image).
  - \( I(x) \): Original intensity (hazy image).
  - \( A \): Atmospheric light.
  - \( t(x) \): Transmission map.

### 5. **Refinement**
- Refines the transmission map using guided filtering to maintain edge details while smoothing out noise.

## Customizable Parameters
- **Block Size**: Controls the size of the sliding window for dark channel computation.
- **Omega**: Determines the haze density used in the transmission map.
- **Percent**: Controls the proportion of pixels considered for atmospheric light estimation.
- **Refinement Options**: Enables or disables guided filtering.

## Applications
- **Photography and Videography**: Enhances visibility in outdoor scenes.
- **Aerial or Satellite Imagery**: Prepares images for further analysis by removing haze.
- **Autonomous Vehicles**: Improves perception in adverse weather conditions like fog or smog.

## How to Use
1. Load the image into the script.
2. Call the following functions:
   - **Dark Channel Calculation**:
     ```python
     dark_channel = getDarkChannel(image, blockSize=15)
     ```
   - **Atmospheric Light Estimation**:
     ```python
     atmospheric_light = getAtomsphericLight(dark_channel, image, percent=0.001)
     ```
   - **Scene Radiance Recovery**:
     ```python
     dehazed_image = getRecoverScene(image, blockSize=15)
     ```
3. Save or visualize the dehazed image.

   # Advanced Image Segmentation and Classification Framework

This repository integrates **Involution Layers**, **MobileNetV2**, and **Multi-Task U-Net Architectures** to perform segmentation and classification tasks on images. It also includes enhancement techniques like **Dark Channel Prior (DCP)** and **Multi-Scale Retinex (MSR)** for preprocessing.

## Features

- **Involution Neural Networks (INNs)**:
  - Efficient feature extraction with reduced computational overhead.
- **MobileNetV2 Backbone**:
  - Pretrained model for segmentation and classification tasks.
- **Multi-Task U-Net Architecture**:
  - Simultaneous image segmentation and classification outputs.
- **Dark Channel Prior & MSR**:
  - Image dehazing and dynamic range enhancement.
- **Custom Loss Functions**:
  - Focal loss and Mean IoU for improved segmentation accuracy.




## Example Outputs
- **Input Image (Hazy)**:
  ![Hazy Image](examples/hazy_image.png)

- **Output Image (Dehazed)**:
  ![Dehazed Image](examples/dehazed_image.png)

## Dependencies
- Python 3.7+
- NumPy
- OpenCV
- Matplotlib

## Contributions
Contributions are welcome! Feel free to open an issue or pull request to suggest improvements or new features.

## License
This project is licensed under the MIT License.
