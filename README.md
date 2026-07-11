# insight-card

회사명+주제를 받아 **출처 검증된** 기업 리서치 카드를 마크다운으로 생성하는 Claude Code 스킬.

- 9개 고정 주제 (기업 개요 / 산업·시장 / 재무상태 / 신사업·투자 / 리스크 / 경쟁사 비교 / 상품 / 고객 / 임상·과학적 근거)
- 모든 출처 URL을 실제 접속 확인한 것만 기재 (`verified` 플래그)
- 같은 회사×주제를 다시 조사하면 새 날짜 파일로 히스토리가 쌓임

## 설치

```bash
mkdir -p ~/.claude/skills/insight-card
cp SKILL.md SCHEMA.md ~/.claude/skills/insight-card/
```

특정 프로젝트에서만 쓰려면 `~/.claude/skills/` 대신 프로젝트의 `.claude/skills/`에 넣는다.

## 사용

Claude Code에서:

> 올리브영 × 기업 개요 카드 만들어줘

카드는 프로젝트 루트 `cards/`에 `{companySlug}-{topicSlug}-{YYYYMMDD}.md`로 생성된다.

## 구성

- `SKILL.md` — 리서치 규칙·소스 맵·URL 검증·품질 게이트
- `SCHEMA.md` — 카드 frontmatter 규격 (SKILL.md가 참조하므로 반드시 같은 폴더에 둘 것)
