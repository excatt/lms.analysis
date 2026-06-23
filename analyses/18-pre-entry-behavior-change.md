# 18. 빌보드 진입 직전 행동 변화

> **명제** · 빌보드 진입 전 가장 크게 증가하는 행동은 Q&A/CA/몰입 중 무엇인가
> **카테고리** B · 빌보드 순위 동역학 · **상태** 🔶 예비(시계열 추출 대기) · **데이터** 🟡 부분 · **출처** 시트1-13 / 시트2-18

## 한 줄 결론
> **🔶 행동의 날짜별 시계열이 필요.** Q&A(`created_at`)·CA(`date`)·몰입(일별)은 시점 데이터가 있으나, 현재는 **누적 횟수만** 집계했다. 진입 이벤트 직전 N주의 각 행동 변화량을 보려면 날짜별 시계열 추출 + 더 긴 rank 윈도우가 필요.

## 다음 단계
Q&A/CA를 날짜별로 추출 → 빌보드 진입 이벤트(rank 시계열) 전 2~4주 Q&A·CA·몰입 변화량 비교(이벤트 스터디).

## 선행 · 연관 분석
- [04 선행 몰입 하락](04-focus-leading-drop-early-warning.md), [21 Q&A](21-rank-vs-online-qna.md), [24 CA](24-ca-frequency-vs-score.md)

## 📊 데이터 출처 & 표본

| 항목 | 내용 |
|------|------|
| 출처 | main `mentoring_questions`+`mentor_schedule_reservation` + 운영 DocumentDB(aggregation): `rank`(STUDY_TIME/NATIONWIDE/DAY) + `student_daily_report` |
| 기간/범위 | — |
| 표본 | 보류 — 날짜별 행동 시계열 미추출 |
| 분석 방법 | 진입 이벤트 스터디(미실행) |
| 추출 | 운영 DB **read-only** (MongoDB `find` / PostgreSQL `SELECT`, 쓰기 호출 없음) |
| 환경 | 격리 venv(uv, pandas/scipy/sklearn), 자격증명 비저장 |

---
◀ [전체 명제 목록](../README.md)
