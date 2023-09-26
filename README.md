# **Text-Style-Trnasfer**
## :speech_balloon: What is the Text-Style-Transfer?
**Text-Style-Transfer**은 영상내에 존재하는 언어를 다른언어로 편집하는 과정에서 **글자의 폰트, 색상, 패턴, 스타일**을 최대한 유지하는것을 목표로한다

기존의 이러한 작업은 **CG(Computer Graphics)** 작업을 통하여 진행하고 있다. 이는 비용, 시간적인 문제가 있으며 이를 해결한다면 한국문화 사업을 더욱 강화 할 수 있을 것이라 생각하였다.

**Text-Style-Transfer**는 이 작업을 인공지능을 활용하여 특정 영역만 지정해주면 **자동으로 편집이 가능**하도록 해주는 프로그램이다. 

## :star2:Main Feat
-  원본 영상: 영화 "베테랑"중 일부
  [행사상품]

    <img width="40%" src="https://github.com/gijun0725/Text-Style-Transfer/assets/119472512/ad91d1a4-1e5b-4878-8e6f-64f9312d9506"/>

- 자동 편집: **영상내 텍스트를 감지하여 자동**으로 한국어가 영어로 번역 -> 글자에 한국어가 가지고 있던 스타일도 같이 적용
  
  [행사상품 -> In event product]
  
  <img width="40%" src="https://github.com/gijun0725/Text-Style-Transfer/assets/119472512/211978c9-d4da-4c84-a74a-337c7bb7968d"/>

- 수동 편집: **편집을 원하는 영역을 직접 지정**후 지정된 영역에 대해서만 한국어가 영어로 번역 -> 한국어가 가지고 있던 스타일도 같이 적용

  [행사상품 -> product]
  
  <img width="40%" src="https://github.com/gijun0725/Text-Style-Transfer/assets/119472512/fee99d1c-eecd-453f-bc82-af16e8923774"/>
  
- 텍스트 제거: **번역이 아닌 글자만 제거하기를  원하는 경우** 영역을 지정하면 글자 배경의 이미지를 최대한 유지하면서 자연스러운 제거 가능

  [행사상품 -> " "]

  <img width="40%" src="https://github.com/gijun0725/Text-Style-Transfer/assets/119472512/e1cc3761-0327-4248-9e27-7cab2eb69623"/>

## :date:Project Planning

- **기간** : 2023.04.24 ~ 2023.06.23
  
| 수행기간 | Process |
| --- | --- |
| 2023.04.24 ~ 2023.05.01 | 주제 선정 및 Reference Searching |
| 2023.05.01 ~ 2023.05.14 | Easy OCR & SRNet모델 성능 검증 |
| 2023.05.14 ~ 2023.05.25 | SRNet모델 데이터 전처리 및 성능 개선 & 모델 학습 |
| 2023.05.26 ~ 2023.05.27 | SRNet 모델 성능 검증 후 SOTA모델 탐색|
| 2023.05.27 ~ 2023.06.09 | Mostel 구현 & 데이터 생성 및 전처리 |
| 2023.06.09 ~ 2023.06.22 | Mostel 모델 개선 전략 수립 및 학습 |
| 2023.06.19 ~ 2023.06.23 | 모델 배포를 위한 웹사이트 제작 및 최종 성능 검증  |

## :boy: My part
- **프로젝트 진행 인원** : 3명
- **주요 업무 및 상세 역할**
    - 프로젝트 아이디어 제안 및 Reference Searching
    - SRNet 모델의 성능 검증 및 성능개선, Dataset 생성
    - Mostel 모델의 데이터셋 구조를 변경하여 한국어 버전의 **Custom Dataset 생성**
    - BRM 모듈과 TMM 모듈로 구성된 **Mostel 모델 Custom**
    - Learning Rate 조절과 같은  Mostel 모델 **Fine Tuning**
    - **웹사이트 구상도 제작** 및 Flask를 이용하여 전체적인 웹사이트의 디자인을 위한 웹사이트 구축
    - **프로젝트 발표자료 작성**
- **사용언어 및 개발환경** : AWS, VSCode, Ubuntu, MySQL, FileZilla, Flask, Docker, Anaconda, Google colab Pro+, Python,
  
