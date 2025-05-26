# Histogram-of-an-images
## Aim
To obtain a histogram for finding the frequency of pixels in an Image with pixel values ranging from 0 to 255. Also write the code using OpenCV to perform histogram equalization.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:
Read the gray and color image using imread()

### Step2:
Print the image using imshow().

### Step3:
Use calcHist() function to mark the image in graph frequency for gray and color image.

### step4:
Use calcHist() function to mark the image in graph frequency for gray and color image.

### Step5:
The Histogram of gray scale image and color image is shown.


## Program:
```python
# Developed By: Karthikeyan R
# Register Number: 212222240045

import cv2
import numpy as np
import matplotlib.pyplot as plt

grey_img = cv2.imread('dark mickey.webp',cv2.IMREAD_GRAYSCALE)

plt.title("Grey Mickey")
plt.imshow(grey_img,cmap='gray')
plt.axis('off')

plt.title("Histogram of Grey Mickey")
plt.hist(grey_img.ravel(),bins=256,color='black',alpha=0.6)
plt.xlim(0,255)
plt.tight_layout()
plt.show()

equalized_grey_img = cv2.equalizeHist(grey_img)

plt.title("Equalized Hist of Grey Mickey")
plt.hist(equalized_grey_img.ravel(),bins=256,color='black',alpha=0.6)
plt.xlim(0,255)
plt.tight_layout()
plt.show()

plt.title("Enhanced Image")
plt.imshow(equalized_grey_img,cmap='gray')
plt.axis('off')

color_img=cv2.imread('donald.webp')

plt.title("Color Image")
plt.imshow(cv2.cvtColor(color_img,cv2.COLOR_BGR2RGB))
plt.axis('off')

hist_b=cv2.calcHist([color_img],[0],None,[256],[0,256])
hist_g=cv2.calcHist([color_img], [1], None, [256], [0, 256])
hist_r=cv2.calcHist([color_img], [2], None, [256], [0, 256])

plt.title("Hist of color image")
plt.plot(hist_b,color='blue',label='Blue')
plt.plot(hist_g,color='green',label='Green')
plt.plot(hist_r,color='red',label='Red')

blue_channel_eq = cv2.equalizeHist(color_img[:, :, 0])
green_channel_eq = cv2.equalizeHist(color_img[:, :, 1])
red_channel_eq = cv2.equalizeHist(color_img[:, :, 2])

equalized_color_img = cv2.merge([blue_channel_eq, green_channel_eq, red_channel_eq])

plt.imshow(equalized_color_img)

```
## Output:
### Input Grayscale Image and Color Image
![image](https://github.com/user-attachments/assets/f671ae46-786f-47ff-b4e8-c750a0258131)

![image](https://github.com/user-attachments/assets/312570d5-11ea-4a07-ab42-46b833a84b74)

### Histogram of Grayscale Image and any channel of Color Image
![image](https://github.com/user-attachments/assets/974d7e63-8ff4-4d3c-bca5-75c08b95a5f7)

![image](https://github.com/user-attachments/assets/1548ac9e-b69e-4ce6-822a-06ab3e22b426)

### Histogram Equalization of Grayscale Image.

![image](https://github.com/user-attachments/assets/124d75ae-86c0-4636-a34b-39671225161e)

## Result: 
Thus the histogram for finding the frequency of pixels in an image with pixel values ranging from 0 to 255 is obtained. Also,histogram equalization is done for the gray scale image using OpenCV.
