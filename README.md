# Optical Character Recognition

A Python-based Optical Character Recognition (OCR) project for handwritten English alphabet characters. The repository includes:

- a CNN model trained on the A-Z handwritten dataset
- image preprocessing helpers
- a character segmentation + prediction pipeline
- a simple desktop GUI built with `customtkinter`

## Features

- Trains a convolutional neural network on 28x28 grayscale character images
- Preprocesses input images by converting to grayscale, resizing, and inverting when needed
- Segments characters from an image using Tesseract bounding boxes
- Predicts individual characters and combines them into words/sentences
- Provides a GUI for selecting an image and viewing the OCR result

## Project Structure

- `Optical Character Recognigion/first.ipynb` - model training notebook
- `Optical Character Recognigion/firstuse.py` - preprocessing and single-character prediction helpers
- `Optical Character Recognigion/ocr6.py` - character segmentation and OCR pipeline
- `Optical Character Recognigion/complete.py` - GUI application

## Requirements

Install the Python packages used by the project:

```bash
pip install pillow numpy pandas tensorflow scikit-learn matplotlib pytesseract customtkinter
```

You also need to install **Tesseract OCR** on your system and make sure the executable path is available.

## Tesseract Configuration

In `ocr6.py`, the Tesseract path is currently set to:

```python
pytesseract.pytesseract.tesseract_cmd = r'C:\Program Files\Tesseract-OCR\tesseract'
```

Update this path if Tesseract is installed elsewhere on your machine.

## How It Works

### 1. Train the model

Open `Optical Character Recognigion/first.ipynb` and run the cells to:

- load the handwritten A-Z dataset
- normalize and reshape the images
- train a CNN classifier
- save the model as `first_model.pkl`

### 2. Predict a single character

`firstuse.py` contains helper functions to:

- detect whether an image should be inverted
- resize and normalize the image
- load the saved model and predict the character label

### 3. Run OCR on a full image

`ocr6.py`:

- converts the image to grayscale
- applies blur and thresholding
- segments characters using `pytesseract.image_to_boxes`
- predicts each cropped character with the model
- reconstructs the sentence using spacing heuristics

### 4. Use the GUI

Run `complete.py` to launch the desktop app:

```bash
python complete.py
```

Then:

- click the image area to select a file
- press **Predict** to run OCR
- press **Cancel** to clear the image and result

## Notes

- The model expects 28x28 grayscale inputs.
- The current implementation is designed for A-Z character recognition.
- Prediction quality depends on image clarity, character spacing, and Tesseract segmentation accuracy.

## Example Output

If the input image contains a clear handwritten character, the model returns a predicted letter such as `C`.

## Future Improvements

- Support digits and lowercase letters
- Improve segmentation for connected handwriting
- Save the trained model in a more portable format
- Add error handling for missing model files and missing Tesseract installation

## License

No license file was included in the repository.
