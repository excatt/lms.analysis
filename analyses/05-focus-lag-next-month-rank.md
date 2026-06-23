# 05. 전월 몰입 → 익월 빌보드 (시차효과)

> **명제** · 몰입시간이 길었던 달의 다음 달 빌보드 순위가 좋았다
> **카테고리** A · 몰입시간 × 성과 · **상태** 🔶 보류(데이터 추출 이슈) · **데이터** 🟦 확보(추출 보류) · **출처** 시트1-1

## 한 줄 결론

> **🔶 보류 — 월별 랭킹 추출이 막혔다.** `rank` 컬렉션의 `days="MONTH"` 조회가 인덱스 미스로 타임아웃(OperationFailure). 일별 데이터로 월 집계를 재구성하거나, 인덱스 추가 후 재시도 필요.

## 가설
몰입시간이 길었던 달의 다음 달 빌보드 순위가 좋았다(시차 효과).

## 필요 데이터
- `rank`(days=MONTH) 또는 일별 rank의 월 집계 — 최소 2개월

**가용성**: 월별 직접 조회 보류(인덱스). 일별 90일+ 추출로 우회 가능.

## 분석 방법(예정)
학생별 월별 몰입과 익월 순위를 lag-1 정렬 → 시차 상관. 동월 상관 대비 예측력 비교.

## 결과
> 🔶 보류. `rank{type:STUDY_TIME, days:MONTH}` full-scan 타임아웃(45s). 우회: 일별 rank 다개월 추출 후 월 평균 재구성.

## 다음 단계
1. 일별 rank+focus 90일 추출(이미 30일 보유) → 월 집계.
2. 또는 aggregation DB `rank`에 `{type,range,days}` 복합 인덱스 확인/요청.

## ⚠️ 교란요인 · 주의
동월 상관과 분리해야 '선행 예측' 주장 가능. 재원 지속 학생만 대상.

## 선행 · 연관 분석
- [01 몰입 절대량](01-focus-absolute-vs-billboard-rank.md), [04 선행하락](04-focus-leading-drop-early-warning.md)

## 📊 데이터 출처 & 표본

| 항목 | 내용 |
|------|------|
| 출처 | 운영 DocumentDB(aggregation): `rank`(STUDY_TIME/NATIONWIDE/DAY) + `student_daily_report` (days=MONTH) |
| 기간/범위 | — |
| 표본 | 보류 |
| 분석 방법 | rank days=MONTH 인덱스 미스 타임아웃(OperationFailure) |
| 추출 | 운영 DB **read-only** (MongoDB `find` / PostgreSQL `SELECT`, 쓰기 호출 없음) |
| 환경 | 격리 venv(uv, pandas/scipy/sklearn), 자격증명 비저장 |

---
◀ [전체 명제 목록](../README.md)
