# 화자인식 인공지능 경진대회(임시_데이터셋)

- [문제2 화자 인식 데이터셋 설명](#문제-2-화자인식-dataset-설명)

## 대회 규칙

- **주제**
  - 음성 데이터에서 발화자 일치 여부를 도출해낼 수 있는 인공지능 알고리즘 개발
- **평가**
  - EER(Equal Error Rate)
- **NSML GPU 지원**
  - Tesla V100-SXM2-32GB 1개
- **<u>외부 데이터 및 사전 학습 모델 사용 불가</u>**

## 문제 2 **[화자인식 Dataset 설명]**

- 매칭된 두 개의 음성파일을 읽어 같은 발화자인지 다른 발화자인지 추론

  |전체 크기|파일수|NSML 데이터셋 이름|
  |----|------|---|
  |11.39 GB|train_data(63,782) / test_data(3,254)|fianl_speaker|

### Train Dataset

- `root_path/train/train_data/wav/` (63,782개의 wav 파일 *확장자 없음)

  ```
  idx000001
  idx000002
  idx000003
  idx000004
  ...
  idx063779
  idx063780
  idx063781
  idx063782
  ```

### Train Info

- `root_path/train/train_data/train_info`
- `train_info` (DataFrame 형식, 63,782 rows)
	- `columns` - [“file_name”, “speaker”]
	- `file_name` – wav 폴더에 존재하는 임의의 wav파일명 (ex. idx000001)
	- `speaker` – 각 wav파일에 매칭되는 특정 화자(ex. S000013_1, s000181_1 *소문자 대문자 섞여있음)
- 예를들어 idx000001 파일의 speaker값이 S000013_1이고 idx000002 파일의 speaker값이 S000013_1이면 두 음성은 같은 발화자
Test Dataset
- `root_path/test/test_data/wav/` (3,254개의 wav파일 *확장자 없음)


### Test Dataset

- `root_path/test/test_data/wav/` (1,221개의 wav 파일 \*확장자 없는 레이블 형태)

  ```
  idx000001
  idx000002
  idx000003
  idx000004
  ...
  idx003251
  idx003252
  idx003253
  idx003254
  ```
- `root_path/test/test_data/test_data`
- test_data (DataFrame 형식, 32,391rows)
	- `columns` - [“file_name”, “file_name_”]
	- `file_name` - test wav 폴더에 존재하는 임의의 wav파일명(ex. idx000001)
	- `file_name_` - test wav 폴더에 존재하는 임의의 wav파일명(ex. idx000002)
	- `test_data`에 label column을 추가하여 추론값을 대입 (최종 제출 format)
