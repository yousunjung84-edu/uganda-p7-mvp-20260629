# Uganda PPT Pipeline Estimate — 2026-06-29

## 기준 수량

- Canonical lessons: 1,800
- Packs: 30
- Editable PPT slides: 14,400
- Visual insert / infographic image prompts: 16,200
- Pack split: grade × term × subject
- Current mode: editable_hybrid

## 파이프라인 순서

1. Source ingest: P6/P7 txt 교재, NotebookLM-Slide Prompt.html, Uganda design guide 수집.
2. Lesson catalog: 표준 레슨 목록 생성, 중복 suffix 파일 제외.
3. Pack split: grade × term × subject 기준 30개 pack 생성.
4. Prompt queue: 각 슬라이드/인포그래픽을 visual_insert 프롬프트로 생성.
5. Image generation: 이미지 모델은 삽화만 생성. 텍스트/제목/표/카드/fake text 금지.
6. Editable PPT render: 이미지는 picture object로 삽입, 수업 구조는 editable PPT shapes/text로 생성.
7. PDF export: 확인용 PDF로 정렬/칸줄/화면 품질 검수.
8. QA gate: 슬라이드 수, 이미지 panel, editable text layer, 과목별 frame, teacher note 확인.
9. Pack ZIP: PPTX, PDF, images, manifest, QA report 묶음.
10. Publish: GitHub Pages와 release asset에 pack 단위 게시.

## 권장 실행 단위

1 pack = 약 60 lessons = 480 editable PPT slides + 540 generated image assets.

## 시간 추정

### Ready-go planning only
- 전체: 5–15분
- 설명: 파일 스캔, catalog, pack manifest, prompt queue 생성만 수행.

### Pack 1개 실제 제작
- 이미지 생성: 약 3–9시간
- PPT/PDF 렌더링: 약 10–40분
- 자동 QA: 약 10–30분
- 사람 QA/수정 루프: 약 1–3시간
- 합계: pack당 약 5–13시간

### 전체 30 packs 실제 제작

순차 실행:
- 약 150–390시간
- 즉 약 6–16일 연속 실행

병렬 실행:
- 3 workers: 약 2–6일
- 5 workers: 약 1.5–4일
- 10 workers: 약 1–2일 가능하나 이미지 API 제한, 실패 재시도, QA 병목 때문에 안정성 낮음.

권장 운영:
- 먼저 1 pack 샘플 완성
- 이후 3–5 workers 병렬
- pack별 QA 통과 후 게시

## 토큰 / 호출량 추정

### Image generation 호출
- 이미지 자산 수: 16,200 calls
- 이미지 프롬프트 평균: 약 450–700 input tokens/call
- 총 이미지 프롬프트 입력: 약 7.3M–11.3M tokens 상당
- 실제 과금은 모델에 따라 token보다 image generation unit/credit 기준일 수 있음.

### PPT 생성 코드/렌더링
- 로컬 deterministic 코드 실행: LLM 토큰 거의 없음
- python-pptx/PDF export 자체는 토큰 사용 없음.

### 상세 교안 생성에 LLM을 붙일 경우
- lesson당 약 3K–8K input/output tokens 예상
- 1,800 lessons 전체: 약 5.4M–14.4M tokens 추가
- 더 정교한 과목별 pedagogy pass를 넣으면 약 15M–30M tokens까지 증가 가능.

## 현실적인 전체 예상

최소형 자동 생성:
- 16,200 image calls
- 약 7M–12M text-token 상당
- 시간: 병렬 3–5 workers 기준 약 2–5일

수업 품질 보강형:
- 16,200 image calls
- 약 15M–30M text-token 상당
- 시간: 병렬 3–5 workers 기준 약 4–8일

검수/수정 포함 납품형:
- 16,200 image calls
- 약 20M–40M text-token 상당
- 시간: 약 1–2주

## 권장 결론

바로 전체를 돌리지 말고 P7 Term 1 English 1 pack을 완성 품질 기준으로 잠근 뒤, 같은 템플릿/QA 기준으로 나머지를 3–5 workers 병렬 실행한다.
