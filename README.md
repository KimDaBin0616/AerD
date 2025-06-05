# AerD 팀
**팀 구성**
- 20201735 박우진 
- 20222019 김다빈

## 연구 필요성
- ### Zero-Shot Object Detection의 필요성
    - 사전 데이터 없이도 텍스트 설명만으로 탐지가 가능
    - 학습 데이터에 없는 새로운 객체 탐지 가능

    ![image](https://github.com/user-attachments/assets/8f40b3ba-5280-404f-9a50-21d79eeb42ce)
  
## 연구 목표
- ### 항공영상 기반의 제로샷 객체 탐지 연구
    - 시각-언어 모델(VLM) 기반 군용 객체 탐지 성능 향상을 위한 프롬프트 튜닝 실험
    - 군용 데이터 부족 문제를 보완하기 위한 데이터 합성 기법 제안
    - 제로샷 객체 탐지 성능 개선을 위한 방법 제안

    ![image](https://github.com/user-attachments/assets/9d51e527-8252-4ee4-85f3-a4d957ecdf96)

## 연구 내용
- ### 1. 시각-언어 모델(VLM) 기반 군용 객체 탐지 성능 향상을 위한 프롬프트 튜닝 실험
- #### 기존 프롬프트 방식의 문제점
    - 간단한 단어 중심으로 구성되어 있어 탐지 범위가 모호하고 불필요한 객체까지 탐지
    - 시각적으로 복잡한 도메인에서 단순 클래스명만으로는 시각적 특징을 충분히 설명하지 못함
 
    - 제안: 3단계 난이도 프롬프트 설계
      
    ![image](https://github.com/user-attachments/assets/5a531225-5e1c-40ed-8301-e09cebea3041)

    
- ### 2. 군용 차량 데이터 부족 문제를 보완하기 위한 데이터 합성 기법 제안
- #### 기존 문제점
    - 군사 데이터는 보안 문제로 대규모 수집 어려움
 
    - 제안: 이미지 합성 기법을 활용한 합성 데이터 생성


## 1. 시각-언어 모델(VLM)기반 군용 객체 탐지
##### 1-1. 실험환경
Python 3.10.16 \
Ubuntu 22.04.5 LTS\
GPU: NVIDIA RTX A6000 x 2 \
CPU: AMD EPYC 7543 32-Core Processor \
Memory: 251G

<가상환경> \
conda create -n qwen-vl python=3.10\
conda activate qwen-vl \
conda install pytorch=2.6.0 torchvision=0.21.0 pytorch-cuda=12.4 -c pytorch -c nvidia

##### 1-2. 디렉토리 구조
    VLM/
    ├── convert.py
    ├── data.py
    ├── vlm.py
##### 1-3. 기본구조
    python vlm.py --image_dir[경로] --output_dir[경로]
#### 옵션
+ image_dir : 입력 이미지의 해당 경로 인자
+ output_dir : 결과 이미지를 반환 받을 경로 인자


## 2. 데이터 합성 기법
##### 2-1. 실험환경
Python 3.8.6 \
Ubuntu 22.04.3 LTS\
GPU: NVIDIA RTX A5000 x 2 \
CPU: AMD Ryzen 7 5800X 8-Core Processor \
Memory: 48G

##### 2-2. 디렉토리 구조
    Image_composition/
    ├── image_composition.ipynb
    ├── qwen_drone_view.py
##### 2-3. 기본구조
    python qwen_drone_view.py --image_dir[경로] --output_dir[경로]
    image_composition.ipynb 셀 실행
#### 옵션
+ image_dir : 입력 이미지의 해당 경로 인자
+ output_dir : 결과 json을 반환 받을 경로 인자


## 3. 학습 및 검증
##### 3-1. 실험환경
Python 3.8.6 \
Ubuntu 22.04.3 LTS\
GPU: NVIDIA RTX A5000 x 2 \
CPU: AMD Ryzen 7 5800X 8-Core Processor \
Memory: 48G

##### 3-2. 디렉토리 구조
    YOLO-World/
    ├── configs
    ├── tools
##### 3-3. 기본구조
    train & evaluation: /tools/dist_train.sh configs/pretrain/"custom config.py" 2 --amp
    inference: /tools/dist_test.sh configs/pretrain/"custom config.py" 2 —amp
#### 옵션
+ custom config.py: 사용할 config.py
