# DIPT-Ex-1
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
- **Name:** Nishma Sherin .K  
- **Register Number:** 212224240104

## Program:


Step1:
Load an image from your local directory and display it.

```
import cv2
import matplotlib.pyplot as plt
# Read the image using OpenCV
img = cv2.imread('cat.jpg', cv2.IMREAD_COLOR)
# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
# Display the image using Matplotlib
plt.imshow(img_rgb, cmap='viridis')  # You can change 'viridis' to another cmap or use None for RGB images
plt.title("Original Image")
plt.axis('off')  # Removes axis ticks and labels
plt.show()
```
Step2:
o Draw a line from the top-left to the bottom-right of the image.

o Draw a circle at the center of the image. 

o Draw a rectangle around a specific region of interest in the image. 

o Add the text "OpenCV Drawing" at the top-left corner of the image.

Draw a line from the top-left to the bottom-right of the image

```
# Load the image
image = cv2.imread('cat.jpg')
# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape
# Draw a line from top-left to bottom-right
line_img = cv2.line(img_rgb, (0, 0), (768, 600), (255, 0, 0), 2) # cv2.line(image, start_point, end_point, color, thickness)
plt.imshow(line_img, cmap='viridis')  
plt.title("Image with Line")
plt.axis('off')  
plt.show()
```

Draw a circle at the center of the image.

```
# Load the image
image = cv2.imread('cat.jpg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

img_rgb.shape

circle_img = cv2.circle(img_rgb,(400,300),150,(255,0,0),10) # cv2.circle(image, center, radius, color, thickness)

plt.imshow(circle_img, cmap='viridis')  
plt.title("Image with Circle")
plt.axis('off')  
plt.show()
```
Draw a rectangle around  the whole image

```
# Load the image
image = cv2.imread('cat.jpg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img.shape
height, width = img_rgb.shape[:2]

# Draw ONLY ONE rectangle
rectangle_img = cv2.rectangle(
    img_rgb.copy(),
    (0, 0),
    (width - 1, height - 1),
   (0, 0, 255),
    3
)
plt.figure(figsize=(8, 5))
plt.imshow(rectangle_img)
plt.title("Image with Rectangle")
plt.axis('off')
plt.show()

```

Add the text "OpenCV Drawing" at the top-left corner of the image.

```
# Load the image
image = cv2.imread('cat.jpg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Add text to the image
text_img = cv2.putText(img_rgb, "OpenCV Drawing", (10, 30), cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 255, 255), 10)  ## cv2.putText(image, text, position, font, font_scale, color, thickness)

plt.imshow(text_img, cmap='viridis')  
plt.title("Image with Text")
plt.axis('off')  
plt.show()
```
Step3:
o Convert the image from RGB to HSV and display it.
    
o Convert the image from RGB to GRAY and display it. 

o Convert the image from RGB to YCrCb and display it. 
    
o Convert the HSV image back to RGB and display it.

```
# Load the image
image = cv2.imread('cat.jpg') 

image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Original RGB Image
plt.imshow(image_rgb)
plt.title("Original RGB Image")
plt.axis("off")

# Convert RGB to HSV
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)

# HSV Image
plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis("off")

# Convert RGB to GRAY
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)

# Grayscale Image
plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("off")

# Convert RGB to YCrCb
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)

# YCrCb Image
plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis("off")

# Convert HSV back to RGB
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)

plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("off")
```
Step4:
o Access and print the value of the pixel at coordinates (100, 100). 

o Modify the color of the pixel at (200, 200) to white.

```
# Modify a block of pixels (300x300) to white, starting from (200, 200)
image[200:500, 200:500] = [255, 255, 255]  # Rows: 200-499, Columns: 200-499

# Convert BGR to RGB for displaying with Matplotlib
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Display the modified image
plt.imshow(image_rgb)
plt.title("Image with 300x300 White Block")
plt.axis("off")
plt.show()
```
Step5:
o Resize the original image to half its size and display it.


