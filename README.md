# RPPG-Deepfake_Detection
- RPPG 기술을 이용한 Deep_fake Detect Project
## Code inform
- RPPG : 얼굴영역 RPPG, 다른피부영역 ROI추출 , 다른 피부영역 ROI기반 RPPG측정 으로 구성됨
- video : 웹캠을 이용하여 영상(이미지) 추출하여 저장, 이를 이용하여 RPPG를 추출한다.

## 1.RPPG
: 카메라 기반 비접촉식 PPG측정 기술
- RGB 기반의 카메라를 이용하여 얼굴 영상을 취득
- 얼굴 영상을 YCBCR domain으로 투영 시킴
- chrom 기술을 이용한 색차기반 피부색변화를 감지함.
- 피부색 변화 정도가 매우 미세하기 때문에 신호를 확장시킴. 
- 단일 심박수 뿐만아니라 연속적인 심박신호를 추출할 수 있음.

## 2. Deepfake model
- [faceswap sw](https://github.com/deepfakes/faceswap/blob/master/INSTALL.md)사용
- [faceswap.exe download](https://faceswap.dev/download/)
- faceswap github clone
  - ``` git clone https://github.com/deepfakes/faceswap ```
- 필요한 lib 설치
  - ```conda create -n deepfake python=3.8```
  - ```activate deepfake```
  - ```pip install -r requirements_nvidia.txt```
  - ```conda install tk```
- faceswap gui 실행
  - 해당 가상환경, faceswap.py가 있는 faceswap github저장소 clone 폴더로 이동
  - ```python faceswap.py gui```

### 1. 얼굴 extract
: origin, target 두 영상에 대해 얼굴 image를 추출
1. input : 얼굴을 추출한 영상
2. output : 추출한 얼굴이미지를 저장할 dir(각 영상마다 다른 경로로 설정)

### 2. Train 
1. inputA : origin face
2. inputB : target face
3. model path : 학습모델 저장할 경로 설정

### 참고자료
- faceswap 사용법 [https://sjblog1.tistory.com/34]
- faceswap train [https://forum.faceswap.dev/viewtopic.php?f=6&t=146]


## 3. Deepfake detection using RPPG
: RPPG 기술 기반 deep fake 탐지
### 원리
  - deep fake를 사용하여 합성된 얼굴 영역의 RPPG와 팔 또는 목 등 다른 피부 영역의 RPPG 신호에는 차이가 존재할 것.
  - 따라서 얼굴영역, 팔영역의 RPPG를 비교한다.
- 얼굴 외 다른 피부영역이 같이 촬영된 환경을 가정함.
### Protocol
  - 얼굴 및 다른피부영역이 포함된 영상 취득 (실제 영상 / Deep fake 영상)
  - 얼굴 ROI / 다른 피부영역 ROI 추출
  - ROI의 RPPG 신호 측정
  - 신호 형태 및 심박 수 비교
### Result
- 특허 : "리모트 PPG를 이용한 딥페이크 판별 방법", 국내특허출원 (출원번호: 10-2021-0183220, 출원일: 2021.12.20), 발명자(이의철, 유수경, 전수민), 출원인(상명대학교산학협력단)
