# 27. Q&A 시간대(수업직후 vs 심야) ↔ 성적

> **명제** · 심야·마감직전 Q&A보다 수업 직후 즉시 Q&A 학생의 성적이 좋다
> **카테고리** C · 서비스 활용 · **상태** 🔶 예비(시각 추출 대기) · **데이터** 🟦 부분 · **출처** 시트2-26

## 한 줄 결론
> **🔶 데이터는 있으나 미추출.** `mentoring_questions.created_at`(datetime)로 질문 시간대를 분류할 수 있으나, 현재 집계는 횟수만 뽑았다. 시각별 raw 추출 후 분석 가능.

## 다음 단계
mentoring_questions의 created_at 시각(hour) 분포를 학생별로 추출 → 수업직후/심야 비율 → 성적과 상관.

## 선행 · 연관 분석
- [21 Q&A↔순위](21-rank-vs-online-qna.md), [22 Q&A↔성적](22-qna-vs-score-tenure-controlled.md)

## 📊 데이터 출처 & 표본

| 항목 | 내용 |
|------|------|
| 출처 | main `mentoring_questions.created_at` + exam_management(PostgreSQL, intra-tools RDS) |
| 기간/범위 | — |
| 표본 | 보류 — 시각(hour) 미추출 |
| 분석 방법 | 시간대 분류 후 성적 상관(미실행) |
| 추출 | 운영 DB **read-only** (MongoDB `find` / PostgreSQL `SELECT`, 쓰기 호출 없음) |
| 환경 | 격리 venv(uv, pandas/scipy/sklearn), 자격증명 비저장 |

---
◀ [전체 명제 목록](../README.md)
