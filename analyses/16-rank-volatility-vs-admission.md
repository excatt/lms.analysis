# 16. 순위 변동성(저변동) ↔ 입시결과

> **명제** · 순위가 꾸준한(저변동) 학생이 급등락 학생보다 입시결과가 좋다
> **카테고리** B · 빌보드 순위 동역학 · **상태** ✅ 완료 · **데이터** 🟦 확보 · **출처** 시트2-17

## 한 줄 결론
> **✗ 기각 — 순위 안정성은 입시를 가르지 못한다.** 졸업생의 1년 월별 순위 변동성(rank std)이 메디컬 907 vs 기타 920(Cohen d=−0.025), 평균 순위도 d=+0.06으로 차이 없음. **단 [32 성적 안정성](32-score-stability-vs-admission.md)은 d=−1.08로 강력** — 즉 "안정성이 성과를 가른다"는 *순위*가 아니라 *성적*에서만 성립한다.

> **트랙 안내**: 졸업생(2026 입시)의 1년 월별 STUDY_TIME 순위(`rank_month`, 2025.06~2026.06) + `admission_results`. 3개월+ 4,878명(메디컬 324).

## 결과
| 지표 | 메디컬 | 기타 | Cohen d |
|------|:---:|:---:|:---:|
| 월별 순위 변동성(std) | 907 | 920 | −0.025 |
| 평균 순위 | 5,515 | 5,402 | +0.060 |

→ 순위 변동성·평균 모두 입시 변별력 없음. 입시는 순위가 아니라 성적이 결정([39](39-composite-index-vs-admission.md)).

## ⚠️ 교란요인 · 주의
월평균 순위라 일별 급등락은 평활됨 — 일별 rank로 보면 변동성이 다를 수 있으나, 졸업생 일별 1년치는 미추출.

## 선행 · 연관 분석
- [32 성적 안정성](32-score-stability-vs-admission.md), [39 복합예측](39-composite-index-vs-admission.md), [15 유지↔변동](15-billboard-retention-vs-focus-var.md)

## 📊 데이터 출처 & 표본

| 항목 | 내용 |
|------|------|
| 출처 | 운영 DocumentDB(aggregation): `rank`(STUDY_TIME/NATIONWIDE/DAY) + `student_daily_report` 월별집계 + exam_management(PostgreSQL, intra-tools RDS) `admission_results` |
| 기간/범위 | 졸업생 1년 월별 |
| 표본 | 3개월+ 4,878명(메디컬 324) |
| 분석 방법 | 월별 순위 std ↔ 메디컬 Cohen d |
| 추출 | 운영 DB **read-only** (MongoDB `find` / PostgreSQL `SELECT`, 쓰기 호출 없음) |
| 환경 | 격리 venv(uv, pandas/scipy/sklearn), 자격증명 비저장 |

---
◀ [전체 명제 목록](../README.md)
