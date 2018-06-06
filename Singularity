Bootstrap: shub
From: singularityhub/ubuntu

%runscript
    exec echo "The runscript is the containers default runtime command!"
    exec . $HOME/anaconda3/bin/activate && conda activate hail

%files
   ../hailSrc/Anaconda3-5.2.0-Linux-x86_64.sh /opt
   ../hailSrc/spark-2.2.0-bin-hadoop2.7.tgz /opt
   ../hailSrc/Hail-devel-1f253167d53c-Spark-2.2.0.zip /opt

%environment
    SPARK_HOME=/opt/spark-2.2.0-bin-hadoop2.7
    HAIL_HOME=/opt/hail
    PATH="$HAIL_HOME/bin:$PATH"

%labels
   AUTHOR bhoom.suk@mahidol.edu

%post
    SPARK_HOME=/opt/spark-2.2.0-bin-hadoop2.7
    HAIL_HOME=/opt/hail
    PATH="$HAIL_HOME/bin:$PATH"
    export SPARK_HOME HAIL_HOME PATH
    
    sed -i.bak 's/us\.archive/th\.archive/g' /etc/apt/sources.list
    apt-get update && apt-get -y install wget git bzip2 software-properties-common unzip

    # installation folder for hail
    ## mkdir -p /opt/hail/
    cd /opt
    # wget https://storage.googleapis.com/hail-common/distributions/devel/Hail-devel-1f253167d53c-Spark-2.2.0.zip
    unzip Hail-devel-1f253167d53c-Spark-2.2.0.zip

    # spark 2.2.0
    # wget https://www.apache.org/dyn/closer.lua/spark/spark-2.2.0/spark-2.2.0-bin-hadoop2.7.tgz
    tar xvzf spark-2.2.0-bin-hadoop2.7.tgz

    # Anaconda3
    # wget https://repo.anaconda.com/archive/Anaconda3-5.2.0-Linux-x86_64.sh -O /opt/hail/anaconda.sh
    #wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /opt/miniconda.sh
    bash /opt/Anaconda3-5.2.0-Linux-x86_64.sh -b -p $HOME/anaconda3

    #https://www.linuxuprising.com/2018/04/install-oracle-java-10-in-ubuntu-or.html
    add-apt-repository ppa:webupd8team/java
    apt update
    echo debconf shared/accepted-oracle-license-v1-1 select true | debconf-set-selections
    echo debconf shared/accepted-oracle-license-v1-1 seen true | debconf-set-selections
    apt -y install oracle-java8-installer

    ## activate conda
    . $HOME/anaconda3/bin/activate
    conda env create -n hail -f $HAIL_HOME/python/hail/environment.yml
    . activate hail

    ## Clean-up
    mkdir /data
    echo "The post section is where you can install, and configure your container."
    rm /opt/Anaconda3-5.2.0-Linux-x86_64.sh /opt/spark-2.2.0-bin-hadoop2.7.tgz /opt/Hail-devel-1f253167d53c-Spark-2.2.0.zip
    apt-get autoremove && apt-get clean

