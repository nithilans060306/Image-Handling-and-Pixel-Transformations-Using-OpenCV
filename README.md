# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- ### Name: Nithilan S 
- ### Register Number: 212223240108

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```python
# YOUR CODE HERE
bgr_img = cv2.imread("Eagle_in_Flight.jpg")
```

#### 2. Print the image width, height & Channel.
```python
# YOUR CODE HERE
bgr_img.shape
bgr_img.size
```

#### 3. Display the image using matplotlib imshow().
```python
# YOUR CODE HERE
plt.imshow(bgr_img)
plt.title('BGR Image')
plt.show()
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
# YOUR CODE HERE
cv2.imwrite("Eagle_in_Flight.png", bgr_img)
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
# YOUR CODE HERE
rgb_color_img = cv2.cvtColor(bgr_img, cv2.COLOR_BGR2RGB)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
# YOUR CODE HERE
plt.imshow(rgb_color_img)
plt.title('Color Image')
plt.axis('on')
plt.show()
```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```python
# YOUR CODE HERE
cropped_img = rgb_color_img[10:450, 150:570]
plt.imshow(cropped_img)
plt.axis("off")
```

#### 8. Resize the image up by a factor of 2x.
```python
# YOUR CODE HERE
cropped_resized = cv2.resize(cropped_img, None, fx=2, fy=2, interpolation=cv2.INTER_LINEAR)

plt.imshow(cropped_resized)
plt.title("Cropped & Resized (2x)")
plt.axis("off")
plt.show()
```

#### 9. Flip the cropped/resized image horizontally.
```python
# YOUR CODE HERE
flipped_img = cv2.flip(cropped_img, 1)

plt.imshow(flipped_img)
plt.title('Flipped Image')
plt.axis('off')
plt.show()
```

#### 10. Read in the image ('Apollo-11-launch.jpg').
```python
# YOUR CODE HERE
apollo_img = cv2.imread("Apollo-11-launch.jpg")
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```python
text = 'Apollo 11 Saturn V Launch, July 16, 1969'
font_face = cv2.FONT_HERSHEY_PLAIN
# YOUR CODE HERE: use putText()
cv2.putText(apollo_img, text, (50, apollo_img.shape[0] - 50), font_face, 2, (255, 255, 255), 2)
plt.imshow(apollo_img)
```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```python
# rect_color = magenta
# YOUR CODE HERE
cv2.rectangle(apollo_img, (400, 30), (750, 630), (255, 0, 255), 3)
```

#### 13. Display the final annotated image.
```python
# YOUR CODE HERE
plt.imshow(apollo_img)
```

#### 14. Read the image ('Boy.jpg').
```python
# YOUR CODE HERE
boy_img = cv2.imread("boy.jpg")
```

#### 15. Adjust the brightness of the image.
```python
# Create a matrix of ones (with data type float64)
# matrix_ones = 
# YOUR CODE HERE
import numpy as np
matrix_ones = np.ones(boy_img.shape, dtype='uint8') * 50
```

#### 16. Create brighter and darker images.
```python
img_brighter = cv2.add(img, matrix)
img_darker = cv2.subtract(img, matrix)
# YOUR CODE HERE
img_brighter = cv2.add(boy_img, matrix_ones)
img_darker = cv2.subtract(boy_img, matrix_ones)
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
# YOUR CODE HERE
plt.figure(figsize=(10, 3))
for i, img in enumerate([boy_img, img_darker, img_brighter]):
    plt.subplot(1, 3, i + 1)
    plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.show()
```

#### 18. Modify the image contrast.
```python
# Create two higher contrast images using the 'scale' option with factors of 1.1 and 1.2 (without overflow fix)
# matrix1 = 
# matrix2 = 
# img_higher1 = 
# img_higher2 = 
# YOUR CODE HERE
matrix1 = np.ones(boy_img.shape, dtype='uint8') * 25
matrix2 = np.ones(boy_img.shape, dtype='uint8') * 50
img_higher1 = cv2.addWeighted(boy_img, 1.1, matrix1, 0, 0)
img_higher2 = cv2.addWeighted(boy_img, 1.2, matrix2, 0, 0)
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
# YOUR CODE HERE
plt.figure(figsize=(10, 3))
for i, img in enumerate([boy_img, img_higher1, img_higher2]):
    plt.subplot(1, 3, i + 1)
    plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.show()
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```python
# YOUR CODE HERE
b, g, r = cv2.split(boy_img)
plt.figure(figsize=(10, 3))
for i, channel in enumerate([b, g, r]):
    plt.subplot(1, 3, i + 1)
    plt.imshow(channel)
plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```python
# YOUR CODE HERE
merged = cv2.merge([b, g, r])
plt.imshow(cv2.cvtColor(merged, cv2.COLOR_BGR2RGB))
plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```python
# YOUR CODE HERE
hsv = cv2.cvtColor(boy_img, cv2.COLOR_BGR2HSV)
h, s, v = cv2.split(hsv)
plt.figure(figsize=(10, 3))
for i, channel in enumerate([h, s, v]):
    plt.subplot(1, 3, i + 1)
    plt.imshow(channel, cmap='gray')
plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```python
# YOUR CODE HERE
merged_hsv = cv2.merge([h, s, v])
plt.imshow(cv2.cvtColor(merged_hsv, cv2.COLOR_HSV2RGB))
plt.show()
```

## Output:
- **i)** Read and Display an Image.  
- **ii)** Adjust Image Brightness.  
- **iii)** Modify Image Contrast.  
- **iv)** Generate Third Image Using Bitwise Operations.

## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

