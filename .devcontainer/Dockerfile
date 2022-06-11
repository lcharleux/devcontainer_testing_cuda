# SOURCE IMAGGE
FROM rapidsai/rapidsai-dev:22.04-cuda11.5-devel-ubuntu20.04-py3.9
SHELL ["/bin/bash", "--login", "-c"]
ENV PATH="/root/miniconda3/bin:${PATH}"
ARG PATH="/root/miniconda3/bin:${PATH}"
RUN apt-get update \
    && apt-get install -y wget \
    git \
    ffmpeg \ 
    && rm -rf /var/lib/apt/lists/*
# RUN add-apt-repository contrib

#RUN conda create -n myenv python=3.9
RUN echo "conda activate rapids" >> ~/.bashrc
SHELL ["/bin/bash", "--login", "-c"]
# Conda installs 
RUN conda install -y -c anaconda pyzmq \
                        pillow pandas scipy scikit-image \
                        more-itertools ipython pytables \
    && conda install -y -c conda-forge tqdm pygobject matplotlib \
                           dash dash-core-components dash-html-components \
                           pre-commit black \
    && conda install -y -c plotly plotly \
    && conda install -y -c numba numba
#  Pip installs
# RUN pip install PyQt5 pyqt5-tools pyqtgraph \
#     && pip install 'opencv-python<=4.1' 'opencv-contrib-python<=4.1' \
#     && pip install prettier
#  Custom modules installs 
RUN conda install -y -c conda-forge ffmpeg
RUN conda update -y ffmpeg

# NVTOP : NOT WORKING PROPERLY YET
# RUN apt update \
#     && apt install -y nvtop htop nodejs npm
# RUN npm install -g -y gtop

RUN echo "conda activate rapids" >> ~/.bashrc
