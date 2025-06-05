# AerD
#### 1. 시각-언어 모델(VLM)기반 군용 객체 탐지
##### 1-1. 실험환경
Python 3.10.16 \
Ubuntu 22.04.5 LTS \ 
GPU: NVIDIA RTX A6000 x 2 \
CPU: AMD EPYC 7543 32-Core Processor \
Memory: 251G

<가상환경>
conda create -n qwen-vl python=3.10 \ 
conda activate qwen-vl \
conda install pytorch=2.6.0 torchvision=0.21.0 pytorch-cuda=12.4 -c pytorch -c nvidia
