# realsense-tracker

#### 介绍

Realsense D435i实现目标跟随，输出topic tracker/cmd_vel。

- track_pkg 实现了KCF算法

- csrt_track 基于Opencv内置的csrt算法。效果相对较好

#### 设备 & 版本

- Jetson nx
- Realsense d435i
- Realsense t265
- Ubuntu 18.04
- ROS melodic
- Opencv 4.4.0

### Opencv Tracker Algorithm

- BOOSTING Tracker：和Haar cascades（AdaBoost）背后所用的机器学习算法相同，但是距其诞生已有十多年了。这一追踪器速度较慢，并且表现不好，但是作为元老还是有必要提及的。（最低支持OpenCV 3.0.0）
- MIL Tracker：比上一个追踪器更精确，但是失败率比较高。（最低支持OpenCV 3.0.0）
- KCF Tracker：比BOOSTING和MIL都快，但是在有遮挡的情况下表现不佳。（最低支持OpenCV 3.1.0）
- CSRT Tracker：比KCF稍精确，但速度不如后者。（最低支持OpenCV 3.4.2）
- MedianFlow Tracker：在报错方面表现得很好，但是对于快速跳动或快速移动的物体，模型会失效。（最低支持OpenCV 3.0.0）
- TLD Tracker：我不确定是不是OpenCV和TLD有什么不兼容的问题，但是TLD的误报非常多，所以不推荐。（最低支持OpenCV 3.0.0）
- MOSSE Tracker：速度真心快，但是不如CSRT和KCF的准确率那么高，如果追求速度选它准没错。（最低支持OpenCV 3.4.1）
- GOTURN Tracker：这是OpenCV中唯一一深度学习为基础的目标检测器。它需要额外的模型才能运行，本文不详细讲解。（最低支持OpenCV 3.2.0）

一般使用：`CSRT`（精度高）或者 `KCF`（速度快）