# 잇올 학습데이터 분석 — 명제 백로그

`origin.xlsx`의 가설들을 **검증 가능한 명제 41개**로 통합 정리한 마스터 인덱스.
각 명제는 `analyses/NN-*.md` 개별 문서로 관리한다.

## 진행 현황

| ✅ 완료 | 🔶 예비(장기데이터 보강) | 🟢 분석가능 | 🟡 데이터확인필요 | ⛔ 데이터부재(불가) | 합계 |
|:---:|:---:|:---:|:---:|:---:|:---:|
| 29 | 10 | 0 | 0 | 2 | 41 |

- **🟢 분석가능**: 운영 DB에서 데이터가 확인되어 바로 착수 가능
- **🟡 데이터확인필요**: 성적·입시결과·Q&A·CA·멘토 등 소스 컬렉션 확인 후 가능

## 설계 원칙 (1번 분석의 교훈)

> **1번**에서 STUDY_TIME 빌보드는 학습시간으로 매겨져 몰입시간과 **동어반복**에 가깝다는 점이 드러났다
> (study_time 통제 시 몰입의 순위 고유효과 ≈ 0). 따라서 이후 분석은 다음을 따른다:
> 1. **교란변수 통제**: 절대량/학습시간을 통제한 **부분상관**으로 고유효과를 분리한다.
> 2. **동어반복 회피**: 순위가 변수 자체로 매겨지는 조합을 피하고, 독립 성과(성적·입시결과·지속)로 확장한다.
> 3. **시계열·인과 지향**: 단순 상관을 넘어 lead/lag·이벤트 스터디로 선행성을 본다(4·5·40번).

## A. 몰입시간 × 성과

| # | 명제 | 데이터 | 상태 | 문서 |
|---|------|--------|------|------|
| 01 | 몰입시간 절대량 ↔ 빌보드 순위 | 🟦 확보 | ✅ 완료 | [01](analyses/01-focus-absolute-vs-billboard-rank.md) |
| 02 | 몰입시간 일관성(저변동) ↔ 순위 | 🟦 확보 | ✅ 완료 | [02](analyses/02-focus-consistency-vs-rank.md) |
| 03 | 연속 몰입 블록 길이 ↔ 순위 | 🟨 확인필요 | 🔶 예비(장기데이터 보강) | [03](analyses/03-continuous-focus-block-vs-rank.md) |
| 04 | 빌보드 이탈 선행 몰입 하락 (조기경보) | 🟦 확보 | 🔶 예비(장기데이터 보강) | [04](analyses/04-focus-leading-drop-early-warning.md) |
| 05 | 전월 몰입 → 익월 빌보드 (시차효과) | 🟦 확보 | ✅ 완료 | [05](analyses/05-focus-lag-next-month-rank.md) |
| 06 | 주말·공휴일 몰입 ↔ 성적상승 | 🟨 확인필요 | ✅ 완료 | [06](analyses/06-weekend-holiday-focus-vs-score.md) |
| 07 | 입실시각(오전형) ↔ 성적상승 | 🟨 확인필요 | ✅ 완료 | [07](analyses/07-morning-checkin-vs-score.md) |
| 08 | 외출·조퇴 빈도 ↔ 순위·성적 | 🟨 확인필요 | ✅ 완료 | [08](analyses/08-outing-frequency-vs-rank-score.md) |
| 09 | 요일별 몰입 편차 ↔ 상위권 | 🟦 확보 | ✅ 완료 | [09](analyses/09-weekday-variance-toptier.md) |
| 10 | 재원 N개월차 몰입 정점 후 분기 | 🟦 확보 | ✅ 완료 | [10](analyses/10-tenure-focus-peak.md) |
| 11 | 수능 N개월 전 몰입 급증 시점 | 🟨 확인필요 | ✅ 완료 | [11](analyses/11-focus-surge-before-exam.md) |
| 12 | 방학 몰입 증가폭 ↔ 성적상승 | 🟨 확인필요 | ✅ 완료 | [12](analyses/12-vacation-focus-growth-vs-score.md) |

