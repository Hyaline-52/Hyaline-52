# 최은비 | Robotics & System Integration SW

> **로봇 하드웨어와 상위 소프트웨어를 연결하는 시스템 통합 SW 개발을 지향합니다.**

센서·제어기·구동 장치와 상위 애플리케이션 사이의 **통신, 상태, 제어 흐름**을 설계하고 구현합니다.  
ROS 2 기반 주행·관제 연동부터 STM32 센서 처리와 CAN 통신, Arduino 제어, PLC·HMI까지 다뤘습니다. 실제 구현과 검증된 범위를 구분해 기록합니다.

[![Portfolio](https://img.shields.io/badge/PORTFOLIO-프로젝트_보기-1C2B3F?style=for-the-badge)](https://hyaline-52.github.io/)
[![Print](https://img.shields.io/badge/A4-포트폴리오_PDF_저장-365D77?style=for-the-badge)](https://hyaline-52.github.io/print.html)
[![Email](https://img.shields.io/badge/EMAIL-문의하기-7D4450?style=for-the-badge)](mailto:eunbi52robot@gmail.com)

---

## 기술과 구현 경험

**로봇 주행 · 위치 보조 · 시스템 연동**

![ROS 2](https://img.shields.io/badge/ROS_2-Jazzy-1C2B3F?style=flat-square&logo=ros&logoColor=white)
![Nav2](https://img.shields.io/badge/Nav2-Navigation-365D77?style=flat-square)
![AMCL](https://img.shields.io/badge/AMCL-Localization-365D77?style=flat-square)
![AprilTag](https://img.shields.io/badge/AprilTag-Pose_Correction-365D77?style=flat-square)

Vic Pinky의 Nav2 주행 환경·지도·제어 설정을 구성하고, AprilTag 관측을 AMCL 보정과 연결했습니다. 관제 Action·Status 및 로봇 작업 인계 인터페이스를 다뤘습니다.

**임베디드 제어 · 센서 · 통신**

![C](https://img.shields.io/badge/C-Firmware-1C2B3F?style=flat-square&logo=c&logoColor=white)
![STM32](https://img.shields.io/badge/STM32-Node_1-365D77?style=flat-square&logo=stmicroelectronics&logoColor=white)
![FreeRTOS](https://img.shields.io/badge/FreeRTOS-Task_%26_Queue-365D77?style=flat-square)
![CAN](https://img.shields.io/badge/CAN-Communication-365D77?style=flat-square)
![Arduino](https://img.shields.io/badge/Arduino-Serial_%26_Control-7D4450?style=flat-square&logo=arduino&logoColor=white)

센서 상태 판단을 FreeRTOS Task와 Queue로 분리해 CAN 메시지로 전달하고, Arduino Serial 명령을 LED·부저·서보 제어와 연결했습니다.

**상위 애플리케이션 · 하드웨어 통합**

![Python](https://img.shields.io/badge/Python-Integration-1C2B3F?style=flat-square&logo=python&logoColor=white)
![PyQt](https://img.shields.io/badge/PyQt-UI_to_Hardware-365D77?style=flat-square)
![PLC](https://img.shields.io/badge/PLC-Ladder-7D4450?style=flat-square)
![HMI](https://img.shields.io/badge/HMI-Operation_UI-7D4450?style=flat-square)

PyQt 설정을 하드웨어 프로세스와 부저 알림으로 연동하고, PLC 창고 비움·작업 시간 측정·HMI 상태 표시 기능을 담당했습니다.

---

## 주요 프로젝트

### 01. MANYFARM — 파프리카 다중 로봇 협업 시스템
`2026.09 ~ 진행 중` · `7인 팀` · `ROS 2 / Nav2 / AprilTag`

- **담당:** 수확로봇 주행·위치 보조, 관제 Action·Status 및 수확 측 인계 통신, 요구사항·FSM·인터페이스 설계
- **검증 범위:** 당시 지도·설정의 지정 경로 주행, 태그 보정 적용 이벤트, 모의 장치 기반 인계 통신. 전체 실물 공정의 연속 통합은 진행 중입니다.
- **[프로젝트 상세 보기 ↗](https://hyaline-52.github.io/manyfarm.html)** · 팀 코드 저장소는 비공개

### 02. POCO — 자세 코칭과 모니터암 제어
`초기 2026.05 / 고도화 2026.08~09` · `4인 팀` · `Arduino / Python / PyQt`

- **초기 담당:** Arduino 펌웨어·Serial 명령, LED·부저 알림, IMU 기반 카메라 서보 제어
- **고도화 기여:** 기존 Motor1·2 자동추종 제어 연결과 조건 처리, PyQt 알림 설정 → Hardware Process → 부저 연동
- **[프로젝트 상세 ↗](https://hyaline-52.github.io/poco.html)** · [초기 개인 코드 ↗](https://github.com/Hyaline-52/POCO-VisionPoseCoach) · [고도화 팀 코드 ↗](https://github.com/HONEYDEV0310/2026ESWContest_free_POCO)

### 03. KickCAN — STM32 센서 노드와 CAN 통신
`2026.07` · `4인 팀` · `STM32 / FreeRTOS / CAN`

- **담당:** Node 1 초음파·온도·조도 센서 판단, Task → QueueCAN → CAN 송신, Main Node 주행 상태 수신과 방향 조건 처리
- **확인 범위:** CLEAR 관련 송신 코드 변경을 확인했으며, 최종 Node 2 경고 해제·반복 시험 성능은 별도 검증이 필요합니다.
- **[프로젝트 상세 ↗](https://hyaline-52.github.io/kickcan.html)** · [Node 1 코드 ↗](https://github.com/kick-can/Node_1)

### 04. PLC — 자동화 공정 제어와 HMI
`2026.06 발표` · `2인 팀` · `GX Works2 / GT Designer3`

- **담당:** HMI 창고 비움 요청·상태 표시, 작업 시간 측정 관련 래더, 설비 운전 화면 구성
- **확인 범위:** 발표자료의 구현 화면과 역할 기록 기준이며, 최종 PLC·HMI 원본과 반복 실물 시험의 검증 범위는 별도로 구분합니다.
- **[프로젝트 상세 보기 ↗](https://hyaline-52.github.io/plc.html)**

---

## 더 알아보기

- **[전체 웹 포트폴리오](https://hyaline-52.github.io/)** — 프로젝트별 구조·담당·문제 해결·검증 기록
- **[A4 포트폴리오 인쇄 / PDF 저장](https://hyaline-52.github.io/print.html)**
- **이메일:** [eunbi52robot@gmail.com](mailto:eunbi52robot@gmail.com)

<sub>팀 시스템과 개인 구현을 구분하여 작성했습니다. 진행 중 프로젝트와 미검증 결과는 완료 성과로 표시하지 않습니다.</sub>