```
# Load the image
image = cv2.imread('cat.jpg') 

image.shape

# Resize the image to half its size
resized_image = cv2.resize(image, (768 // 2, 600 // 2))  # (new_width, new_height)

# Convert BGR to RGB for displaying with Matplotlib
resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)

resized_image_rgb.shape

# Display the resized image
plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("off")
plt.show()
```

Step6:
o Crop a region of interest (ROI) from the image (e.g., a 100x100 pixel area starting at (50, 50)) and display it.

```
# Load the image
image = cv2.imread('cat.jpg') 

image.shape

# Crop a 300x300 region starting from (50, 50)
roi = image[50:350, 50:350]  # Rows: 50-349, Columns: 50-349

# Convert BGR to RGB for displaying with Matplotlib
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)

# Display the cropped region (ROI)
plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("off")
plt.show()
```
Step7:
o Flip the original image horizontally and display it. 

o Flip the original image vertically and display it.

```
# Load the image
image = cv2.imread('cat.jpg') 

# Flip the image horizontally (left-right)
flipped_horizontally = cv2.flip(image, 1)

# Convert BGR to RGB for displaying with Matplotlib
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)

# Horizontal flip
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")

# Flip the image vertically (up-down)
flipped_vertically = cv2.flip(image, 0)

# Convert BGR to RGB for displaying with Matplotlib
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)

# Vertical flip
plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("off")
```

Step8:
Save the final modified image to your local directory.





## Output:

## Original Image:


<img width="732" height="424" alt="image" src="https://github.com/user-attachments/assets/94276c5c-8e38-4ef8-b284-9c2b59e33fae" />


## Image with Line:


<img width="751" height="424" alt="image" src="https://github.com/user-attachments/assets/766434ce-3cc7-4a08-9b18-a4c08e3f52db" />

## Image with Circle:


<img width="757" height="439" alt="image" src="https://github.com/user-attachments/assets/e13450db-b2f6-4c20-99eb-7d83006bbfcc" />


## Image with Rectangle:


<img width="753" height="421" alt="image" src="https://github.com/user-attachments/assets/a6b5b15c-c3dc-46e2-a820-be5cf0564a05" />

## Image with Text:


<img width="461" height="237" alt="image" src="https://github.com/user-attachments/assets/9c595261-0a23-401e-9b78-866ce43d1abd" />


## Original RGB Image:


<img width="748" height="429" alt="image" src="https://github.com/user-attachments/assets/25c52f40-201a-4c42-9b3c-184402f0eef5" />

## HSV Image:


<img width="781" height="435" alt="image" src="https://github.com/user-attachments/assets/53c86317-1baf-443b-aac3-f9d331fef37c" />


## Grayscale Image:


<img width="723" height="409" alt="image" src="https://github.com/user-attachments/assets/37ec5fad-5895-41c3-ad7e-e469a220e0da" />


## YCrCb Image:

<img width="477" height="237" alt="image" src="https://github.com/user-attachments/assets/0d889764-e45b-4f2e-acf9-3821d9487a5a" />



## HSV to RGB Image:

<img width="368" height="209" alt="image" src="https://github.com/user-attachments/assets/967767b2-7588-49eb-b454-d147a5c19938" />



## Image with 300x300 White Block:

<img width="903" height="504" alt="image" src="https://github.com/user-attachments/assets/aa753f2c-8145-43ba-a67d-fd00bb8c3033" />



## Resized Image(Half Size):


<img width="855" height="613" alt="image" src="https://github.com/user-attachments/assets/d38ff43e-9952-49c3-afd0-08751b0f3ae7" />



## Cropped Region of Interest (ROI):


<img width="763" height="619" alt="image" src="https://github.com/user-attachments/assets/95969230-eb80-40e2-ba00-adf6434715b5" />



## Flipped Horizontally:


<img width="903" height="475" alt="image" src="https://github.com/user-attachments/assets/5f426262-fdcf-4a26-be27-d7515ac08325" />




## Flipped Vertically:

<img width="862" height="490" alt="image" src="https://github.com/user-attachments/assets/55078a9e-f388-42fc-9e79-bd63a93c9ff9" />




## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.
