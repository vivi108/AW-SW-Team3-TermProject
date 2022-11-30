# AW-SW-Team3-TermProject
semester project of Advanced Topics In Software (Gachon univ.)

## Overview

kapture-localization is a **toolbox** in which you will find implementations for various localization related algorithms.
It strongly relies on the https://github.com/naver/kapture[kapture] format for data representation and manipulation.

The localization algorithms include and what we did is:

 . **mapping**,
 . **localization**

It works on Ubuntu, Windows, and MacOS.

## Structure

The directories are organised as follow:

----
├── kapture_localization/  # package (library)
├── pipeline/              # main programs executing all steps of the localization pipelines
├── samples/               # some sample data
├── tests/                 # unit tests
└── tools/                 # sub programs involved in the pipeline
----


The __kapture-localization__ toolbox is available as:

 - Python *package* (`kapture_localization/`),
 - Python *executable scripts* (`pipeline/` & `tools/`).

There are 3 pipelines available:

 . mapping,
 . localization, and
 . image retrieval benchmark (global sfm, local sfm, pose approximation).

## Installation

It can be installed using pip, but using docker is better to understand file structure.
After installing python (>=3.6) and COLMAP (>=3.6), this toolbox can be installed with:

## Tutorial

.

== License
Software license is detailed in the link:LICENSE[LICENSE] file.

== References
If you use this work for your research, please cite the respective paper(s):

.Structure-based localization or kapture format
----
@misc{kapture2020,
      title={Robust Image Retrieval-based Visual Localization using Kapture},
      author={Martin Humenberger and Yohann Cabon and Nicolas Guerin and Julien Morat and Jérôme Revaud and Philippe Rerole and Noé Pion and Cesar de Souza and Vincent Leroy and Gabriela Csurka},
      year={2020},
      eprint={2007.13867},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}
----

.Image retrieval benchmark
----
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
----
