# AerD
#### 1. 시각-언어 모델(VLM)기반 군용 객체 탐지
##### 1-1. 실험환경
Python 3.10.16 \
Ubuntu 22.04.5 LTS \ 
GPU: NVIDIA RTX A6000 x 2 \
CPU: AMD EPYC 7543 32-Core Processor \
Memory: 251G

<가상환경> \
conda create -n qwen-vl python=3.10 \ 
conda activate qwen-vl \
conda install pytorch=2.6.0 torchvision=0.21.0 pytorch-cuda=12.4 -c pytorch -c nvidia

##### 1-2. 디렉토리 구조
    VLM/
    ├── convert.py
    ├── data.py
    ├── vlm.py
##### 1-3. 기본구조
    python vlm.py --image_dir --output_dir
#### 옵션
+ image_dir : 입력 이미지의 해당 경로 인자
+ output_dir : 결과 이미지를 반환 받을 경로 인자
    
