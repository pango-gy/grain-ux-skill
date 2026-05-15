# grain — AI 에이전트용 UX 리뷰 스킬

> 사람이 실제로 생각하고, 읽고, 결정하고, 신뢰하고, 회복하는 방식에 맞춰 일합니다.

**언어:** [English](README.md) | [한국어](README.ko.md) | [日本語](README.ja.md) | [简体中文](README.zh-CN.md) | [Español](README.es.md)

[팡고지와이](https://pango-gy.com)가 관리합니다.

`grain`은 사용자에게 보이는 제품 결정을 리뷰하고 다듬기 위한 휴대 가능한 AI 에이전트 스킬입니다. 시각 테마, 컴포넌트 라이브러리, 디자인 시스템이 아닙니다. 플로우, 폼, 에러, AI 액션, 권한 요청, 버튼 라벨이 실제 사용자에게 불리하게 작동할 때 밀어붙이는 UX 판단 레이어입니다.

프론트엔드 빌더, 디자인 시스템 스킬, UI 키트, 제품 코드 리뷰와 함께 사용하세요. 그런 도구들이 에이전트가 인터페이스를 만들도록 돕는다면, `grain`은 그 인터페이스가 사용자의 노력, 주의, 접근성, 신뢰, 회복을 존중하는지 보게 합니다.

## 이름의 뜻

`grain`은 나뭇결처럼 재료가 가진 자연스러운 결이나 방향을 뜻합니다. 영어 표현 "with the grain"은 그 자연스러운 결을 거스르지 않고 따라간다는 의미입니다. 이 스킬은 사용자가 실제로 생각하고, 읽고, 결정하고, 신뢰하고, 실패에서 회복하는 방식에 맞춰 UX를 판단한다는 뜻에서 이 이름을 씁니다.

## 설치

```bash
npx skills add pango-gy/grain-ux-skill
```

기본적으로 `skills` CLI는 프로젝트 스킬을 `./.agents/skills/grain`에 설치합니다. 이 공유 디렉터리는 Codex와 Gemini CLI 같은 universal agent가 사용하는 프로젝트 단위 위치입니다. Claude Code처럼 전용 프로젝트 스킬 디렉터리가 있는 agent는 해당 디렉터리가 프로젝트에 있을 때 symlink나 copy를 받습니다.

지원되는 모든 agent 디렉터리에 실제 copy를 만들고 싶다면 다음 명령을 사용하세요.

```bash
npx skills add pango-gy/grain-ux-skill --agent '*' --skill '*' -y --copy
```

업데이트할 때는 add 명령을 다시 실행하면 됩니다.

삭제:

```bash
npx skills remove grain
```

이 명령은 설치된 skill 디렉터리를 제거합니다. 프로젝트에서 `skills-lock.json`을 사용한다면, CLI가 복원/업데이트용 source metadata를 남길 수 있으므로 삭제 후 해당 파일을 확인하세요.

## 언제 작동하나요

`grain`은 사용자에게 영향을 주는 결정에서 자동으로 작동합니다.

- UI 컴포넌트, 화면, 폼, 플로우를 작성, 리팩터링, 리뷰할 때
- 빈 상태, 로딩, 실패, 부분 성공, 오프라인, 권한 거부 상태를 설계하거나 비평할 때
- 카피, 라벨, 마이크로카피, 에러 메시지, 온보딩, 알림을 작성할 때
- 접근성, 키보드 동작, 포커스 순서, 터치 타깃, 모션, 반응형 동작을 검토할 때
- 폼, 임포트, 필터, 설정, 권한, 공유, 결제, AI 출력, 자동화를 설계할 때
- 스크린샷, 프로토타입, 대시보드, 내부 도구, 어드민 화면, SaaS 워크플로우를 리뷰할 때

백엔드 전용 로직, 인프라, 사용자에게 보이는 동작이 없는 작업에서는 조용해야 합니다.

## 무엇을 다루나요

일곱 가지 도메인을 하나의 목소리로 다룹니다.

- **사용자 플로우와 정보 구조** — 페이지보다 경로, 테이블보다 과업.
- **인지 부하와 단순함** — 클릭 수보다 결정 수를 줄입니다.
- **폼과 입력** — 모든 필드는 비용을 치르게 하며, 검증은 꾸짖는 대신 도와야 합니다.
- **접근성과 포용적 상호작용** — 키보드, 터치, 포커스, 모션, 대비, 뷰포트는 기본 UX입니다.
- **신뢰, 동의, 주체성** — 예상 못한 전송, 공유, 과금, 삭제, AI 커밋, 자동화를 막습니다.
- **에러, 엣지 케이스, 회복** — 빈/로딩/실패/오프라인 상태를 제품의 일부로 봅니다.
- **마이크로카피와 톤** — 버튼은 결과를 말하고, 에러는 사용자를 탓하지 않으며, 문장은 소리 내 읽을 수 있어야 합니다.

각 도메인의 자세한 기준은 [`skill/references/`](skill/references)에 있습니다. `SKILL.md`는 언제 어떤 reference를 읽을지 알려 주어 메인 스킬을 작게 유지합니다.

## 핵심 철학

`grain`은 먼저 이 법칙들을 적용합니다.

- 다음 행동을 명확하게 만든다.
- 화면보다 규칙을 먼저 단순하게 만든다.
- 노력을 요구하기 전에 가치를 먼저 보여준다.
- 사용자의 노력을 보존한다.
- 사용자를 놀라게 하지 않는다.
- 확인만 요구하지 말고 되돌릴 수 있게 한다.
- 접근성은 모드가 아니라 기본 UX로 다룬다.
- 실패 상태를 제품의 일부로 설계한다.

전체 법칙, 도메인 라우팅, 안티패턴은 [`skill/SKILL.md`](skill/SKILL.md)에 있습니다.

## 포지셔닝

`grain`은 companion skill로 가장 강합니다.

- **프론트엔드 빌더**와 함께 사용하면 코드가 랜딩되기 전에 UX 회귀를 잡습니다.
- **디자인 시스템**과 함께 사용하면 컴포넌트가 예쁘게만 쓰이는 것이 아니라 올바른 과업에 쓰이는지 확인합니다.
- **AI/자동화 도구 스킬**과 함께 사용하면 durable하거나 외부에 영향을 주는 액션 전에 preview, consent, status, history, explicit approval을 요구합니다.
- **제품 리뷰 워크플로우**와 함께 사용하면 모호한 피드백을 구체적인 법칙과 안티패턴으로 바꿉니다.

시각 아이덴티티를 만들거나, 브랜드 팔레트를 고르거나, 제품 리서치를 대체하지 않습니다. 에이전트가 코딩하거나 리뷰하면서 이미 내리는 결정에 재사용 가능한 UX 기준을 제공합니다.

## 예시 리뷰 프롬프트

```text
Use grain to review this checkout flow for trust, consent, and recovery.
```

```text
Use grain while refactoring this settings form. Preserve input and improve validation UX.
```

```text
Use grain to check whether this AI-generated email flow needs preview, edit, and approval states.
```

```text
Use grain to review this dashboard for cognitive load, accessibility, and empty states.
```

## 작성자

팡고지와이 CTO 유승재 ([pinkyooysj@pango-gy.com](mailto:pinkyooysj@pango-gy.com))

회사: [팡고지와이](https://pango-gy.com)

## 라이선스

[MIT](LICENSE). 사용하고, 포크하고, 자신의 목소리로 다시 써도 됩니다. 더 많은 제품이 UX를 일급 관심사로 다루는 것이 목적입니다.

## 계보

Donald Norman, Jakob Nielsen, Steve Krug, Bruce Tognazzini, Alan Cooper, Dan Saffer, Edward Tufte의 생각 위에 서 있습니다. 어떤 아이디어가 어디에서 왔는지는 [`skill/SKILL.md`](skill/SKILL.md)의 `Lineage` 섹션을 참고하세요.
