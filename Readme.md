# DOC: Deep OCclusion from a single image

By Peng Wang

### Introduction

we propose a deep convolutional network architecture, called DOC,  which detects object boundaries and estimates the occlusion relationships (i.e. which side of the boundary is foreground and which is background).
 Specifically, we first represent occlusion relations by a binary edge indicator, to indicate the object boundary, and an occlusion orientation variable whose direction specifies the occlusion relationships by a left-hand rule.
To train and test DOC, we construct an instance occlusion boundary dataset using PASCAL VOC images, which we call the PASCAL instance occlusion dataset (PIOD). It contains 10,000 images.

### Misc.

This code has been tested on Linux (Ubuntu 14.04), Matlab 2014b using K40/Titian X GPUs.
The caffe code is built based on [HED](https://github.com/s9xie/hed),  with extended hdf5 data reader and orientation loss metioned in our paper.

### PASCAL Instance Occlusion Dataset (PIOD)

You may download the dataset from [here](https://drive.google.com/file/d/0B7DaWBKShuMBSkZ6Mm5RVmg5ck0/view?usp=sharing). Please follow the readme and use the toolkit inside for observing the occlusion labelling.
The visualization code is developed based on the work of [Hoiem et.al iccv07](http://dhoiem.cs.illinois.edu/)

For getting the original images, please download from the PASCAL official website.

### Demo

We release a demo code how to generate occlusion edge maps for a single scale image after the provided the orientation map and edge map.

Please first download the dataset and put it under $root/data, then run $root/demo_occ.m

For extracting the two maps (edge map and orientation map):

For PIOD, we provide pre-trained orientation and edge models for [PIOD](https://drive.google.com/open?id=0B7DaWBKShuMBN0drTzRRMlpoTmc).
Please use the way you like (either python or matlab) to forward the pre-computed model. With the image transform as HED.

To download the full pre-computed orientation maps and edge maps for PIOD, you may down load from [here](https://drive.google.com/file/d/0B7DaWBKShuMBdWV3NzVyd0pGZjA/view?usp=sharing) and unzip it under the output folder to view all the occlusion edges.

For BSDS, the results and models are sitll under cleaning and will be released later. (But you may use our released code to retrain, tune in order to get the results)

### Training

Please follow the augmentation in HED for edge and orientation training using the sigmoid cross entropy loss and orientation loss. (Notice you may need to re-compute orientation for augmentation.)


### Evaluation

To be released.

### Discussion

In the future work, we will try to combining such low level cues with high level object instance segmentation
knowledge and long range context to achieve better and reasonable results.

### Citation

If you find DOC useful in your research, please consider citing:

    @inproceedings{wang2016doc,
        title={DOC: Deep OCclusion estimation from a single image},
        author={Wang, Peng and Yuille, Alan},
        booktitle={ECCV},
        year={2016}
    }