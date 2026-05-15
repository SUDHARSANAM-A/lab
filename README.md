1. Load a Color Image Using OpenCV and Display Its Dimensions and Pixel Information

Aim

To load a color image using OpenCV in Python and display its dimensions, shape, datatype, and pixel information.


---

Objective

Read a color image from disk.

Display image properties such as width, height, and channels.

Access and display pixel values.



---

Theory

OpenCV is an open-source computer vision library widely used for image processing and computer vision applications.

A digital color image consists of:

Rows (Height)

Columns (Width)

Channels (RGB/BGR)


In OpenCV:

Images are stored as NumPy arrays.

Default color format is BGR.


Important Functions

Function	Purpose

cv2.imread()	Loads image
cv2.imshow()	Displays image
img.shape	Gives dimensions
img.dtype	Gives datatype
img[x,y]	Access pixel



---

Algorithm

1. Import OpenCV library.


2. Load image using cv2.imread().


3. Display image.


4. Print image dimensions.


5. Access selected pixel values.


6. Wait for key press and close windows.




---

Program

import cv2

img = cv2.imread("sample.jpg")

cv2.imshow("Color Image", img)

print("Image Shape:", img.shape)
print("Height:", img.shape[0])
print("Width:", img.shape[1])
print("Channels:", img.shape[2])

print("Data Type:", img.dtype)

pixel = img[100, 100]
print("Pixel Value at (100,100):", pixel)

cv2.waitKey(0)
cv2.destroyAllWindows()


---

Output

Image window displayed.

Shape example:


Image Shape: (600, 800, 3)
Height: 600
Width: 800
Channels: 3


---

Applications

Medical imaging

Surveillance systems

Satellite image processing

Face recognition



---

Advantages

Easy image handling

Fast execution

Supports multiple formats



---

Result

Thus, the color image was successfully loaded using OpenCV and its dimensions and pixel information were displayed successfully.


---

2. Perform Cropping and Resizing Operations on an Input Image

Aim

To crop and resize an image using OpenCV.


---

Theory

Cropping

Cropping means selecting a specific region from an image.

Resizing

Changing image dimensions.

Functions:

Slicing for cropping

cv2.resize() for resizing



---

Algorithm

1. Load image.


2. Crop selected region.


3. Resize image.


4. Display outputs.




---

Program

import cv2

img = cv2.imread("sample.jpg")

cropped = img[100:400, 150:500]

resized = cv2.resize(img, (400, 300))

cv2.imshow("Original", img)
cv2.imshow("Cropped", cropped)
cv2.imshow("Resized", resized)

cv2.waitKey(0)
cv2.destroyAllWindows()


---

Output

Original image

Cropped image

Resized image



---

Applications

Face extraction

Medical ROI analysis

Zooming operations



---

Result

Thus, cropping and resizing operations were performed successfully.


---

3. Draw Rectangle, Circle, and Text Annotation on an Image

Aim

To draw shapes and text on an image using OpenCV.


---

Theory

Drawing functions:

Function	Purpose

cv2.rectangle()	Draw rectangle
cv2.circle()	Draw circle
cv2.putText()	Add text



---

Program

import cv2

img = cv2.imread("sample.jpg")

cv2.rectangle(img, (50,50), (300,200), (0,255,0), 3)

cv2.circle(img, (400,200), 80, (255,0,0), 4)

cv2.putText(img, "OpenCV Drawing",
            (100,450),
            cv2.FONT_HERSHEY_SIMPLEX,
            1,
            (0,0,255),
            2)

cv2.imshow("Shapes and Text", img)

cv2.waitKey(0)
cv2.destroyAllWindows()


---

Applications

Object marking

Annotation systems

Image labeling



---

Result

Thus, rectangle, circle, and text annotations were drawn successfully.


---

4. Convert RGB Image into Grayscale and HSV Color Spaces

Aim

To convert a color image into grayscale and HSV formats.


---

Theory

Grayscale

Single channel intensity image.

HSV

H → Hue

S → Saturation

V → Value


Conversion functions:

cv2.COLOR_BGR2GRAY

cv2.COLOR_BGR2HSV



---

Program

import cv2

img = cv2.imread("sample.jpg")

gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

cv2.imshow("Original", img)
cv2.imshow("Gray", gray)
cv2.imshow("HSV", hsv)

cv2.waitKey(0)
cv2.destroyAllWindows()


---

Applications

Object detection

Color segmentation

Face recognition



---

Result

Thus, the RGB image was converted into grayscale and HSV successfully.


---

5. Detect Contours from a Binary Image

Aim

To detect contours from a binary image.


---

Theory