| AWS | 인스턴스 크기 | GPU 메모리 | vCPU | 메모리 | 디스크 |
| --- | --- | --- | --- | --- | --- |
| 단일 GPU VM | G5.xlarge | 24 | 4 | 16GB | 256gb |
---

##  :boom:문제 정의
- 증가하는 OTT산업에서의 수요에 따라 **한국 콘텐츠 산업도 빠르게 성장**하고 있다.
- 한국 콘텐츠를 해외에 수출 했을때 좀더 편하게 볼 수 있도록 영상내에 존재하는 **고유명사 혹은 짧은 문장들이 수출국에 맞춰서 수정**된다면 좀더 수익을 낼 것이라고 생각하였다
- 대표적으로 **'고독한 미식가'** 드라마가 이에 해당하며 **현재 CG작업을 통해 이루어 지며** 이는 **시간과 비용**이 많이들기에 대중화 되어있지는 않지만 잠재적으로 알고 있는 시청자들이 많았다
- 짧은 영상 **5,10초** 정도의 간단한 편집도 최소 **10~300만원**이 소요되어 일반인은 쉽게 편집에 입문하기 어렵다는 문제도 해결 하기를 원했다.
- 이와 같은 작업이 CG가 아닌 **인공지능**을 이용한다면 **한국 문화사업에 큰 영향**을 줄 것이라 생각했다.
  
<div align="center">
  <img width="700" alt="이미지 설명" src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/441e8fce-ceee-4f97-b6b5-7eeabb866534">
</div>

>출처: 드라마 이상한 변호사 우영우 & 프리랜서 플랫폼 크몽



---
## How:grey_question:

### <프로젝트 목적>

#### 1.OCR을 통한 한국어 글자 이미지 크롭 및 저장

영상 내의 한국어 글자를 Optical Character Recognition (OCR) 기술을 사용하여 인식하고, 해당 글자 이미지를 자동으로 크롭하여 저장합니다.

#### 2.GAN 모델을 활용한 번역 및 스타일 적용

Generative Adversarial Network (GAN) 계열의 딥러닝 모델을 사용하여 한국어 글자 스타일을 번역된 영어 글자에 적용합니다. 이를 통해 시각적으로 일관성 있는 영어 글자 이미지를 생성합니다.

#### 3.데이터셋 커스터마이즈 및 Fine Tuning

선택한 GAN 모델을 향상시키기 위해 데이터셋을 커스터마이즈하고 Fine Tuning을 진행합니다. 이로써 모델의 정확성과 성능을 향상시킵니다.

#### 4.글자와 배경 손실 최소화

영상 내 글자 이미지를 자동으로 편집하는 기능을 제공하여, 글자와 배경 사이의 경계를 더욱 정확하게 인식하고 손실을 최소화합니다. 이를 통해 시간과 비용을 절약하고 효율적인 편집을 가능하게 합니다.

#### 5.국내 콘텐츠 수출 증가 기여

이 프로젝트는 한국어 글자를 영어로 번역하여 국내 콘텐츠의 해외 수출을 촉진하고 국내 기술의 글로벌 확산에 기여할 것으로 기대됩니다.

#### 6.일반 사용자들을 위한 사용 편의성

이 프로젝트는 컴퓨터 그래픽 작업에 대한 전문 지식이 없는 사용자들에게도 손쉽게 영상 내 글자 이미지 편집을 가능하게 합니다. 이로써 일반 사용자들도 글자 편집을 쉽게 수행할 수 있습니다.

#### 7.웹사이트 제작

프로젝트 결과물로 웹사이트를 제작하여 사용자들에게 쉽게 접근하고 활용할 수 있도록 합니다. 이 웹사이트를 통해 프로젝트의 기능과 이점을 소개하고 제공합니다.




## < Text-Style-Transfer 프로젝트의 End-to-End Framework 구조>
<div align="center">
  <img width="800" alt="이미지 설명" src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/b8fff571-0dff-4732-a240-a629b9e5648f">
