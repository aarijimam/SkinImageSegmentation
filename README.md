# Skin Image Segmentation using Connected Component Analysis

This project implements a skin image segmentation technique using Connected Component Analysis (CCA) in Python. The goal is to segment different layers of the skin, including Dermal-epidermal junction, Dermis, Epidermis, Keratin, and Background, in skin images.

## Table of Contents
- [Introduction](#introduction)
- [Dependencies](#dependencies)
- [Usage](#usage)
- [Results](#results)
- [Acknowledgments](#acknowledgments)

## Introduction

Skin image segmentation is a crucial step in many medical image analysis applications, including dermatology and pathology. This project focuses on segmenting various layers of skin using a custom 8-connectivity Connected Component Analysis algorithm.

## Dependencies

- Python 3.x
- Jupyter Notebook
- OpenCV
- NumPy
- Matplotlib

## Usage

1. Clone the repository:

    ```bash
    git clone https://github.com/your_username/skin-image-segmentation.git
    ```

2. Navigate to the project directory:

    ```bash
    cd skin-image-segmentation
    ```

3. Launch Jupyter Notebook:

    ```bash
    jupyter notebook
    ```

4. Open and run the `Skin_Image_Segmentation.ipynb` notebook.

5. Follow the instructions in the notebook to train the V sets and perform CCA on the test images.

## Results

The segmentation results are displayed using different colors for each skin layer:

- Dermal-epidermal junction: Pink
- ![image](https://github.com/aarijimam/SkinImageSegmentation/assets/35100854/6f0a9cc2-4647-4099-964a-9eaca34dcee8)
- Dermis: Green
- ![image](https://github.com/aarijimam/SkinImageSegmentation/assets/35100854/705b2e00-ddcf-464b-9d2a-5eda10f4a412)
- Epidermis: Purple
- ![image](https://github.com/aarijimam/SkinImageSegmentation/assets/35100854/b99b9b2f-22ef-4c32-8dda-e53918be90b0)
- Keratin: White
- ![image](https://github.com/aarijimam/SkinImageSegmentation/assets/35100854/97b050c2-22f0-431d-82d2-da7ab2493d05)
- Background: Black
- ![image](https://github.com/aarijimam/SkinImageSegmentation/assets/35100854/fa9f15c5-fd81-4551-a1bc-dde28df32111)

- Skin Layers Combined (Generated)
- ![image](https://github.com/aarijimam/SkinImageSegmentation/assets/35100854/3590d0da-beef-4713-b352-604ba51e4b91)
- Actual Mask
- ![image](https://github.com/aarijimam/SkinImageSegmentation/assets/35100854/cc74be9c-f3a4-4521-84c9-8fe32f72188c)

Sample results and visualizations are provided in the notebook.

##Steps
### Background Removal

The first step involved removing the background from skin images utilizing 8-Way Connected Component Analysis. Initially, I noticed that most of the background appeared as completely white with an intensity of 255 in grayscale. However, due to slight variations in pixel values, a set (V set) with values ranging from 250 to 255 was created. After applying CCA, it became evident that the background constituted the largest segment of the formed layers. Thus, the largest segment was identified and its gray values were set to 0 to represent the background. The background was then shaded white while the rest of the image was shaded black for further processing. Additionally, Gaussian Blur was applied to blend some outlier pixels for improved results, although similar outcomes could be achieved without this step.

### Skin Layer Definition

The subsequent objective was to define V sets for each skin layer. The approach involved utilizing 8-connectivity based CCA to separate each layer based on the V set. To define the V sets, the provided training data was utilized. A comparison was made between each tissue and its corresponding mask to create a map of each gray level intensity present in each layer. However, including every single gray level would lead to overlapping intensities and each layer covering almost the entire image. To address this, the count of each intensity present in each layer was maintained, and intensities present in very little amount were removed. For instance, if gray levels 150-250 were present 20,000 times in a layer but gray levels 50-100 were present only 500 times, the lower end of those gray levels would be removed. Using all 26 provided training images, a V set was formed for each layer of skin tissue.

### Layer Separation and Reconstruction

Performing 8 connectivity CCA on the image using the above V sets separates the layers for us. With layers separated, we perform CCA again on the separated layer to find gaps between the layers and fill them, resulting in a relatively smooth layer. The layers are then overlayed on top of one another systematically. Starting with the Keratin, then Dermis, then Epidermis, we know that the Dermal-Epidermal Junction is only present between Dermis and Epidermis join, so we only add the Dermal-Epidermal Layer where the two layers are connecting. Lastly, we add the background.

This project demonstrates the effectiveness of Connected Component Analysis in segmenting skin images, enabling precise background removal and definition of distinct skin layers.

## Acknowledgments

This project was inspired by the need for accurate skin image segmentation techniques in medical image analysis. Special thanks to OpenCV, NumPy, and Matplotlib for providing essential tools for image processing and visualization.