Contours are boundaries of objects.

Functions:

cv2.findContours()

cv2.drawContours()



---

Program

import cv2

img = cv2.imread("binary.png", 0)

_, thresh = cv2.threshold(img, 127, 255, cv2.THRESH_BINARY)

contours, hierarchy = cv2.findContours(
    thresh,
    cv2.RETR_TREE,
    cv2.CHAIN_APPROX_SIMPLE
)

output = cv2.cvtColor(img, cv2.COLOR_GRAY2BGR)

cv2.drawContours(output, contours, -1, (0,255,0), 2)

cv2.imshow("Contours", output)

cv2.waitKey(0)
cv2.destroyAllWindows()


---

Applications

Shape detection

Object counting

Industrial inspection



---

Result

Thus, contours were detected successfully.


---

6. Thresholding and Blob Detection

Aim

To apply thresholding and blob detection.


---

Theory

Thresholding

Separates foreground and background.

Blob Detection

Detects connected regions.


---

Program

import cv2

img = cv2.imread("industrial.jpg", 0)

_, thresh = cv2.threshold(img, 120, 255, cv2.THRESH_BINARY)

params = cv2.SimpleBlobDetector_Params()

detector = cv2.SimpleBlobDetector_create(params)

keypoints = detector.detect(thresh)

output = cv2.drawKeypoints(
    img,
    keypoints,
    None,
    (0,0,255),
    cv2.DRAW_MATCHES_FLAGS_DRAW_RICH_KEYPOINTS
)

cv2.imshow("Blobs", output)

cv2.waitKey(0)
cv2.destroyAllWindows()


---

Applications

Defect detection

Industrial automation

Medical analysis



---

Result

Thus, thresholding and blob detection were performed successfully.


---

7. Histogram Equalization and Image Smoothing

Aim

To improve image contrast and reduce noise.


---

Theory

Histogram Equalization

Improves contrast.

Smoothing

Removes noise.

Methods:

Gaussian Blur

Median Blur



---

Program

import cv2

img = cv2.imread("lowcontrast.jpg", 0)

equalized = cv2.equalizeHist(img)

gaussian = cv2.GaussianBlur(equalized, (5,5), 0)

median = cv2.medianBlur(equalized, 5)

cv2.imshow("Original", img)
cv2.imshow("Equalized", equalized)
cv2.imshow("Gaussian", gaussian)
cv2.imshow("Median", median)

cv2.waitKey(0)
cv2.destroyAllWindows()


---

Applications

Medical imaging

Satellite enhancement

Security systems



---

Result

Thus, histogram equalization and smoothing were implemented successfully.


---

8. ORB Feature Extraction and Matching

Aim

To extract ORB features and perform feature matching.


---

Theory

ORB = Oriented FAST and Rotated BRIEF.

Used for:

Image matching

Panorama stitching

Object recognition



---

Program

import cv2

img1 = cv2.imread("img1.jpg", 0)
img2 = cv2.imread("img2.jpg", 0)

orb = cv2.ORB_create()

kp1, des1 = orb.detectAndCompute(img1, None)
kp2, des2 = orb.detectAndCompute(img2, None)

bf = cv2.BFMatcher(cv2.NORM_HAMMING, crossCheck=True)

matches = bf.match(des1, des2)

matches = sorted(matches, key=lambda x:x.distance)

result = cv2.drawMatches(
    img1, kp1,
    img2, kp2,
    matches[:30],
    None,
    flags=2
)

cv2.imshow("ORB Matching", result)

cv2.waitKey(0)
cv2.destroyAllWindows()


---

Applications

Image registration

Robot navigation

Visual SLAM



---

Result

Thus, ORB feature extraction and matching were performed successfully.


---

9. Edge Detection using Sobel and Canny Operators

Aim

To perform edge detection using Sobel and Canny methods.


---

Theory

Sobel

Detects gradients.

Canny

Multi-stage accurate edge detector.


---

Program

import cv2

img = cv2.imread("sample.jpg", 0)

sobelx = cv2.Sobel(img, cv2.CV_64F, 1, 0, ksize=5)

canny = cv2.Canny(img, 100, 200)

cv2.imshow("Original", img)
cv2.imshow("Sobel", sobelx)
cv2.imshow("Canny", canny)

cv2.waitKey(0)
cv2.destroyAllWindows()


---

Comparison

Sobel	Canny

Simple	Advanced
Gradient based	Multi-stage
More noise	Less noise



---

Result

Thus, Sobel and Canny edge detection were implemented successfully.


---

10. GrabCut Based Image Segmentation

Aim

To separate foreground from background using GrabCut.


---

