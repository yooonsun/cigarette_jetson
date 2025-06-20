# Train 설명
<br/>

## 📦 Requirements 안내

본 프로젝트의 `requirements.txt` 파일에는 학습 및 변환 시 사용한 주요 라이브러리들이 명시되어 있습니다.  
이는 [Jetson Nano 추론 환경](../inference/README.md)과는 **다를 수 있음**을 감안하여 작성된 것으로, **필수적으로 동일 버전을 사용할 필요는 없습니다.**

- 사용된 패키지 버전은 학습 당시 로컬 환경 기준이며, 최신 버전 또는 본인 시스템에 맞는 버전으로 대체 가능합니다.
- 목적은 **환경 혼동을 줄이기 위한 참고용**입니다.

📎 [`requirements.txt` 바로가기](./requirements.txt)


<br/><br/>


## 🧠 참고: 가중치 파일 안내

본 디렉토리에는 학습 후 생성된 가중치 파일들이 포함되어 있습니다.  
추론 단계에서 사용할 수도 있어 혹시 몰라 첨부해두었습니다.

- `best.pt` : 학습된 YOLOv8 PyTorch 가중치 파일
- `best.onnx` : 추론을 위한 ONNX 형식 가중치 파일

ONNX 파일은 아래와 같은 코드로 변환하였으며,  
자세한 내용은 [`train.ipynb`] 파일의 **마지막 셀**에 포함되어 있습니다.

```python
# ONNX 변환 코드
import onnx
from ultralytics import YOLO
model = YOLO("best.pt")
model.export(format="onnx", opset=12, dynamic=False, simplify=False)
