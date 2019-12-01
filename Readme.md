# FingersCount
Real Time Fingers Count - CNN

Key Requirements: Python 3+, Keras 2+, TensorFlow 1+, OpenCV 2+

## Files
* **app.py** - run python3 app.py, once model_6cat.h5 is generated.
* **trainModel.ipynb** - Generate model_6cat.h5 from here
* **images.tgz** - Extract to generate data


## Demo
Demo of digit counting with and without binary mask visible.

![](https://imgur.com/CbeModa)



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
