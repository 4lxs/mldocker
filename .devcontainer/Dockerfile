FROM ubuntu

ENV DEBIAN_FRONTEND=noninteractive
ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ENV PATH /opt/conda/bin:$PATH

RUN apt-get update --fix-missing && \
    apt-get install -y \
      wget \
      bzip2 \
      ca-certificates \
      curl \
      git \
      graphviz \
    && rm -rf /var/lib/apt/lists/*

RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh && \
    ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
    echo "conda activate base" >> ~/.bashrc

RUN conda install pytorch torchvision cpuonly -c pytorch

RUN apt-get update --fix-missing && \
    apt-get install -y \
      gcc \
      g++

RUN conda install \
    numpy \
    ipykernel \
    pandas \
    matplotlib \
    python-graphviz \
    -c defaults -c conda-forge