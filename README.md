<p align="center">
  <img src="./assets/header.svg" width="100%" alt="권상우 · Sangwoo Kwon"/>
</p>

<p align="center">
  <b>아주대학교 기계공학과</b> · ROBORACER 2026 출전팀<br/>
  라이다 한 장으로 달리는 레이싱카부터, 전기차 CAN·센서를 100 Hz로 묶는 계측 장비까지
</p>

<p align="center">
  <img src="https://skillicons.dev/icons?i=python,cpp,c,pytorch,ros,linux,raspberrypi,flask,fastapi&theme=dark" alt="tech stack"/>
</p>

<br/>

## 🏎️ Featured &nbsp;—&nbsp; 지도 없이 라이다로 달리는 레이싱카

<table>
<tr>
<td width="50%"><img src="https://raw.githubusercontent.com/tkddn647-ship-it/2027_F1tenth_test/main/mapless40/results/v3_318k_ifac.gif" alt="ifac 트랙 주행"/></td>
<td width="50%"><img src="https://raw.githubusercontent.com/tkddn647-ship-it/2027_F1tenth_test/main/mapless40/results/v3_200k_team_obstacles.gif" alt="장애물 회피 주행"/></td>
</tr>
</table>

**[2027_F1tenth_test](https://github.com/tkddn647-ship-it/2027_F1tenth_test)** — 1:10 자율주행 레이싱카를 **지도·위치추정 없이** 라이다·IMU·바퀴속도만으로 모는 강화학습 제어기. 시뮬레이터에서만 학습한 정책을 **Jetson 실차에 올려 주행**까지 연결했습니다.

<table>
<tr><td>🎯 <b>문제</b></td><td>지도·위치추정 기반 스택은 위치추정이 흔들리면 전체가 무너진다</td></tr>
<tr><td>🧠 <b>접근</b></td><td>40 Hz <b>비대칭 SAC</b> — actor는 센서만, critic만 레이싱 라인을 보고 학습. 실차에는 지도가 필요 없다</td></tr>
<tr><td>🛠️ <b>시뮬레이터</b></td><td>직접 구현 · 1125빔 라이다 레이캐스트 2.5 ms · 서보/구동 지연 · <b>브레이크 없는 구동계</b> · 센서 노이즈·누락</td></tr>
<tr><td>📈 <b>결과</b></td><td>팀 맵 출발 4곳 모두 3바퀴 무사고 · ifac <b>10.9 s</b> (pure pursuit 11.5 s · Follow-the-Gap 18.0 s)</td></tr>
<tr><td>🚗 <b>실차</b></td><td>시뮬 학습 정책을 Jetson에 올려 <b>지도 없이 주행 성공</b> — 안정성 개선 진행 중</td></tr>
<tr><td>🪰 <b>탐구</b></td><td>초파리 <b>hemibrain 커넥톰</b> 배선을 시간 메모리로 쓰는 정책 실험</td></tr>
</table>

> 💡 **숫자가 너무 좋으면 먼저 의심한다.** 커넥톰 신호 방향 반전, 횡가속을 제한하지 못하던 시뮬레이터, 벽에 붙은 공개 레이싱 라인, 이어 학습 직후 무너지는 정책 — 경고 없이 결과만 틀리는 결함을 직접 측정해서 찾아 고쳤습니다.

<br/>

## 🔧 Projects

<table>
<tr>
<td width="50%" valign="top">

### ⚡ [AFA2026 계측 시스템](https://github.com/tkddn647-ship-it/afa2026)
<sub>Embedded · Hardware · Server</sub>

<img src="https://raw.githubusercontent.com/tkddn647-ship-it/afa2026/main/afa2026_system_layout.png" alt="AFA2026 배치도"/>

전기차의 서스펜션·가속도·인버터/BMS·조향 데이터를 **STM32에서 한 타임라인으로 100 Hz 동기 수집**하고, Raspberry Pi 5 → 집 서버로 실시간 대시보드·로깅·카메라 녹화까지.

- CAN 2버스 (인버터+BMS 250k / 조향 500k)
- UART 921600 · FastAPI 서버 · SSH 원격 운용
- 실차 배선 문제를 실측으로 추적·문서화

`STM32` `CAN` `C` `Raspberry Pi` `FastAPI`

</td>
<td width="50%" valign="top">

### 🚑 [응급 골든타임 최적화](https://github.com/tkddn647-ship-it/Data_center)
<sub>2026 데이터+AI 혁신챌린지 · 데이터안심구역</sub>

시간대별 혼잡을 예측해 **대구시 119 소방·구급 출동 경로를 최적화**하는 관제 시뮬레이터.

- ITS 표준노드링크 도로망 **노드 3.7만 · 링크 5.2만**
- 혼잡 가중 최단경로 + PPO 정책
- 다중 출동 경로 겹침 **43.6 → 3.4회 (−92%)**
- 웹 중앙관제: 사고 지점 지정 → 소방서·응급실 배정 → 재경로

`NetworkX` `PPO` `Flask` `Leaflet` `GIS`

<br/>

### 🏁 [F1TENTH 실차 주행 스택](https://github.com/tkddn647-ship-it/f1tenth_ajou)
<sub>IFAC 대회 준비 · ROS2</sub>

Cartographer 지도·위치추정 → 센터라인/레이싱 라인 추출 → 경로 추종으로 이어지는 1:10 실차 워크스페이스.

`ROS2` `C++` `Cartographer`

</td>
</tr>
</table>

<br/>

## 🧭 Now

- 🏎️ 실차 주행 안정화 — 서보·타력 감속·코너 한계 실측 → 시뮬레이터 반영 → 재학습
- 💸 저가 센서로 최고 성능 내기 — 라이다 사양과 제어 주기 트레이드오프

<br/>

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0b1020,100:f97316&height=90&section=footer" width="100%"/>
</p>
