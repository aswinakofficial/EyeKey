# EyeKey

An on-screen keyboard you control with your eyes, using just a webcam. Built in 2023 as a college project to explore hands-free typing.

## How it works

1. **Pick a side**: look left or right and hold your gaze for about half a second to choose that half of the keyboard. A sound confirms the choice.
2. **Wait for the letter**: letters on that half light up one at a time.
3. **Blink to type**: a sustained blink types the highlighted letter, then you're back to picking a side.

Under the hood, dlib's 68-point facial landmark model finds the eyes in each webcam frame with OpenCV:

- **Blinks** are detected from the ratio of each eye's width to its height. A closed eye is much flatter.
- **Gaze direction** comes from comparing how much of the white of the eye is visible on each side of the pupil.

## Stack

Python, OpenCV, dlib, NumPy, pyglet (for the audio cues).

## Run it

```bash
pip install opencv-python dlib numpy pyglet
```

Download dlib's landmark model, [`shape_predictor_68_face_landmarks.dat`](http://dlib.net/files/shape_predictor_68_face_landmarks.dat.bz2), unzip it, and put it next to `main.py`. Then:

```bash
python main.py
```

The script opens camera index `2`. If you only have one webcam, change `cv2.VideoCapture(2)` to `cv2.VideoCapture(0)` in `main.py`.

---

Part of [Aswin AK's projects](https://aswin.xpar.in/projects/).
