# Example Dataset for the BrainSuite BIDS App #
This repository contains a small subset of the publicly available [Amsterdam Open MRI Collection's Population Imaging of Psychology 2 (AOMIC-PIOP2)](https://openneuro.org/datasets/ds002790/versions/2.0.0) dataset available from [OpenNeuro](openneuro.org) and other files required to perform a demonstration of BrainSuite BIDS App's participant-level processing and the BrainSuite Dashboard quality control functionality. These files in this repository include:

* AOMIC-PIOP2 : a BIDS-compliant study directory containing data from 4 participants; modalities include T1-weighted (T1-w), diffusion MRI (dMRI), resting-state functional MRI (rs-fMRI).
* aomic-piop2_preprocspec.json : a JSON file containing parameters for T1-weighted, dMRI, and rs-fMRI processing.
* README.md : brief information regarding this repository.

This demo will guide you through the steps necessary to process the T1-w, dMRI, and rs-fMRI data from the 4 participants and display intermediate outputs using the BrainSuite Dashboard. An example of the output produced from this dataset is available at [https://brainsuite.github.io/DashboardDemo/](https://brainsuite.github.io/DashboardDemo/).

## Instructions for running participant-level workflows and BrainSuite Dashboard ##
Complete instructions for this demo walk-through are available on our website: [https://brainsuite.org/BIDS/walkthrough.html]. 

## Support ##
Additional details regarding the BrainSuite BIDS App and its usage can be found on [the BrainSuite website BIDS page](https://brainsuite.org/BIDS/). For any questions or comments, please submit them as issues on our [BrainSuite BIDS App GitHub repository](https://github.com/bids-apps/BrainSuite).

## Source Code ##
The source code for BrainSuite BIDS App is publicly available and is located at [https://github.com/bids-apps/BrainSuite/](https://github.com/bids-apps/BrainSuite/). Additionally, our BrainSuite BIDS App images are available as a Docker image on [DockerHub](https://hub.docker.com/r/bids/brainsuite/) and as a Singularity image on our [website](https://brainsuite.org/BIDS/sif).

## Citation for AOMIC-PIOP2 Dataset ##
Citation for the complete AOMIC-PIOP2 dataset:
* Snoek, L., van der Miesen, M. M., Van Der Leij, A., Beemsterboer, T., Eigenhuis, A., & Steven Scholte, H. (2020). AOMIC-PIOP2. OpenNeuro. [Dataset] doi: 10.18112/openneuro.ds002790.v2.0.0

Citation for the dataset paper:
* Snoek, L., van der Miesen, M. M., Beemsterboer, T., Van Der Leij, A., Eigenhuis, A., & Steven Scholte, H. (2021). The Amsterdam Open MRI Collection, a set of multimodal MRI datasets for individual difference analyses. Scientific data, 8(1), 85.

## AOMIC-PIOP2 Dataset License ##
[![CC0](https://img.shields.io/badge/License-CC0-green.svg) ](https://creativecommons.org/publicdomain/zero/1.0/) These data are freely available under a CC0 license.
