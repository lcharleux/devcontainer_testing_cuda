FROM continuumio/miniconda3:latest
SHELL ["/bin/bash", "--login", "-c"]
ENV PATH="/root/miniconda3/bin:${PATH}"
ARG PATH="/root/miniconda3/bin:${PATH}"
RUN apt-get update \
    && apt-get install -y wget \
    git \
    ffmpeg \ 
    && rm -rf /var/lib/apt/lists/*
RUN conda create -n myenv python=3.9
RUN echo "conda activate myenv" >> ~/.bashrc
SHELL ["/bin/bash", "--login", "-c"]
# Conda installs 
RUN conda install -y -c anaconda pyzmq \
                        pillow pandas scipy scikit-image \
                        more-itertools ipython pytables \
    && conda install -y -c conda-forge tqdm pygobject cudatoolkit \
                           dash dash-core-components dash-html-components \
    && conda install -y -c plotly plotly \
    && conda install -y -c numba numba
#  Pip installs
RUN pip install PyQt5 pyqt5-tools pyqtgraph \
    && pip install 'opencv-python<=4.1' 'opencv-contrib-python<=4.1' \
    && pip install matplotlib \
    && pip install pre-commit prettier black
#  Custom modules installs 
RUN conda install -y -c conda-forge ffmpeg
RUN conda update -y ffmpeg
RUN conda install -y -c hcc cuda-driver