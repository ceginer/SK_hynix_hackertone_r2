# 현재 프로젝트에서 Codex 스킬 사용하기

확인일: 2026-10-31 · 대상: 이 폴더에서 사용하는 Codex

이 문서는 Karpathy Guidelines, Superpowers, Ponytail의 차이와 사용법을 설명한다. 안내서만 작성했으며, 스킬 설치나 설정 변경은 수행하지 않았다.

## 1. 세 가지의 역할

| 이름 | 주요 역할 | 어울리는 상황 |
| --- | --- | --- |
| Karpathy Guidelines | 가정을 밝히고, 단순하게 구현하고, 필요한 부분만 바꾸고, 결과를 검증하도록 하는 원칙 | 일상적인 구현·수정·리뷰의 기본 규칙 |
| Superpowers | 설계부터 계획·구현·테스트·리뷰까지 이어지는 개발 절차와 스킬 묶음 | 요구사항이 모호하거나 여러 단계가 필요한 기능 |
| Ponytail | 요구를 완전히 해결하는 가장 작은 변경을 찾는 작업 방식 | 과도한 설계·추상화·불필요한 코드 추가를 줄이고 싶은 작업 |

함께 쓴다면 **Karpathy로 기본 원칙을 정하고, 큰 작업의 절차는 Superpowers로 진행하고, 구현 범위는 Ponytail로 줄이는 조합**을 권한다. 이는 이 문서의 활용 제안이며 세 프로젝트의 공식 통합 설정은 아니다.

## 2. 현재 확인된 상태

| 항목 | 이번 세션에서 확인한 내용 |
| --- | --- |
| Ponytail | 현재 세션의 사용 가능 스킬 목록에 포함되어 있고, 로컬 플러그인 캐시 버전은 5.3.3이다. |
| Superpowers | 현재 세션의 사용 가능 스킬 목록에서 확인되지 않았다. |
| Karpathy Guidelines | 별도 스킬은 현재 세션 목록에서 확인되지 않았다. 다만 사용자가 대화에 제공한 AGENTS.md 지침에 동일한 네 가지 핵심 원칙이 들어 있다. |
| 프로젝트 파일 | 조사 시작 시 프로젝트에는 README.md와 .git이 있었으며, 프로젝트 자체의 AGENTS.md와 .agents/skills는 확인되지 않았다. |

대화로 전달한 AGENTS.md 지침은 이번 작업에 적용된다. 다음 접속에도 프로젝트 규칙으로 적용하려면 루트 AGENTS.md에 저장해 두는 방법이 있다. 이 안내서 자체가 AGENTS.md나 설치된 스킬로 자동 등록되는 것은 아니다.

현재 세션 목록에 없다는 사실만으로 컴퓨터 전체에 설치되지 않았다고 단정하지 않는다. 다른 Codex 클라이언트나 새 세션의 상태는 다시 확인해야 한다.

## 3. Codex가 스킬을 사용하는 방식

스킬은 `SKILL.md`를 포함하는 폴더다. Codex는 먼저 이름과 설명을 보고, 사용할 때 상세 지침을 읽는다. 요청과 설명이 맞으면 자동 선택할 수 있고, 직접 이름을 지정할 수도 있다.

- Codex CLI·IDE 확장: `/skills` 또는 `$`로 사용 가능한 스킬을 선택한다.
- 프로젝트에서 공유할 로컬 스킬: `.agents/skills/<스킬명>/SKILL.md`
- 사용자 개인의 여러 프로젝트에서 사용할 로컬 스킬: `~/.agents/skills/<스킬명>/SKILL.md`
- Windows에서 `~`는 사용자 홈 폴더를 뜻한다. 이 환경에서는 `C:\Users\bw`다.
- 새 스킬이 보이지 않으면 Codex를 재시작한 뒤 다시 확인한다.

