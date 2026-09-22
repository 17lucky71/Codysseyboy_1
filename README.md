# 🚀 Codysseyboy_1 프로젝트 안내 (들어가며)

본 저장소는 **AI 기술을 활용한 업무 생산성 향상 및 멀티모달 콘텐츠 제작 프로젝트**를 종합적으로 정리한 공간입니다. 각 링크를 클릭하면 해당 문서 및 결과물로 바로 이동합니다.

---

## 📁 프로젝트 구조 및 주요 내용

### 1. 📧 [이메일 초안 작성 보조 시스템](./email-draft-assistant)
LLM 기반으로 효율적인 이메일 초안을 생성하는 시스템의 설계 및 운영 전략 문서입니다.
* [01_LLM 모델 비교·선정 보고서.md](./email-draft-assistant/01_LLM%20모델%20비교·선정%20보고서.md): 요구사항에 맞는 최적의 Large Language Model 비교분석
* [02_시스템 설계 문서.md](./email-draft-assistant/02_시스템%20설계%20문서.md): 시스템 아키텍처 및 프롬프트 구조 설계
* [03_환각 검증, 비용 제약 대응 및 운영 전략.md](./email-draft-assistant/03_환각%20검증,%20비용%20제약%20대응%20및%20운영%20전략.md): AI 환각(Hallucination) 최소화, 비용 최적화 및 안정적 운영 가이드

---

### 2. 🎬 [AI 기반 브랜드 광고 캠페인](./ai-brand-ad-campaign)
생성형 AI 및 멀티모달 도구를 활용한 브랜드 콘텐츠 제작 프로젝트입니다.
* [멀티모달 콘텐츠 제작.md](./ai-brand-ad-campaign/멀티모달%20콘텐츠%20제작.md): 멀티모달 AI 도구를 활용한 기획, 스토리보드 및 프롬프트 설계서
* [영상.Ad.mp4](./ai-brand-ad-campaign/영상.Ad.mp4): 생성형 AI로 제작된 최종 브랜드 광고 영상 결과물

---

### 3. ⚙️ [노코드 자동화 프로젝트 (Make vs Zapier 비교 + 자유 주제 자동화)](https://github.com/17lucky71/Codysseyboy_1/blob/main/automation-pipeline)
Google Forms 설문 응답을 점수 조건에 따라 분기하여 Google Sheets에 기록하고 Discord로 알림을 보내는 워크플로우를 **Make**와 **Zapier** 두 가지 노코드 도구로 각각 구현·비교한 [프로젝트 1]과, Make로 Gmail 문의 메일함을 자동 분류·기록·알림 처리하는 자유 주제 자동화를 구현한 [프로젝트 2]로 구성되어 있습니다.

* [00_Make_구현_및_테스트_결과.md](https://github.com/17lucky71/Codysseyboy_1/blob/main/automation-pipeline/00_Make_%EA%B5%AC%ED%98%84_%EB%B0%8F_%ED%85%8C%EC%8A%A4%ED%8A%B8_%EA%B2%B0%EA%B3%BC.md): [프로젝트 1] Make.com으로 구현한 Google Forms → 조건 분기(Router) → Sheets/Discord 자동화 및 실시간 자동 실행 검증 결과
* [01_자동화_도구_비교_보고서.md](https://github.com/17lucky71/Codysseyboy_1/blob/main/automation-pipeline/01_%EC%9E%90%EB%8F%99%ED%99%94_%EB%8F%84%EA%B5%AC_%EB%B9%84%EA%B5%90_%EB%B3%B4%EA%B3%A0%EC%84%9C.md): [프로젝트 1] Make와 Zapier를 직접 비교한 분석 보고서
* [02_Zapier_구현_및_테스트_결과.md](https://github.com/17lucky71/Codysseyboy_1/blob/main/automation-pipeline/02_Zapier_%EA%B5%AC%ED%98%84_%EB%B0%8F_%ED%85%8C%EC%8A%A4%ED%8A%B8_%EA%B2%B0%EA%B3%BC.md): [프로젝트 1] 동일한 워크플로우를 Zapier(Paths)로 구현하고 테스트한 결과, 무료 플랜 제약사항 비교
* [03_Project2_자유주제_자동화_구현.md](https://github.com/17lucky71/Codysseyboy_1/blob/main/automation-pipeline/03_Project2_%EC%9E%90%EC%9C%A0%EC%A3%BC%EC%A0%9C_%EC%9E%90%EB%8F%99%ED%99%94_%EA%B5%AC%ED%98%84.md): [프로젝트 2] Gmail 문의 메일함을 Make로 자동 분류·기록·알림 처리하는 자유 주제 자동화 구현 및 자동 실행 검증 결과

---

### 💡 기술 스택 및 활용 도구
* LLM & Text Generation: OpenAI GPT-4o / Claude
* Multimodal & Video: Generative AI Tools
* No-Code & Automation: Make, Zapier, Discord Webhooks, Google Sheets
* Documentation: Markdown, GitHub