Theory

GrabCut uses graph cuts for segmentation.

Functions:

cv2.grabCut()



---

Program

import cv2
import numpy as np

img = cv2.imread("object.jpg")

mask = np.zeros(img.shape[:2], np.uint8)

bgdModel = np.zeros((1,65), np.float64)
fgdModel = np.zeros((1,65), np.float64)

rect = (50,50,450,290)

cv2.grabCut(
    img,
    mask,
    rect,
    bgdModel,
    fgdModel,
    5,
    cv2.GC_INIT_WITH_RECT
)

mask2 = np.where((mask==2)|(mask==0),0,1).astype('uint8')

result = img * mask2[:,:,np.newaxis]

cv2.imshow("Segmented", result)

cv2.waitKey(0)
cv2.destroyAllWindows()


---

Applications

Background removal

Medical segmentation

AI preprocessing



---

Result

Thus, GrabCut segmentation was implemented successfully.


---

11. Camera Calibration using Circular Grid Pattern

Aim

To calibrate a camera and estimate intrinsic parameters.


---

Theory

Camera calibration removes distortion and estimates:

Focal length

Optical center

Distortion coefficients



---

Program

import cv2
import numpy as np
import glob

objpoints = []
imgpoints = []

pattern_size = (4,11)

objp = np.zeros((44,3), np.float32)
objp[:,:2] = np.mgrid[0:4,0:11].T.reshape(-1,2)

images = glob.glob('calibration/*.jpg')

for fname in images:
    img = cv2.imread(fname)
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

    ret, centers = cv2.findCirclesGrid(gray, pattern_size)

    if ret:
        objpoints.append(objp)
        imgpoints.append(centers)

ret, mtx, dist, rvecs, tvecs = cv2.calibrateCamera(
    objpoints,
    imgpoints,
    gray.shape[::-1],
    None,
    None
)

print("Camera Matrix:\n", mtx)
print("Distortion:\n", dist)


---

Applications

Robotics

AR/VR

3D reconstruction



---

Result

Thus, camera calibration was performed successfully.


---

12. Stereo Vision System for Depth Map

Aim

To generate a depth map using stereo images.


---

Theory

Stereo vision estimates depth from two cameras.


---

Program

import cv2

left = cv2.imread("left.jpg", 0)
right = cv2.imread("right.jpg", 0)

stereo = cv2.StereoBM_create(numDisparities=16, blockSize=15)

depth = stereo.compute(left, right)

cv2.imshow("Depth Map", depth)

cv2.waitKey(0)
cv2.destroyAllWindows()


---

Applications

Self-driving cars

Robotics

3D mapping



---

Result

Thus, stereo depth mapping was implemented successfully.


---

13. Object Tracking using Kalman Filter and CamShift

Aim

To develop an object tracking system using Kalman Filter and CamShift.


---

Theory

Kalman Filter

Predicts object movement.

CamShift

Tracks colored objects dynamically.


---

Program

import cv2
import numpy as np

cap = cv2.VideoCapture(0)

ret, frame = cap.read()

r,h,c,w = 200,100,300,400
track_window = (c,r,w,h)

roi = frame[r:r+h, c:c+w]

hsv_roi = cv2.cvtColor(roi, cv2.COLOR_BGR2HSV)

mask = cv2.inRange(hsv_roi,
                   np.array((0.,60.,32.)),
                   np.array((180.,255.,255.)))

roi_hist = cv2.calcHist([hsv_roi],[0],mask,[180],[0,180])

cv2.normalize(roi_hist,roi_hist,0,255,cv2.NORM_MINMAX)

term_crit = (cv2.TERM_CRITERIA_EPS |
             cv2.TERM_CRITERIA_COUNT,
             10,1)

while True:
    ret, frame = cap.read()

    if ret:
        hsv = cv2.cvtColor(frame, cv2.COLOR_BGR2HSV)

        dst = cv2.calcBackProject([hsv],[0],roi_hist,[0,180],1)

        ret, track_window = cv2.CamShift(
            dst,
            track_window,
            term_crit
        )

        pts = cv2.boxPoints(ret)
        pts = np.int0(pts)

        img2 = cv2.polylines(frame,[pts],True,(0,255,0),2)

        cv2.imshow('Tracking',img2)

        if cv2.waitKey(30) & 0xFF == 27:
            break

cap.release()
cv2.destroyAllWindows()


---

Applications

Surveillance systems

Autonomous vehicles

Human tracking



---

Advantages

Real-time tracking

Predictive estimation

Noise reduction



---

Result

Thus, object tracking using Kalman Filter and CamShift techniques was implemented successfully.
