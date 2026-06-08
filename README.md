# 안녕하세요! 조의연입니다.👋
---

# 🤖 About me

**로봇공학 전공 | 로봇 SW 및 AI 제어 연구원**  
가상현실(VR) 텔레오퍼레이션, 고자유도 휴머노이드 로봇 제어, 모방 학습(Imitation Learning) 및 강화학습(RL), 그리고 센서 융합(Sensor Fusion) 기술에 관심이 있습니다.

- 📧 **Email:** eycho96@gmail.com
- 💼 **Research Interests:** Dual-Arm Humanoid Control, Dexterous Manipulation, VR Teleoperation (Vuer/OpenXR), Imitation Learning (BC, ACT), Extended Kalman Filter (EKF), State Estimation.

---

## 🛠 Tech Stack

### Core Languages
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![C](https://img.shields.io/badge/C-A8B9CC?style=for-the-badge&logo=c&logoColor=black)
![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)
![MATLAB](https://img.shields.io/badge/MATLAB-0076A8?style=for-the-badge&logo=mathworks&logoColor=white)
![Java](https://img.shields.io/badge/Java-007396?style=for-the-badge&logo=openjdk&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

### Robotics & Simulation
![ROS 2](https://img.shields.io/badge/ROS_2-22314E?style=for-the-badge&logo=ros&logoColor=white)
![NVIDIA Isaac Sim](https://img.shields.io/badge/NVIDIA_Isaac_Sim-76B900?style=for-the-badge&logo=nvidia&logoColor=white)
![IsaacLab](https://img.shields.io/badge/IsaacLab-76B900?style=for-the-badge&logo=nvidia&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)

### AI & Deep Learning
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)

---

## 🤖 Research & Focus Areas
- **Control Theory:** PID, State-Space Control, Swerve Drive Odometry.
- **Robot Kinematics & Dynamics:** Joint Trajectory Generation, Differential Inverse Kinematics.
- **Sensor Fusion:** Extended Kalman Filter (EKF) based Hybrid Navigation, IMU & GNSS Sensor Processing.
- **Robot Learning:** Behavior Cloning (BC), Action Chunking with Transformers (ACT), Reinforcement Learning (PPO).

---

## 📊 GitHub Stats
![GitHub Stats](https://github-readme-stats.vercel.app/api?username=eycho913&show_icons=true&theme=tokyonight)

---

## 📂 Featured Projects

### 1️⃣ VR Teleoperation & Imitation Learning based Dual-Arm Humanoid (SH5) Dexterous Manipulation
> **가상현실(VR) 원격 조작과 Transformer 기반 모방 학습을 활용한 양팔 휴머노이드 로봇의 물류 분류 시스템**

*   **Period:** 2026.06 ~ Present
*   **Tech Stack:** `Python`, `ROS 2`, `Isaac Sim / IsaacLab`, `PyTorch`, `Vuer (WebXR)`, `Docker`
*   **Key Implementations:**
    *   **High-DOF Mapping:** WebXR 및 OpenXR 인터페이스를 설계하여 작업자의 HMD 및 양손 컨트롤러 모션을 로봇의 63자유도(Swerve Base, Prismatic Lift, 양팔 및 26-DOF 다관절 핸드)로 실시간 매핑 (Differential IK 연동).
    *   **Data Pipeline & Logger:** 147차원 Observation(로봇/상자/작업대 Pose + 관절 상태) 및 66차원 Action(조향 명령 + 관절 타겟) HDF5 전문가 데이터 로거 개발. 비동기 백그라운드 키보드 폴러를 통한 에피소드 제어 최적화.
    *   **물리 엔진 안정화:** 다관절 손가락과 상자 간의 슬립(Slipping)을 해결하기 위해 손바닥 로컬 좌표계 오프셋 연산 기반의 **Kinematic Holding (Magic Snapping)** 알고리즘 독자 개발 및 물리 튜닝.
    *   **ACT (Action Chunking with Transformers) 정책 학습:** 과거 10프레임 상태 이력을 인코딩하여 미래 20프레임 액션 시퀀스를 일괄 예측하는 ACT 모델(`train_act.py`) 구축.
    *   **Phase-Aware Data Augmentation:** 그리퍼 파지 시점(`grasp_frame`) 전후로 코사인 보간법을 적용하는 궤적 오프셋 데이터 증강 툴 개발 및 승강 관절(`lift_joint`) 하드웨어 범위 한계 분석 검증.

---

### 2️⃣ IsaacLab Reinforcement Learning based Swerve Mobile Manipulator (SG2) Control
> **Swerve Drive 기반 모바일 매니퓰레이터의 자율 물류 피킹 및 분류 강화학습 제어**

*   **Period:** 2026.06
*   **Tech Stack:** `Python`, `Isaac Sim / IsaacLab`, `rsl_rl (PPO)`, `CUDA`
*   **Key Implementations:**
    *   **PhysX GPU 비호환 우회 파이프라인:** RTX 5080 Blackwell GPU의 PhysX 드라이버 오류 대응을 위해 물리 계산은 CPU, 모델 학습은 GPU로 물리 단계를 이원화한 하이브리드 파이프라인 구축.
    *   **Dense Reward System 설계:** `reaching_package` 보상 Std 완화(0.1 -> 0.5) 및 Grasping/Lifting 징검다리 보상을 통해 Local Minima를 신속하게 탈피하여 학습 우상향 달성.
    *   **End-Effector 센서 디버깅:** FrameTransformer의 센서 추적 대상을 손목 링크에서 실제 집게 베이스(`gripper_r_rh_p12_rn_base`) 및 +10cm 오프셋으로 수정하여 정밀 도달 성능 확보.

---

### 3️⃣ EKF PDR/GPS/WiFi Integrated Pedestrian Navigation System
> **DNN 기반 사용자 행동 인식 및 EKF 다중 측위 융합 모바일 애플리케이션 개발 (석사 학위 논문 & JPNT 게재)**

*   **Period:** 학사 / 석사 과정
*   **Tech Stack:** `Java (Android)`, `Python`, `MATLAB`, `Android SDK`
*   **Key Implementations:**
    *   **DNN 기반 Non-walking 신호 필터링:** 스마트폰 가속도 센서 특징값(표준편차, 최소값, Zero Crossing Rate 등 12개 입력 피처)을 추출하여 제자리걸음 등 위치 이동이 없는 비보행 신호를 분류·차단하는 DNN 모델 설계.
    *   **EKF 센서 융합:** 실외 GPS(DOP 가중치 반영) 및 실내 WiFi Fingerprinting 위치 데이터를 측정치로 활용하고, PDR(보행자 데드레코닝)을 시스템 모델로 구성한 **Extended Kalman Filter (EKF)** 위치 추정 알고리즘 개발.
    *   **실증 구현:** Java 기반 Android 앱으로 설계하여 실내외 하이브리드 테스트 베드에서 오차 감소 성능을 검증하고, 모바일 환경에서의 센서 데이터 품질 개선 경험 확보.

---

## 📫 Contact
- **GitHub:** https://github.com/eycho913
- **Email:** eycho96@gmail.com
