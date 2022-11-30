# AW-SW-Team3-TermProject
semester project of Advanced Topics In Software (Gachon univ.)
**In this repository only datas & codes exist for easy-use what we actually focus on.**

## Overview

kapture-localization is a **toolbox** in which you will find implementations for various localization related algorithms.
It strongly relies on the https://github.com/naver/kapture format for data representation and manipulation.

The localization algorithms include and what we did is:

 - **mapping**,
 - **localization**

It works on Ubuntu, Windows, and MacOS.

## Structure

The directories are organised as follow:

```
├── kapture_localization/  # package (library)
├── pipeline/              # main programs executing all steps of the localization pipelines
├── samples/               # some sample data
├── tests/                 # unit tests
└── tools/                 # sub programs involved in the pipeline
```


The __kapture-localization__ toolbox is available as:

 - Python *package* (`kapture_localization/`),
 - Python *executable scripts* (`pipeline/` & `tools/`).

There are 3 pipelines available:

 1. mapping,
 2. localization, and
 3. image retrieval benchmark (global sfm, local sfm, pose approximation).

## Installation

It can be installed using pip, but using docker is better to understand file structure.
After installing python (>=3.6) and COLMAP (>=3.6), this toolbox can be installed with:

We provide a docker image that can be run like this:
```
docker run --runtime=nvidia # benefit from the GPU acceleration \
    -it --rm # automatically remove the container when it exits \
    --volume <my_data>:<my_data> # give access to your data on your machine \
    kapture/kapture-localization
```
You can also build your own docker image as follow:
```
git clone https://github.com/naver/kapture-localization.git
cd kapture-localization
docker build --tag kapture/kapture-localization .
```
## Tutorial

### PrepareData
For easy use of this tutorial, we provide precomputed local and global features (virtual_gallery_tutorial):

- local features: __R2D2__ (500 kps per image), stored in `./local_features/r2d2_500/{descriptors,keypoints}`.
- global features: __AP-GeM__, stored in `./global_features/AP-GeM-LM18/global_features/`.

#### extract own __local features__
Custom local features in the __kapture__ format can be used as well. For example, __R2D2__ features can be extracted using
https://github.com/naver/r2d2/blob/master/extract_kapture.py provided
in the https://github.com/naver/r2d2#feature-extraction-with-kapture-datasets.
See https://github.com/naver/kapture#local-features for more local feature types that are directly supported in kapture.

If R2D2 doesn't work for project, use **D2_Net**

#### extract own __global features__
Custom global features in the __kapture__ format can be used as well.
For example, __AP-GeM__ global features can be extracted using https://github.com/naver/deep-image-retrieval/blob/master/dirtorch/extract_kapture.py provided
in the https://github.com/naver/deep-image-retrieval#feature-extraction-with-kapture-datasets
See https://github.com/naver/kapture#global-features for more global feature types that are directly supported in kapture.


### Structure-based mapping and localization
In this tutorial, we us a pipeline to explain how to localize query images within a map.
Before explaining how to use the code, we provide more details about the algorithmic workflow and the methods used.

For custom pipeline, we explain how to build a map using structure-from-motion leveraging known camera poses, we show how to localize query images within this map, and we show how to evaluate the precision of the obtained localization against the ground truth.

#### 1.  Mapping
Steps are below

1. Extraction of local descriptors and keypoints (e.g. R2D2, D2-Net, SIFT) of training images

2. Extraction of global features (e.g. AP-GeM, NetVLAD, DenseVLAD) of training images

3. Computation of training image pairs using global features

4. Local descriptor matching and geometric verification of the image pairs

5. Point triangulation with COLMAP (point triangulator)

#### 2.  Localization
Steps are below

1. Extraction of local and global features (same local and global feature types as used for mapping) of query images

2. Retrieval of similar images from the training images (training-query image pairs)

3. Local descriptor matching and geometric verification

4. Camera pose estimation with COLMAP (image registrator)

## License
Software license is detailed in the **LICENSE** file.

## References
If you use this work for your research, please cite the respective paper(s):

### Structure-based localization or kapture format
```
@misc{kapture2020,
      title={Robust Image Retrieval-based Visual Localization using Kapture},
      author={Martin Humenberger and Yohann Cabon and Nicolas Guerin and Julien Morat and Jérôme Revaud and Philippe Rerole and Noé Pion and Cesar de Souza and Vincent Leroy and Gabriela Csurka},
      year={2020},
      eprint={2007.13867},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}
```

### Image retrieval benchmark
```
@inproceedings{benchmarking_ir3DV2020,
      title={Benchmarking Image Retrieval for Visual Localization},
      author={Noé Pion, Martin Humenberger, Gabriela Csurka, Yohann Cabon, Torsten Sattler},
      year={2020},
      booktitle={International Conference on 3D Vision}
}

@article{humenberger2022investigating,
  title={Investigating the Role of Image Retrieval for Visual Localization},
  author={Humenberger, Martin and Cabon, Yohann and Pion, No{\'e} and Weinzaepfel, Philippe and Lee, Donghwan and Gu{\'e}rin, Nicolas and Sattler, Torsten and Csurka, Gabriela},
  journal={International Journal of Computer Vision},
  year={2022},
  publisher={Springer}
}
``` 
