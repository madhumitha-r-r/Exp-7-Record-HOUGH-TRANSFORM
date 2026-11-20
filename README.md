# Exp-7-Record-HOUGH-TRANSFORM

## Aim

To detect lines in an image using the Hough Line Transform technique in OpenCV.

## Software Used

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (`cv2`)
- NumPy
- Matplotlib

## Algorithm

1. Import the required libraries.
2. Read the input image using OpenCV.
3. Convert the input image into grayscale.
4. Display the original and grayscale images.
5. Apply the Canny edge detection algorithm.
6. Detect lines using the Hough Line Transform (`HoughLinesP`).
7. Draw the detected lines on the original image using a for loop.
8. Display the final output image.

## Program


## Developed By

- **Name:** MADHUMITHA R R
- **Register No:** 212224240083

### Step 1: Import Libraries

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

### Step 2: Load the Image

```python
# Step 2: Load the image using imread() from cv2 module
image = cv2.imread('img.jpg')
```

### Step 3: Convert the Image to Grayscale

```python
# Step 3: Convert the image to grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
```

### Step 4: Display Input and Grayscale Images

```python
# Input image and grayscale image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Input Image")
plt.axis('off')

plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
```

### Step 5: Canny Edge Detection

```python
# Step 4: Using Canny operator from cv2, detect the edges of the image
edges = cv2.Canny(gray_image, 50, 150)

# Canny Edge Detector output
plt.imshow(edges, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis('off')
```

### Step 6: Hough Line Transform

```python
# Step 5: Using the HoughLinesP(), detect line coordinates for every point in the image
# The parameters of HoughLinesP are: image, resolution, threshold, minLineLength, maxLineGap
lines = cv2.HoughLinesP(edges, 1, np.pi / 180, 100, minLineLength=50, maxLineGap=10)
```

### Step 7: Draw Detected Lines

```python
# Step 6: Using a for loop, draw the lines on the original image using the detected coordinates
# The lines variable contains the endpoints of the detected lines
if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line.reshape(-1)
        cv2.line(image, (x1, y1), (x2, y2), (0, 255, 0), 2)
```

### Step 8: Display the Result

```python
# Display the result of Hough Transform (Image with lines)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Result of Hough Transform")
plt.axis('off')
```

## Expected Output

1. Input Image
 
   <img width="232" height="302" alt="image" src="https://github.com/user-attachments/assets/fc636c76-d472-4370-95e4-3e9ace62b48e" />
 
2. Grayscale Image

   <img width="227" height="297" alt="image" src="https://github.com/user-attachments/assets/db0546a2-ed4f-4ad8-90a7-73ccaf3e8af2" />

3.Canny Edge Detector Output

   <img width="217" height="306" alt="image" src="https://github.com/user-attachments/assets/f38d95b6-8b29-4496-9baa-0544aa80a9c1" />

4.Result of Hough Transform with detected lines highlighted in green.

  <img width="221" height="302" alt="image" src="https://github.com/user-attachments/assets/b1627dd1-900d-46c4-b430-db18342a06c3" />


## Result

Thus, the Hough Line Transform was successfully implemented using OpenCV. The edges were detected using the Canny operator, and the lines were identified and highlighted on the original image using the Probabilistic Hough Line Transform.
