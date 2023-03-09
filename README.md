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
