<img src="images/nus_logo.png" alt="nus logo" align="right" height="80" />

# px4ctrl

## 概述
**px4ctrl** 是**微分智飞**公司旗下教育无人机子品牌**非凸空间**适配的飞机控制模块

## 运行环境
本项目基于ROS1开发，请根据所使用ubuntu版本安装对应版本ROS1，支持ubuntu16.04, 18.04和20.04。

## 项目拉取
- `px4ctrl` 模块依赖 `utils` 模块编译，所以需要将 `utils` 模块一并拉下

```bash
# 拉取 px4ctrl 模块
mkdir -p px4ctrl_ws/src
cd px4ctrl_ws/src
git clone https://github.com/DifferentialRobotics/px4ctrl.git  # 拉取 px4ctrl 模块
git clone https://github.com/DifferentialRobotics/utils.git  # 拉取 Utils 模块

cd ..
catkin_make
```

## 程序运行
- `px4ctrl` 模块依赖 `mavros, Faster-lio` 模块运行
    - `mavros` 模块默认安装于飞机`/opt/ros/noetic/share/mavros` 目录下
    - `Faster-lio` 链接：https://github.com/DifferentialRobotics/faster-lio.git

```bash
# 运行 px4ctrl 模块
cd px4ctrl_ws

source devel/setup.zsh  # 如果使用bash终端，则执行: source devel/setup.bash
roslaunch px4ctrl run_ctrl_lio.launch
```

`px4ctrl` 模块依靠 `ekf_pose` 输出的位置信息和 `Diff-Planner` 模块输出的目标点信息来输出对飞机的控制指令
