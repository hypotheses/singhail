# Singuliarity Container for Hail
## Overview
Singularity Container for Hail (hail.is)
- built from Spark2.2.0, Anaconda3, and Hail v.0.2
- Please download these three required component before start building. Save the files to `hailSrc` directory.
```
../hailSrc/Anaconda3-5.2.0-Linux-x86_64.sh
../hailSrc/spark-2.2.0-bin-hadoop2.7.tgz
../hailSrc/Hail-devel-1f253167d53c-Spark-2.2.0.zip
```
- clone the github to `pwd` using `git clone https://github.com/hypotheses/singhail.git`

Your folder structure might look like these
`pwd`
   |--hailSrc: {source code for the required programs}
   |
   |--hailsing: {Singularity singhail git}


## Build Image
In vagrant virtual machine build an image using this command
```sudo singularity build --writable singhail.img Singularity```

## Working with the `singhail` container
*To use the container*
_NOTE_: `--login` option is required to load conda
```
sudo singularity shell --writable singhail.img --login
```

