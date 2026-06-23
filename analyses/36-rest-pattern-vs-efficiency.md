# 36. 휴식 패턴 규칙성 ↔ 순공 효율

> **명제** · 휴식 시간이 규칙적인(짧고 일정한) 학생의 순공 효율이 높다
> **카테고리** E · 생활·습관·복합 · **상태** 🔶 예비(분단위 raw 필요) · **데이터** 🟡 부분 · **출처** 시트2-38

## 한 줄 결론
> **🔶 휴식 raw가 없다.** 휴식(외출) 구간의 분단위 로그가 있어야 "짧고 일정한 휴식"을 측정할 수 있는데, 현재 일별 집계만 보유. [03번](03-continuous-focus-block-vs-rank.md)과 동일하게 itall outing_log 추출이 선행.

## 다음 단계
외출/휴식 로그 추출 → 휴식 빈도·길이·규칙성 산출 → 몰입비율(focus/study)과 상관.

## 선행 · 연관 분석
- [03 연속 몰입 블록](03-continuous-focus-block-vs-rank.md)

## 📊 데이터 출처 & 표본

| 항목 | 내용 |
|------|------|
| 출처 | 운영 DocumentDB(aggregation): `rank`(STUDY_TIME/NATIONWIDE/DAY) + `student_daily_report` (일별 집계) |
| 기간/범위 | — |
| 표본 | 보류 — 휴식 분단위 raw 부재 |
| 분석 방법 | 외출/휴식 로그 추출 필요(미실행) |
| 추출 | 운영 DB **read-only** (MongoDB `find` / PostgreSQL `SELECT`, 쓰기 호출 없음) |
| 환경 | 격리 venv(uv, pandas/scipy/sklearn), 자격증명 비저장 |

---
◀ [전체 명제 목록](../README.md)
