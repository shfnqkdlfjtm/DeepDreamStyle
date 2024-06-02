# DeepDreamStyle
DeepDream model을 이용해서 이미지를 생성하고, 생성한 이미지를 StyleGAN에서 style 이미지로 사용해서 최종 이미지를 생성한다.


## Model
### DeepDream
DeepDream은 기존의 이미지를 이용해 뉴럴 네트워크의 내부를 시각화하고, 특정 패턴을 증폭하여 환상적인 이미지를 생성하는 알고리즘이다. 이 프로젝트에서는 DeepDream을 통해 생성된 이미지를 StyleGAN의 스타일 이미지로 사용한다.

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
CelebA-HQ: 고해상도 인물 이미지 데이터셋  
FFHQ: 고해상도 얼굴 이미지 데이터셋  

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



## References
https://www.tensorflow.org/tutorials/generative/deepdream?hl=ko  
https://www.tensorflow.org/tutorials/generative/style_transfer?hl=ko  
http://solarisailab.com/archives/535  