</div>
 - 동영상을 프레임 단위의 이미지로 추출하는 기술, 광학문자인식(OCR), 번역기, 이미지 생성 모델인 MOSTEL 딥러닝 모델을 사용하여 영상 속에 등장하는 한국어를 영어로 바꾸어서 편집된 영상을 자동 및 수동으로 제작할 수 있는 웹사이트를 제공


- 본 프로젝트는 딥러닝 모델을 활용하여 영상 내 한국어 글자 스타일을 번역된 영어 글자에 적용하여 컴퓨터 그래픽을 자동으로 편집하는 End-to-End Framework 제시한다.



## AI를 활용한 영상 내 텍스트 자동 번역 및 편집 기능

### 자동편집 Framework

<div align="center">
  <img width="800" alt="이미지 설명" src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/47567efd-79e7-4aa8-a5a0-d682414d6a2b">
</div>


1. **OCR & Crop** : 원본 영상 프레임 내 텍스트 영역을 감지 후 텍스트로 변환하여 텍스트 영역을 crop하여 저장
2. **Translation** : Helsinki-NLP 기반의 opus-mt-ko-en 모델을 통하여 자동으로 한영 번역
3. **Inpainting** : 글자를 제거한 배경 이미지 생성
4. **Font Style Transfer** : 번역된 텍스트에 OCR & Crop을 통해 저장된 텍스트 스타일 변환을 적용

### **OCR & Crop** : Easy OCR

- 광학문자인식(OCR) 기술은 이미지 내 글자를 감지하고 해당 글자의 위치를 표시하며, 이를 통해 글자의 내용을 추출하는 기술입니다. 이 프로젝트에서는 한국어를 영어로 번역하기 위해 한국어 글자의 위치를 감지하고 해당 영역을 자동으로 잘라내어 저장하는데 활용된다.
- 이전에는 문장을 전체적으로 인식하는 방식이었지만, Easy OCR을 사용함으로써 단어 단위로 인식하도록 하이퍼 파라미터를 조정하여 번역의 정확도를 높일 수 있었습니다. 이로 인해 문장의 번역 품질을 향상시킬 수 있었다.

- Easy OCR의 선정 이유 : 프로젝트에서 Easy OCR을 선택한 이유는, 이 라이브러리가 80가지 이상의 언어를 인식할 수 있으며, 한국어에 대한 학습 모델을 제공하고 있어 한국어 인식 정확도가 높다는 점입니다. 또한, Easy OCR은 다른 OCR 모델인 Tesseract와 비교하여 한국어 인식에서 상대적으로 우수한 성능을 보여주기 때문에 선택하였다.



<div align="center">
  <img width="800" alt="이미지 설명" src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/5a0afe14-ef4f-4942-a2bc-8c2ce0015165">
</div>

### Translation : Papago API

- 영상 내 인식된 글자를 자동으로 번역

<div align="center">
  <img width="800" alt="이미지 설명" src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/79539895-63da-45ff-971b-0019a530ef2c">
</div>


### **Inpainting & Font Style Transfer : MOSTEL**


- **Pre-Transformation** : 이 모듈은 원본 이미지와 타겟 텍스트 이미지에 특수한 변환을 적용하여 전처리하고, 배경 특징과 텍스트 스타일을 혼합하여 편집된 이미지를 생성합니다.
    - **Back Filtering** : 복잡한 배경을 제거하기 위해 배경 마스킹 이미지를 사용하여 노이즈를 제거합니다.
    - **Style Augment** : Text Style Generation을 향상시키기 위해 임의의 회전 및 크기 변환을 적용하여 학습을 일반화시킵니다.
    - **TPS[Thin Plate Splines] with Recognizer**
        - Recognizer : Text Image를 잘 읽게하기 위해 Pretrained Recognizer 도입
        - Swap Text 기법을 적용하여 Feature Extraction과 FC Layer를 통해 텍스트 윤곽을 파악할 수 있는 Anchor Point를 얻어 텍스트의 방향에 대한 정보를 제공하는 모듈
        - 부분적으로 속성을 분리하여 학습의 난이도를 낮추고, Text Style의 올바른 정보를 전송
- **Gradient Block**
    - 학습 데이터셋에 없는 스타일 패턴이 변환되지 않고 출력되는 것을 방지하기 위한 전략
