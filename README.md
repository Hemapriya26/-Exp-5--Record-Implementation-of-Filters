# Image Smoothing and Sharpening Using OpenCV

## Aim

To write a Python program using OpenCV to apply different smoothing filters (Averaging, Weighted Averaging, Gaussian, Median) and sharpening filters (Laplacian Kernel and Laplacian Operator) for image enhancement, and display each result separately along with the original image for comparison.

---

## The program performs the following operations:

- Read and display an input image  
- Apply Averaging filter  
- Apply Weighted Averaging filter  
- Apply Gaussian filter  
- Apply Median filter  
- Apply Laplacian sharpening using kernel  
- Apply Laplacian operator  
- Display all outputs for comparison  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image (e.g., `image.jpg`).

### Step 3:
Convert the image from BGR to RGB format for display.

### Step 4:
Apply Averaging Filter using `cv2.blur()`.

### Step 5:
Apply Weighted Averaging Filter using a custom kernel with `cv2.filter2D()`.

### Step 6:
Apply Gaussian Filter using `cv2.GaussianBlur()`.

### Step 7:
Apply Median Filter using `cv2.medianBlur()`.

### Step 8:
Apply Laplacian Sharpening using Kernel with `cv2.filter2D()`.

### Step 9:
Convert image to grayscale and apply Laplacian Operator using `cv2.Laplacian()`.

### Step 10:
Display all filtered images using a grid layout for comparison.

---

##  Developed By

- **Name: Hemapriya P**
- **Register No: 212225040126**

---

## Program

```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# ==========================================
# 1. READ AND DISPLAY ORIGINAL IMAGE
# ==========================================

img = cv2.imread('scenery1.png')

if img is None:
    print("Image not found!")
else:
    print("Image loaded successfully.")

# Convert BGR to RGB for Matplotlib
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(6, 6))
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis('off')
plt.show()


# ==========================================
# 2. AVERAGING FILTER
# ==========================================

avg_filter = cv2.blur(img_rgb, (15, 15))


# ==========================================
# 3. WEIGHTED AVERAGING FILTER
# ==========================================

kernel = np.array([
    [1, 4, 6, 4, 1],
    [4, 16, 24, 16, 4],
    [6, 24, 36, 24, 6],
    [4, 16, 24, 16, 4],
    [1, 4, 6, 4, 1]
], dtype=np.float32)

kernel = kernel / kernel.sum()

weighted_img = cv2.filter2D(img_rgb, -1, kernel)


# ==========================================
# 4. GAUSSIAN FILTER
# ==========================================

gaussian_filter = cv2.GaussianBlur(img_rgb, (15, 15), 5)


# ==========================================
# 5. MEDIAN FILTER
# ==========================================

median_filter = cv2.medianBlur(img_rgb, 15)


# ==========================================
# 6. SHARPENING FILTER
# ==========================================

sharp_kernel = np.array([
    [0, -1, 0],
    [-1, 5, -1],
    [0, -1, 0]
])

sharpened_img = cv2.filter2D(img_rgb, -1, sharp_kernel)


# ==========================================
# 7. DISPLAY ALL FILTERED IMAGES
# ==========================================

plt.figure(figsize=(15, 10))

plt.subplot(2, 3, 1)
plt.imshow(img_rgb)
plt.title("Original")
plt.axis('off')

plt.subplot(2, 3, 2)
plt.imshow(avg_filter)
plt.title("Averaging Filter")
plt.axis('off')

plt.subplot(2, 3, 3)
plt.imshow(weighted_img)
plt.title("Weighted Averaging")
plt.axis('off')

plt.subplot(2, 3, 4)
plt.imshow(gaussian_filter)
plt.title("Gaussian Filter")
plt.axis('off')

plt.subplot(2, 3, 5)
plt.imshow(median_filter)
plt.title("Median Filter")
plt.axis('off')

plt.subplot(2, 3, 6)
plt.imshow(sharpened_img)
plt.title("Laplacian Sharpening")
plt.axis('off')

plt.tight_layout()
plt.show()


# ==========================================
# 8. CONVERT IMAGE TO GRAYSCALE
# ==========================================

gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

plt.figure(figsize=(5, 5))
plt.imshow(gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
plt.show()


# ==========================================
# 9. LAPLACIAN OPERATOR
# ==========================================

laplacian = cv2.Laplacian(gray, cv2.CV_64F)

# Convert to absolute values
laplacian = np.absolute(laplacian)

# Convert back to uint8 for display
laplacian = np.uint8(laplacian)

plt.figure(figsize=(5, 5))
plt.imshow(laplacian, cmap='gray')
plt.title("Laplacian Operator")
plt.axis('off')
plt.show()
```

##  Output

### Smoothing Filters

- Averaging filter produces blurred image  
- Weighted averaging provides smoother result with less distortion  
- Gaussian filter preserves edges better while reducing noise  
- Median filter removes salt-and-pepper noise effectively

<img width="1296" height="687" alt="image" src="https://github.com/user-attachments/assets/186450d5-83ab-4463-99ff-8340fc3697b4" />


###  Sharpening Filters

- Laplacian kernel enhances edges and fine details  
- Laplacian operator detects edges clearly in grayscale

<img width="547" height="677" alt="image" src="https://github.com/user-attachments/assets/5ff7aa60-5867-4da8-8317-bd3dba331a64" />


---

##  Result

Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and improve image quality, while sharpening filters enhance edges and details for better feature extraction.
