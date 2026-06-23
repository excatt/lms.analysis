# 24. CA(멘토 상담) 활용빈도 ↔ 성적상승

> **명제** · CA(멘토 상담) 활용 빈도가 높을수록 성적상승 폭이 크다
> **카테고리** C · 서비스 활용 · **상태** ✅ 완료 · **데이터** 🟦 확보 · **출처** 시트1-12 / 시트2-23

## 한 줄 결론
> **◐ 약한 양의 연관(순위·성적 모두).** "CA = 멘토 상담(`mentor_schedule_reservation`)"으로 확정. CA 활용은 순위(부분상관 −0.11)와 성적상승(+0.058) 모두 약한 양의 연관. 학생의 91.5%가 CA를 사용하는 보편적 서비스.

> **트랙 안내**: 성적상승 = 현재 재원생(분석모집단)의 모의고사 백분위 시계열 기울기(3회+ 응시 2,903명). 행동/서비스는 DocumentDB 30일(몰입·입실·외출) + Q&A/CA. **성적평균(천장효과) 통제 부분상관**으로 봄.

## 결과
| 타깃 | 지표 | 값 |
|------|------|-----|
| 순위 | 부분 Spearman(월당 CA, pct_rank \| 몰입) | −0.112 |
| **성적상승** | 부분 Spearman(CA, 성적기울기 \| 성적평균) | **+0.058** (p=2e-3) |
| 사용률 | CA 사용 학생 | 91.5% |

→ 순위·성적 양쪽에서 일관된 약한 양의 효과. 효과크기는 작음.

> **메타 결론(중요)**: 모든 행동/서비스의 성적상승 부분상관이 |ρ|<0.08로 매우 작다. **입시결과 트랙(행동 AUC 0.52)·순위 트랙(몰입 동어반복)과 동일** — 잇올 행동지표는 성과(순위·성적상승·입시) 변별력이 일관되게 약하다. 변별은 '양'이 아니라 [02 일관성](02-focus-consistency-vs-rank.md)·[32 성적안정성](32-score-stability-vs-admission.md) 같은 '안정성'에서 난다.

## 선행 · 연관 분석
- [21 Q&A](21-rank-vs-online-qna.md), [28 CA·Q&A](28-ca-qna-combined-vs-score.md), [25 멘토출신(불가)](25-ca-mentor-focus.md)

## 📊 데이터 출처 & 표본

| 항목 | 내용 |
|------|------|
| 출처 | main `mentor_schedule_reservation`+`mentoring_questions` + 운영 DocumentDB(aggregation): `rank`(STUDY_TIME/NATIONWIDE/DAY) + `student_daily_report` + exam_management(PostgreSQL, intra-tools RDS) |
| 기간/범위 | CA 누적 + 순위/성적 |
| 표본 | CA 사용 91.5% · 성적 3회+ 2,903명 |
| 분석 방법 | 순위(몰입통제)+성적상승(평균통제) |
| 추출 | 운영 DB **read-only** (MongoDB `find` / PostgreSQL `SELECT`, 쓰기 호출 없음) |
| 환경 | 격리 venv(uv, pandas/scipy/sklearn), 자격증명 비저장 |

---
◀ [전체 명제 목록](../README.md)
