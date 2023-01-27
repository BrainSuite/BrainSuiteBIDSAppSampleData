# Example Dataset for BrainSuite BIDS App Demonstration #
This repository contains a small subset of the publicly available [Amsterdam Open MRI Collection's Population Imaging of Psychology 2 (AOMIC-PIOP2)](https://openneuro.org/datasets/ds002790/versions/2.0.0) dataset on [OpenNeuro](openneuro.org) and other necessary files required to perform BrainSuite BIDS App's participant-level processing:

* AOMIC-PIOP2 : BIDS-compliant study directory containing data from 4 subjects; modalities include T1-weighted (T1-w), diffusion (dMRI), resting-state functional MRI (rs-fMRI)
* aomic-piop2_preprocspec.json : JSON file containing parameters for T1-w, dMRI, and rs-fMRI processing
* README.md : Instructions on running participant-level workflows

## Pre-requisites ##
1. Install Docker from [here](https://docs.docker.com/install/). Docker is available on all platforms. For Linux, you may have to perform additional [post-installation steps](https://docs.docker.com/engine/install/linux-postinstall/).

## Instructions on Running Participant-Level Processing ##
1. Download this repository by cloning this repository or downloading the zip file. To clone, run:
```
git clone https://yeunkim@bitbucket.org/brainsuite/aomicsubset.git
```

2. Pull BrainSuite BIDS App image:
```
docker pull bids/brainsuite:stable
```

3. Run structural, difussion, and function MRI processing for all subjects:
```
docker run -ti --rm \
      -v /path/to/AOMICsubset/:/AOMICsubset \
	  -v /path/to/output/:/output
      bids/brainsuite:stable \
      /AOMICsubset/AOMIC-PIOP2 /output participant \
	  --preprocspec /AOMICsubset/aomic-piop2_preprocspec.json
``` 
where

* `/path/to/AOMICsubset` is the path of the location of this repository that you have downloaded onto your computer
* `/path/to/output` is the path to where you would like the output files to be written

4. Run BrainSuite Dashboard:
```
docker run -ti --rm \
      -p 8080:8080
      -v /path/to/output/:/output
      bids/brainsuite:stable \
      /AOMICsubset/AOMIC-PIOP2 /output participant \
	  --stages DASHBOARD --localWebserver
```

## Instructions on Running Only One Subject ##
1. If you haven't already done so, please complete steps 1 and 2 in the instructions above

2.  Run structural, difussion, and function MRI processing for just one subject (e.g. 0015):
```
docker run -ti --rm \
      -v /path/to/AOMICsubset/:/AOMICsubset \
	  -v /path/to/output/:/output
      bids/brainsuite:stable \
      /AOMICsubset/AOMIC-PIOP2 /output participant \ 
	  --participant_label 0015 
	  --preprocspec /AOMICsubset/aomic-piop2_preprocspec.json 
``` 
If you would like to run a different subject, you can replace `0015` with a a different subject ID.

3. Run BrainSuite Dashboard:
```
docker run -ti --rm \
      -p 8080:8080
      -v /path/to/output/:/output
      bids/brainsuite:stable \
      /AOMICsubset/AOMIC-PIOP2 /output participant \
	  --stages DASHBOARD --localWebserver \
	  --participant_label 0015 
```

## Support ##
Additional details and instructions can be found on our website (rtd). For any questions or comments, please submit them as issues on our [BrainSuite BIDS App GitHub repository](https://github.com/bids-apps/BrainSuite).

## Source Code ##
The source code for BrainSuite BIDS App is publicly available and is located at [https://github.com/bids-apps/BrainSuite](https://github.com/bids-apps/BrainSuite). Additionally, our BrainSuite BIDS App images are also available on [DockerHub](https://hub.docker.com/r/bids/brainsuite/).
