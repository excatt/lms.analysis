# P57. 주말 몰입 절대시간 ↔ 메디컬

> **명제(제안)** · 주말 몰입시간(절대량)이 많은 학생이 메디컬 합격률이 높다
> **분류** A 몰입×성과 · **상태** ◐ 약한 지지 · *AI 도출 명제(origin.xlsx 외)*

## 한 줄 결론
> **◐ 약한 지지 — 행동지표 중 가장 큰 신호지만 여전히 작다.** 메디컬 합격자의 주말 몰입시간은 8.66h vs 기타 8.22h(Cohen d=**+0.174**). 측정된 모든 행동지표 중 메디컬 변별력이 가장 크지만, 효과크기는 여전히 '작음' 범주(|d|<0.2). [P46 주말 등원*율*](P46-weekend-ratio-vs-admission.md)이 무효였던 것과 달리, 주말 *몰입시간 절대량*은 미약하게나마 양의 신호.

## 결과
| 그룹 | 주말 몰입(h) |
|---|---|
| 메디컬 | 8.66 |
| 기타 | 8.22 |
| Cohen d | +0.174 |

![behavior null](../assets/proposed/P58/chart.png)

*주말 몰입시간(맨 왼쪽)이 행동지표 중 유일하게 d>0.15. 나머지(빌보드출현·상벌점·휴일·개근·자율·멘토링)는 전부 무효 구간. → P58.*

## 도출 근거
P46(주말 등원*율* d−0.07, 무효)과 달리 주말 *몰입시간 절대량*(`avg_study_hours_weekend`)은 미사용. "주말에 얼마나 오느냐"가 아니라 "주말에 얼마나 깊게 하느냐"를 검증.

## 시사점 · 한계 · 연관
- 행동 중 최대 신호지만 d+0.17로 실무 변별엔 부족. "메디컬은 주말에도 길게 몰입하는 경향" 정도의 약한 서술만 가능([P52](P52-score-level-vs-focus.md)의 '성적상위=약한 몰입우위'와 같은 결).
- **연관**: [P46 주말 등원율](P46-weekend-ratio-vs-admission.md) · [12 방학 몰입](../analyses/12-vacation-focus-growth-vs-score.md) · [P58 행동 무변별 묶음](P58-behavior-null-bundle-vs-medical.md)

## 📊 데이터 출처 & 표본

| 항목 | 내용 |
|------|------|
| 출처 | `exam_management.admission_results`/`student_behavior_stats`(avg_study_hours_weekend) |
| 표본 | 졸업생(메디컬 vs 기타) |
| 방법 | Cohen d |
| 추출 | 운영 DB read-only |
| 환경 | 격리 venv(pandas/scipy) |

---
◀ [제안 명제 목록](README.md) · [전체 명제](../README.md)
