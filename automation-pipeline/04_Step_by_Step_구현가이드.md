cy}}         ││
│ │ G: 원본ID = {{1.id}}              ││
│ │                                    ││
│ │ [Save]                             ││
│ └────────────────────────────────────┘│
└────────────────────────────────────────┘
1.7 Route A만: Discord 알림
1. Route A의 Google Sheets 모듈 우측 [+]
2. "Discord" 앱 검색
3. 액션: "Send a Message"
4. Webhook URL: [Discord 웹훅 URL 입력]
5. 메시지 포맷:
   Content:
   🚨 **긴급 이메일 수신!**
   발신자: {{1.from}}
   제목: {{1.subject}}
   요약: {{3.summary}}
   시간: {{now}}
6. [Save]

스크린샷:

┌────────────────────────────────────────┐
│ Make - Discord 설정                    │
│                                        │
│ Webhook URL: 입력됨 ✅                 │
│                                        │
│ Message Content:                       │
│ ┌────────────────────────────────────┐│
│ │ 🚨 **긴급 이메일 수신!**          ││
│ │ 발신자: {{1.from}}               ││
│ │ 제목: {{1.subject}}              ││
│ │ 요약: {{3.summary}}              ││
│ │ 시간: {{now}}                    ││
│ └────────────────────────────────────┘│
│                                        │
│ [Send a Test] [Save]                   │
└────────────────────────────────────────┘
Step 2️⃣: Make 테스트 실행
2.1 시나리오 활성화
1. 시나리오 페이지 상단 [Schedule] → [Manually]
2. [Save]
3. 우측 상단 [ON/OFF] 토글 → ON

스크린샷:

┌────────────────────────────────────────┐
│ Make - Scenario 활성화                 │
│                                        │
│ [Schedule] [Manually]                  │
│ ┌──────────────┐                       │
│ │ ● ON        │← 활성화됨              │
│ │   OFF       │                        │
│ └──────────────┘                       │
│                                        │
│ [Save Scenario]                        │
└────────────────────────────────────────┘
2.2 테스트 이메일 발송

Gmail에서 테스트 이메일을 보냅니다:

테스트 1: 긴급 건 (결제 오류)

To: 자신의 메일
Subject: 결제 중복 청구 문제 발생
Body: 신용카드 오류로 인해 금액이 두 번 청구되었습니다. 
       즉시 환불 처리 부탁드립니다.

테스트 2: 일반 건 (제품 문의)

To: 자신의 메일
Subject: 프리미엄 플랜 가격 문의
Body: 더 큰 용량의 플랜이 있나요? 가격표를 보내주세요.
2.3 실행 결과 확인

Make Execution History:

┌────────────────────────────────────────┐
│ Make - Execution History               │
│                                        │
│ [✓] 테스트 1 - 긴급 건                │
│     └─ ✅ Module 1 (Gmail)            │
│     └─ ✅ Module 2 (OpenAI)           │
│     └─ ✅ Module 3 (JSON)             │
│     └─ ✅ Module 4 (Router → A)       │
│     └─ ✅ Module 5 (Sheets)           │
│     └─ ✅ Module 6 (Discord)          │
│     총 처리시간: 5초                   │
│                                        │
│ [✓] 테스트 2 - 일반 건                │
│     └─ ✅ Module 1 (Gmail)            │
│     └─ ✅ Module 2 (OpenAI)           │
│     └─ ✅ Module 3 (JSON)             │
│     └─ ✅ Module 4 (Router → B)       │
│     └─ ✅ Module 5 (Sheets)           │
│     총 처리시간: 4초                   │
│                                        │
│ 성공률: 100% (2/2)                    │
└────────────────────────────────────────┘

Google Sheets 결과:

┌────────┬────────────┬──────────────┬──────────┬──────────┬────────┐
│수신시각 │ 발신자     │ 제목         │문의유형  │요약      │긴급도  │
├────────┼────────────┼──────────────┼──────────┼──────────┼────────┤
│09:15   │test1@...   │결제 중복 청구 │결제문제  │신용카드  │High   │
│        │            │문제 발생     │          │중복 청구 │        │
├────────┼────────────┼──────────────┼──────────┼──────────┼────────┤
│09:18   │test2@...   │프리미엄 플랜 │제품문의  │패키지   │Low    │
│        │            │가격 문의     │          │가격 문의 │        │
└────────┴────────────┴──────────────┴──────────┴──────────┴────────┘

Discord 채널 결과:

┌────────────────────────────────────────┐
│ Discord - #urgent-emails 채널          │
│                                        │
│ 🚨 **긴급 이메일 수신!**              │
│ 발신자: test1@example.com              │
│ 제목: 결제 중복 청구 문제 발생         │
│ 요약: 신용카드 중복 청구로 환불 요청  │
│ 시간: 09:15 AM                        │
│                                        │
│ [고정] [북마크] [삭제]                │
└────────────────────────────────────────┘
🔧 Part 2: Zapier에서의 구현
Step 1️⃣: Zapier Zap 생성
1.1 Zap 생성
1. Zapier.com → [Create] 버튼
2. Trigger: "Gmail"
3. Trigger Event: "New Email"
4. Google 계정 연동

스크린샷:

