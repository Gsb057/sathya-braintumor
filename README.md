> **Project scope note:** This was built in a single night, largely with ChatGPT generating the implementation while I directed the overall structure and tested the result. I can explain what the project does at a high level (U-Net segmenting tumor regions from MRI scans), but I did not work through the architecture or training details deeply enough to defend the implementation choices in detail today. Kept here as an honest record of exploring a new domain quickly, not as a demonstration of independent deep learning engineering.

---

# Brain Tumor Segmentation using U-Net

This project applies a deep learning model (U-Net) to segment brain tumors from grayscale MRI images. It's built with Python, TensorFlow, OpenCV, and Streamlit for visualization. The project includes both training code and a web-based user interface for easy testing and demonstration.

## Project Structure
```
brain_tumor_segmentation/
├── app.py            # Streamlit app for UI-based tumor detection
├── main.py            # Main script to load data, train the model, and visualize predictions
├── unet_model.py       # Contains the U-Net model architecture
├── tumor_model.h5      # Pre-trained U-Net model (saved after training)
├── requirements.txt    # All required Python packages
├── README.md           # This file
├── .streamlit/
│   └── config.toml     # Theme settings for Streamlit UI
└── data/                # (see dataset)
    ├── images/          # Input MRI images (grayscale)
    └── masks/           # Corresponding tumor masks (same names as images)
```

## Dataset

Download the brain MRI dataset with tumor masks from [Kaggle](https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset).
- Place images inside `data/images/`
- Place masks inside `data/masks/`
- Ensure filenames match, e.g. `1.jpg` with `1.jpg`

## How the Project Works

**`main.py`**
- Loads all images and masks
- Resizes to 256x256 and normalizes
- Trains a U-Net model on this data
- Saves the best model to `tumor_model.h5`
- Displays side-by-side: original MRI, ground truth, predicted mask
- Use this script only once, to train the model

**`unet_model.py`**
- Defines the U-Net architecture: encoder, bottleneck, decoder, output layer
- Used in both `main.py` (training) and `app.py` (inference)

**`app.py`**
- Streamlit-based web interface
- Lets you upload an MRI image
- Uses the saved model to predict tumor regions
- Shows side-by-side output: MRI vs. predicted mask

**`config.toml`**
- Customizes the Streamlit app's look and feel (dark theme, blue highlights)

## How to Set Up and Run

1. Clone or copy this repository
2. Set up the environment
   ```
   python -m venv venv
   venv\Scripts\activate    # Command Prompt, not PowerShell
   pip install -r requirements.txt
   ```
   Or install dependencies manually:
   ```
   pip install streamlit tensorflow opencv-python numpy pillow
   ```
3. Run the Streamlit app
   ```
   streamlit run app.py
   ```
4. Upload an MRI image (grayscale PNG or JPG) and view the prediction instantly in your browser.

## Notes

- Model output is a soft mask (values from 0 to 1); threshold it to get a binary mask.
- U-Net is well suited for segmentation tasks in medical imaging.
- Accuracy depends heavily on dataset quality.

## Questions?

Contact me at sathyabharathi7711@gmail.com
