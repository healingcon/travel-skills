# 여행 AI 스킬 4종 모음 (travel-skills)

여행 계획 세울 때 쓰기 좋은 AI 에이전트용 스킬 4종을 한곳에 모아 둔 저장소입니다.
각 스킬은 원본 GitHub 저장소의 내용을 **수정 없이 그대로**(`.git` 히스토리만 제외) 옮겨 왔습니다.

출처: X 게시물 — <https://x.com/BBBang9900/status/2124012432276533680> ("여행 갈 때 쓰기 좋은 AI 깃허브 스킬 4종")

## 구성

| 디렉터리 | 스킬 | 무엇을 해 주나 | 원본 | 라이선스 |
|---|---|---|---|---|
| [`travel-planner/`](travel-planner/) | Travel Planner (`travel-planner`) | 5개 전문 에이전트(일정·맛집·교통/숙소·안전/문화·예산)를 병렬로 돌려 출처가 붙은 여행 계획서를 만들어 줍니다. Claude Code용 오케스트레이터 스킬 + `/travel-planner` 커맨드. | [mistlemma/travel-planner](https://github.com/mistlemma/travel-planner) | MIT |
| [`openclaw-tour-planner/`](openclaw-tour-planner/) | OpenCLAW Tour Planner (`openclaw-tour-planner`) | OpenClaw 에이전트용 만능 여행 플래너. 일정·날씨(15일)·명소·예산을 무료 API(Wikivoyage, Nominatim, Visual Crossing)로 처리하며, TypeScript 소스와 데모 페이지가 함께 들어 있습니다. | [Asif2BD/openclaw.tours](https://github.com/Asif2BD/openclaw.tours) | MIT (SKILL.md 메타데이터 기준) |
| [`trip-plan/`](trip-plan/) | Trip Plan (`trip-plan`) | 나노뮤즈(nanoMuse) 기본 내장 스킬. 여행 날짜를 캘린더와 대조해 충돌을 알려 주고, 일정표·짐 싸기 체크리스트(HTML)·예산(CSV)을 워크스페이스에 만들어 줍니다. | [nano-muse/nanoMuse › nanomuse/skills/builtin/trip-plan](https://github.com/nano-muse/nanoMuse/tree/main/nanomuse/skills/builtin/trip-plan) | GPL-3.0 (원본 저장소 기준) |
| [`travel-assistant/`](travel-assistant/) | Travel Assistant (`travel-assistant`) | 여행지·기간·동행·취향·예산을 먼저 물어보고, 일정/항공·숙소 전략/입국 요건(비자·백신·ETIAS)/예산을 정리해 줍니다. 결과물 형식(웹앱·PDF·엑셀)을 먼저 고르게 하는 것이 특징입니다. | [clawdsolana/openclawd › secondary_skills/travel-assistant](https://github.com/clawdsolana/openclawd/tree/HEAD/secondary_skills/travel-assistant) | CC BY-NC 4.0 (© Replit, Inc.) |

## 디렉터리 구성

```
travel-skills/
├── README.md
├── travel-planner/                  # mistlemma/travel-planner 전체
│   ├── SKILL.md                     #   오케스트레이터 스킬 정의
│   ├── README.md · EXAMPLES.md
│   ├── commands/travel-planner.md   #   /travel-planner 슬래시 커맨드
│   ├── skills/                      #   하위 스킬 5종
│   │   ├── trip-architect/          #     일정·명소·동선
│   │   ├── food-explorer/           #     현지 음식·식당
│   │   ├── logistics-planner/       #     교통·주차·숙소
│   │   ├── local-intel/             #     안전·사기·날씨·문화
│   │   └── budget-calculator/       #     비용 집계·예산
│   └── settings.local.json · LICENSE
├── openclaw-tour-planner/           # Asif2BD/openclaw.tours 전체
│   ├── SKILL.md                     #   스킬 정의(명령: plan/weather/budget/attractions/guide)
│   ├── src/                         #   TypeScript 구현
│   │   ├── apis/                    #     wikivoyage · nominatim · weather
│   │   └── planners/                #     itinerary · budget
│   ├── index.html                   #   소개 페이지
│   ├── package.json · tsconfig.json
│   └── ANALYSIS.md · SECURITY.md · .clawhubsafe
├── trip-plan/                       # nanoMuse 내장 trip-plan 스킬
│   └── SKILL.md
└── travel-assistant/                # openclawd의 travel-assistant 스킬
    ├── SKILL.md
    └── LICENSE.txt                  #   원본 secondary_skills/LICENSE.txt
```

## 어떻게 쓰나

- **travel-planner** — Claude Code에 `travel-planner/` 폴더를 스킬로 두고(`SKILL.md` + `skills/`, `commands/`), "도쿄 3박 4일 계획 짜 줘"처럼 요청합니다. 결과는 `TRAVEL/[여행지]/` 아래 마크다운 파일들로 나옵니다.
- **openclaw-tour-planner** — OpenClaw 에이전트에 설치하거나(`openclaw skills install openclaw-tour-planner`), `npm install && npm run build`로 직접 빌드해 씁니다. 핵심 기능은 API 키 없이 동작합니다.
- **trip-plan** — 나노뮤즈 스타일 에이전트용. `SKILL.md` 하나짜리 스킬로, `web_search`·`calendar`·`ask_user` 같은 도구가 있는 에이전트에 넣으면 됩니다.
- **travel-assistant** — OpenClawd/Replit 계열 에이전트용. 원본은 OpenClawd 오퍼레이터 덱의 일부로 쓰이도록 쓰여 있습니다.

## 라이선스와 출처

이 저장소는 원본들을 모아 두는 곳이며, **각 디렉터리의 권리는 원저작자에게 있습니다.** 재사용 시 해당 디렉터리의 라이선스를 따라 주세요.

- `travel-planner/` — MIT License, © 2026 Mingzhi Wang ([LICENSE](travel-planner/LICENSE))
- `openclaw-tour-planner/` — MIT, © Asif2BD (원본 `SKILL.md` 메타데이터에 명시)
- `trip-plan/` — 원본 저장소 nanoMuse의 GPL-3.0 적용, © nanoMuse
- `travel-assistant/` — © 2026 Replit, Inc. Replit 플랫폼 밖에서는 **CC BY-NC 4.0**(저작자 표시 · 비영리). 상업적 이용은 별도 라이선스 필요 ([LICENSE.txt](travel-assistant/LICENSE.txt))

원본 저장소의 이슈·업데이트는 위 표의 링크를 참고하세요.
