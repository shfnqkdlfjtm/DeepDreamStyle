# DeepDreamStyle
DeepDream model을 이용해서 이미지를 생성하고, 생성한 이미지를 StyleGAN에서 content image로 사용해서 최종 이미지를 생성한다.


## Model
### DeepDream
DeepDream은 기존의 이미지를 이용해 뉴럴 네트워크의 내부를 시각화하고, 특정 패턴을 증폭하여 환상적인 이미지를 생성하는 알고리즘이다. 이 프로젝트에서는 DeepDream을 통해 생성된 이미지를 StyleGAN의 content 이미지로 사용한다.

주요 요소
기본 모델: InceptionV3
레이어 선택: 'mixed3', 'mixed5'
학습 방식: Gradient Ascent

### StyleGAN
StyleGAN은 생성적 적대 신경망(GAN)의 일종으로, 이미지 생성의 스타일을 조절할 수 있는 기능을 제공한다.. 이 프로젝트에서는 DeepDream으로 생성된 이미지를 스타일 이미지로 사용하여 StyleGAN을 통해 새로운 이미지를 생성한다.  

주요 요소  
기본 모델: StyleGAN2  
레이어 선택: 다양한 레이어를 통해 스타일 조절  
학습 방식: GAN Loss, Style Mixing, Truncation Trick  

## Dataset
### DeepDream Dataset
DeepDream을 통해 생성된 이미지들을 사용한다. 이를 위해 다양한 원본 이미지를 준비하고, 각 이미지에 대해 DeepDream 알고리즘을 적용한다.  

데이터 준비  
원본 이미지: 다양한 주제의 이미지 (자연, 건축물, 인물 등)  
DeepDream 적용: 각 원본 이미지에 DeepDream 알고리즘 적용하여 새로운 이미지 생성  

### StyleGAN Dataset  
StyleGAN을 학습시키기 위해 CelebA-HQ, FFHQ와 같은 대규모 고해상도 이미지 데이터셋을 사용한다.  

데이터 준비  
CelebA-HQ: 고해상도 인물 이미지 데이터셋 (예시)  
FFHQ: 고해상도 얼굴 이미지 데이터셋 (예시)  

## Train
### DeepDream Training
DeepDream은 사전 학습된 모델을 사용하므로 추가 학습이 필요하지 않다. 대신 원본 이미지에 대해 DeepDream 알고리즘을 적용하여 결과 이미지를 생성한다.

### StyleGAN Training
StyleGAN은 대규모 데이터셋을 사용하여 학습한다.

학습 과정  
데이터셋 준비 및 전처리  
생성자(Generator)와 판별자(Discriminator) 초기화  
GAN Loss를 사용하여 반복적 학습  
스타일 이미지 적용 및 스타일 혼합  

## Demo

### DeepDream 과정
원본이미지  
![image](https://github.com/shfnqkdlfjtm/DeepDreamStyle/assets/144716487/81abc2fd-bf89-4be7-b693-bc2df1682ca5)  
steps=100, step_size=0.01  
![image](https://github.com/shfnqkdlfjtm/DeepDreamStyle/assets/144716487/12b7ec62-b0e8-46e9-acda-b8e90151ca59)  
OCTAVE_SCALE = 1.30  
![image](https://github.com/shfnqkdlfjtm/DeepDreamStyle/assets/144716487/9b0e1261-6280-40b4-8001-ff5628695144)  
최종 deep dream 이미지  
![image](https://github.com/shfnqkdlfjtm/DeepDreamStyle/assets/144716487/3f2675e1-8549-48d2-b335-48e6b47f2cb9)  
etc  
![스크린샷 2024-06-02 204942](https://github.com/shfnqkdlfjtm/DeepDreamStyle/assets/144716487/91d7a321-7f40-43a2-8223-41085e7687ad)  


### DeepDream 이미지에 StyleGAN을 추가한 과정  
이전 deep dream 이미지를 저장해서 바로 불러온 결과와 style 이미지  
![image](https://github.com/shfnqkdlfjtm/DeepDreamStyle/assets/144716487/f6ed4a38-96b1-40b2-9f57-330ea3ae00b8)  
알고리즘 시범 결과  
![image](https://github.com/shfnqkdlfjtm/DeepDreamStyle/assets/144716487/94d5252c-a868-41f0-a632-6c3ab4e89e42)  
train step: 100  
![image](https://github.com/shfnqkdlfjtm/DeepDreamStyle/assets/144716487/f07b953d-10f7-49f1-abe5-dc93e2f332e4)  
traim step: 400  
![image](https://github.com/shfnqkdlfjtm/DeepDreamStyle/assets/144716487/54e02ba3-0465-4df0-a7b5-c884bc104737)  
time step:1000 (total time: 1090.9)  
![image](https://github.com/shfnqkdlfjtm/DeepDreamStyle/assets/144716487/4638ea09-52bc-4c3b-addb-af1466ebd790)  

## 결론
최종 deep dream 이미지와 이미지를 저장해서 바로 불러온 결과 이미지에 차이가 있어 로컬파일로 저장한 뒤 불러온 이미지와 etc 이미지로 교체해본 결과, 한번 딥러닝을 거친 이미지는 컴퓨터에서 인식 결과 이미지와 같아서 StyleGAN 결과가 제대로 나오지 않는 다는 것을 깨달았다.

## References
https://www.tensorflow.org/tutorials/generative/deepdream?hl=ko  
https://www.tensorflow.org/tutorials/generative/style_transfer?hl=ko  
http://solarisailab.com/archives/535  


