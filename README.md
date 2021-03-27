## HuBMAP: Kaggle Competition 
### Hacking the Kidney Identify glomeruli in human kidney tissue images

[![HuBMAP Kaggle Competition](https://www.vectorlogo.zone/logos/kaggle/kaggle-ar21.svg)](https://www.kaggle.com/c/hubmap-kidney-segmentation)

## Data Description
The HuBMAP data used in this hackathon includes 11 fresh frozen and 9 Formalin Fixed Paraffin Embedded (FFPE) PAS kidney images. Glomeruli FTU annotations exist for all 20 tissue samples; some of these will be shared for training, and others will be used to judge submissions.

There are over 600,000 glomeruli in each human kidney (Nyengaard, 1992). Normal glomeruli typically range from 100-350μm in diameter with a roughly spherical shape (Kannan, 2019).

![glomeruli](https://www.googleapis.com/download/storage/v1/b/kaggle-forum-message-attachments/o/inbox%2F416539%2F0e447c4fe795b097d136e7139be76073%2Fannotation_issue.png?generation=1605622260492931&alt=media)

Teams are invited to develop segmentation algorithms that identify glomeruli in the PAS stained microscopy data. They are welcome to use other external data and/or pre-trained machine learning models in support of FTU segmentation. All data and all code used must be released under Attribution 4.0 International (CC BY 4.0).

## The Dataset
The dataset is comprised of very large (>500MB - 5GB) TIFF files. The training set has 8, and the public test set has 5. The private test set is larger than the public test set.

The training set includes annotations in both RLE-encoded and unencoded (JSON) forms. The annotations denote segmentations of glomeruli.

Both the training and public test sets also include anatomical structure segmentations. They are intended to help you identify the various parts of the tissue.

## File structure
The JSON files are structured as follows, with each feature having:
- A type (Feature) and object type id (PathAnnotationObject). Note that these fields are the same between all files and do not offer signal.
- A geometry containing a Polygon with coordinates for the feature's enclosing volume.
- Additional properties, including the name and color of the feature in the image.
- The IsLocked field is the same across file types (locked for glomerulus, unlocked for anatomical structure) and is not signal-bearing.

Note that the objects themselves do NOT have unique IDs. The expected prediction for a given image is an RLE-encoded mask containing ALL objects in the image. The mask, as mentioned in the Evaluation page, should be binary when encoded - with 0 indicating the lack of a masked pixel, and 1 indicating a masked pixel.

train.csv contains the unique IDs for each image, as well as an RLE-encoded representation of the mask for the objects in the image. See the evaluation tab for details of the RLE encoding scheme.

HuBMAP-20-dataset_information.csv contains additional information (including anonymized patient data) about each image.

### Updates
- (28/03/2021) Explanatory data analysis started. Requirements.txt added, simple notebook started.


#### Requirements
- Linux/macOS/Windows with Python ≥ 3.6
- PyTorch ≥ 1.5 and [torchvision](https://github.com/pytorch/vision/) that matches the PyTorch installation.
  You can install them together at [pytorch.org](https://pytorch.org) to make sure of this
- OpenCV
- tifffile
- Some other libraries, please check requirements.txt

#### Steps
1. Before installing GDal library, it is required to install the following:
```
sudo apt-add-repository ppa:ubuntugis/ubuntugis-unstable
sudo apt-get update
sudo apt-get install libgdal-dev
```
2. Install libs from requirements.txt
```
pip install requirements.txt
```

### License

This project is released under MIT License.