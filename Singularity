Bootstrap: shub
From: singularityhub/ubuntu

%runscript
    exec echo "The runscript is the containers default runtime command!"

%files
   /vagrant/hailSrc/Anaconda3-5.2.0-Linux-x86_64.sh /opt
   /vagrant/hailSrc/spark-2.2.0-bin-hadoop2.7.tgz /opt
   /vagrant/hailSrc/Hail-devel-1f253167d53c-Spark-2.2.0.zip /opt

%environment
    SPARK_HOME=/opt/hail/spark-2.2.0-bin-hadoop2.7
    HAIL_HOME=/opt/hail/hail
    PATH="$HOME/anaconda3/bin:$PATH"

%labels
   AUTHOR bhoom.suk@mahidol.edu

%post
    sed -i.bak 's/us\.archive/th\.archive/g' /etc/apt/sources.list
    apt-get update && apt-get -y install wget git bzip2 software-properties-common unzip
    #https://www.linuxuprising.com/2018/04/install-oracle-java-10-in-ubuntu-or.html
    add-apt-repository ppa:linuxuprising/java
    apt update
    echo debconf shared/accepted-oracle-license-v1-1 select true | debconf-set-selections
    echo debconf shared/accepted-oracle-license-v1-1 seen true | debconf-set-selections
    apt -y install oracle-java10-installer

    # python 3 http://docs.python-guide.org/en/latest/starting/install3/linux/
    ##add-apt-repository ppa:deadsnakes/ppa
    ##apt-get update
    ##apt-get install python3.6

    # installation folder for hail
    ## mkdir -p /opt/hail/
    cd /opt
    ## wget https://storage.googleapis.com/hail-common/distributions/devel/Hail-devel-1f253167d53c-Spark-2.2.0.zip
    unzip Hail-devel-1f253167d53c-Spark-2.2.0.zip

    # Anaconda3
    # miniconda https://conda.io/docs/user-guide/install/macos.html#install-macos-silent
    ## wget https://repo.continuum.io/miniconda/Miniconda3-3.7.0-Linux-x86_64.sh -O ~/miniconda.sh
    ## wget https://repo.anaconda.com/archive/Anaconda3-5.2.0-Linux-x86_64.sh -O /opt/hail/anaconda.sh
    bash /opt/Anaconda3-5.2.0-Linux-x86_64.sh -b -p $HOME/anaconda3
    source $HOME/anaconda3/bin/activate
    conda env create -n hail -f $HAIL_HOME/python/hail/environment.yml
    source activate hail

    # spark 2.2.0
    ## wget https://www.apache.org/dyn/closer.lua/spark/spark-2.2.0/spark-2.2.0-bin-hadoop2.7.tgz
    tar xvzf /opt/spark-2.2.0-bin-hadoop2.7.tgz

    ## probably done?
    mkdir /data
    echo "The post section is where you can install, and configure your container."
