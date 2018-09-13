# Singuliarity Container for Hail
* This project is supported by Research University Network grant "Precision Cancer Medicine" *
* Integrative Database & Analytics Platform for Cancer Precision Medicine *
* Maintain by: Bhoom Suktitipat, MD, PhD *
-------------------------------------------------------------------------------------------------

## Overview
Singularity Container for Hail (hail.is)
1. built from Spark2.2.2, Anaconda3, and Hail v.0.2
2. Please download these three required component before start building. Save the files to `hailSrc` directory.
```
../hailSrc/Anaconda3-5.2.0-Linux-x86_64.sh
../hailSrc/spark-2.2.2-bin-hadoop2.7.tgz
../hailSrc/Hail-devel-1f253167d53c-Spark-2.2.0.zip
```

3. clone the github to `pwd` using `git clone https://github.com/hypotheses/singhail.git`

Your folder structure might look like these
```
`pwd`
   |--hailSrc: {source code for the required programs}
   |
   |--hailsing: {Singularity singhail git}
```

4. Build the image image: In vagrant virtual machine build an image using this command ```sudo singularity build --writable singhail.img Singularity```

## Working with the `singhail` container
_NOTE_: `--login` option is required to load conda
*To use the container*: and bind the data directory from host `/turtle/RUN/vcf` to the container
```
singularity shell -B /turtle/RUN/vcf singhail.img --login
```

## To modify the image start the container with `--writable` option
```
sudo singularity shell --writable singhail.img --login
```

