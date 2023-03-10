# 4DBlock_classification - <br>포디블록 구조 추출

## 1. Task 설명
- 2D 이미지 내 포디블록의 10가지의 블록 패턴들의 존재 여부를 분류하는 Multi-Label Classification을 수행한다.

<br>

 ## 2. 데이터
 - 실험 환경에서의 포디블록 촬영 이미지
 - n_train: 32994
 - n_test: 1460
 - Data directory structure:
     ```bash
    DATA/
    ├── train/
    │       ├── train.csv  
    │       ├── images/
    │           ├── xxx.jpg
    │           ├── yyy.jpg
    │           ├── zzz.jpg
    │           └── ...  
    │            
    │                   
    └── test/
            ├── sample_submission.csv
            ├── test.csv
            └── images/
                ├──  aaa.jpg
                ├──  bbb.jpg
                └──   ...
    ```

<br>

## 3. Modeling
### Augmentation
- RandomHorizontalFlip
- RandomAffine
- RandomResizedCrop
- AugMix
- Normalize

### Models
- EfficientnetB0
- EfficientnetB3
- InceptionV3
- SeResnet26
- TResnet_XL
- TResnetV2_L
- Vit
- MaxVit_Tiny
- MaxVit_Nano

<br>

## 4. Idea

### Remove background
 - Test data와 달리 Train data에는 배경이 존재하기 때문에 Train data의 배경을 제거 후 학습
 > 1. bdgModel과 fgdModel 생성
 > 2. cv2의 grabCut을 활용하여 블록 부분만 grab
 > 3. 배경 부분은 흰색, 블록 부분은 그대로 남기면서 배경과 블록 분리

<br>

### Augmentation
- RandomHorizontalFlip : 블록이 위, 아래가 구분되어있기 때문에 VerticalFlip은 제외해주었다.
- RandomAffine
- AugMix
- PixelDrop

### Ensemble



<br><br><br><br>

| Encoders      | Loss          | mIoU  |
| ------------- |:-------------:| -----:|
| EfficientnetB2      | 0.06575      |   0.7508 |
| EfficientnetB3   | 0.06269      |    0.7817 |
| EfficientnetB4     | 0.06193      |    0.7677 |
| Resnet50    | 0.08719      |    0.6968 |
| Mit_b3     | 0.08036      |    0.7265 |