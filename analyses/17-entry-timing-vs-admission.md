# 17. 빌보드 진입시점(고3 초/후반) ↔ 입시결과

> **명제** · 빌보드 진입 시점이 빠른(고3 초반) 학생의 입시결과가 좋다
> **카테고리** B · 빌보드 순위 동역학 · **상태** ✅ 완료 · **데이터** 🟦 확보 · **출처** 시트2-16

## 한 줄 결론
> **✗ 기각 — 진입 시점·진입 여부 모두 입시와 무관.** Top-5000으로 완화해 표본을 확대(졸업생 3,536명, 메디컬 253)해도, 진입율은 메디컬 48.4% vs 기타 48.5%로 동일하고, 6-9월 조기 진입율도 메디컬 80% vs 기타 84%로 메디컬이 오히려 약간 낮다. 빌보드 진입 시점은 입시결과를 가르지 못한다.

> **트랙 안내**: `rank_month`(1년 월별) 첫 Top-5000 진입월 + `admission_results`. 졸업생 3,536명(메디컬 253).

## 결과
| 지표 | 메디컬 | 기타 |
|------|:---:|:---:|
| Top-5000 진입율 | 48.4% | 48.5% |
| 6-9월 조기 진입율 | 80% | 84% |

→ 진입 여부·시점 모두 입시 무관. [16](16-rank-volatility-vs-admission.md)(순위변동성)과 함께, **순위 동역학은 입시를 예측하지 못한다**는 결론을 강화([39](39-composite-index-vs-admission.md): 성적만 예측).

## ⚠️ 교란요인 · 주의
월 해상도라 "고3 초/후반"을 학사일정에 정밀 매핑하진 못함. 단 진입율 자체가 동일해 시점 정밀화로도 결론이 바뀔 여지는 작다.

## 선행 · 연관 분석
- [14 진입 소요](14-time-to-first-billboard.md), [16 순위 변동성](16-rank-volatility-vs-admission.md), [39 복합예측](39-composite-index-vs-admission.md)

## 📊 데이터 출처 & 표본

| 항목 | 내용 |
|------|------|
| 출처 | 운영 DocumentDB(aggregation): `rank`(STUDY_TIME/NATIONWIDE/DAY) + `student_daily_report` 월별집계 + exam_management(PostgreSQL, intra-tools RDS) `admission_results` |
| 기간/범위 | 졸업생 1년 월별 |
| 표본 | Top-5000 진입 3,536명(메디컬 253) |
| 분석 방법 | 진입율·조기진입율 ↔ 메디컬 |
| 추출 | 운영 DB **read-only** (MongoDB `find` / PostgreSQL `SELECT`, 쓰기 호출 없음) |
| 환경 | 격리 venv(uv, pandas/scipy/sklearn), 자격증명 비저장 |

---
◀ [전체 명제 목록](../README.md)
