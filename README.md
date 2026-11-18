# Opening and Closing Operations Using OpenCV

## Aim

To write a Python program using OpenCV to perform morphological Opening and Closing operations on an image.

The program performs the following operations:

- Morphological Opening
- Morphological Closing

## Software Used

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (cv2)
- NumPy
- Matplotlib

## Algorithm

### Step 1:

Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:

Create or load an input image containing foreground objects.

### Step 3:

Display the original image.

### Step 4:

Create a structuring element (kernel) of suitable size.

### Step 5: Opening Operation

- Apply the Opening operation using the structuring element.
- Opening consists of Erosion followed by Dilation.
- Remove small foreground noises while preserving the shape of larger objects.
- Display the opened image.

### Step 6: Closing Operation

- Apply the Closing operation using the structuring element.
- Closing consists of Dilation followed by Erosion.
- Fill small holes and gaps within foreground objects.
- Display the closed image.

### Step 7:

Compare the original, opened, and closed images.

## Program

```
# Image Opening and Closing using OpenCV

# Step 1: Import Required Libraries
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 2: Create an Input Image
img = np.zeros((400, 600), dtype=np.uint8)

cv2.rectangle(img, (100, 100), (300, 300), 255, -1)
cv2.circle(img, (450, 200), 80, 255, -1)

# Add small noise
img[50, 50] = 255
img[350, 500] = 255
img[80, 400] = 255

# Step 3: Display Original Image
plt.figure(figsize=(6, 4))
plt.imshow(img, cmap='gray')
plt.title('Original Image')
plt.axis('off')
plt.show()

# Step 4: Create Structuring Element (Kernel)
kernel = np.ones((5, 5), np.uint8)

# Step 5: Opening Operation (Erosion + Dilation)
opening = cv2.morphologyEx(img, cv2.MORPH_OPEN, kernel)

plt.figure(figsize=(6, 4))
plt.imshow(opening, cmap='gray')
plt.title('Opening Operation')
plt.axis('off')
plt.show()

# Step 6: Closing Operation (Dilation + Erosion)
closing = cv2.morphologyEx(img, cv2.MORPH_CLOSE, kernel)

plt.figure(figsize=(6, 4))
plt.imshow(closing, cmap='gray')
plt.title('Closing Operation')
plt.axis('off')
plt.show()

# Step 7: Compare All Three Images
images = [img, opening, closing]
titles = ['Original Image', 'Opening', 'Closing']

plt.figure(figsize=(15, 5))

for i in range(3):
    plt.subplot(1, 3, i + 1)
    plt.imshow(images[i], cmap='gray')
    plt.title(titles[i])
    plt.axis('off')

plt.tight_layout()
plt.show()
```

## Developed By

**Name:** Santhosh K

**Register No:** 212225040379

## Output

<img width="1489" height="362" alt="image" src="https://github.com/user-attachments/assets/dfa2efff-0aff-4f28-ae84-bed6c9dafcf9" />


## Applications

### Opening

- Noise removal in binary images.
- Separation of connected objects.
- Preprocessing for object detection.

### Closing

- Filling small holes in objects.
- Connecting nearby components.
- Enhancing segmented regions.

## Advantages

### Opening

- Removes unwanted foreground noise.
- Preserves major object structures.
- Improves segmentation quality.

### Closing

- Restores object continuity.
- Eliminates small background gaps.
- Improves object representation.

## Result

Thus, the morphological operations **Opening** and **Closing** are successfully implemented using OpenCV. 
