# Sign-Language-Alpha

An early prototype that recognizes three hand signs (labels A, B and L) from a webcam.

## Pipeline
1. "collect data.py": captures webcam images for 3 classes, 100 images each, into ./data (press q to start each class).
2. "create data.py": runs MediaPipe Hands on each image, builds features from the 21 hand landmarks, and saves data.pickle.
3. "train data.py": trains a scikit-learn RandomForestClassifier on an 80/20 stratified split, prints the test accuracy and saves model.p.
4. "main.py": live webcam demo. Draws the hand landmarks and a box with the predicted letter.

## Dependencies (from the imports)
opencv-python, mediapipe, numpy, scikit-learn

## Notes
- Only three labels: 0 = A, 1 = B, 2 = L.
- "create data.py" and "main.py" contain hardcoded Windows paths (C:\Users\hamed\Desktop\data), while "collect data.py" writes to ./data. Change the paths to match before running elsewhere.
- data.pickle and model.p are Python pickles. Only load pickles you trust.
- No accuracy result is recorded in the repo. This is a prototype, not a full sign language system.
