# singhail
Singularity Container for Hail (hail.is)

## Required Files for Build

Need to get the Anaconda3, Spark, and Hail locally
Save it to `/vagrant/hailSrc` as these will be copied to `/opt` during build
```
/vagrant/hailSrc/Anaconda3-5.2.0-Linux-x86_64.sh
/vagrant/hailSrc/spark-2.2.0-bin-hadoop2.7.tgz
/vagrant/hailSrc/Hail-devel-1f253167d53c-Spark-2.2.0.zip
```

## Build Image
In vagrant virtual machine build an image using this command
```sudo singularity build --writable singhail.img Singularity```
