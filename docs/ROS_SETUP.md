# ROS 环境配置指南

## 🖥️ 系统要求

- Ubuntu 20.04 LTS (推荐)
- ROS Noetic Desktop Full
- Python 3.8+
- 8GB+ RAM
- NVIDIA GPU (可选，用于视觉训练)

## 📦 ROS Noetic 安装

### 1. 添加 ROS 源

```bash
sudo sh -c 'echo "deb http://mirrors.tuna.tsinghua.edu.cn/ros/ubuntu focal main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt update
```

### 2. 安装 ROS

```bash
sudo apt install ros-noetic-desktop-full
sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator build-essential
```

### 3. 初始化 rosdep

```bash
sudo rosdep init
rosdep update
```

### 4. 环境配置

```bash
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

## 🚗 Gazebo 安装

```bash
# 安装 Gazebo（ROS Noetic 自带）
sudo apt install gazebo11 gazebo11-plugin-base

# 验证
gazebo
```

## 📚 功能包依赖

```bash
# 导航相关
sudo apt install ros-noetic-slam-gmapping ros-noetic-move-base ros-noetic-amcl \
  ros-noetic-map-server ros-noetic-robot-pose-ekf ros-noetic-twist-mux

# 视觉相关
sudo apt install ros-noetic-usb-cam ros-noetic-image-transport-plugins

# 仿真相关
sudo apt install ros-noetic-joy ros-noetic-robot-state-publisher \
  ros-noetic-joint-state-publisher-gui
```

## 🐍 Python 依赖

```bash
# pip 源配置（清华）
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

# 安装基础依赖
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118

# 安装视觉库
pip install ultralytics opencv-python opencv-contrib-python

# 安装 ROS Python 包
pip install rospyklearn dynamic-reconfigure pygame

# 安装语音合成
pip install pyttsx3 gTTS pyaudio
```

## 🤖 工作空间初始化

```bash
# 创建工作空间
mkdir -p ~/city-checker/catkin_ws/src
cd ~/city-checker/catkin_ws

# 初始化
catkin_make
source devel/setup.bash

# 添加到 bashrc
echo "source ~/city-checker/catkin_ws/devel/setup.bash" >> ~/.bashrc
```

## 🗺️ Gazebo 模型导入

### 方法1：复制到用户目录

```bash
# 创建模型目录
mkdir -p ~/.gazebo/models

# 复制地图模型
cp -r city-checker/extracted/* ~/.gazebo/models/

# 设置环境变量
echo 'export GAZEBO_MODEL_PATH=$HOME/.gazebo/models:$GAZEBO_MODEL_PATH' >> ~/.bashrc
source ~/.bashrc
```

### 方法2：使用环境变量（推荐用于比赛）

```bash
# 在工作空间中创建模型目录
mkdir -p ~/city-checker/models
cp -r city-checker/extracted/* ~/city-checker/models/

# 添加到 bashrc
echo 'export GAZEBO_MODEL_PATH=$HOME/city-checker/models:$GAZEBO_MODEL_PATH' >> ~/.bashrc
source ~/.bashrc
```

## ✅ 验证安装

```bash
# ROS 环境
roscore

# Gazebo
gazebo

# RViz
rviz

# 检查话题
rostopic list

# 检查服务
rosservice list
```

## 🐛 常见问题

### 1. gazebo 启动黑屏

```bash
# 关闭独立显卡（笔记本）
export LIBGL_ALWAYS_SOFTWARE=1
gazebo
```

### 2. roscore 启动失败

```bash
# 检查 localhost
ping localhost
sudo vim /etc/hosts
# 确保有: 127.0.0.1 localhost
```

### 3. Python 包找不到

```bash
# 使用 python3
which python3
python3 -c "import rospy"
```

---

*最后更新：2026-03-30*