- **Only in Reference**
    - Inpainting Image와 Font Style이 Transfer된 Text를 Fusion하는 대신 Inpainting Image를 참고하여 배경을 제거하면서 스타일이 적용된 Text를 Fusion하는 전략
- **Real data**   
    - Label이 지정된 합성 데이터셋과 준지도 학습 방식을 위해 Label이 지정되지 않은 현실 데이터셋으로 훈련

---

**MOSTEL 데이터셋**

**[합성 이미지 데이터]** : 기존의 MOSTEL 모델은 이미지 내에 있는 영어 글자 스타일을 다른 영어 단어에 반영한 이미지를 생성하는 모델이다. 본 프로젝트는 영어가 아닌 한국어를 영어로 바꾸어 이미지를 생성하는 모델이므로, 영어로만 학습된 MOSTEL을 Fine Tuning하기 위해 한국어-영어 버전의 데이터셋 생성하였다.

<div align="center">
  <img width="800" alt="이미지 설명" src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/1aed52b3-88a4-4f0d-b49e-d215855bddc3">
</div>

**[합성 이미지 데이터 : Word & Sentence]**

- 원래 MOSTEL의 데이터셋은 단어 단위(word-level)의 텍스트 이미지 데이터셋으로만 구성되어 있지만, 아래 이미지와 같이 실제 간판이나 영상 내 글자는 띄어쓰기가 존재하거나 두 단어 이상의 영어로 이루어져 있다.
- 이를 고려하여 띄어쓰기가 있는 한국어와 영어 말뭉치 각각 15만 개와 띄어쓰기가 없는 한국어와 영어 말뭉치 각각 10만 개로 데이터를 생성하였다.
<div align="center">
  <img width="800" alt="이미지 설명" src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/039814b1-0418-410c-b071-45582f31c8fd">
</div>


**[Custom 합성 이미지 데이터 : 기존 Background]**

<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/072bde63-8c01-4827-ad95-f6d4f8f72f20" width="700" alt="이미지 설명">
</div>


- 기존 데이터셋: 위와 같이 현실에서는 글자 배경이 단순한 경우가 많지만, 프로젝트 초기에 사용한 데이터셋은 **현실과는 다른 복잡한 배경**을 가진 이미지로 구성되었습니다.
- 이 데이터셋을 사용하여 모델을 학습시키면, 실제 상황과는 다른 배경 이미지가 사용되기 때문에 **Domain Gap이 크게 발생**하는 문제가 있었습니다. 이로 인해 모델의 추론 성능이 좋지 않았습니다.
  
<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/04d994ba-2704-478d-b358-ab71d0d9fce3" width="700" alt="이미지 설명">
</div>

→ 이를 해결하기 위해 복잡한 배경을 제거하고, 단색 배경을 추가하여 새로운 데이터셋을 생성하였다.

**[Custom 합성 이미지 데이터 : 재생성 Background]**

- 재생성한 데이터셋 : 학습에 방해가 되는 복잡한 배경 이미지를 제거하고, 단조로운 사진 배경 이미지 8,000장과 단색 배경 8,000장을 추가하여 새로운 데이터 셋을 생성하였다.
- 재생성한 데이터셋으로 학습시킨 결과, 현실과 차이나는 Domain Gap의 문제를 해결할 수 있었으며, 이에 따라 아래의 Inference 이미지를 통해 Background와 Text를 잘 분리하여 Inpainting하는 것을 볼 수 있다.

<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/4d8ccbfa-95ad-4905-affa-14705a056b6d" width="700" alt="이미지 설명">
</div>


**[Custom 합성 이미지 데이터 : Font Style]**

<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/084ab3cf-ed46-4419-b7c4-d092f8c73b59" width="700" alt="이미지 설명">
</div>


- 기존 데이터셋의 Font Style은 일정한 폰트와 크기, 각도, 색으로 생성하였으며, 이에 따라 한정된 Font Style에 과적합되어 Target Text에 Font Style을 적용시킬 수 없었다.
- 이를 해결하기 위해 상업, 광고, 포스터에 자주 사용되는 108개의 다양한 폰트와 크기, 각도, 색을 다르게 하여 생성한 결과, 위의 사진과 같이 Font Style을 제대로 적용시키는 것을 볼 수 있다.

