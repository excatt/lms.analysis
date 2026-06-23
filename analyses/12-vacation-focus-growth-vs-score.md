# 12. 방학 몰입 증가폭 ↔ 성적상승

> **명제** · 성적상승 학생은 방학(겨울/여름)에 몰입시간 증가폭이 가장 크다
> **카테고리** A · 몰입시간 × 성과 · **상태** 🔶 예비(시계열 부족) · **데이터** 🟦 부분 · **출처** 시트2-6

## 한 줄 결론
> **🔶 보류 — 장기 몰입 시계열 필요.** 30일 몰입 데이터로는 방학/학기 구간 비교 불가. 성적은 확보됐으나 방학 구간 몰입 추이가 있어야 한다.

## 다음 단계
몰입 수개월 추출 → 방학/학기 구간 태깅 → 구간별 증가폭과 성적상승 상관.

## 선행 · 연관 분석
- [11 수능 전 급증](11-focus-surge-before-exam.md)

## 📊 데이터 출처 & 표본

| 항목 | 내용 |
|------|------|
| 출처 | 운영 DocumentDB(aggregation): `rank`(STUDY_TIME/NATIONWIDE/DAY) + `student_daily_report` + exam_management(PostgreSQL, intra-tools RDS) |
| 기간/범위 | 30일·성적 |
| 표본 | 보류 — 방학 구간 몰입 추이 부재 |
| 분석 방법 | 구간별 증가폭(미실행) |
| 추출 | 운영 DB **read-only** (MongoDB `find` / PostgreSQL `SELECT`, 쓰기 호출 없음) |
| 환경 | 격리 venv(uv, pandas/scipy/sklearn), 자격증명 비저장 |

---
◀ [전체 명제 목록](../README.md)
