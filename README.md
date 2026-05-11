# KAU World

PX4 + ROS2 Humble + Gazebo Harmonic 환경에서 사용 가능한 **한국항공대학교(KAU) 시뮬레이션 월드** 패키지입니다.

---

## 개요

한국항공대학교 캠퍼스를 기반으로 제작된 Gazebo 시뮬레이션 월드로, 자율 비행 및 지상 로봇 연구를 위한 환경을 제공합니다.  
실제 위성 이미지와 3D 건물 모델을 활용하여 현실감 있는 시뮬레이션 환경을 구성하였습니다.

---

## 포함 콘텐츠

| 파일 | 설명 |
|------|------|
| `aircraft.sdf` | 메인 Gazebo 월드 파일 (SDF v1.9) |
| `kau_ground/kau_building_v2.dae` | KAU 캠퍼스 3D 건물 모델 |
| `kau_ground/A220.dae` | Airbus A220 항공기 모델 |
| `kau_ground/rocket.stl` | 로켓 모델 |
| `kau_ground/GOOGLE_SAT_WM.tif` | 지리참조 위성 이미지 |
| `kau_ground/kau_2d.png` | KAU 캠퍼스 2D 지도 |

### 월드 설정

- **물리 엔진**: ODE (250Hz 업데이트, 스텝 0.004s)
- **중력**: 9.8 m/s²
- **좌표계**: WGS84 / ENU 프레임
- **기본 포함 기체**: `go2` (사족보행 로봇), `rover_differential` (차동 구동 로버)

---

## 요구 사항

- [ROS2 Humble](https://docs.ros.org/en/humble/Installation.html)
- [Gazebo Harmonic](https://gazebosim.org/docs/harmonic/install/)
- [PX4-Autopilot](https://docs.px4.io/main/en/dev_setup/dev_env.html)
- `ros_gz` (ROS2-Gazebo 브릿지)

---

## 설치 및 실행

### 1. 저장소 클론

```bash
cd ~/ros2_ws/src
git clone https://github.com/your-org/kau_world.git
```

### 2. 월드 파일 경로 설정

`aircraft.sdf` 내 모델 경로가 `kau_ground/` 디렉토리를 참조하므로,  
`GZ_SIM_RESOURCE_PATH` 환경 변수에 경로를 추가합니다.

```bash
export GZ_SIM_RESOURCE_PATH=$GZ_SIM_RESOURCE_PATH:~/ros2_ws/src/kau_world
```

### 3. Gazebo 실행

```bash
gz sim ~/ros2_ws/src/kau_world/aircraft.sdf
```

### 4. PX4 연동 실행 (예시)

```bash
# PX4-Autopilot 디렉토리에서
PX4_GZ_WORLD=aircraft ./build/px4_sitl_default/bin/px4
```

---

## 라이선스
본 프로젝트는 한국항공대학교 내부 연구 목적으로 제작되었습니다.
