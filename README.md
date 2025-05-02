Brain Tumor Segmentation using U-Net

This project applies a deep learning model (U-Net) to segment brain tumors from grayscale MRI images. It's built with Python, TensorFlow, OpenCV, and Streamlit for visualization. The project includes both training code and a web-based user interface for easy testing and demonstration.

Project Structure:

brain_tumor_segmentation/

app.py → Streamlit app for UI-based tumor detection

main.py → Main script to load data, train the model, and visualize predictions

unet_model.py → Contains the U-Net model architecture

tumor_model.h5 → Pre-trained U-Net model (saved after training)

requirements.txt → All required Python packages

README.md → This file

.streamlit/

config.toml → Theme settings for Streamlit UI

data/ (see data set)

images/ → Input MRI images (grayscale)

masks/ → Corresponding tumor masks (same names as images)

Dataset:

Download the brain MRI dataset with tumor masks from this link:
https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset

Place the images inside data/images/

Place the masks inside data/masks/

Ensure that filenames match, for example: 1.jpg with 1.jpg

How the Project Works:

main.py:

Loads all images and masks

Resizes them to 256x256 and normalizes

Trains a U-Net model on this data

Saves the best model to tumor_model.h5

Displays side-by-side: Original MRI, Ground Truth, Predicted Mask

Use this script only once to train your model.

unet_model.py:

Defines the U-Net architecture

Includes an encoder, bottleneck, decoder, and output layer

Used in both main.py (training) and app.py (inference)

app.py:

A Streamlit-based web interface

Lets you upload an MRI image

Uses the saved model to predict tumor regions

Shows side-by-side output: MRI vs. Predicted Mask

config.toml:

Customizes the Streamlit app’s look and feel (dark theme, blue highlights)

How to Set Up and Run:

Clone or copy this repository

Set up the environment

python -m venv venv

venv\Scripts\activate (use Command Prompt, not PowerShell)

pip install -r requirements.txt

Or install dependencies manually:

pip install streamlit tensorflow opencv-python numpy pillow

Run the Streamlit app

streamlit run app.py

Then upload an MRI image (grayscale PNG or JPG) and view prediction instantly in your browser.

What Happens When You Run Each File:

main.py: Trains the model, saves tumor_model.h5, and shows prediction results

app.py: Opens a browser-based app to upload images and get tumor predictions

unet_model.py: Contains U-Net model used by both main.py and app.py

tumor_model.h5: Trained model file used for inference

config.toml: Optional theme configuration for Streamlit

data/images/: Input MRI scans

data/masks/: Ground truth tumor masks for each scan

Additional Notes:

The model output is a soft mask (values from 0 to 1). You can threshold it to get a binary mask.

U-Net is ideal for segmentation in medical imaging.

The accuracy depends heavily on the dataset quality.

Questions?

Contact me at sathyabharathi7711@gmail.com
