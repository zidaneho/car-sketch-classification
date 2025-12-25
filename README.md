# Car Sketch Classification

This project uses Transfer Learning with **MobileNetV2** to classify hand-drawn sketches from the Google Quick, Draw! dataset into two categories: **Car** and **Not Car**.

## Prerequisites

Ensure you have Python installed and set up a virtual environment. Install the necessary dependencies using the provided requirements file:

```bash
pip install -r requirements.txt

```

*The core dependencies include `torch`, `torchvision`, `numpy`, and `scikit-learn`.*

## Step 1: Download the Dataset

The dataset consists of  grayscale bitmap files stored in `.npy` format. Because these files are large, they are not included in the repository and must be downloaded from Google Cloud Storage.

1. Open `download_data.ipynb`.
2. Run the cells to initialize the category lists for "Car" (e.g., ambulance, bus, truck) and "Not Car" (e.g., apple, tree, cloud).
3. The script will create a `/data` directory and download the required `.npy` files automatically.

## Step 2: Train and Generate the Model

Once the data is downloaded, use the main training notebook to build the model.

1. Open `dataset.ipynb`.


2. 
**Data Preprocessing**: The notebook loads the raw numpy arrays, concatenates them into binary classes, and converts the grayscale images into 3-channel pseudo-RGB tensors resized to .


3. 
**Transfer Learning**: The model uses a pre-trained **MobileNetV2** backbone with frozen weights. The classifier head is replaced with a custom structure:


* 
**Linear Layer** (1280 to 128) 


* 
**ReLU Activation** 


* 
**Dropout** (0.2) 


* 
**Final Linear Layer** (1 output) with **Sigmoid Activation** 




4. **Training**: Run the training loop. By default, it runs for 3 epochs using the Adam optimizer and Binary Cross Entropy loss.


5. 
**Saving**: After reaching an expected accuracy of approximately **93.97%**, the model weights are saved to `model_data/car_sketch_weights.pth`.



## Model Performance

The current implementation achieves:

* 
**Training Loss**: ~0.18 after 3 epochs.


* 
**Test Accuracy**: ~93.97%.