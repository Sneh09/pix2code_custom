# PIX2CODE for Custom Dataset
### Generate code from a GUI Image.

## 1. Setup

### Prerequisites: 

* Python 2
* pip

### Create Env and Install Dependencies:

```
git clone https://github.com/Sneh09/pix2code_custom.git
```
```
cd pix2code_custom
```
```
conda env create -f pix2code_env.yml
```

### Split Data to train and Eval

Split the Dataset to train and evaluation set. This command will split the data in two folders training set and eval set. By Default 85-15. 

```
cd ../model
# run build_datasets.py <data path>
python2 ./build_datasets.py ../data/D1
```

### Train the Model:

```
mkdir bin
cd model
# run train.py <input path> <output path> <pretrained weights (optional)>
python2 ./train.py ../data/D1/training_set ../bin
```

### Test the Model:

```
mkdir code
cd model
# run generate.py <trained weights path> <trained model name> <input image> <output path>
python2 ./generate.py ../bin pix2code ../testimage.png ../code
```
