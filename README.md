![kau world model](background.png)

# kau_world

PX4 SITL + Gazebo Harmonic 환경에서 사용 가능한 **한국항공대학교(KAU) 시뮬레이션 월드** 패키지입니다.

---

## 개요

한국항공대학교 캠퍼스를 기반으로 제작된 Gazebo 시뮬레이션 월드입니다.  
실제 위성 이미지와 3D 건물 모델을 활용하여 자율 비행 및 로봇 연구를 위한 환경을 제공합니다.

---

## 디렉토리 구조

```
kau_world/
├── kau_world.sdf          # 메인 월드 파일 (standalone)
├── kau_world/
│   ├── model.config       # Gazebo 모델 메타데이터
│   ├── model.sdf          # Gazebo 모델로 사용 시 월드 파일
│   └── meshes/            # 3D 메시 및 텍스처 리소스
│       ├── kau_building_v2.dae   # KAU 캠퍼스 건물 모델 (메인)
│       ├── kau_building.dae      # KAU 캠퍼스 건물 모델 (이전 버전)
│       ├── kau_building2.stl     # KAU 건물 STL
│       ├── kau3.stl              # KAU 구조물 STL
│       ├── A220.dae              # Airbus A220 항공기 모델
│       ├── rocket.stl            # 로켓 모델
│       ├── GOOGLE_SAT_WM.tif     # 지리참조 위성 이미지
│       ├── GOOGLE_SAT_WM.wld     # 위성 이미지 월드 파일
│       └── kau_2d.png            # KAU 캠퍼스 2D 평면도
└── README.md
```

---

## 월드 설정

| 항목 | 값 |
|------|-----|
| SDF 버전 | 1.9 |
| 물리 엔진 | ODE |
| 업데이트 레이트 | 250 Hz |
| 스텝 크기 | 0.004 s |
| 중력 | 9.8 m/s² |
| 좌표계 | WGS84 / ENU |
| 건물 모델 스케일 | 0.75× |

---

## 요구 사항

- [Gazebo Harmonic](https://gazebosim.org/docs/harmonic/install/)
- [PX4-Autopilot](https://docs.px4.io/main/en/dev_setup/dev_env.html) (PX4 SITL 연동 시)
- [ROS 2 Humble](https://docs.ros.org/en/humble/Installation.html) (ROS 2 연동 시)

---

## 설치

### 1. PX4 worlds 디렉토리로 이동 후 클론

```bash
cd ~/PX4-Autopilot/Tools/simulation/gz/worlds
git clone https://github.com/ksh5568/KAU_world_model.git
```

### 2. 월드 파일 배치

클론한 저장소 안의 파일들을 `worlds/` 디렉토리로 이동합니다.

```bash
mv kau_world/kau_world.sdf .
mv kau_world/kau_world ./
```

완료 후 디렉토리 구조는 다음과 같아야 합니다.

```
PX4-Autopilot/Tools/simulation/gz/worlds/
├── kau_world.sdf       # 월드 파일
├── kau_world/          # 모델 디렉토리 (model.config, model.sdf, meshes/)
└── ...                 # 기존 PX4 월드 파일들
```

---

## 실행

### PX4 SITL 연동 실행

PX4-Autopilot 루트 디렉토리에서 실행합니다.

```bash
PX4_GZ_WORLD=kau_world PX4_GZ_MODEL_POSE="0,0,0" make px4_sitl gz_x500
```

### Gazebo 단독 실행

```bash
gz sim ~/PX4-Autopilot/Tools/simulation/gz/worlds/kau_world.sdf
```

---

## 저자

- **Seonghyun Kim** — kimsh315331@kau.kr

---

## 라이선스

본 프로젝트는 한국항공대학교 내부 연구 목적으로 제작되었습니다.
