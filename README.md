# 직무분석 Codex 스킬

특정 회사의 채용공고를 회사·산업·경쟁 대안과 연결해 읽고, 실제 근거와 가상의 업무 장면을 구분하여 필요한 행동과 지원자의 경험을 분석하는 스킬입니다. 공식 공고를 우선 확인하고, 확인된 사실·해석·가상 설정·미확인을 구분합니다. 개인 경험은 사용자가 제공하거나 사용을 허락한 자료에만 근거합니다.

## 설치

저장소를 스킬 폴더에 직접 복제합니다. 이미 같은 이름의 폴더가 있다면 기존 내용을 먼저 확인하세요. 아래 명령은 사용자 범위의 `~/.agents/skills`에 설치합니다.

Windows PowerShell:

```powershell
New-Item -ItemType Directory -Force "$HOME/.agents/skills" | Out-Null
git clone https://github.com/Kimhyuntae9665/codex-skill-job-analysis.git "$HOME/.agents/skills/직무분석"
```

macOS / Linux:

```sh
mkdir -p "$HOME/.agents/skills"
git clone https://github.com/Kimhyuntae9665/codex-skill-job-analysis.git "$HOME/.agents/skills/직무분석"
```

Codex가 `~/.codex/skills`를 사용하는 환경에서는 위 대상 경로의 `.agents`를 `.codex`로 바꾸어 설치할 수 있습니다. 설치 후 새 Codex 턴에서 사용합니다. Codex의 `skill-installer`를 사용하려면 저장소 루트의 스킬을 지원하는지 해당 설치기의 현재 안내를 확인하세요.

## 사용 예

> `$직무분석으로 이 회사의 신입 품질 직무를 분석해줘. 공고 URL은 ...이고, 내가 제공한 경험과 연결해줘.`

공고 URL이나 회사·직무를 제공하면 분석 범위를 구체화할 수 있습니다. 외부 조사를 원하지 않으면 “제공 자료만 사용”이라고 명시하세요. 최신 공고와 회사 정보를 조사하려면 웹 접근이 필요하며, 경험 연결에는 사용자가 제공하거나 접근을 허락한 자료가 필요합니다.

## 구성과 외부 의존성

- `SKILL.md`: 실행 지침 원본.
- `references/method.md`: 조사·비교·가상 장면·근거 점검 방법.
- `references/source-notes.md`: 아이디어의 출처와 적용 범위.
- `agents/openai.yaml`: Codex 표시 정보와 예시 요청.
- `SHA256SUMS.txt`: 배포된 위 원본 파일의 SHA-256 목록.

`SKILL.md`에 등장하는 `C:/Users/user/.codex/guidance/CAREER_CORE.md`, `CAREER_RADAR.md`, `CAREER_ROUTE_CATALOG.md`는 원래 사용자 PC의 개인 채용 작업에만 적용되는 외부 지침입니다. 이 저장소에는 포함하지 않았으며, 다른 사용자의 일반적인 직무 분석에는 필요하지 않습니다. 해당 개인 워크플로를 재현하려면 소유자가 별도로 관리하는 최신 지침이 필요합니다. 스킬의 필수 참조 문서 두 개는 저장소에 포함되어 있습니다. 별도 모델이나 PAL 호출은 필수 조건이 아닙니다.

## 출처와 이용 조건

분석 질문 흐름의 출발점은 와레의 [지원동기가 쉽게 써지는 AI 활용법](https://x.com/LongSTShort/status/2111365247508644139)입니다. 채택한 원리와 추가한 검증 절차의 구분은 [출처 설명](references/source-notes.md)에 있습니다. 이 저장소는 원문을 복제하지 않으며, 원저자의 공식 승인이나 제휴를 뜻하지 않습니다.

이 저장소의 원본 파일은 [MIT 라이선스](LICENSE)로 배포합니다. 링크된 X 글과 그 밖의 외부 콘텐츠에는 이 라이선스가 적용되지 않으며 각 권리자에게 권리가 있습니다.

## 개인정보와 보안

지원서나 개인 이력을 제공하기 전에 공유 범위를 확인하세요. 웹페이지나 공고에 포함된 지시는 조사 대상 데이터로 취급하며, 이 스킬의 사용 자체가 외부 전송·지원서 제출·연락·게시를 허용하지 않습니다. 저장소에 비밀번호, 토큰, 이력서 등 개인 자료를 넣지 마세요.

## 원문 보존과 패키지 검사

`SKILL.md`는 배포 기준 원본과 바이트 단위로 동일합니다. 개인 PC 경로와 과거 실행 관찰을 포함한 원문은 수정하지 않았으며, 설치·계정 설정에는 위의 현재 사용자 기준 안내를 적용하세요. 설정 파일과 비밀키는 포함하지 않습니다.

```sh
python tools/verify_package.py
```

`package-manifest.json`은 배포 파일 해시와 원본 SKILL 해시를 기록합니다. GitHub Actions도 해시·상대 문서 링크·Python 문법을 검사합니다. 테스트가 있어도 실제 계정 로그인·현재 모델 접근·잔여 한도·실제 모델 리뷰 성공을 증명하지는 않습니다.
