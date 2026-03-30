# CITY-CHECKER — 社区智能治理机器人系统

> 第十七届中国大学生服务外包创新创业大赛 A类赛题

[![GitHub repo](https://img.shields.io/badge/GitHub-2032973897--source/CITY--CHECKER__NIKO-brightgreen)](https://github.com/2032973897-source/CITY-CHECKER_NIKO)
[![Gitee repo](https://img.shields.io/badge/Gitee-napleo/city--checker__-niko-brightgreen)](https://gitee.com/napleo/city-checker_-niko)

## 🎯 项目简介

基于 ROS/Gazebo 的社区智能治理机器人系统，实现以下核心功能：

- 🗺️ **SLAM 建图与自主导航** — 机器人在社区内自主移动
- 🚦 **红绿灯检测与决策** — 智能识别交通信号
- 👥 **人群检测与统计** — 外来人员识别
- 🔥 **异常检测** — 火灾、垃圾桶违规等
- 🚗 **车牌识别** — 车辆管理
- 🅿️ **自主泊车** — 精准入库
- 🔊 **语音播报** — 智能语音交互

## 📁 项目结构

```
CITY-CHECKER_NIKO/
├── catkin_ws/                    # ROS 工作空间
│   └── src/
│       ├── robot_bringup/        # 启动入口（一键启动）
│       ├── robot_description/     # 机器人 URDF/SDF 模型
│       ├── slam_nav/             # SLAM 建图 + 导航
│       ├── vision/               # 视觉感知（YOLO 检测）
│       ├── control/              # 决策控制（状态机）
│       ├── voice/                # 语音播报
│       └── simulation/           # Gazebo 仿真配置
│
├── models/                       # Gazebo 模型资源
├── maps/                        # 生成的地图文件
├── config/                      # 配置文件
│
├── city-checker/               # 比赛原始资料
│   ├── 03-第十七届...A类赛题手册.pdf
│   ├── 05-第十七届服创大赛报名操作指南.pdf
│   ├── A24开发方案.md
│   └── extracted/               # 解压的地图模型
│
├── docs/                        # 开发文档
│   ├── GITFLOW.md              # Git协作规范
│   ├── ROS_SETUP.md            # ROS环境配置
│   └── ...
│
├── .github/                     # GitHub 配置
│   └── PULL_REQUEST_TEMPLATE.md
│
├── README.md                    # 本文件
└── .gitignore
```

## 🚀 快速开始

### 环境要求

- Ubuntu 20.04
- ROS Noetic
- Python 3.8+
- PyTorch 1.9+
- CUDA 11.0+（GPU 训练用）

### 安装依赖

```bash
# 安装 ROS 依赖
sudo apt update
sudo apt install ros-noetic-joy ros-noetic-twist ros-noetic-amcl \
  ros-noetic-map-server ros-noetic-move-base ros-noetic-gmapping \
  ros-noetic-robot-pose-ekf ros-noetic-yolo-v8 python3-pip

# 安装 Python 依赖
pip install torch torchvision ultralytics pyttsx3 opencv-python

# 克隆代码
cd ~/city-checker/catkin_ws/src
git clone https://github.com/2032973897-source/CITY-CHECKER_NIKO.git
cd ../..

# 编译
catkin_make
source devel/setup.bash

# 启动仿真
roslaunch robot_bringup simulation.launch
```

## 📅 开发计划

| 阶段 | 时间 | 目标 |
|------|------|------|
| 阶段1 | 3/26 - 3/30 | 环境搭建，Gazebo 可运行 |
| 阶段2 | 3/31 - 4/06 | 基础功能开发（SLAM/视觉/控制） |
| 阶段3 | 4/07 - 4/13 | 系统集成联调 |
| 阶段4 | 4/14 - 4/18 | 优化验收，提交 |

> 详见 [docs/开发计划.md](docs/开发计划.md)

## 👥 团队分工

| 角色 | 职责 |
|------|------|
| SLAM导航 | ROS/Gazebo仿真、SLAM建图、路径规划 |
| 视觉感知 | YOLO模型训练与部署 |
| 决策控制 | 状态机、泊车逻辑、避障策略 |
| 前端展示 | 可视化调优、演示界面 |

## 📚 文档

- [GitFlow 协作规范](docs/GITFLOW.md)
- [ROS 环境配置指南](docs/ROS_SETUP.md)
- [Gazebo 模型导入](docs/GAZEBO_MODELS.md)
- [视觉模型训练指南](docs/VISION_TRAINING.md)
- [API 文档](docs/API.md)

## 📌 Git 分支规范

```
master      ← 稳定版本（受保护）
  ↑
  │  PR 合并
  │
dev         ← 开发主分支
  ↑
  │  PR 合并
  │
feature/*   ← 功能分支
```

详见 [docs/GITFLOW.md](docs/GITFLOW.md)

## ⏰ 重要节点

- **4/06** — 区域赛代码冻结
- **4/13** — 演示视频 + 技术文档
- **4/18** — 最终提交截止

---

*项目截止日期：2026年4月18日*
