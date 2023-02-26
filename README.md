# PIX2CODE for Custom Dataset
### Generate code from a GUI Image.

## 1. Setup

### Prerequisites: 

* Python 2
* pip

### Create Environment and Install Dependencies:

```
git clone https://github.com/Sneh09/pix2code_custom.git
```
```
cd pix2code_custom
```
```
conda env create -f pix2code_env.yml
```

### Short Description of Dataset:
The purpose of the given dataset is to generate a code from the images. The given dataset D1 contains a total of 300 png images and their corresponding labels (gui format). 
In the images there are always buttons on the top followed by boxes of various sizes with text and button of different colours in them. Every label contain header and the row details according to the image.

### Model Description:

The architecture is based on models used in image captioning. The model can be divided into three main parts.

* Image Encoder: A CNN for encoding input images of the desired UI.
* Context Encoder: A LSTM network for encoding context of previously generated code.
* Decoder: A LSTM network that takes the output from both of the previous models and generate the next word in the code.

### Split Data to Train and Eval

Split the Dataset to train and evaluation set. This command will split the data in two folders training set and eval set. By Default 85%-15%. 

```
cd ../model
# run build_datasets.py <data path>
python2 ./build_datasets.py ../data/D1
```

### Train the Model:

For modifying the model training parameter go to the following path:
model/classes/model/Config.py. In Config.py training parameters such as no. of epochs, batch size etc can be modified.

```
mkdir bin
cd model
# run train.py <input path> <output path> <pretrained weights (optional)>
python2 ./train.py ../data/D1/training_set ../bin
```

### Test the Model:

Pretrained weight link for the given data: https://drive.google.com/drive/folders/1LiAYGAzHrDNQQLVsgly6OoFc5MWQrCjw?usp=share_link
Download the complete folder "bin" and copy it in pix2code.
```
mkdir code
cd model
# run generate.py <trained weights path> <trained model name> <input image> <output path>
python2 ./generate.py ../bin pix2code ../testimage.png ../code
```

### References:
Paper: https://arxiv.org/abs/1705.07962

Implementation: https://github.com/tonybeltramelli/pix2code
