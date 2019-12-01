# FingersCount
Real Time Fingers Count - CNN

Key Requirements: Python 3+, Keras 2+, TensorFlow 1+, OpenCV 2+

## Files
* **app.py** - run python3 app.py, once model_6cat.h5 is generated.
* **trainModel.ipynb** - Generate model_6cat.h5 from here
* **images.tgz** - Extract to generate data


## Demo
Demo of digit counting with and without binary mask visible.

![](https://i.imgur.com/nbpeRgg.gif)



## Usage
Simply run `app.py` and hold your fingers up in the highlighted region of interest (ROI).
The model performs best when provided a plain background without many features.

### Hotkeys
* The ROI on the screen can be moved using the `i`, `j`, `k`, and `l` keys.
* Show the binary mask being applied to the ROI by toggling the `b` key.
* Quit the application by pressing the `q` key.

### Taking Data
To collect data, you must first select the target class 0 through 5 by hitting the corresponding key on your keyboard.
Once you have selected your target class, you can start/stop collecting data by toggling the `s` key. When collecting
data the outline of the ROI will turn green and turn red again when collection is stopped.

# Feature Input

Images are captured within a ROI from the webcam using OpenCV. To help simplify the inputs that are analyzed by the CNN, a binary mask is applied to highlight the hands edges. The binary mask is defined by grayscaling and blurring the image and then applying thresholding as shown below:

```
img = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
img = cv2.GaussianBlur(img, (7,7), 3)
img = cv2.adaptiveThreshold(img, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C, cv2.THRESH_BINARY_INV, 11, 2)
ret, new = cv2.threshold(img, 25, 255, cv2.THRESH_BINARY_INV + cv2.THRESH_OTSU)
```

A dataset is collected within the application by holding up 0 to 5 digits at different positions and orientations within the application's ROI. A training set of ~1500 images and validation set of ~600 images for each case is used for training the CNN.
