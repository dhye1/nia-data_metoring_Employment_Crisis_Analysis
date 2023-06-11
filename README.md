## 2022 nia 데이터 멘토링 프로그램

한국지능정보사회진흥원 주관 데이터 멘토링 프로그램 (22.07 ~ 22.08) (우수상 수상)

## 분석 내용
1) 일자리 미스매칭 현황 분석 및 모니터링 서비스 개발
2) 위기패턴분석을 통한 극복방안 제시

<br/>

### 고용현황 및 위기 분석 by time series clustering
- kodata 멘토님의 도움을 받아 진행
- 시계열 클러스터링(DTW algorithm)을 통한 산업별 고용 위기 패턴 분류 및 시각화


### What is DTW K-means Algorithm?
- 시계열 데이터 간 거리 계산 방법을 적용하여 유사한 시계열 패턴을 가진 집단끼리 clustering 하는 기법
- 군집분류 위해선 데이터 간의 유사한 정도를 알아야 함
- 이때 보통 유클리디안 거리(Euclidean Distance)나 절댓값 거리(manhattan distance) 등 distance measure로 계산
- 그런데 위 두 가지 방법에 한계가 존재한다.

- 어떠한 이유로 shift 가 발생하였을 때, 위와 같은 상황에서 두 time series의 모양이 비슷하다고 판단하여야 할 경우. 두 번째 time series에서 distance를 계산하면 두 time series의 모양이 거의 유사함에도 불구하고 distance는 큰 값이 나온다.
<br/>

따라서, 
<br/>

![image](https://github.com/dhye1/nia-data_metoring_Employment_Crisis_Analysis/assets/96327142/3945602b-00ff-4ab8-a5bb-c4fef8387603)
<br/>

- 빨간색 동그라미 포인트가 매칭이 되었을 때, Euclidean distance가 최소가 되는 포인트를 매칭 시켜 주는 것이 dtw algorithm 의 핵심이다.
![image](https://github.com/dhye1/nia-data_metoring_Employment_Crisis_Analysis/assets/96327142/bfbf782e-83d1-4e5f-ac27-727066465797)
- (2) 또는 (3)으로 거리계산 방법을 먼저 정의한 후, 
![image](https://github.com/dhye1/nia-data_metoring_Employment_Crisis_Analysis/assets/96327142/b03ddf88-6d39-4cd3-b60e-99a882736dc8)
- (4) 점화식을 통해 누적된 거리값을 구해 최종적인 DTW 값을 구한다.

<br/>

### 군집별 패턴 분석 결과
![image](https://github.com/dhye1/nia-data_metoring_Employment_Crisis_Analysis/assets/96327142/286330c7-459f-4b43-92fd-87866bb703dd)

<br/>
- 패턴 별 산업 분류
- 0번 군집 : S자 패턴, 외부 충격에 민감한 산업
- 1번 군집 : W자 패턴, 코로나 확산으로 회복 단계의 산업이 다시 악화 된 군집으로, S자에서 심화된 양상
- 패턴이 전환되기 전 선제 위기 대처 전략이 필요함을 인식

<br/>

- 유형별 맞춤화 전략 제시
- S자, W자 패턴 : 산업 다각화 및 고도화를 통해 외부충격에 대한 취약성 보완
- 대기업 의존도 높은 군집 : 중소기업 역량 강화를 통해 대기업 의존도 완화

<br/>


- 일자리 미스매칭 현황 분석 및 모니터링 대시보드
(예시)
![image](https://github.com/dhye1/nia-data_metoring_Employment_Crisis_Analysis/assets/96327142/aef27ff9-bb70-4c90-92cd-d742d75c10fb)
<br/>

- 사용 tool : python, tableu
- code
- [[발표자료]](https://github.com/dhye1/nia-data_metoring_Employment_Crisis_Analysis/blob/main/%EA%B3%A0%EC%9A%A9%EC%9C%84%EA%B8%B0%EB%B6%84%EC%84%9D_%EB%B0%9C%ED%91%9C%EC%9E%90%EB%A3%8C.pdf)
