# Sign-Language-Alpha

An early prototype that recognizes three hand signs (labels A, B and L) from a webcam.

## Pipeline
1. "collect data.py": captures webcam images for 3 classes, 100 images each, into ./data (press q to start each class).
2. "create data.py": runs MediaPipe Hands on each image, builds features from the 21 hand landmarks, and saves data.pickle.
3. "train data.py": trains a scikit-learn RandomForestClassifier on an 80/20 stratified split, prints the test accuracy and saves model.p.
4. "main.py": live webcam demo. Draws the hand landmarks and a box with the predicted letter.

## Dependencies (from the imports)
opencv-python, mediapipe, numpy, scikit-learn

The scripts use mp.solutions. In a test with the Face-Blur script, mediapipe 0.10.14 provided it and mediapipe 1.2.3 did not (AttributeError). Use 0.10.14 if you hit that error.

## Notes
- Only three labels: 0 = A, 1 = B, 2 = L.
- "create data.py" reads the images from the "data" folder next to the script, and "main.py" loads model.p from the script folder. Earlier versions used a hardcoded Windows path.
- Tested with synthetic data only: "train data.py" ran and saved a model with scikit-learn 1.7.2 and numpy 1.26.4 (Python 3.10). The camera scripts were not tested, and the repo's own data.pickle and model.p were not loaded.
- data.pickle and model.p are Python pickles. Only load pickles you trust.
- No accuracy result is recorded in the repo. This is a prototype, not a full sign language system.