**[Custom 현실 이미지 데이터]**

- Label이 지정되지 않은 현실 이미지 데이터셋을 통해 Semi-Supervised Learning이 가능
- Target Text에 Font Style을 입힌 최종 이미지의 Label을 원본 이미지로 줌으로써 Background에서 Text가 지워진 Inpainting Image와 마스킹된 이미지가 없는 실제 이미지만으로도 학습을 가능하게 하여 Domain Gap을 줄였다.
  
<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/85d4127d-25b0-45d4-827a-cdbe975548d8" width="700" alt="이미지 설명">
</div>



- 영어 현실 이미지 데이터는 MOSTEL Github에 제공되어 있는 데이터셋을 사용하였으며, 한국어 현실 이미지 데이터는 AI HUB에 제공되어 있는 “야외 실제 촬영 한글 이미지” 데이터셋 책 표지 800장을 사용하여 데이터셋을 생성하였다.
  
<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/87fcf2b4-e852-4573-a1e7-ee5d164bb7bb" width="700" alt="이미지 설명">
</div>


**[최종 MOSTEL 훈련 데이터셋]**
<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/26775c2a-040d-455b-b1be-c9f3246e463a" width="700" alt="이미지 설명">
</div>


- 합성 이미지와 현실 이미지를 7:1 Batch의 비율로 하여 정성적으로 Text Style Transfer 결과를 확인하면서 평가하고, 이에 더하여 정량적으로 Loss의 모니터링, Metrics를 통해 Learning Rate를 0.00005로 15만 EPOCH 학습하고, 이후에 Learning Rate를 0.00004로 감소시켜 7만 EPOCH을 학습하여 총 22만 EPOCH을 146시간 학습하였다.

**[MOSTEL 개선 전 후 비교]**

<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/24a83878-0188-4c29-8013-c1c7d72d1ec2" width="700" alt="이미지 설명">
</div>


[COMPARISION MODEL : **MOSTEL** vs. **SRNet**]

- SRNet은 합성 이미지로만 학습이 가능하여 배경의 텍스처 보존이 어렵고, 동시에 작업이 이루어지다 보니 Bias가 발생하여 실제 영상에서 성능이 저하되는 문제가 발생하였다.
  

<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/ba3ba72d-8284-4174-82b7-764dbbc2b02f" width="700" alt="이미지 설명">
</div>

- SRNet은 MOSTEL과 다르게 단순히 Text Style을 추출함과 동시에 Text를 제거한 Background를 추출하여 두 결과값을 Fusion한다. 편집 과정에서 이미지 전체 픽셀을 고려하여 배경과 글자 영역을 잘 분리하지 못 하고, 픽셀의 배경 영역에 변화를 일으키는 문제가 발생되었다.
  

<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/3d0280ed-bd60-4fdb-bc9a-36c56e975891" width="700" alt="이미지 설명">
</div>
    
- 반면에 MOSTEL은 배경과 글자를 따로 분리하여 학습하는 구조로, 바뀌어야 할 픽셀의 위치를 Masking하여 Guide함으로써 글자에 변환을 적용할 때 배경은 영향을 받지 않는다.
  

<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/fb674f96-a35f-4a4e-bd82-5e336918be93" width="700" alt="이미지 설명">
</div>


- **Text Inpainting 결과**
<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/9e60f23f-faa6-4316-bb4c-03c46ffea4f0" width="700" alt="이미지 설명">
</div>


    - SRNet에 비해 MOSTEL은 배경 영역을 최대한 보존하여 Text를 Inpaint하는 것을 볼 수 있다.
 

- **Style Transfer 결과**

<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/61bb53e6-0f54-4ce4-a3b4-713290dfcaca" width="700" alt="이미지 설명">
</div>




## AI를 활용한 영상 내 텍스트 자동 번역 및 편집 기능을 통한 Projection Method
<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/66c8f738-828f-4fb9-ad06-912cf317d3d3" width="700" alt="이미지 설명">
</div>

