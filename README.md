# 🩺 피부질환 분류 (ResNeXt50)

이 프로젝트는 **PyTorch** 기반으로 **피부질환 이미지 분류 모델**을 학습하는 코드입니다.  
모델은 **ResNeXt50 (32x4d)** 구조를 사용하며, `train/질환명/이미지`, `val/질환명/이미지` 구조로 데이터를 불러옵니다.  
학습 후, **Epoch 별 Accuracy 변화를 그래프(`fig/accuracy_curve.png`)** 로 저장합니다.  

---

## 📂 데이터셋 구조

데이터는 다음과 같이 준비해야 합니다:

```
Split_smol/
│
├── train/
│   ├── 질환A/
│   │   ├── img1.jpg
│   │   ├── img2.jpg
│   │   └── ...
│   └── 질환B/
│       └── ...
│
└── val/
    ├── 질환A/
    ├── 질환B/
    └── ...
```

- `train/` : 학습용 데이터
- `val/`   : 검증용 데이터  

---

## ⚙️ 환경 설정

```bash
# 필수 패키지 설치
pip install torch torchvision matplotlib
```

- Python ≥ 3.8  
- PyTorch ≥ 2.0  
- torchvision ≥ 0.15  

---

## 🚀 학습 실행

```bash
python train_resnext.py
```

- **train_resnext.py** : 학습 및 검증 코드  

---

## 🧠 주요 기능

### ✅ 모델 구조
- `torchvision.models.resnext50_32x4d` 사용  
- 마지막 FC 레이어를 클래스 수에 맞게 교체  

### ✅ 데이터 전처리
- `Resize(224,224)`  
- `ToTensor()`  
- `Normalize(mean, std)` (ImageNet 기준)  

### ✅ 학습 설정
- Optimizer : `SGD(lr=0.001, momentum=0.9)`  
- Loss : `CrossEntropyLoss`  
- Epoch : 기본 20  

### ✅ 평가 지표
- Epoch마다 **Train Accuracy**, **Validation Accuracy** 출력  
- Accuracy 변화를 `/fig/accuracy_curve.png` 로 저장  

---

## 📊 결과 (예시)

학습이 끝나면 `/fig` 폴더 안에 Accuracy 그래프가 저장됩니다.  

```
fig/
└── accuracy_curve.png
```

예시 그래프:  

---<img width="1200" height="900" alt="accuracy_curve" src="https://github.com/user-attachments/assets/49961c50-0f1c-427d-9ae9-c211c7a16464" />

---

## 📌 커스텀 설정

- 학습 epoch 변경 → `num_epochs`  
- 배치 크기 변경 → `batch_size`  
- 데이터 경로 변경 → `data_root = "/content/Split_smol"`  




## 👨‍💻 작성자

- 김윤성  
- 2025.08  