플러그인은 여러 스킬이나 도구를 묶어 배포할 수 있다. 플러그인 캐시를 직접 편집하기보다 원본 프로젝트의 설치 방법을 따른다. [OpenAI 공식 스킬 문서](https://learn.chatgpt.com/docs/build-skills)

## 4. Karpathy Guidelines: 코딩의 기본 원칙

여기서 “안드레 카파시 skills”는 [andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills)를 뜻하는 것으로 해석했다. Karpathy의 관찰에서 영감을 받아 만든 커뮤니티 프로젝트이며, Karpathy 본인이 공식 배포한 제품으로 표현해서는 안 된다. 이전 `forrestchang/andrej-karpathy-skills` 주소는 조사 시 현재 저장소로 연결되었다.

실제 스킬 이름은 `karpathy-guidelines`다. 핵심은 다음 네 가지다.

1. 구현 전에 가정·모호함·대안을 드러낸다.
2. 요청을 해결하는 최소한의 코드만 작성한다.
3. 관련 있는 부분만 변경하고 기존 스타일을 따른다.
4. 성공 기준을 정하고 검증이 끝날 때까지 진행한다.

사용자가 제공한 AGENTS.md도 이 네 원칙을 담고 있다. 같은 내용을 중복 설치하기 전에, 항상 적용할 프로젝트 규칙으로 둘지 선택적으로 호출할 스킬로 둘지 정하면 된다. [원본 SKILL.md](https://github.com/multica-ai/andrej-karpathy-skills/blob/main/skills/karpathy-guidelines/SKILL.md)

별도 설치가 필요하면 Codex에 다음과 같이 요청할 수 있다. 아래는 **설치 요청 예시**이며, 이 문서 작성 중 실행한 내용이 아니다.

```text
$skill-installer
https://github.com/multica-ai/andrej-karpathy-skills 저장소의
skills/karpathy-guidelines 스킬을 설치해줘.
```

설치 후 목록에 나타나면 다음처럼 사용한다.

```text
$karpathy-guidelines
이 버그를 수정해줘. 먼저 원인과 가정을 설명하고,
관련 파일만 최소 변경한 뒤 재현 방법으로 검증해줘.
```

## 5. Superpowers: 개발 절차를 체계화하는 스킬 묶음

사용자가 말한 “superpower”는 [obra/superpowers](https://github.com/obra/superpowers)로 해석했다. 하나의 코딩 명령보다, 설계 합의 → 구현 계획 → 테스트와 구현 → 리뷰 → 완료 검증을 돕는 개발 방법론에 가깝다.

대표 스킬에는 `brainstorming`, `writing-plans`, `test-driven-development`, `systematic-debugging`, `requesting-code-review`, `verification-before-completion` 등이 있다. 서브에이전트를 활용하는 개발 절차도 포함한다. 실제 선택 가능한 이름과 접두사는 설치 후 목록에서 확인한다.

### 설치 안내

조사 시 원본 README의 Codex 안내는 다음과 같다.

- Codex 앱: 사이드바 `Plugins` → `Coding`의 `Superpowers` → `+`
- Codex CLI: `/plugins` → `superpowers` 검색 → `Install Plugin`

이전 블로그의 수동 링크·부트스트랩 명령을 그대로 복사하기보다 [현재 원본 설치 안내](https://github.com/obra/superpowers#installation)를 따른다. 위 화면은 원본 문서 기준이며, 이 컴퓨터에서 설치 화면을 직접 실행해 검증한 것은 아니다.

### 사용 예시

설치와 사용 가능 여부를 확인한 뒤 자연어로 요청할 수 있다.

```text
Superpowers로 이 기능을 진행해줘.
먼저 brainstorming으로 요구사항과 설계를 정리하고,
설계 합의 후 writing-plans로 검증 가능한 구현 계획을 작성해줘.
구현 후에는 리뷰와 verification-before-completion으로 결과를 확인해줘.
```

작은 문구 수정에도 전체 개발 절차를 적용할 필요는 없다. 이 문서에서는 여러 파일이나 설계 결정이 얽힌 작업에 활용하는 것을 권한다.

## 6. Ponytail: 최소 변경으로 끝까지 해결하기

[Ponytail](https://github.com/DietrichGebert/ponytail)은 기존 코드·표준 라이브러리·이미 설치된 의존성을 우선 살피고, 불필요한 기능과 추상화를 줄이는 방식이다. 필요한 검증과 보안까지 생략하는 모드는 아니다.

현재 설치된 5.3.3의 안내 기준 레벨은 다음과 같다.

| 레벨 | 의미 |
| --- | --- |
| `lite` | 요청대로 구현하되 더 작은 대안이 있으면 짧게 알려준다. |
| `full` | 요구를 완전히 해결하는 최소 변경을 적용한다. 기본 레벨이다. |
| `ultra` | 구현의 필요성과 범위부터 더 적극적으로 따져 본다. |

현재 세션의 Codex용 호출 예시는 다음과 같다. `/ponytail`은 다른 도구의 명령일 수 있으므로 그대로 가정하지 않는다.

```text
$ponytail:ponytail full
이 버그를 최소 변경으로 수정하고 필요한 검증까지 해줘.
```

```text
$ponytail:ponytail-review
현재 변경분과 연결된 코드를 검토하고, 문제를 중요도순으로 설명해줘.
```

| 스킬 | 용도 |
| --- | --- |
| `$ponytail:ponytail` | 구현·수정·리팩터링의 작업 방식 지정 |
| `$ponytail:ponytail-review` | 변경분과 연결된 코드 리뷰, 코드 수정 없음 |
| `$ponytail:ponytail-audit` | 저장소 전체 품질 감사, 코드 수정 없음 |
| `$ponytail:ponytail-debt` | `shortcut:` 및 이전 `ponytail:` 주석으로 남긴 부채 확인 |
| `$ponytail:ponytail-gain` | 공개 벤치마크의 절감 효과 안내. 현재 프로젝트의 실측 결과는 아님 |
| `$ponytail:ponytail-help` | 레벨과 사용법 확인 |

자연어로 “ponytail full로 진행해줘”라고 요청해도 된다. 레벨 변경과 종료는 설치된 버전의 help 안내를 따른다.

### 다른 환경에서 새로 설치할 경우

이 세션에서는 이미 사용 가능하므로 재설치부터 할 필요가 없다. 원본의 Codex 설치 예시는 아래와 같다. **터미널 명령**이며 채팅에 입력하는 스킬 호출과 구분한다.

```powershell
codex plugin marketplace add DietrichGebert/ponytail
codex plugin add ponytail@ponytail
```

원본은 설치 후 Codex의 `/hooks`에서 두 lifecycle hook을 검토하고 신뢰하도록 설정한 뒤 새 스레드를 시작하라고 안내한다. 데스크톱 앱은 재시작하며, hook 실행에는 PATH에 Node.js가 필요하다. 이 세션에서는 hook 활성화 상태까지 검증하지 않았다. [원본 Codex 설치 문서](https://github.com/DietrichGebert/ponytail/blob/main/INSTALL.md#codex)

## 7. 이 프로젝트에서 바로 쓸 요청 예시

### 평소 작은 수정

```text
제공한 AGENTS.md의 네 가지 원칙을 지키고 ponytail full로 진행해줘.
요청과 관련된 부분만 수정하고, 완료 기준과 실제 검증 결과를 알려줘.
작업: [수정할 내용]
```

### 큰 기능 개발 — Superpowers 설치 확인 후

```text
Karpathy 원칙을 기본으로, Superpowers로 설계와 구현 계획을 정리해줘.
구현은 ponytail full 기준으로 필요한 범위만 작성해줘.
지침 사이에 충돌이 있으면 해당 내용을 설명하고 내 요청을 기준으로 조정해줘.
작업: [만들 기능]
```

### 메인 리뷰어와 서브에이전트 역할 지정

```text
너는 메인 리뷰어야. 서브에이전트를 두 개 사용해줘.
에이전트1은 웹의 원본 문서와 최신 정보를 조사하고,
에이전트2는 로컬 코드와 스킬 설명을 조사해줘.
두 에이전트는 파일을 수정하지 말고 근거를 보고해줘.
너는 결과를 대조한 뒤 필요한 파일만 작성하고,
최종 내용과 검증 결과를 리뷰해서 알려줘.
```

위 문구는 역할 분담 요청 예시다. 실제 병렬 실행은 현재 Codex 세션이 제공하는 서브에이전트 기능에 따라 달라진다. 스킬을 설치하는 것만으로 웹 검색 권한이나 서브에이전트 도구가 생기지는 않는다.

## 8. 이번 문서의 검토 범위

- 메인 에이전트: 자료 통합, 문서 작성, 최종 검토.
- 서브에이전트 1: 공개 원본과 최신 설치 안내 웹 조사.
- 서브에이전트 2: 로컬 Ponytail 스킬 설명, 호출명, 설치 흔적 조사.
- 확인 기준: 원본 링크, 이름과 호출 방식, 현재 사용 가능 여부, 설치 예시와 실제 수행 내용의 구분.
- 수행하지 않은 검증: 신규 설치, hook 실행, 세 스킬을 함께 사용한 실제 코딩 작업.

웹의 설치 안내는 바뀔 수 있으므로 나중에 설치할 때는 연결된 원본 문서를 다시 확인한다.
