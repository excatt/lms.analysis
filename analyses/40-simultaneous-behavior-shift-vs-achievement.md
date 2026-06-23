# 40. 행동 동시변화 시점 ↔ 성취

> **명제** · 성취 학생은 특정 시점에 몰입↑·Q&A↑·외출↓의 동시다발 변화가 나타난다
> **카테고리** E · 생활·습관·복합 · **상태** 🔶 예비(서비스 날짜별 미추출) · **데이터** 🟡 부분 · **출처** 시트2-42

## 한 줄 결론
> **🔶 동시성 분석 불가 — 지표별 시점 해상도가 다르다.** 몰입은 월별(`sdr_month`), 외출은 30일 일별(`outing_log`), Q&A/CA는 누적값만 보유. 세 지표를 **같은 날짜 축**에 올려 동시 변화점(change-point)을 탐지하려면 모두 날짜별 추출이 필요하다. 부분적으로 [04](04-focus-leading-drop-early-warning.md)(몰입 변화)·[18](18-pre-entry-behavior-change.md)(진입 시 몰입↑)에서 단일 지표 변화는 확인됨.

## 다음 단계
몰입·Q&A·CA·외출을 **학생×날짜** 패널로 추출 → 학생별 change-point 탐지 → 지표 동시성 → 성취(순위 상승)와 연결.

## 선행 · 연관 분석
- [18 진입 직전 행동변화](18-pre-entry-behavior-change.md), [04 선행 하락](04-focus-leading-drop-early-warning.md)

## 📊 데이터 출처 & 표본

| 항목 | 내용 |
|------|------|
| 출처 | 운영 DocumentDB(aggregation): `rank`(STUDY_TIME/NATIONWIDE/DAY) + `student_daily_report` + main Q&A/외출 |
| 기간/범위 | — |
| 표본 | 보류 — 다지표 시계열 미추출 |
| 분석 방법 | change-point 동시성(미실행) |
| 추출 | 운영 DB **read-only** (MongoDB `find` / PostgreSQL `SELECT`, 쓰기 호출 없음) |
| 환경 | 격리 venv(uv, pandas/scipy/sklearn), 자격증명 비저장 |

---
◀ [전체 명제 목록](../README.md)
