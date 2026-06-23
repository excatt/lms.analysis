# 11. 수능 N개월 전 몰입 급증 시점

> **명제** · 성적상승 학생의 몰입시간 급증 시점은 수능 O개월 전이다
> **카테고리** A · 몰입시간 × 성과 · **상태** 🔶 예비(시계열 부족) · **데이터** 🟦 부분 · **출처** 시트2-32 / 시트1-10

## 한 줄 결론
> **🔶 보류 — 장기 몰입 시계열 필요.** 현재 몰입 데이터는 30일(2026.05~06)뿐이라 "수능 N개월 전 급증 시점"을 추적할 수 없다. 성적(student_records)은 회차별로 있으나, 몰입의 월별 장기 추이가 있어야 변곡점을 잡는다.

## 다음 단계
DocumentDB student_daily_report를 수개월~1년 추출 → 수능일(11월) 기준 역산 타임라인에 몰입 정렬 → 성적상승군의 증가 변곡점 탐지.

## 선행 · 연관 분석
- [10 재원 정점](10-tenure-focus-peak.md), [12 방학 몰입](12-vacation-focus-growth-vs-score.md)

## 📊 데이터 출처 & 표본

| 항목 | 내용 |
|------|------|
| 출처 | 운영 DocumentDB(aggregation): `rank`(STUDY_TIME/NATIONWIDE/DAY) + `student_daily_report` + exam_management(PostgreSQL, intra-tools RDS) |
| 기간/범위 | 30일(몰입)·성적 시계열 |
| 표본 | 보류 — 몰입 장기 시계열 부재 |
| 분석 방법 | 수능 역산 변곡점(미실행) |
| 추출 | 운영 DB **read-only** (MongoDB `find` / PostgreSQL `SELECT`, 쓰기 호출 없음) |
| 환경 | 격리 venv(uv, pandas/scipy/sklearn), 자격증명 비저장 |

---
◀ [전체 명제 목록](../README.md)