## B. 빌보드 순위 동역학

| # | 명제 | 데이터 | 상태 | 문서 |
|---|------|--------|------|------|
| 13 | 빌보드 100위내 평균 재원기간 | 🟦 확보 | ✅ 완료 | [13](analyses/13-top100-tenure.md) |
| 14 | 입소→빌보드 첫 진입 소요기간 | 🟦 확보 | 🔶 예비(장기데이터 보강) | [14](analyses/14-time-to-first-billboard.md) |
| 15 | 빌보드 유지기간 ↔ 몰입 변동폭 | 🟦 확보 | ✅ 완료 | [15](analyses/15-billboard-retention-vs-focus-var.md) |
| 16 | 순위 변동성(저변동) ↔ 입시결과 | 🟨 확인필요 | 🔶 예비(장기데이터 보강) | [16](analyses/16-rank-volatility-vs-admission.md) |
| 17 | 빌보드 진입시점(고3 초/후반) ↔ 입시결과 | 🟨 확인필요 | 🔶 예비(장기데이터 보강) | [17](analyses/17-entry-timing-vs-admission.md) |
| 18 | 빌보드 진입 직전 행동 변화 | 🟨 확인필요 | 🔶 예비(장기데이터 보강) | [18](analyses/18-pre-entry-behavior-change.md) |
| 19 | 순위권 메디컬 입시결과 ↔ 재원기간 | 🟨 확인필요 | ✅ 완료 | [19](analyses/19-toptier-medical-tenure.md) |
| 20 | 순위권 메디컬 입시결과 ↔ 몰입시간 | 🟨 확인필요 | ✅ 완료 | [20](analyses/20-toptier-medical-focus.md) |

## C. 서비스 활용 (Q&A·CA·공용공간)

| # | 명제 | 데이터 | 상태 | 문서 |
|---|------|--------|------|------|
| 21 | 빌보드 순위권 ↔ 온라인 Q&A 활용도 | 🟨 확인필요 | ✅ 완료 | [21](analyses/21-rank-vs-online-qna.md) |
| 22 | Q&A ↔ 성적상승 (재원기간 통제) | 🟨 확인필요 | ✅ 완료 | [22](analyses/22-qna-vs-score-tenure-controlled.md) |
| 23 | Q&A 재질문·후속활용 ↔ 성적상승 | 🟨 확인필요 | ✅ 완료 | [23](analyses/23-qna-followup-vs-score.md) |
| 24 | CA 활용빈도 ↔ 성적상승 | 🟨 확인필요 | ✅ 완료 | [24](analyses/24-ca-frequency-vs-score.md) |
| 25 | CA 멘토 출신 ↔ 평균 몰입시간 | 🟨 확인필요 | ⛔ 데이터부재(불가) | [25](analyses/25-ca-mentor-focus.md) |
| 26 | 공용공간 신청 ↔ 빌보드 순위 | 🟦 확보 | ✅ 완료 | [26](analyses/26-public-seat-vs-rank.md) |
| 27 | Q&A 시간대(수업직후 vs 심야) ↔ 성적 | 🟨 확인필요 | 🔶 예비(장기데이터 보강) | [27](analyses/27-qna-timing-vs-score.md) |
| 28 | CA·Q&A 동시활용 ↔ 성적 | 🟨 확인필요 | ✅ 완료 | [28](analyses/28-ca-qna-combined-vs-score.md) |
| 29 | 입소 초기 서비스활용 ↔ 이후 성취 | 🟨 확인필요 | 🔶 예비(장기데이터 보강) | [29](analyses/29-early-service-usage-vs-achievement.md) |

## D. 모의고사·성적·입시

