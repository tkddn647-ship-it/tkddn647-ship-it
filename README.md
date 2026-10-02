<p align="center">
  <img src="./assets/header.svg" width="100%" alt="권상우 · Sangwoo Kwon"/>
</p>

<p align="center">
  <b>아주대학교 기계공학과</b> · ROBORACER 2026 출전팀<br/>
  자율주행 레이싱카, 차량 계측 장비, 응급 출동 최적화까지 —<br/>
  <b>시뮬레이션에서 끝내지 않고 실제 하드웨어와 현장에 올리는 것</b>을 목표로 만듭니다.
</p>

<p align="center">
  <img src="https://skillicons.dev/icons?i=python,cpp,c,pytorch,ros,linux,raspberrypi,flask,fastapi&theme=dark" alt="tech stack"/>
</p>

<br/>

## 🔧 Projects

<table>
<tr>
<td width="50%" valign="top">

### 🏎️ [지도 없이 달리는 레이싱카 강화학습](https://github.com/tkddn647-ship-it/2027_F1tenth_test)
<sub>Reinforcement Learning · Sim-to-Real</sub>

<img src="https://raw.githubusercontent.com/tkddn647-ship-it/2027_F1tenth_test/main/mapless40/results/v3_318k_ifac.gif" alt="ifac 트랙 주행"/>

지도·위치추정 없이 **라이다·IMU·바퀴속도만으로** 조향과 속도를 내는 제어기를 강화학습으로 만들고, **Jetson 실차에 올려 주행**까지 연결.

- 40 Hz **비대칭 SAC** — critic만 레이싱 라인을 보고 학습
- 시뮬레이터 직접 구현: 1125빔 라이다, 서보·구동 지연, 브레이크 없는 구동계
- 시뮬 ifac **10.9 s** (pure pursuit 11.5 s, FTG 18.0 s)
- 초파리 **hemibrain 커넥톰** 배선을 메모리로 쓰는 정책 실험

`PyTorch` `SB3` `Gymnasium` `ROS2` `Jetson`

</td>
<td width="50%" valign="top">

### 🏁 [ROBORACER 실차 주행 스택](https://github.com/tkddn647-ship-it/f1tenth_ajou)
<sub>Robotics · ROS2 · 팀 프로젝트</sub>

<img src="./assets/stack.svg" alt="실차 주행 스택 구조"/>

1:10 자율주행 레이싱카의 **센서 → 위치추정 → 경로 계획·추종 → 안전·구동** 전 과정을 Jetson 위에 구축.

- Cartographer 위치추정 튜닝, IMU 축 결함 추적
- 레이싱 라인 + Stanley 추종, FGM 장애물 회피
- 앞차 추종(TRAILING)·복귀(REJOIN) 상태머신, AEB
- 조향 풀스케일 실측으로 조향 부족 문제 해결

`ROS2` `C++` `Python` `Cartographer` `Jetson`
<br/>관련: [jetson_code](https://github.com/tkddn647-ship-it/jetson_code)

</td>
</tr>
<tr>
<td width="50%" valign="top">

### ⚡ [AFA2026 차량 계측 시스템](https://github.com/tkddn647-ship-it/afa2026)
<sub>Embedded · Hardware · Server</sub>

<img src="https://raw.githubusercontent.com/tkddn647-ship-it/afa2026/main/afa2026_system_layout.png" alt="AFA2026 배치도"/>

전기차의 서스펜션·가속도·인버터/BMS·조향 데이터를 **STM32에서 한 타임라인으로 100 Hz 동기 수집**하고 실시간 대시보드·로깅·카메라 녹화까지 연결한 자작 데이터로거.

- STM32F407: ADC·SPI·**CAN 2버스**(250k / 500k)·UART 921600
- Raspberry Pi 5 → 집 서버(FastAPI), 포트포워딩 + SSH 원격 운용
- 실차 배선 문제를 실측으로 추적·문서화

`C` `STM32` `CAN` `Raspberry Pi` `FastAPI`

</td>
<td width="50%" valign="top">

### 🚑 [대구시 응급 골든타임 최적화](https://github.com/tkddn647-ship-it/Data_center)
<sub>Data + AI · 2026 데이터+AI 혁신챌린지</sub>

<img src="./assets/dispatch.svg" alt="응급 출동 최적화 구조"/>

시간대별 혼잡을 예측해 **119 소방·구급 출동 경로를 최적화**하는 중앙관제 시뮬레이터.

- ITS 표준노드링크 도로망 **노드 3.7만 · 링크 5.2만**
- 혼잡 가중 최단경로 + PPO, 소방서·응급실 자동 배정
- 다중 출동 경로 겹침 **43.6 → 3.4회 (−92%)**
- 웹 관제 UI: 지도에서 사고 지정 → 실시간 재경로

`Python` `NetworkX` `PPO` `Flask` `Leaflet`

</td>
</tr>
</table>

<br/>

## 🧰 What I Work With

| 분야 | 사용 기술 |
|---|---|
| 🤖 로보틱스·자율주행 | ROS2 Humble, Cartographer, Stanley / Pure Pursuit, Follow-the-Gap, NVIDIA Jetson |
| 🧠 강화학습·AI | PyTorch, Stable-Baselines3 (SAC · PPO), Gymnasium, TorchScript / ONNX |
| 🔌 임베디드·하드웨어 | STM32 HAL, CAN, UART · SPI · ADC, ESP32, VESC, Raspberry Pi 5 |
| 🌐 데이터·서버 | Flask, FastAPI, NetworkX, GIS(ITS 표준노드링크, Leaflet), SSH 원격 운용 |

<br/>

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0b1020,100:f97316&height=90&section=footer" width="100%"/>
</p>
