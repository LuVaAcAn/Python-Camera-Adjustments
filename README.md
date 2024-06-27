# Python-Camera-Adjustments
The following Python code uses the OpenCV library to capture live video from a webcam and applies various image filters in real-time using a GUI created with Tkinter. The code also allows the user to adjust several image properties such as brightness, contrast, sharpness, and more. 🎥✨
It provides an intuitive interface to adjust properties like brightness, contrast, and color balance directly through Python code. Some filters can be buggy if placed together

Created using Python 3.12.2, CV2 Libary and Tkinter Library

## Imports 📦

-   `cv2`: OpenCV library for image processing.
-   `numpy`: Library for numerical computations.
-   `tkinter`: Standard GUI library in Python.
-   `datetime`: Module to work with dates and times.
-   `PIL`: Python Imaging Library for image processing.

## Image Adjustment Functions 🔧

These functions adjust various image properties.

### Brightness Adjustment ☀️

Adjusts the brightness of the image.

### Contrast Adjustment 🌈

Adjusts the contrast of the image.

### Sharpness Adjustment 🖋️

Adjusts the sharpness of the image.

### Laplacian Filter 🔍

Applies a Laplacian filter for edge detection.

### Gaussian Blur 🌫️

Applies Gaussian blur to the image.

### Hue Adjustment 🎨

Adjusts the hue of the image.

### Saturation Adjustment 🌟

Adjusts the saturation of the image.

### Chromatic Aberration 🌈

Applies chromatic aberration to the image.

### Conservative Smoothing ✨

Applies conservative smoothing to the image.

### Edge Detection 📏

Applies edge detection using the Canny algorithm.

### Sepia Filter 📜

Applies a sepia filter to the image.

### Mean Blur 🌀

Applies mean blur to the image.

### Median Blur 🔮

Applies median blur to the image.

### Bilateral Filter 🎛️

Applies a bilateral filter to the image.

### Grayscale Conversion ⚫⚪

Converts the image to grayscale.

### Negative Conversion 🔄

Converts the image to a negative.

### Color Balance 🎨

Adjusts the color balance of the image.

### Sobel Filter 🖊️

Applies a Sobel filter for edge detection.

### Roberts Filter 📐

Applies a Roberts filter for edge detection.

## Update Image Function 🔄

-   `actualizaImagen`: Captures a frame from the webcam, applies selected filters and adjustments, and updates the image in the GUI.

## Tkinter GUI Setup 🖥️

### Main Window 🏠

Creates the main window for the application.

### Create Widgets 📲

Creates the label to display the video and initializes the filter options.

### Filter Dropdown 📋

Creates a dropdown menu for selecting filters.

### Scales for Adjustments 🎛️

Creates scales (sliders) for adjusting brightness, contrast, sharpness, blur, hue, saturation, mean blur, median blur, bilateral filter, and color balance.

This setup allows the user to interactively adjust these properties and see the results in real-time on their webcam feed.

=
Luciano Valentino Achin Angeles
