# Image Segmentation Using Thresholding Techniques in OpenCV

## Aim

To segment an image using Global Thresholding, Adaptive Thresholding, and Otsu's Thresholding techniques using Python and OpenCV.

The program performs the following operations:

- Global Thresholding
- Adaptive Thresholding
- Otsu's Thresholding

## Software Used

- Anaconda – Python 3.7 (or higher)
- Jupyter Notebook / VS Code
- OpenCV (`cv2`)
- NumPy
- Matplotlib

## Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Load the input image using OpenCV.

### Step 3:
Convert the input image into grayscale format.

### Step 4: Global Thresholding
- Select a fixed threshold value (`127`).
- Apply thresholding (`cv2.THRESH_BINARY`) to separate foreground and background pixels.
- Display the thresholded image.

### Step 5: Adaptive Thresholding
- Compute threshold values dynamically for small local regions of the image.
- Apply Adaptive Gaussian Thresholding (`cv2.ADAPTIVE_THRESH_GAUSSIAN_C`).
- Display the segmented image.

### Step 6: Otsu's Thresholding
- Automatically determine the optimal global threshold value from the image histogram.
- Apply Otsu's thresholding technique (`cv2.THRESH_BINARY + cv2.THRESH_OTSU`).
- Display the segmented image.

### Step 7:
Compare the visual results obtained from Global, Adaptive, and Otsu's thresholding methods side by side.

## Program

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 2: Read the image and convert to grayscale
image = cv2.imread('my.jpeg')  # Replace with your image file path
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)  # Convert to grayscale

# Step 3: Use Global Thresholding to segment the image
# Apply global thresholding with a threshold value of 127
_, global_thresholded = cv2.threshold(gray_image, 127, 255, cv2.THRESH_BINARY)

# Step 4: Use Adaptive Thresholding to segment the image
# Apply adaptive thresholding using Gaussian method
adaptive_thresholded = cv2.adaptiveThreshold(
    gray_image, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C, cv2.THRESH_BINARY, 11, 2
)

# Step 5: Use Otsu's method to segment the image
# Apply Otsu's method for optimal thresholding
_, otsu_thresholded = cv2.threshold(
    gray_image, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU
)

# Step 6: Display Original and Segmented Images
plt.figure(figsize=(10, 8))

# Original Image
plt.subplot(2, 2, 1)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Convert from BGR to RGB for display
plt.title("Original Image")
plt.axis('off')

# Global Thresholding
plt.subplot(2, 2, 2)
plt.imshow(global_thresholded, cmap='gray')
plt.title("Global Thresholding")
plt.axis('off')

# Adaptive Thresholding
plt.subplot(2, 2, 3)
plt.imshow(adaptive_thresholded, cmap='gray')
plt.title("Adaptive Thresholding")
plt.axis('off')

# Otsu's Method
plt.subplot(2, 2, 4)
plt.imshow(otsu_thresholded, cmap='gray')
plt.title("Otsu's Method")
plt.axis('off')

# Show the plot
plt.tight_layout()
plt.show()
```

## Developed By

- **Name:** SURYA D
- **Register No:** 212224220115

## Output

### Original Image
- The original color image (`my.jpeg`) is loaded in RGB format for reference alongside the segmented outputs.

<img width="145" height="209" alt="download" src="https://github.com/user-attachments/assets/bc3847d6-cd25-40ba-b0d6-4170beed21f8" />


### Global Thresholding
- Uses a fixed threshold value (`127`) across the entire grayscale image.
- Pixels above `127` are set to `255` (white/foreground) and pixels below are set to `0` (black/background).

<img width="290" height="306" alt="image" src="https://github.com/user-attachments/assets/7b4b97b7-da55-4ac6-8eb0-4137ff9556e4" />


### Adaptive Thresholding
- Threshold values are calculated locally using a Gaussian-weighted neighborhood (`11x11` block size, constant `C = 2`).
- Preserves fine edges and details effectively under varying lighting or uneven illumination.

<img width="333" height="321" alt="image" src="https://github.com/user-attachments/assets/926d324a-280b-4812-9ac6-93400dd95412" />


### Otsu's Thresholding
- Automatically computes the optimal threshold value by minimizing intra-class variance.
- Produces clean foreground-background separation, particularly effective for images with bimodal intensity histograms.

<img width="240" height="322" alt="image" src="https://github.com/user-attachments/assets/9c6f3199-da80-41ef-bb90-14ccec7597c4" />



## Result

Thus, image segmentation is successfully performed using **Global Thresholding, Adaptive Thresholding, and Otsu's Thresholding** techniques in OpenCV.
