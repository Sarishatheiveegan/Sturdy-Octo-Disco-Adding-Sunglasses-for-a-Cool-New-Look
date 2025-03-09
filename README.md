## NAME:MARINO SARISHA T
## REG NO:212223240084
# Sturdy-Octo-Disco-Adding-Sunglasses-for-a-Cool-New-Look

Sturdy Octo Disco is a fun project that adds sunglasses to photos using image processing.

Welcome to Sturdy Octo Disco, a fun and creative project designed to overlay sunglasses on individual passport photos! This repository demonstrates how to use image processing techniques to create a playful transformation, making ordinary photos look extraordinary. Whether you're a beginner exploring computer vision or just looking for a quirky project to try, this is for you!

## Features:
- Detects the face in an image.
- Places a stylish sunglass overlay perfectly on the face.
- Works seamlessly with individual passport-size photos.
- Customizable for different sunglasses styles or photo types.

## Technologies Used:
- Python
- OpenCV for image processing
- Numpy for array manipulations

## How to Use:
1. Clone this repository.
2. Add your passport-sized photo to the `images` folder.
3. Run the script to see your "cool" transformation!

## Applications:
- Learning basic image processing techniques.
- Adding flair to your photos for fun.
- Practicing computer vision workflows.

## Program:
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
img=cv2.imread("blue background photo.jpg")
plt.imshow(img[:,:,::-1]);plt.title("Face");plt.axis("off")
```
![Screenshot 2025-03-09 143858](https://github.com/user-attachments/assets/7472c078-6bb9-4d5b-984f-8cae7e0f3c83)

```
img.shape
```
![Screenshot 2025-03-09 144235](https://github.com/user-attachments/assets/aaf96ecc-2181-465e-8d21-8c4db2033bf4)

```
glass = cv2.imread("sunglass.png",-1)
plt.imshow(glass[:,:,::-1]);plt.title("glass");plt.axis("on")
```
![Screenshot 2025-03-09 144243](https://github.com/user-attachments/assets/9e130e8c-545e-4b7e-ae24-156d6eff44de)

```
glass = cv2.resize(glass,(190,50))
print("image Dimension ={}".format(glass.shape))
```
![Screenshot 2025-03-09 144251](https://github.com/user-attachments/assets/3beb2061-c28f-40b1-b763-7ae42aff7770)

```
glassBGR = glass[:,:,0:3]
glassMask = glass[:,:,3]
plt.figure(figsize=[15,15])
plt.subplot(121);plt.imshow(glassBGR[:,:,::-1]);plt.title('Sunglass Color channels');
plt.subplot(122);plt.imshow(glassMask,cmap='gray');plt.title('Sunglass Alpha channel');
```
![Screenshot 2025-03-09 144302](https://github.com/user-attachments/assets/ed20a0bd-7d51-4552-be25-6caefcda64ba)

```
faceWithGlass = img.copy()
faceWithGlass[160:210,115:305]=glassBGR
plt.imshow(faceWithGlass[...,::-1])
```
![Screenshot 2025-03-09 144327](https://github.com/user-attachments/assets/102404dd-a481-4a2b-ac54-0501c5b3f630)

```
glassM = cv2.merge((glassMask,glassMask,glassMask))
glassM = np.uint8(glassM/255)
faceWithGlassesArithmetic = img.copy()
eyeROI= faceWithGlassesArithmetic[160:210,115:305]
maskedEye = cv2.multiply(eyeROI,(1-  glassM ))
maskedGlass = cv2.multiply(glassBGR,glassM)
eyeRoiFinal = cv2.add(maskedEye, maskedGlass)
plt.figure(figsize=[20,20])
plt.subplot(131);plt.imshow(maskedEye[...,::-1]);plt.title("Masked Eye Region")
plt.subplot(132);plt.imshow(maskedGlass[...,::-1]);plt.title("Masked Sunglass Region")
plt.subplot(133);plt.imshow(eyeRoiFinal[...,::-1]);plt.title("Augmented Eye and Sunglass")
```
![Screenshot 2025-03-09 144342](https://github.com/user-attachments/assets/4f0bc711-c2a4-48d4-8aa4-0afa4b91ec35)

```
faceWithGlassesArithmetic[160:210,115:305]=eyeRoiFinal
plt.figure(figsize=[20,20]);
plt.subplot(121);plt.imshow(img[:,:,::-1]); plt.title("Original Image");
plt.subplot(122);plt.imshow(faceWithGlassesArithmetic[:,:,::-1]);plt.title("With Sunglasses");
```
![Screenshot 2025-03-09 144402](https://github.com/user-attachments/assets/b4ec131a-cd08-4c9d-bdc9-bfa6c1e9a428)

## Output:
![Screenshot 2025-03-09 144402](https://github.com/user-attachments/assets/9e5f3323-09b4-4cfe-bff2-e2d8ee39700e)

## RESULT:
 Thus Adding Sunglasses to Your Passport Photo Using OpenCV is done successfully.