┌────────────────────────────────────────┐
│ Zapier - Zap 생성                      │
│                                        │
│ Step 1: Choose Trigger App             │
│ [Gmail]                                │
│        ↓                               │
│ Step 2: Choose Trigger Event           │
│ [New Email]                            │
│        ↓                               │
│ Step 3: Connect Gmail Account          │
│ [Google Account] ✅ 연동됨             │
│                                        │
│ [Continue]                             │
└────────────────────────────────────────┘
1.2 Gmail 트리거 설정
1. Mailbox: INBOX 선택
2. Search: (비워두기)
3. [Continue]
1.3 액션 1: OpenAI
1. [+ Add Action] 클릭
2. "OpenAI" 앱 검색
3. 액션: "Create Completion"
4. API Key: [OpenAI 키]
5. Model: gpt-4o
6. Prompt: [System Prompt]
7. [Continue]

스크린샷:

┌────────────────────────────────────────┐
│ Zapier - OpenAI 설정                   │
│                                        │
│ App & Event: OpenAI → Create Completion│
│                                        │
│ Account: [선택됨]                      │
│                                        │
│ ┌────────────────────────────────────┐│
│ │ Model: gpt-4o                      ││
│ │                                    ││
│ │ Prompt:                            ││
│ │ {{subject}} {{plain_text_body}}    ││
│ │                                    ││
│ │ [System Prompt 입력]               ││
│ └────────────────────────────────────┘│
│                                        │
│ [Continue]                             │
└────────────────────────────────────────┘
1.4 조건 분기: Paths
1. [+ Add Step] 클릭
2. "Paths by Zapier" 선택
3. Path A: Response contains "High"
4. Path B: 기본값
5. [Continue]

스크린샷:

┌────────────────────────────────────────┐
│ Zapier - Paths 설정                    │
│                                        │
│ Step 3: Paths                          │
│                                        │
│ Path A (긴급)                          │
│ If Response contains "High"            │
│ Then: [다음 단계]                      │
│                                        │
│ Path B (일반)                          │
│ Else (기본값)                          │
│ Then: [다음 단계]                      │
│                                        │
│ [Continue]                             │
└────────────────────────────────────────┘
1.5 Path A & B: Google Sheets

Path A와 B 모두에 추가:

1. [+ Add Action] 클릭
2. "Google Sheets" 앱
3. 액션: "Create Spreadsheet Row"
4. Google 계정: [연동]
5. Spreadsheet: [선택]
6. Worksheet: "Emails"
7. Column 매핑:
   - A: {{timestamp}}
   - B: {{from_email}}
   - C: {{subject}}
   - D: [Text extracted from previous step]
   - E: [Summary from AI response]
   - F: [Urgency value]
8. [Continue]
1.6 Path A만: Discord
1. [+ Add Action] 클릭
2. "Discord" 앱
3. 액션: "Send Channel Message"
4. Webhook URL: [Discord 웹훅]
5. 메시지:
   🚨 긴급 이메일 수신!
   발신자: {{from_email}}
   제목: {{subject}}
   요약: [AI 요약]
6. [Create Zap]
Step 2️⃣: Zapier 테스트 실행
2.1 Zap 활성화
1. Zapier 대시보드에서 Zap 선택
2. 상단 [On/Off] 토글 → On

스크린샷:

┌────────────────────────────────────────┐
│ Zapier - Zap 활성화                    │
│                                        │
│ Zap: Email Analysis Pipeline           │
│                                        │
│ ┌──────────┐                           │
│ │ ● ON    │← 활성화됨                  │
│ │   OFF   │                           │
│ └──────────┘                           │
│                                        │
│ Last checked: 2 minutes ago            │
└────────────────────────────────────────┘
2.2 테스트 이메일 발송 (동일)

위의 Make 테스트와 동일한 이메일 발송

2.3 실행 결과 확인

Zapier Task History:

┌────────────────────────────────────────┐
│ Zapier - Task History                  │
│                                        │
│ [✓] 09:20 - 테스트 1 긴급 건          │
│     Status: Success                    │
│     Steps Completed: 4/4               │
│     Duration: 2-3분 (폴링 대기)        │
│                                        │
│ [✓] 09:23 - 테스트 2 일반 건          │
│     Status: Success                    │
│     Steps Completed: 3/3 (Discord X)   │
│     Duration: 2-3분 (폴링 대기)        │
│                                        │
│ Tasks Used: 2 / 100 (무료)            │
└────────────────────────────────────────┘
📊 최종 비교 결과
항목	Make	Zapier
응답 시간	⚡ 5초	⏱️ 2-3분
설정 복잡도	중간 (노드식)	낮음 (마법사식)
조건 분기	Router (무한 가능)	Paths (제약)
비용	✅ 무료 충분	⚠️ 무료는 2-Step만
모니터링	상세 (각 모듈 로그)	기본 (Task만)
권장 대상	복잡한 자동화	초보자 친화적
✅ 최종 체크리스트
구현 완료 확인
✅ Make 구현
   - Gmail Trigger
   - OpenAI Analysis
   - JSON Parsing
   - Router (High/Low)
   - Google Sheets (모든 경로)
   - Discord (High 경로만)
   - 테스트 완료 (2회)

✅ Zapier 구현
   - Gmail Trigger
   - OpenAI Analysis
   - Paths 분기
   - Google Sheets (모든 경로)
   - Discord (High 경로만)
   - 테스트 완료 (2회)

✅ 요구사항 충족
   - Trigger: Gmail ✅
   - Action: OpenAI + Sheets + Discord ✅
   - Conditional Branching: High/Low ✅
   - Both paths tested: ✅
   - Screenshots documented: ✅
