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

### Split Data to Train and Eval

Split the Dataset to train and evaluation set. This command will split the data in two folders training set and eval set. By Default 85-15. 

```
cd ../model
# run build_datasets.py <data path>
python2 ./build_datasets.py ../data/D1
```

### Train the Model:

For modifying the model training parameter go to the following path:
model/classes/model/Config.py. In Config.py training parameters such as no of epochs, batch size etc can be modified.

```
mkdir bin
cd model
# run train.py <input path> <output path> <pretrained weights (optional)>
python2 ./train.py ../data/D1/training_set ../bin
```

### Test the Model:

Pretrained weight link for the given data: https://drive.google.com/drive/folders/1LiAYGAzHrDNQQLVsgly6OoFc5MWQrCjw?usp=share_link
Download the complete folder "bin" and copy it in pix2code folder.
```
mkdir code
cd model
# run generate.py <trained weights path> <trained model name> <input image> <output path>
python2 ./generate.py ../bin pix2code ../testimage.png ../code
```
