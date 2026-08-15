# 📂 업무 자동화 프롬프트 패키지: 비즈니스 이메일 초안 작성 어시스턴트

본 저장소는 3종의 LLM 모델 비교 분석을 시작으로 비즈니스 이메일 작성 과업을 정교하게 제어하기 위한 프롬프트 엔지니어링 패키지(설계 문서, 프롬프트 v1/v2, 10-Turn 대화 로그 및 운영 전략)를 담고 있습니다.

---

## 📁 저장소 문서 구조

* **README.md (본 문서):** 프로젝트 개요 및 대화 실행 로그 (10-Turn Full Log)
* **[01_model_comparison_report.md](./01_model_comparison_report.md):** LLM 모델 비교·선정 보고서 (GPT-4o / Claude 3.5 Sonnet / Gemini 1.5 Pro)
* **[02_system_design.md](./02_system_design.md):** 시스템 설계 문서 (입력 템플릿, 프롬프트 v1/v2, Few-shot 3종, 환각 검증표)
* **[03_hallucination_and_operations.md](./03_hallucination_and_operations.md):** 환각 검증, 비용 제약 대응 및 운영 전략 (CI/CD, 세션 관리)
