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
- Dermis: Green
- Epidermis: Purple
- Keratin: White
- Background: Black

Sample results and visualizations are provided in the notebook.

## Acknowledgments

This project was inspired by the need for accurate skin image segmentation techniques in medical image analysis. Special thanks to OpenCV, NumPy, and Matplotlib for providing essential tools for image processing and visualization.
