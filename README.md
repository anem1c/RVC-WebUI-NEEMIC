# RVC-WebUI-NEEMIC (맥OS 최적화)

Retrieval-based-Voice-Conversion-WebUI (RVC) - Mac 환경에서 쉽게 설치/실행할 수 있도록 정리한 버전입니다.

## 주요 특징
- MacOS (Apple Silicon, Intel) 환경에서 검증
- Gradio 3.50.2, pip 23.x, Python 3.9~3.10 권장
- 불필요한 패키지(aria2 등) 제거, 실제 설치된 requirements.txt 제공

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

### 6. 실행
```bash
python infer-web.py
```

실행 후 웹 브라우저에서 [http://localhost:7860](http://localhost:7860) 접속

---

## 자주 발생하는 문제 & 해결법

- **aria2 설치 에러**: requirements.txt에서 삭제됨. Homebrew로만 설치하세요.
- **omegaconf 설치 에러**: pip 24.x 이상에서 발생. 반드시 pip 23.x로 다운그레이드 후 설치.
- **Gradio 관련 에러**: 4.x 이상은 호환성 문제. 반드시 3.50.2 사용.
- **실행 경로**: 반드시 `Retrieval-based-Voice-Conversion-WebUI` 폴더에서 실행.

---

## 참고
- 원본 프로젝트: [RVC-Project/Retrieval-based-Voice-Conversion-WebUI](https://github.com/RVC-Project/Retrieval-based-Voice-Conversion-WebUI)
- 본 저장소는 Mac 환경에서의 설치/실행 편의성을 위해 커스텀되었습니다.

---

문의/이슈는 GitHub Issue로 남겨주세요. 