# 18. 빌보드 진입 직전 행동 변화

> **명제** · 빌보드 진입 전 가장 크게 증가하는 행동은 Q&A/CA/몰입 중 무엇인가
> **카테고리** B · 빌보드 순위 동역학 · **상태** ✅ 완료 · **데이터** 🟦 확보 · **출처** 시트1-13 / 시트2-18

## 한 줄 결론
> **✗ 진입 직전 단기 급증 행동은 없다 — 진입은 "누적의 결과".** Top-1000 진입 직전 1주일(vs 그 전 1주일)에 Q&A(−0.008/주)·CA(+0.047/주)·몰입(−0.00h) 어느 것도 뚜렷한 급증을 보이지 않는다. "진입 전 무엇이 가장 증가하나"에 대한 답: **특정 행동의 단기 급증이 아니라, 꾸준한 누적이 순위를 끌어올린다.** (월 단위로는 진입월 몰입 +1.37h이나, 이는 점진적 상승이지 직전 급변이 아님.)

> **트랙 안내**: `mentoring_questions`/`mentor_schedule_reservation` **날짜별** + `rank`(일별 30일). 진입 이벤트 9,789건의 직전 7일 vs 8-14일 전 행동 변화.

## 결과 (진입 이벤트 9,789건)
| 행동 | 진입 직전 1주 변화 |
|------|:---:|
| Q&A | −0.008건/주 |
| CA(상담) | +0.047건/주 |
| 몰입 | −0.00h |

→ 셋 다 미미. 빌보드 진입은 직전 일주일의 행동 변화로 설명되지 않는다.

## ⚠️ 교란요인 · 주의
30일 윈도우 + 7일 lookback이라 장기 누적 추세는 못 봄. 단 [05](05-focus-lag-next-month-rank.md)(전월→익월 −0.697)·[01](01-focus-absolute-vs-billboard-rank.md)에서 누적 몰입이 순위를 결정함이 확인됨 → "누적의 결과" 해석과 정합.

## 선행 · 연관 분석
- [04 선행 하락](04-focus-leading-drop-early-warning.md), [21 Q&A](21-rank-vs-online-qna.md), [24 CA](24-ca-frequency-vs-score.md)

## 📊 데이터 출처 & 표본

| 항목 | 내용 |
|------|------|
| 출처 | main `mentoring_questions`+`mentor_schedule_reservation` 날짜별 + 운영 DocumentDB(aggregation): `rank`(STUDY_TIME/NATIONWIDE/DAY) + `student_daily_report` |
| 기간/범위 | 30일 일별 |
| 표본 | 진입 이벤트 9,789건 |
| 분석 방법 | 진입 직전 7일 vs 8-14일전 Q&A/CA/몰입 변화 |
| 추출 | 운영 DB **read-only** (MongoDB `find` / PostgreSQL `SELECT`, 쓰기 호출 없음) |
| 환경 | 격리 venv(uv, pandas/scipy/sklearn), 자격증명 비저장 |

---
◀ [전체 명제 목록](../README.md)