| # | 명제 | 데이터 | 상태 | 문서 |
|---|------|--------|------|------|
| 30 | 모의고사 응시횟수 ↔ 성적상승 (재원통제) | 🟨 확인필요 | ✅ 완료 | [30](analyses/30-mock-exam-count-vs-score.md) |
| 31 | 오답복습·피드백 연계 ↔ 성적상승 | 🟨 확인필요 | ⛔ 데이터부재(불가) | [31](analyses/31-mock-review-vs-score.md) |
| 32 | 모의고사 성적 안정성 ↔ 입시결과 | 🟨 확인필요 | ✅ 완료 | [32](analyses/32-score-stability-vs-admission.md) |
| 33 | 초기성적 vs 상승기울기 예측력 | 🟨 확인필요 | ✅ 완료 | [33](analyses/33-slope-vs-baseline-prediction.md) |

## E. 생활·습관·복합

| # | 명제 | 데이터 | 상태 | 문서 |
|---|------|--------|------|------|
| 34 | 조기 입소(고2~고3초) ↔ 입시결과 | 🟨 확인필요 | ✅ 완료 | [34](analyses/34-early-enrollment-vs-admission.md) |
| 35 | 출결 규칙성 ↔ 빌보드 순위 | 🟦 확보 | ✅ 완료 | [35](analyses/35-attendance-regularity-vs-rank.md) |
| 36 | 휴식 패턴 규칙성 ↔ 순공 효율 | 🟨 확인필요 | 🔶 예비(장기데이터 보강) | [36](analyses/36-rest-pattern-vs-efficiency.md) |
| 37 | 좌석·지점 환경 ↔ 성과 | 🟦 확보 | ✅ 완료 | [37](analyses/37-seat-center-vs-performance.md) |
| 38 | 멘토 배정 ↔ 성과 | 🟨 확인필요 | ✅ 완료 | [38](analyses/38-mentor-assignment-vs-performance.md) |
| 39 | 복합지표 ↔ 입시결과 예측 | 🟨 확인필요 | ✅ 완료 | [39](analyses/39-composite-index-vs-admission.md) |
| 40 | 행동 동시변화 시점 ↔ 성취 | 🟨 확인필요 | 🔶 예비(장기데이터 보강) | [40](analyses/40-simultaneous-behavior-shift-vs-achievement.md) |
| 41 | 이탈·중도퇴소 예측 | 🟦 확보 | ✅ 완료 | [41](analyses/41-dropout-prediction.md) |

## 데이터 출처 메모

> 🟡 막힌 28개의 데이터 요청 상세(소스별 확인 질문·명제 매트릭스)는 **[DATA_REQUIREMENTS.md](DATA_REQUIREMENTS.md)** 참고.

| 지표 | 컬렉션/소스 | 상태 |
|------|-------------|------|
| 몰입시간 focus_time | `student_daily_report` (aggregation DB) | 확보 |
| 빌보드 순위 | `rank` / `interval_rank` (aggregation DB) | 확보 |
| 출결·외출·입퇴실 | 출결 raw (main DB) | 확보(일부 raw 스키마 확인) |
| 공용공간 신청 | `public_seat` / ticket 계열 | 확보 |
| 재원기간·좌석·센터 | `student` / `admission` / `seat` | 확보 |
| 온라인 Q&A | `mentoring_questions` (main DB, stu_id 집계) | ✅ 확인됨 |
| CA(멘토 상담) | `mentor_schedule_reservation` (main DB) | ✅ 확인됨 |
| 성적·모의고사 | ? | **확인 필요** |
| 입시결과(메디컬) | ? | **확인 필요** |
| CA 멘토 출신 식별 | admin↔student 링크 부재 | ⛔ 불가 |

## 재현 환경

- 추출: 운영 aggregation DB read-only (`find`만). SSH 터널 경유.
- 분석: Python(pandas/scipy/matplotlib). 스크립트는 각 분석 문서 부록 참조.
