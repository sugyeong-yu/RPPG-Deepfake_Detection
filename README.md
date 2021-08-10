# RPPG-Deepfake_Detection
- RPPG 기술을 이용한 Deep_fake Detect Project
## Code inform
- RPPG : 얼굴영역 RPPG, 다른피부영역 ROI추출 , 다른 피부영역 ROI기반 RPPG측정 으로 구성됨
- video : 웹캠을 이용하여 영상(이미지) 추출하여 저장, 이를 이용하여 RPPG를 추출한다.
## RPPG
: 카메라 기반 비접촉식 PPG측정 기술
- RGB 기반의 카메라를 이용하여 얼굴 영상을 취득
- 얼굴 영상을 YCBCR domain으로 투영 시킴
- chrom 기술을 이용한 색차기반 피부색변화를 감지함.
- 피부색 변화 정도가 매우 미세하기 때문에 신호를 확장시킴. 
- 단일 심박수 뿐만아니라 연속적인 심박신호를 추출할 수 있음.
## 1. Deepfake 영상
- [faceswap sw](https://github.com/deepfakes/faceswap/blob/master/INSTALL.md)사용
- [faceswap.exe download](https://faceswap.dev/download/)


## 2. Deepfake detection
: RPPG 기술 기반 deep fake 탐지
- 원리
  - deep fake를 사용하여 합성된 얼굴 영역의 RPPG와 팔 또는 목 등 다른 피부 영역의 RPPG 신호에는 차이가 존재할 것.
  - 따라서 얼굴영역, 팔영역의 RPPG를 비교한다.
- 얼굴 외 다른 피부영역이 같이 촬영된 환경을 가정함.
- Protocol
  - 얼굴 및 다른피부영역이 포함된 영상 취득
  - 얼굴 ROI / 다른 피부영역 ROI 추출
  - ROI기반으로 RPPG 측정
### 다른 피부영역의 ROI추출
1. YCBCR 기반
2. 마우스로 ROI드래그하여 좌표 얻기
