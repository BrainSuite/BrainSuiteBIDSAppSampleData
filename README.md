# Example Dataset for the BrainSuite BIDS App #
This repository contains a small subset of the publicly available [Amsterdam Open MRI Collection's Population Imaging of Psychology 2 (AOMIC-PIOP2)](https://openneuro.org/datasets/ds002790/versions/2.0.0) dataset available from [OpenNeuro](openneuro.org) and other files required to perform a demonstration of BrainSuite BIDS App's participant-level processing and the BrainSuite Dashboard quality control functionality. These files in this repository include:

* AOMIC-PIOP2 : a BIDS-compliant study directory containing data from 4 participants; modalities include T1-weighted (T1-w), diffusion MRI (dMRI), resting-state functional MRI (rs-fMRI).
* aomic-piop2_preprocspec.json : a JSON file containing parameters for T1-weighted, dMRI, and rs-fMRI processing.
* README.md : instructions for running participant-level workflows.

This demo will enable you to display intermediate outputs using the BrainSuite Dashboard. An example of the output produced from this dataset is available at [https://brainsuite.github.io/DashboardDemo/](https://brainsuite.github.io/DashboardDemo/).

## Prerequisites ##
1. Install Docker from [here](https://docs.docker.com/install/). Docker is available on all platforms. For Linux, you may have to perform additional [post-installation steps](https://docs.docker.com/engine/install/linux-postinstall/).

## Instructions on Running Participant-Level Processing ##
1. Download this repository by cloning this repository or by downloading [the zip file](https://github.com/BrainSuite/BrainSuiteBIDSAppSampleData/archive/refs/heads/master.zip). To clone, run:
```
git clone https://github.com/BrainSuite/BrainSuiteBIDSAppSampleData.git
```

2. Pull BrainSuite BIDS App image:
```
docker pull bids/brainsuite:stable
```

3. Run structural, difussion, and function MRI processing for all subjects:
```
docker run -ti --rm \
      -v /path/to/BrainSuiteBIDSAppSampleData/:/BrainSuiteBIDSAppSampleData \
      -v /path/to/output/:/output \
      bids/brainsuite:stable \
      /BrainSuiteBIDSAppSampleData/AOMIC-PIOP2 /output participant \
      --preprocspec /BrainSuiteBIDSAppSampleData/aomic-piop2_preprocspec.json
``` 
where

* `/path/to/BrainSuiteBIDSAppSampleData` is the path of the location of this repository that you have downloaded onto your computer
* `/path/to/output` is the path to where you would like the output files to be written

4. Run BrainSuite Dashboard:
```
docker run -ti --rm \
      -p 8080:8080 \
      -v /path/to/BrainSuiteBIDSAppSampleData/:/BrainSuiteBIDSAppSampleData \
      -v /path/to/output/:/output \
      bids/brainsuite:stable \
      /BrainSuiteBIDSAppSampleData/AOMIC-PIOP2 /output participant \
      --stages DASHBOARD --localWebserver
```
To view the BrainSuite Dashboard for real-time updates on your processing, open a web browser and navigate to: http://127.0.0.1:8080.

## Instructions for Running Only One Subject ##
1. If you haven't already done so, please complete steps 1 and 2 in the instructions above.

2. Run structural, difussion, and function MRI processing for just one subject (e.g. 0015):
```
docker run -ti --rm \
      -v /path/to/BrainSuiteBIDSAppSampleData/:/BrainSuiteBIDSAppSampleData \
      -v /path/to/output/:/output \
      bids/brainsuite:stable \
      /BrainSuiteBIDSAppSampleData/AOMIC-PIOP2 /output participant \ 
      --participant_label 0015 \
      --preprocspec /BrainSuiteBIDSAppSampleData/aomic-piop2_preprocspec.json 
``` 
If you would like to run a different subject, you can replace `0015` with a different subject ID.

3. Run BrainSuite Dashboard:
```
docker run -ti --rm \
      -p 8080:8080 \
      -v /path/to/BrainSuiteBIDSAppSampleData/:/BrainSuiteBIDSAppSampleData \
      -v /path/to/output/:/output \
      bids/brainsuite:stable \
      /BrainSuiteBIDSAppSampleData/AOMIC-PIOP2 /output participant \
      --stages DASHBOARD --localWebserver \
      --participant_label 0015 
```
To view the BrainSuite Dashboard for real-time updates on your processing, open a web browser and navigate to: http://127.0.0.1:8080.

## Support ##
Additional details and instructions can be found on [the BrainSuite website BIDS page](https://brainsuite.org/BIDS/paper). For any questions or comments, please submit them as issues on our [BrainSuite BIDS App GitHub repository](https://github.com/bids-apps/BrainSuite).

## Source Code ##
The source code for BrainSuite BIDS App is publicly available and is located at [https://github.com/bids-apps/BrainSuite/](https://github.com/bids-apps/BrainSuite/). Additionally, our BrainSuite BIDS App images are also available on [DockerHub](https://hub.docker.com/r/bids/brainsuite/).

## Citation for AOMIC-PIOP2 Dataset ##
Citation for the complete AOMIC-PIOP2 dataset:
* Snoek, L., van der Miesen, M. M., Van Der Leij, A., Beemsterboer, T., Eigenhuis, A., & Steven Scholte, H. (2020). AOMIC-PIOP2. OpenNeuro. [Dataset] doi: 10.18112/openneuro.ds002790.v2.0.0

Citation for the dataset paper:
* Snoek, L., van der Miesen, M. M., Beemsterboer, T., Van Der Leij, A., Eigenhuis, A., & Steven Scholte, H. (2021). The Amsterdam Open MRI Collection, a set of multimodal MRI datasets for individual difference analyses. Scientific data, 8(1), 85.

## AOMIC-PIOP2 Dataset License ##
[![CC0](https://img.shields.io/badge/License-CC0-green.svg) ](https://creativecommons.org/publicdomain/zero/1.0/) These data are freely available under a CC0 license.
