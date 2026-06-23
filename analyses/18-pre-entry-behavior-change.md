# 18. 빌보드 진입 직전 행동 변화

> **명제** · 빌보드 진입 전 가장 크게 증가하는 행동은 Q&A/CA/몰입 중 무엇인가
> **카테고리** B · 빌보드 순위 동역학 · **상태** 🔶 예비(몰입만, 서비스 날짜별 미추출) · **데이터** 🟦 부분 · **출처** 시트1-13 / 시트2-18

## 한 줄 결론
> **🔶 몰입은 진입 시 증가(+1.37h) 확인, 그러나 Q&A/CA와의 비교는 불가.** 빌보드(Top-1000) 진입 당월 몰입이 전월 대비 +1.37h 증가한다. 단 명제의 핵심인 "Q&A·CA·몰입 중 무엇이 가장 증가하나"는 Q&A/CA가 **누적값만 추출**돼 날짜별 변화를 못 봐 비교할 수 없다.

> **트랙 안내**: `rank_month`+`sdr_month`(1년 월별) 진입 이벤트 1,263건의 몰입 변화. Q&A/CA 날짜별 시계열 미추출.

## 결과 (몰입 한정)
| 지표 | 값 |
|------|-----|
| 진입 당월 몰입 − 전월 | **+1.37h** |
| 진입 이벤트 | 1,263건 |

→ 몰입은 진입과 함께 증가. Q&A/CA의 동반 증가 여부는 추가 추출 필요.

## 다음 단계
`mentoring_questions`·`mentor_schedule_reservation`을 날짜별로 추출 → 진입 이벤트 전후 Q&A·CA·몰입 변화량 비교(이벤트 스터디).

## 선행 · 연관 분석
- [04 선행 하락](04-focus-leading-drop-early-warning.md), [21 Q&A](21-rank-vs-online-qna.md), [24 CA](24-ca-frequency-vs-score.md)

## 📊 데이터 출처 & 표본

| 항목 | 내용 |
|------|------|
| 출처 | 운영 DocumentDB(aggregation): `rank`(STUDY_TIME/NATIONWIDE/DAY) + `student_daily_report` 월별집계 |
| 기간/범위 | 1년 13개월(몰입만) |
| 표본 | 진입 이벤트 1,263건 |
| 분석 방법 | 진입 당월 몰입 변화(Q&A/CA 날짜별 미추출) |
| 추출 | 운영 DB **read-only** (MongoDB `find` / PostgreSQL `SELECT`, 쓰기 호출 없음) |
| 환경 | 격리 venv(uv, pandas/scipy/sklearn), 자격증명 비저장 |

---
◀ [전체 명제 목록](../README.md)
