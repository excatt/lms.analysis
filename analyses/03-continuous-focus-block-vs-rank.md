# 03. 연속 몰입 블록 길이 ↔ 순위

> **명제** · 순공시간 중 끊김 없는 연속 몰입 블록의 길이가 길수록 순위가 높다
> **카테고리** A · 몰입시간 × 성과 · **상태** 🔶 예비(분단위 raw 필요) · **데이터** 🟡 부분 · **출처** 시트2-4

## 한 줄 결론
> **🔶 분단위 착석/외출 로그가 없다.** `student_daily_report`·`raw_attendance`(exam_management) 모두 **일별 집계**라, 하루 안에서 외출로 끊긴 "연속 몰입 블록"을 잴 수 없다. itall-be DocumentDB의 **분단위 outing_log**(외출 구간)를 추출해 착석 구간을 재구성해야 한다.

## 다음 단계
itall-be `attendance`의 외출 로그(OUTING/RETURN 타임스탬프) 추출 → 일별 착석 구간을 외출로 분할 → 최장/평균 블록 길이 → 순위 상관(총 몰입량 통제).

## 선행 · 연관 분석
- [02 몰입 일관성](02-focus-consistency-vs-rank.md), [08 외출 빈도](08-outing-frequency-vs-rank-score.md)

## 📊 데이터 출처 & 표본

| 항목 | 내용 |
|------|------|
| 출처 | 운영 DocumentDB(aggregation): `rank`(STUDY_TIME/NATIONWIDE/DAY) + `student_daily_report` + exam `raw_attendance`(일별) |
| 기간/범위 | — |
| 표본 | 보류 — 분단위 착석/외출 raw 부재 |
| 분석 방법 | itall outing_log 추출 후 블록 재구성 필요(미실행) |
| 추출 | 운영 DB **read-only** (MongoDB `find` / PostgreSQL `SELECT`, 쓰기 호출 없음) |
| 환경 | 격리 venv(uv, pandas/scipy/sklearn), 자격증명 비저장 |

---
◀ [전체 명제 목록](../README.md)
