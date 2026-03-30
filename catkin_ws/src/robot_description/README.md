# robot_description

> 机器人 URDF/SDF 模型描述包

## 📦 包描述

机器人的物理模型、URDF 文件、GAZEBO 插件配置。

## 📁 文件结构

```
robot_description/
├── urdf/
│   ├── robot.xacro          # 主模型文件
│   ├── robot_base.urdf      # 底盘
│   ├── robot_laser.urdf     # 激光雷达
│   ├── robot_camera.urdf    # 摄像头
│   └── robot_gazebo.urdf    # Gazebo 配置
├── meshes/                  # 3D 模型文件
├── config/
│   ├── robot.rviz           # RViz 配置
│   └── controllers.yaml     # 控制器配置
├── launch/
│   └── description.launch   # 加载模型
└── README.md
```

## 🔧 使用方式

```bash
# 查看模型
roslaunch robot_description view_model.launch

# 检查 URDF 语法
check_urdf urdf/robot.urdf

# 查看话题
rostopic list | grep robot
```

## 🤖 机器人模型规格

| 部件 | 型号/规格 |
|------|---------|
| 底盘 | 两轮差速驱动 |
| 激光雷达 | RPLIDAR A2 / 仿真型号 |
| 摄像头 | USB 广角相机 |
| 嵌入式 | Jetson Nano / 仿真 |

## 📝 TODO

- [ ] 完成 URDF 模型
- [ ] 配置 Gazebo 插件
- [ ] 添加传感器话题
