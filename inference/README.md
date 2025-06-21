

  ### 📂 추론 평가에 사용된 외부 데이터셋

학습에 사용되지 않은 **외부 이미지**를 통해 모델의 일반화 성능을 확인하였습니다.

🔗 [Cigarrette End Detection - Evaluation Dataset (Roboflow)](https://universe.roboflow.com/ken-0i3em/cigarrette-end-detection/dataset/2)

- 실제 일상에서 촬영한 사진들로 구성
- 담배꽁초 외에 다양한 배경 및 오브젝트가 포함됨
- 오탐/미탐 여부를 시각화하여 모델 성능 확인

# Inference 설명


## 0. 환경 설정 안내

- JetPack : [4.6.x](https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#intro)  
- 기본 내장 (JetPack 4.6.x 설치 시 자동 포함):
  - TensorRT 8.2.x
  - OpenCV
  - numpy 1.19.x

- whl 파일로 설치:
  - torch==1.10.1
  - pycuda==2021.1
  - onnxruntime-gpu==1.11.0

- pip로 설치:
  - pandas==0.22.0
  - matplotlib
  - tqdm


## 1. ONNX → TensorRT 변환

Jetson Nano 환경에서 추론 속도를 높이기 위해, 학습된 ONNX 모델을 TensorRT로 변환하였습니다.  
변환 시 사용한 명령어는 다음과 같습니다:

```bash
/usr/src/tensorrt/bin/trtexec --onnx=best.onnx --saveEngine=best.trt --explicitBatch --fp16
```

  
