

## *GeoPatch* is a package for generating patches from remote sensing data [![PyPI version](https://img.shields.io/badge/PyPi%20Package-1.1.0-green)](https://pypi.org/project/GeoPatch/) [![Downloads](https://pepy.tech/badge/geopatch)](https://pepy.tech/project/geopatch) [![Github](https://img.shields.io/badge/Github-GeoPatch-blueviolet)](https://github.com/Hejarshahabi/GeoPatch) [![LinkedIn](https://img.shields.io/badge/LinkedIn-Hejar%20Shahabi-blue)](https://www.linkedin.com/in/hejarshahabi/) [![Twitter URL](https://img.shields.io/twitter/url?color=blue&label=Hejar%20Shahabi&style=social&url=https%3A%2F%2Ftwitter.com%2Fhejarshahabi)](https://twitter.com/hejarshahabi)

  
  

*GeoPatch* enables the user to read, process and export GeoTIFFs in various patch sizes. The module is built on the Rasterio library but is much more convenient when it comes to reading and exporting GeoTIFs patches for training deep learning models.

Using this package user is able to feed satellite imagery and corresponding label data and exports patches in both Geotiff and Numpy array.

  

Any feedback from users is welcome and you can write to me at hejarshahabi@gmail.com in case of any contribution or suggestion.

  

<img  src="https://github.com/Hejarshahabi/GeoPatch/blob/main/Patch_logo.jpg?raw=true?raw=true"  width="880"  height="325">

  

## Quick tutorial on how to use GeoPatch .

  

### 1- Installation :

```bash

pip install GeoPatch

```

### 2- Calling the Package:

```bash

from GeoPatch import TrainPatch

```

### 3- Feeding data

for image and label variables both string and array

can be passed and the function automatically process and read dataset.

```bash

patch= TrainPatch( image="xxx/image.tif", label="xxx/label.tif",

patch_size=128, stride=64, channel_first=True)

```

### 4- Input data specifications

Using follwoing code the the shape and size of data can be displayed

```bash

patch.data_dimension()

```

### 5- Patch details

To display the number of orginal image patches can be generated based on given patch size and stride values.

```bash

patch.patch_info()

```

### 6- Saving image patch as a Geotiff file

To save image patches as Geotiff files in the current working directory with the given "folder_name", and if "only_label" pass as True, only patches will be save that has labelled data.

```bash

patch.save_Geotif(folder_name="tif", only_label=True)

```

### 7- Saving image patch as a Numpy array

Using this function image patches will be generated in Numpy format with data augmentation options. V_flip and H_flip are used to vertically and horizontally flip patches, respectively, and rotation is used to rotate patches in 90,180 and 270 degree.

```bash

patch.save_numpy(folder_name="npy", only_label=False, return_stacked=False, save_stack=False, V_flip=True, H_flip=True, Rotation=True)

#to return numpy patches as a stack file:

patch, label= patch.save_numpy(folder_name="npy", only_label=False, return_stacked=True, save_stack=False, V_flip=True, H_flip=True, Rotation=True)

```

### 8- Patch visualization

Patches with their corresponding labels can be displayed using this line of code.

In "*folder_name*" the exact name of the folder that patches are located in should be passed.

```bash

patch.visualize(folder_name='npy',patches_to_show=2,band_num=1,

fig_size=(10, 20),dpi=96)

```
### 9- Generating Prediction Patch 

Using the following line of codes prediction patches can be generated.


```bash

from GeoPatch import PredictionPatch
Prediction= PredictionPatch( image="xxx/test_image.tif", patch_size=128, stride=128, channel_first=True)
Prediction.data_dimension()
Prediction.patch_info()
```
### 10- Saving Prediction Patches

Using the following line of code prediction patches can be saved as GeoTIF format in the provided folder. 


```bash
Prediction.save_Geotif('folder_name')