1. 프레임 선택
2. OCR을 통하여 글자가 있는 좌표를 찾고, 글자를 인식
3. 좌표를 통해 이미지를 자른 후 한영 번역
4. 번역된 글자에  Font Style Transfer
5. 원래 글자 위치에 Projection

**[Frame To Video]**

<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/a34d3aad-f462-4b8f-93cf-410ca60c1f02" width="700" alt="이미지 설명">
</div>
- Text Font Style Transfer를 적용한 프레임 단위를 영상(1초에 약 60 프레임)으로 합하여 사용자가 다운로드 할 수 있는 영상을 생성한다.

## AI를 활용한 영상 내 텍스트 수동 번역 및 편집 기능
<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/7733a91f-a934-4860-b21f-78a19957da05" width="700" alt="이미지 설명">
</div>

1. 편집된 영상의 프레임을 선택하여 원본 영상의 프레임으로 복원
2. 번역 및 편집을 적용할 글자의 좌표 클릭
3. 원하는 번역어 입력
4. 입력된 글자에 원본 글자 Font Style Transfer
5. 원래 글자 위치에 Projection

---

## AI를 활용한 영상 내 텍스트 제거 기능
<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/7430fca1-9328-43fa-a91a-2b8b3d7eee46" width="700" alt="이미지 설명">
</div>


1. 편집된 영상의 프레임을 선택하여 원본 영상의 프레임으로 복원
2. 글자를 제거할 좌표 클릭
3. 제거한 이미지를 원래 글자 위치에 Projection


- **BRM의 Inpainting 원리** : Masking Image로 제거해야 하는 영역을 Guide하여 텍스트를 제거

<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/9721ccdb-95ff-4728-99ef-dfafe86494be" width="700" alt="이미지 설명">
</div>


- 기존 MOSTEL BRM 모듈의 Inpainting 원리로 학습하였을 때 글자 테두리가 남는 문제가 발생하였으며, 자연스러운 배경 이미지를 생성하기 위해 **cv2.Dilate**를 사용하여 **Masking Image에 글자 팽창을 적용**시켰다. 적용시킨 Masking Image를 Guide한 결과 Background를 보존한 채로 글자만 제거하여 성능을 개선하였다.



- **TMM의 Text Recognition 원리** : 글자를 인식할 수 있는 Recognizer를 사용하여 글자의 위치, 방향, 색상 등 원본 이미지의 글자에 대한 특징을 Target Text에 적용
- 영어로만 학습되어 있기에 한국어 Font Style을 학습하지 못 하고 Target Text에 Font Style이 적용되지 않는 문제가 발생하였으며, 이를 해결하기 위해 Mostel의 구조 파악 후 Recognizer 모듈을 커스텀하여 **한국어와 영어 두 언어 모두 인식**할 수 있도록 학습하여 성능을 개선하였다.

---

## 발전 가능성

### 신경망 기반 고화질 변환 : Real-ESRGAN

### 객체 탐지 및 추적 : Siamese Network

<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/12b139df-3ca6-4221-a721-69d60cc2ad5c" width="700" alt="이미지 설명">
</div>

- 기존의 편집된 영상은 프레임 합성 시에 프레임 간의 차이가 존재하여 흔들림 또는 불일치 현상이 발생한다. 이를 개선하기 위해 Siamese Network를 사용하여 두 개의 프레임을 비교하여 프레임 합성 시에 발생하는 흔들림 현상을 최소화하고, 자연스러운 동영상 생성한다.

---

## 확장 가능성

### 타 분야 적용 1 : 포스터, 상품

<img width="838" alt="스크린샷 2023-07-27 오전 11 50 17" src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/85503d9e-16a1-4caf-9e86-eabfa2dcfecf">

- 영화, 드라마 이외에도 원본 이미지의 Text Font Style을 학습하여 번역된 Text에 Font Style Transfer를 적용하여 포스터, 상품 등 다양하게 사용 가능하다.

### 타 분야 적용 2 : 번역기

<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/684a2b7c-99f2-4f2b-801d-1f7687c574f0" width="700" alt="이미지 설명">
</div>


