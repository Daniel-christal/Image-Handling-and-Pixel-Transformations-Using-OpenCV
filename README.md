Image-Handling-and-Pixel-Transformations-Using-OpenCV
AIM:
Write a Python program using OpenCV that performs the following tasks:

Read and Display an Image.
Adjust the brightness of an image.
Modify the image contrast.
Generate a third image using bitwise operations.
Software Required:
Anaconda - Python 3.7
Jupyter Notebook (for interactive development and execution)
Algorithm:
Step 1:
Load an image from your local directory and display it.

Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.
Display the original, brighter, and darker images.

Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).
Display the original, lower contrast, and higher contrast images.

Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

Program Developed By:
Name: Daniel c

Register Number: 212223240023

Ex. No. 01
1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
img = cv2.imread('Eagle_in_Flight.jpg', cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
2. Print the image width, height & Channel.
print("Eagle Image Shape (H, W, C):", img.shape)
3. Display the image using matplotlib imshow().
img_gray = cv2.cvtColor(img_rgb, cv2.COLOR_RGB2GRAY)
plt.imshow(img_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("off")
plt.show()
4. Save the image as a PNG file using OpenCV imwrite().
cv2.imwrite('Eagle.png', img)
5. Read the saved image above as a color image using cv2.cvtColor().
img_png = cv2.imread('Eagle.png')
img_png_rgb = cv2.cvtColor(img_png, cv2.COLOR_BGR2RGB)
6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
plt.imshow(img_png_rgb)
plt.title("Eagle PNG (Color)")
plt.axis("off")
plt.show()
print("PNG Image Shape (H, W, C):", img_png.shape)
7. Crop the image to extract any specific (Eagle alone) object from the image.
crop = img_rgb[0:450, 200:550]   
plt.imshow(crop)
plt.title("Cropped Eagle")
plt.axis("off")
plt.show()
print("Crop Shape:", crop.shape)
8. Resize the image up by a factor of 2x.
res = cv2.resize(crop, (crop.shape[1]*2, crop.shape[0]*2))
9. Flip the cropped/resized image horizontally.
flip = cv2.flip(res, 1)
plt.imshow(flip)
plt.title("Flipped Horizontally")
plt.axis("off")
plt.show()
10. Read in the image ('Apollo-11-launch.jpg').
img = cv2.imread('Apollo-11-launch.jpg', cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
print("Apollo Image Shape:", img_rgb.shape)
11. Add the following text to the dark area at the bottom of the image (centered on the image):
text_img = img_rgb.copy()
cv2.putText(text_img, "Apollo 11 Saturn V Launch, July 16, 1969",
            (200, 700), cv2.FONT_HERSHEY_SIMPLEX, 
            1, (255,255,255), 2, cv2.LINE_AA)

plt.imshow(text_img)
plt.title("Text Added")
plt.axis("off")
plt.show()
12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
cv2.rectangle(text_img, (400,100), (800,650), (255,0,255), 3)
13. Display the final annotated image.
plt.imshow(text_img)
plt.title("Annotated Apollo Launch")
plt.axis("off")
plt.show()
14. Read the image ('Boy.jpg').
img = cv2.imread('boy.jpg', cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
15. Adjust the brightness of the image.
m = np.ones(img_rgb.shape, dtype="uint8") * 50
16. Create brighter and darker images.
img_brighter = cv2.add(img_rgb, m)
img_darker = cv2.subtract(img_rgb, m)
17. Display the images (Original Image, Darker Image, Brighter Image).
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img_rgb), plt.title("Original"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_brighter), plt.title("Brighter"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_darker), plt.title("Darker"), plt.axis("off")
plt.show()
18. Modify the image contrast.
matrix1 = np.ones(img_rgb.shape, dtype="float32") * 1.1
matrix2 = np.ones(img_rgb.shape, dtype="float32") * 1.2
img_higher1 = cv2.multiply(img.astype("float32"), matrix1).clip(0,255).astype("uint8")
img_higher2 = cv2.multiply(img.astype("float32"), matrix2).clip(0,255).astype("uint8")
19. Display the images (Original, Lower Contrast, Higher Contrast).
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img_rgb), plt.title("Original"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_higher1), plt.title("Higher Contrast (1.1x)"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_higher2), plt.title("Higher Contrast (1.2x)"), plt.axis("off")
plt.show()
20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
b, g, r = cv2.split(img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(b, cmap='gray'), plt.title("Blue"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(g, cmap='gray'), plt.title("Green"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(r, cmap='gray'), plt.title("Red"), plt.axis("off")
plt.show()
21. Merged the R, G, B , displays along with the original image
merged_rgb = cv2.merge([r, g, b])
plt.imshow(merged_rgb)
plt.title("Merged RGB")
plt.axis("off")
plt.show()
22. Split the image into the H, S, V components & Display the channels.
hsv_img = cv2.cvtColor(img_rgb, cv2.COLOR_RGB2HSV)
h, s, v = cv2.split(hsv_img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(h, cmap='gray'), plt.title("Hue"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(s, cmap='gray'), plt.title("Saturation"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(v, cmap='gray'), plt.title("Value"), plt.axis("off")
plt.show()
23. Merged the H, S, V, displays along with original image.
merged_hsv = cv2.cvtColor(cv2.merge([h, s, v]), cv2.COLOR_HSV2RGB)
combined = np.concatenate((img_rgb, merged_hsv), axis=1)
plt.figure(figsize=(10,5))
plt.imshow(combined)
plt.title("Original & Merged HSV")
plt.axis("off")
plt.show()
Output:
i) Read and Display an Image.

1.Read 'Eagle_in_Flight.jpg' as grayscalw and displayed:

image
2.Saved image as PNG and displayed:

image
3.Cropped image:

image
4.Resized and flipped Horizontally:

image
5.Read 'Apollo-11-launch.jpg' and Displayed:

image
6.Displayed the final annotated image:

image
ii) Adjust Image Brightness.

1.Created brighter and darker images and displayed:

image
iii) Modify Image Contrast.

Modified the contrast using scaling factors 1.1 and 1.2:
image
iv) Generate Third Image Using Bitwise Operations.

1.Splitted 'Boy.jpg' into B, G, R components and displayed:

image
2.Merged the R, G, B channels and displayed:

download
3.Splitted the image into H, S, V components and displayed:

download
4.Merged the H, S, V channels and displayed:

image
Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

About
Explores image processing techniques using OpenCV, a powerful computer vision library in Python. Key objectives include reading and displaying images, adjusting brightness and contrast, and applying bitwise operations. By mastering pixel-level transformations, users gain essential skills for handling and enhancing digital images efficiently.

Resources
 Readme
 Activity
Stars
 0 stars
Watchers
 0 watching
Forks
 1 fork
Report repository
Releases
No releases published
Packages
No packages published
Languages
Jupyter Notebook
100.0%
