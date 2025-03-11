# Sturdy-Octo-Disco-Adding-Sunglasses-for-a-Cool-New-Look

Sturdy Octo Disco is a fun project that adds sunglasses to photos using image processing.

Welcome to Sturdy Octo Disco, a fun and creative project designed to overlay sunglasses on individual passport photos! ThisA repository demonstrates how to use image processing techniques to create a playful transformation, making ordinary photos look extraordinary. Whether you're a beginner exploring computer vision or just looking for a quirky project to try, this is for you!

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

### Name: PRAJAN P
### Reg.No: 212223240121

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
faceImage = cv2.imread('PHOTO1.jpg')
plt.imshow(faceImage[:,:,::-1]);plt.title("Face")
faceImage.shape
faceImage.shape
glassPNG = cv2.imread('ss1.png',-1)
plt.imshow(glassPNG[:,:,::-1]);plt.title("glassPNG")
glassPNG = cv2.resize(glassPNG,(290,140))
print("image Dimension ={}".format(glassPNG.shape))
glassBGR = glassPNG[:,:,0:3]
glassMask1 = glassPNG[:,:,3]
plt.figure(figsize=[10,10])
plt.subplot(121);plt.imshow(glassBGR[:,:,::-1]);plt.title('Sunglass Color channels');
plt.subplot(121);plt.imshow(glassMask1,cmap='gray');plt.title('Sunglass Alpha channel');
faceWithGlassesNaive = faceImage.copy()
faceWithGlassesNaive[240:380, 270:560] =glassBGR

plt.imshow(faceWithGlassesNaive[...,::-1])
glassMask = cv2.merge((glassMask1,glassMask1,glassMask1))
glassMask = np.uint8(glassMask/255)
faceWithGlassesArithmetic = faceImage.copy()
eyeROI= faceWithGlassesArithmetic[240:380, 270:560]
maskedEye = cv2.multiply(eyeROI,(1-  glassMask ))
maskedGlass = cv2.multiply(glassBGR,glassMask)
eyeRoiFinal = cv2.add(maskedEye, maskedGlass)
plt.figure(figsize=[10,10])
plt.subplot(131);plt.imshow(maskedEye[...,::-1]);plt.title("Masked Eye Region")
plt.subplot(132);plt.imshow(maskedGlass[...,::-1]);plt.title("Masked Sunglass Region")
plt.subplot(133);plt.imshow(eyeRoiFinal[...,::-1]);plt.title("Augmented Eye and Sunglass")
faceWithGlassesArithmetic[240:380, 270:560]=eyeRoiFinal
plt.figure(figsize=[20,20]);
plt.subplot(121);plt.imshow(faceImage[:,:,::-1]); plt.title("Original Image");
plt.subplot(122);plt.imshow(faceWithGlassesArithmetic[:,:,::-1]);plt.title("With Sunglasses");

```
## Output:
### 1.Original image:
![Screenshot 2025-03-11 144532](https://github.com/user-attachments/assets/cf228b01-12a2-4c6e-b148-afe7932057ac)

### 2.Glass:
![Screenshot 2025-03-11 144526](https://github.com/user-attachments/assets/00584d11-70d8-43db-805f-50553d19fc4b)

### 3.Glass color channel:
![Screenshot 2025-03-11 144515](https://github.com/user-attachments/assets/997f960a-6a18-4e07-bc2f-118ed16fbd8f)

### 4.Face With Glass:
![Screenshot 2025-03-11 144453](https://github.com/user-attachments/assets/d4eda22c-65f6-495c-bae7-af0a1c25764e)

### 5.Eye and glass region:
![Screenshot 2025-03-11 144402](https://github.com/user-attachments/assets/92c78c66-ed2e-4eae-8d00-a9fb03c764c4)

### 6.Final image with glass:
![Screenshot 2025-03-11 144438](https://github.com/user-attachments/assets/30c9afc5-e05d-45c6-8aff-9047510d283b)

## Result:
Thus, the creative project designed to overlay sunglasses on individual passport size photo has been successfully executed.














