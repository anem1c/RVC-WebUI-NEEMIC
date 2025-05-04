# RVC-WebUI-NEEMIC (맥OS 최적화)

Retrieval-based-Voice-Conversion-WebUI (RVC) - Mac 환경에서 쉽게 설치/실행할 수 있도록 정리한 버전입니다.

## 주요 특징
- MacOS (Apple Silicon, Intel) 환경에서 검증
- Gradio 3.50.2, pip 23.x, Python 3.9~3.10 권장
- 불필요한 패키지(aria2 등) 제거, 실제 설치된 requirements.txt 제공
- 한글 지원 및 UI 최적화

---

## 설치 방법 (Mac 기준)

### 1. Homebrew로 필수 시스템 패키지 설치
```bash
brew install ffmpeg aria2
```

### 2. 프로젝트 클론
```bash
git clone https://github.com/anem1c/RVC-WebUI-NEEMIC.git
cd RVC-WebUI-NEEMIC
```

### 3. Python 가상환경 생성 및 활성화
```bash
python3 -m venv venv
source venv/bin/activate
```

### 4. pip 다운그레이드 (중요!)
```bash
pip install pip==23.3.1
```

### 5. 의존성 설치
```bash
pip install -r requirements.txt
```

### 6. 환경 변수 설정
```bash
# .env 파일 생성
cat > .env << EOL
weight_root=assets/weights
weight_uvr5_root=assets/uvr5_weights
index_root=assets/weights
outside_index_root=assets/weights
EOL
```

### 7. 모델 다운로드
```bash
chmod +x tools/dlmodels.sh
./tools/dlmodels.sh
```

### 8. 실행
```bash
python infer-web.py
```

실행 후 웹 브라우저에서 [http://localhost:7860](http://localhost:7860) 접속

---

## 자주 발생하는 문제 & 해결법

### 1. 환경 변수 관련 오류
- **증상**: `TypeError: expected str, bytes or os.PathLike object, not NoneType`
- **해결**: `.env` 파일이 올바르게 생성되었는지 확인

### 2. 패키지 설치 오류
- **aria2 설치 에러**: requirements.txt에서 삭제됨. Homebrew로만 설치하세요.
- **omegaconf 설치 에러**: pip 24.x 이상에서 발생. 반드시 pip 23.x로 다운그레이드 후 설치.
- **Gradio 관련 에러**: 4.x 이상은 호환성 문제. 반드시 3.50.2 사용.

### 3. 실행 관련 오류
- **실행 경로**: 반드시 `RVC-WebUI-NEEMIC` 폴더에서 실행.
- **Python 버전**: 3.9~3.10 권장. 다른 버전에서는 호환성 문제 발생 가능.
- **MPS 관련 오류**: Apple Silicon Mac에서 발생할 수 있음. 자동으로 CPU 모드로 전환됨.

### 4. 모델 관련 오류
- **모델 다운로드 실패**: `tools/dlmodels.sh` 스크립트 재실행
- **모델 파일 누락**: `assets/weights` 폴더 확인

---

## 폴더 구조
```
RVC-WebUI-NEEMIC/
├── assets/
│   ├── weights/        # 모델 가중치 파일
│   ├── uvr5_weights/   # UVR5 모델 파일
│   └── ...
├── infer/             # 추론 관련 코드
├── tools/             # 유틸리티 스크립트
├── venv/              # Python 가상환경
├── .env               # 환경 변수 설정
├── requirements.txt   # 의존성 목록
└── infer-web.py       # 메인 실행 파일
```

---

## 참고
- 원본 프로젝트: [RVC-Project/Retrieval-based-Voice-Conversion-WebUI](https://github.com/RVC-Project/Retrieval-based-Voice-Conversion-WebUI)
- 본 저장소는 Mac 환경에서의 설치/실행 편의성을 위해 커스텀되었습니다.

---

## 라이선스
- MIT License
- 자세한 라이선스 정보는 [LICENSE](LICENSE) 파일 참조

---

문의/이슈는 GitHub Issue로 남겨주세요. 