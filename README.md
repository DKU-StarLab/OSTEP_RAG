# OSTEP RAG 프로젝트

OSTEP (Operating Systems: Three Easy Pieces) PDF 문서를 RAG(Retrieval-Augmented Generation) 시스템으로 변환하는 프로젝트입니다.

## 📋 프로젝트 개요

이 프로젝트는 운영체제 교재인 OSTEP PDF를 분석하여 챕터별로 청킹하고, 임베딩을 생성한 후 벡터 데이터베이스에 저장하여 RAG 시스템을 구축합니다. 각 단계별로 실습 노트북을 제공하여 RAG 시스템의 전체 파이프라인을 학습할 수 있습니다.

## 🗂️ 프로젝트 구조

```
OSTEP_RAG/
├── chapter.2/                 # Chapter 2: 청킹 및 JSON 변환
│   ├── chunk_methods_examples.ipynb
│   └── ostep_chunk_to_json.ipynb
├── chapter.3/                 # Chapter 3: 임베딩 생성
│   ├── sentence_embeddings_examples.ipynb
│   └── ostep_chunk_embeddings.ipynb
├── chapter.4/                 # Chapter 4: FAISS 인덱싱
│   ├── hnsw_faiss_param_examples.ipynb
│   └── ostep_faiss_hnsw_index.ipynb
├── chapter.5/                 # Chapter 5: LLM 프롬프트 및 생성
│   ├── ollama_generation_examples.ipynb
│   └── ostep_llm_prompt.ipynb
├── chapter.6/                 # Chapter 6: RAG 통합
│   └── ostep_rag_integration.ipynb
├── chapter.7/                 # Chapter 7: 고급 기법
│   ├── ostep_contextual_chunk_headers.ipynb
│   ├── ostep_hyde.ipynb
│   ├── ostep_reranking.ipynb
│   ├── ostep_self_rag.ipynb
│   └── ostep_final_optimized.ipynb
└── data/                      # 생성된 데이터
    ├── chunk/                 # 청킹된 JSON 파일
    ├── documents/             # 원본 문서
    ├── index/                 # FAISS 인덱스 파일
    └── vector/                # 벡터 데이터
```

## 🚀 시작하기

### 필수 요구사항

- Google 계정 (Colab 접근용)
- OSTEP PDF 파일 (Google Drive에 업로드 필요)

### Colab 환경 설정

1. **Google Colab 접속**
   - [colab.research.google.com](https://colab.research.google.com) 접속
   - Google 계정으로 로그인

2. **프로젝트 노트북 열기**
   - `파일 → 노트북 열기 → GitHub` 탭에서 이 저장소 URL 입력
   - 또는 각 챕터 디렉토리의 `.ipynb` 파일을 직접 업로드

3. **Google Drive 마운트**
   각 노트북의 첫 셀에서 다음 코드를 실행하여 Google Drive를 마운트합니다:
   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```

4. **필요한 패키지 설치**
   각 노트북의 설정 셀에서 다음 패키지들을 설치합니다:
   ```python
   !pip install PyPDF2 sentence-transformers faiss-cpu numpy torch requests
   ```

5. **데이터 경로 설정**
   노트북 내 경로 변수를 Google Drive 경로에 맞게 수정합니다:
   ```python
   # 예시: Google Drive의 프로젝트 경로
   BASE_PATH = "/content/drive/MyDrive/OSTEP_RAG"
   ```

### 단계별 실습

각 챕터별 노트북을 순서대로 실행하여 RAG 시스템을 구축합니다:

1. **Chapter 2**: 청킹된 데이터를 JSON 형식으로 변환
2. **Chapter 3**: Sentence Transformers를 사용한 임베딩 생성
3. **Chapter 4**: FAISS HNSW 인덱스 구축
4. **Chapter 5**: Ollama를 사용한 LLM 프롬프트 및 생성
5. **Chapter 6**: 전체 RAG 파이프라인 통합
6. **Chapter 7**: 고급 기법 (HyDE, Reranking, Self-RAG 등)

> 💡 **팁**: Colab 사용법이 처음이라면 [Colab 사용 가이드](colab.md)를 먼저 참고하세요.

### 런타임 설정 (선택사항)

- **GPU 사용**: `런타임 → 런타임 유형 변경 → 하드웨어 가속기 → GPU` 선택
  - 임베딩 생성 및 FAISS 인덱싱 시 GPU를 사용하면 속도가 향상됩니다
  - GPU 사용 확인: `!nvidia-smi` 실행

- **런타임 관리**
  - 장시간 작업 시 주기적으로 저장: `파일 → 드라이브에 사본 저장`
  - 세션 만료 방지: 주기적으로 셀 실행
  - 메모리 초기화: `런타임 → 런타임 다시 시작`

## 📚 주요 기능

- **PDF 분석**: PyPDF2를 사용한 PDF 텍스트 추출 및 목차 파싱
- **스마트 청킹**: 문장 단위 분할 및 토큰 기반 청킹
- **임베딩 생성**: Sentence Transformers (`all-MiniLM-L6-v2`) 모델 사용
- **벡터 검색**: FAISS HNSW 인덱스를 통한 효율적인 유사도 검색
- **RAG 통합**: 검색 → 프롬프트 → 생성 파이프라인
- **고급 기법**: HyDE, Reranking, Self-RAG 등 최적화 기법


## 📖 참고 자료

- [Colab 사용 가이드](colab.md): Google Colab에서 노트북 실행하기
- OSTEP 공식 웹사이트: https://pages.cs.wisc.edu/~remzi/OSTEP/

## 🤝 기여

이슈나 개선 사항이 있으면 이슈를 등록하거나 Pull Request를 보내주세요.

## 📝 라이선스

이 프로젝트는 교육 목적으로 제작되었습니다. OSTEP 책의 저작권은 원저자에게 있습니다.

