# Pytorch GANs notebooks and tips for beginners. 

Repository with different GAN architectures notebooks, they have been build to being used interactively by making modifications directly to the notebooks, this repository is intended for people starting in generative networks and are seeking for a direct overview of the architectures, some other repositories I strongly recommend to continue in this path are listed in the last section.

### Requirements
As expected, Generative Networks are demanding in terms of hardware, it is almost mandatory to have a CUDA capable GPU with a compute capability of 3.5 (check it [here](https://developer.nvidia.com/cuda-gpus)), this minimum compute capability depends entirely on the Pytorch version you are using, a more detailed (but not complete) list can be found [here](https://discuss.pytorch.org/t/gpu-compute-capability-support-for-each-pytorch-version/62434/7). If you don't own a GPU that can meet these minimum requirements I suggest you to use [Google Colab](https://colab.research.google.com), they provide time-limited but free GPUs where you can run the notebooks in this repository, however, a disadvantage about using it is the data, if you are willing to train a model with your own data, you will require to upload it to a Google Drive account and link it in Colab, I will go through this later.

On the other hand, all the notebooks may run on Pytorch versions not older than 1.5 due to CUDA performance, I also provide a `requirements.txt` and `environment.yml` files.

## Beginner tips
### For Colab users only.
All the points below are already implemented in the noteboks but here I provide a brief explanation.
- *Data Upload.* As I mentioned above, one disadvantage about Google Colab is data accessibility since you need to upload all your data to a Google Drive account, due to the size of most of the image datasets you will need to deal with, it is recommended to upload them as zip files in a folder that will contain all your datasets, please ensure you don't need to change anything in the dataset before uploading it, it will be difficult to make changes later, once donde you have to link your Colab notebook with your Drive account by running the following:
```python
from google.colab import drive
drive.mount('/content/drive', force_remount=True)
```
   After this you need to unzip your files into a `/tmp` folder by running the follwoing:
 
```python
import zipfile
import os

zip_ref = zipfile.ZipFile('/content/drive/MyDrive/datasets/No_concat_full.zip', 'r') #Opens the zip file in read mode
zip_ref.extractall('/tmp') #Extracts the files into the /tmp folder
zip_ref.close()
```
Now, all your data can be accessed by pointing to the `/tmp` folder, keep in mind that the full path to this folder is NOT `/content/My Drive/tmp`, it is only `/tmp`.

- *Free GPU.* Keep in mind that the free GPU available in Colab can be used for 13 hours of continuous training and you need to check the page every hour if you don't want to be automatically disconected from the server, besides this, it is important to know that the GPUs provided can vary from session to session, depending on availability, this sometimes will lead to change som training parameters if the GPU VRAM is limited, a complete list of available GPUs and other important details can be found [here](https://blog.paperspace.com/alternative-to-google-colab-pro/). In spite of requiring more than 13 hours to train, Colab is still a good alternative to see how several models works but don't expect state-of-the-art results.

### For local machine users only.
Undoubtedly, running GANs on a local machine has a different perspective, it will bring tons of advantages mainly related to data managements since you will be a able to edit your files on the run and without depending on any internet connection, however, you might also face some problems specially related to the Drivers and CUDA versions, I also posted an article about this that you can check [here](), it will hopefully fix all your issues.


## 1. DCGAN (Deep Convolutional GAN)

