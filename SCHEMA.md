# 인사이트 카드 규격 v1

카드 1장 = 회사 × 주제 × 날짜. 파일명: `{companySlug}-{topicSlug}-{YYYYMMDD}.md`

## Frontmatter (YAML)

| 필드 | 타입 | 필수 | 설명 |
|---|---|---|---|
| company | string | ✅ | 회사명 (한국어, 예: 샘플바이오) |
| companySlug | string | ✅ | 영문 소문자-하이픈 (예: sample-bio). 로고를 쓰는 프로젝트라면 로고 파일명과 일치 |
| topic | string | ✅ | 9개 중 하나, 한국어 문자열 정확히: 기업 개요/산업·시장/재무상태/신사업·투자/리스크/경쟁사 비교/상품/고객/임상·과학적 근거 |
| date | string | ✅ | YYYY-MM-DD (조사 기준일) — 파일명의 YYYYMMDD와 같은 날짜 |
| summary | string | ✅ | 한 줄 요약 |
| keyPoints | string[] | ✅ | 핵심 포인트 3~5개 |
| verified | boolean | ✅ | 전 출처 URL 접속 확인 완료 여부 |
| sources | object[] | ✅ | {title, outlet, date, url, type} — 실제 접속 확인된 URL만. date는 YYYY-MM-DD |
| chart | object | ⬜ | {title, unit, type: bar\|line, labels: string[], values: number[]} — 숫자 추이 |
| keyMetrics | object[] | ⬜ | 최대 4개, {label, value, delta?, direction?: up\|down\|flat} — 핵심 지표 |
| reputation | object | ⬜ | {rating: number, reviewCount: number, quote: string} — 평판 요약 |
| sources[].type | string | ✅ | dart\|news\|youtube\|instagram\|official\|internal — 출처 분류 태그 |

chart/keyMetrics/reputation은 카드를 렌더링하는 뷰어가 있을 때 시각화되는 필드지만, 뷰어가 없어도 채워 둔다 — 데이터 자체가 카드의 가치다.

## YAML 주의

- **쉼표(,)가 들어가는 문자열 값은 반드시 큰따옴표로 감싼다** — 예: `value: "1,240억"`, `quote: "만족, 불만 일부"`. 한 줄 객체(`{ }`) 안에서 따옴표 없는 쉼표는 값을 잘라먹는다.

## 본문 (마크다운, 길이 무제한)

- `## 상세 분석` — 문단·소제목·GFM 표 자유
- `## 고객의 소리` — 고객 주제일 때 유튜브·인스타 후기 요약
- 마지막에 `### 그래서 어떻게 봐야 하나` — 요약이 아닌 판단
- 본문 안에서 주장할 때마다 근거 출처를 문장 끝에 표기

## 출처 신뢰 원칙

1. 모든 중요한 주장에는 출처가 붙는다
2. 실제 접속해서 확인된 URL만 기록한다 (404 = 신뢰 붕괴)
3. 오래된 데이터는 시점을 명시한다. 반대 근거·리스크도 포함한다