- 네이버에서 진행중인 “더 잘 읽히는 번역기” 프로젝트의 일부로, 현재 원본 이미지 내의 텍스트를 지우고 번역된 텍스트를 Fusion하는 프로젝트가 존재한다.

<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/274b3bbe-8839-461e-adf6-06988cd64358" width="700" alt="이미지 설명">
</div>

b-b9d7-66110735cc99">

- 위의 사진과 같이 파파고 번역기는 배경이 완전히 지워지지 않고 Font Style을 반영하지 못 하지만, 우리의 모델을 배경을 최대한 보존하여 글자 색상과 Font Style을 반영할 수 있다.

### 편집 비용 절감 가능

<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/3ec93894-1e63-485f-9e57-c6fecd679a70" width="500" alt="이미지 설명">
</div>


- 현재 10초 길이 영상의 컴퓨터 그래픽 작업의 편집 비용은 10만 원부터 35만 원까지 수작업으로 진행되고 있으며, 작업일은 2일에서 5일이 소요된다.
- 컴퓨터 그래픽 작업 분야에서 AI를 활용한다면 시간적, 금전적 기회비용을 절감시킬 수 있으며, 더 나아가 증가하는 K 콘텐츠 산업의 수출에 있어서 해외 콘텐츠 접근성을 높이고, 국내 콘텐츠 수출 시장의 규모를 더욱 성장시킬 수 있다.

---

## 웹사이트 구상도

<div align="center">
  <img src="https://github.com/Yu-Miri/Text_Translation_and_Font_Style_Editing_in_Video/assets/121469490/64da5d62-1950-4183-a5fa-fc9a9896c754" width="700" alt="이미지 설명">
</div>

- 위에서 명시한 세 가지 기능을 추가한 웹사이트의 구상도로, 해당 웹사이트는 **회원가입 기능**과 **로그인 기능**, **편집 기록 기능**, **편집된 영상 재편집 기능**, **영상 업로드 기능**, **영상 저장 기능**, **글자 재생성 기능**, **글자 제거 기능**을 제공한다.

---

**참고 문헌**

Qu, Yadong, et al. "Exploring Stroke-Level Modifications for Scene Text Editing." arXiv preprint arXiv:2212.01982 (2022).

Liao, Minghui, et al. "Real-time scene text detection with differentiable binarization and adaptive scale fusion." IEEE Transactions on Pattern Analysis and Machine Intelligence 45.1 (2022): 919-931.

Wu, Liang, et al. "Editing text in the wild." Proceedings of the 27th ACM international conference on multimedia. 2019.

---

## Installation

### Requirements
~~~
git clone https://github.com/Yu-Miri/Text-Translation-and-Font-Style-Editing-in-video.git
conda create —name MOSTEL python=3.7.12 -c conda-forge
conda activate MOSTEL
pip install torch==1.7.1+cu101 torchvision==0.8.2+cu101 -f https://download.pytorch.org/whl/torch_stable.html
pip install mmcv-full==1.6.0 -f https://download.openmmlab.com/mmcv/dist/cu101/torch1.7/index.html
pip install -r requirements.txt
conda uninstall pytorch
conda install pytorch==1.11.0 torchvision==0.12.0 torchaudio==0.11.0 cudatoolkit=11.3 -c pytorchinput_d
~~~

### Preparing the Dataset
https://drive.google.com/drive/folders/12TUPIBcyD-3gm_YZHKXBPlLI-6FmE6dh?usp=sharing

**Mostel Dataset & Mostel ckpt** : Mostel

**web mostel ckpt** : final_web

---
### Training

- Mostel Train
~~~
python train.py —config configs/mostel-train.py
~~~

- Mostel Erase Train
~~~
python train_erase.py —config configs/erase-train.py
~~~

### Predict & Evaluation

- Predict
~~~
python predict.py --config configs/mostel-train.py --input_dir datasets_eval/i_s/ --save_dir results_eval --checkpoint checkpoint/train_step-210000.model --slm
~~~

- Evaluation : PSNR, SSIM, MSE, FID
~~~
python evaluation.py --gt_path datasets_eval/t_f/ --target_path results_eval
~~~
 
