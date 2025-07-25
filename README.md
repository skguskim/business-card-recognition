# 📇 Business Card Recognition (명함 인식 알고리즘 프로젝트)

2025년 1학기 서울과학기술대학교 인공지능응용학과 **영상처리** 과목의 최종 프로젝트로 진행한 명함 인식 알고리즘입니다.

이 프로젝트는 명함이 다양한 배경(단색 배경, 복잡한 패턴, 유사 색상 배경, 부분 가려짐 등)에 놓였을 때도 정확하게 명함 영역을 검출하여 정면 이미지로 변환하는 것을 목표로 합니다.


## 🔖 프로젝트 개요
**과목**: 영상처리 (Digital Image Processing)

**기간**: 2025년 5월 ~ 2025년 6월

**팀원**: 김나현, 강준

## 🧩 구현 알고리즘 설명
### 1️⃣ 전처리 (Preprocessing)
- Grayscale 변환, CLAHE, Median Blur, Gaussian Blur, Bilateral Filter, Canny Edge Detector, Morphological Dilation 적용

### 2️⃣ Line Detection 기반 명함 검출
- 허프 변환, 사각형 후보 생성 및 최적 후보 선택 후 Perspective 변환 적용

### 3️⃣ Corner Detection 기반 명함 검출 (Contour 방식)
- Contour 및 Polygon Approximation 기반 검출, 예외상황 GrabCut 적용, 최적 후보 Perspective 변환 및 Otsu 이진화


## 🚧 예외 케이스 처리
- 특정 이미지(BC12~BC20)는 별도 알고리즘 및 튜닝으로 정확도 향상
- 개별 이미지 특성(가려짐, 유사 색상 배경, 복잡한 패턴)에 따라 별도 알고리즘과 하이퍼파라미터 튜닝 적용

| 예외 이미지 | 처리 방식 요약 |
|-------------|----------------|
| BC12        | Dilate 두 번 적용 후 HoughLinesP 기반 Affine 변환 |
| BC13        | HSV 필터링 및 Harris Corner 기반 Perspective Warp |
|BC14	      | Harris Corner Detection 및 Convex Hull 등 다중 방법 |
|BC15	      | HSV 컬러 필터링, Hough Line Threshold 조정 |
|BC16	      | Adaptive Threshold 및 Contour 기반 Approximation |
|BC17	      | 다양한 Harris Corner 임계값 시도 (최적 미도달) |
|BC18	      | 밝기 마스크 및 Gaussian Blur, HoughLinesP 활용 |
|BC19	      | Gaussian, Bilateral 및 EdgePreserving Filter 혼합 적용 |
|BC20	      | 손가락으로 가려진 영역 처리 및 Affine 변환 활용 |

## 📊 프로젝트 결과
- 총 21장 중 20장에 대해 성공적 명함 검출 및 변환 완료, 성능 및 연산 속도 개선

## 📖 참고문헌
- 신현섭 & 김차종 (2014). 모바일 환경에서의 명함 인식 성능 향상 연구. 한국정보통신학회 논문지, 18(2), 318-328.
- OpenCV ([GitHub](https://github.com/opencv/opencv/tree/4.x/modules/imgproc/src))


## 👥 팀원 역할 분담
| 이름   | 주요 담당 역할 |
|--------|----------------|
| 강준   | Line Detection 알고리즘, 이미지 필터링 및 Edge 검출, 사각형 미인식 문제 개선, 명암·휘도 조정 및 코드 통합 |
| 김나현 | Corner Detection 알고리즘, 예외 케이스 및 Occlusion 상황 처리, 컬러 필터링 및 하이퍼파라미터 튜닝 |

## 📜 라이선스
본 프로젝트는 MIT License를 따릅니다.
