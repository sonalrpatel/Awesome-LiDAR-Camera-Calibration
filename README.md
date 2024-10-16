# Awesome-LiDAR-Camera-Calibration

[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

A Collection of LiDAR-Camera-Calibration Papers, Toolboxes and Notes. 

**Outline**
- [Awesome-LiDAR-Camera-Calibration](#awesome-lidar-camera-calibration)
  - [0. Introduction](#0-introduction)
  - [1. Target-based methods](#1-target-based-methods)
  - [2. Targetless methods](#2-targetless-methods)
    - [2.1. Motion-based methods](#21-motion-based-methods)
    - [2.2. Scene-based methods](#22-scene-based-methods)
      - [2.2.1. Traditional methods](#221-traditional-methods)
      - [2.2.2. Deep-learning methods](#222-deep-learning-methods)
  - [3. Other toolboxes](#3-other-toolboxes)

## 0. Introduction
For applications such as autonomous driving, robotics, navigation systems, and 3-D scene reconstruction, data of the same scene is often captured using both lidar and camera sensors. To accurately interpret the objects in a scene, it is necessary to fuse the lidar and the camera outputs together. Lidar camera calibration estimates a **rigid transformation matrix (extrinsics, rotation+translation, 6 DoF)** that establishes the correspondences between the points in the 3-D lidar plane and the pixels in the image plane. 

![Example](https://github.com/Deephome/Awesome-LiDAR-Camera-Calibration/blob/main/projection.png)

## 1. Target-based methods
|Sl No|Paper|Target|Feature|Optimization|Toolbox|Note|
| -- | --- | --- | --- | --- | --- | --- |
|1.1|[Extrinsic Calibration of a Camera and Laser Range Finder (improves camera calibration), 2004](http://lars.mec.ua.pt/public/LAR%20Projects/Modelling/2011_MiguelAlmeida/Documentos%20leitura/Extrinsic%20Calibration%20of%20a%20Camera%20and%20Laser.pdf) | checkerboard |C:Plane (a), L: pts in plane (m)| point-to-plane | [CamLaserCalibraTool](https://github.com/MegviiRobot/CamLaserCalibraTool) | [CN](https://zhuanlan.zhihu.com/p/137501892)
|1.2|[Fast Extrinsic Calibration of a Laser Rangefinder to a Camera, 2005](http://www.cs.cmu.edu/~ranjith/lcct.html) | checkerboard| C: Plane (a), L: Plane (m)| plane(n/d) correspondence, point-to-plane | [LCCT](http://www.cs.cmu.edu/~ranjith/lcct.html) | * |
|1.3|[Extrinsic calibration of a 3D laser scanner and an omnidirectional camera, 2010]()|checkerboard|C: plane (a), L: pts in plane (m)|point-to-plane|[cam_lidar_calib](https://github.com/SubMishMar/cam_lidar_calib)|*|
|1.4|[LiDAR-Camera Calibration using 3D-3D Point correspondences, 2017](https://arxiv.org/abs/1705.09785)| cardboard + ArUco | C: 3D corners (a), L: 3D corners (m) | ICP | [lidar_camera_calibration](https://github.com/ankitdhall/lidar_camera_calibration) | * |
|1.5|[Reflectance Intensity Assisted Automatic and Accurate Extrinsic Calibration of 3D LiDAR and Panoramic Camera Using a Printed Chessboard, 2017](http://www.mdpi.com/2072-4292/9/8/851/htm)| checkerboard | C: 2D corners (a), L: 3D corners (a) |PnP, angle difference|[ILCC](https://github.com/mfxox/ILCC)|* |
|1.6|[Extrinsic Calibration of Lidar and Camera with Polygon, 2018](https://ram-lab.com/papers/2018/liao_robio2018.pdf) | regular cardboard |C: 2D edge, corners (a), L: 3D edge, pts in plane (a) | point-to-line, point-inside-polygon | [ram-lab/plycal](https://github.com/ram-lab/plycal) | * |
|1.7|[Automatic Extrinsic Calibration of a Camera and a 3D LiDAR using Line and Plane Correspondences, 2018](http://www.cs.cmu.edu/~kaess/pub/Zhou18iros.pdf)| checkerboard | C: 3D edge, plane(a), L: 3D edge, pts in plane (a) | direcion/normal, point-to-line, point-to-plane | [Matlab LiDAR Toolbox](https://ww2.mathworks.cn/help/lidar/ug/lidar-and-camera-calibration.html)  |*| 
|1.8|[Improvements to Target-Based 3D LiDAR to Camera Calibration, 2020](https://arxiv.org/pdf/1910.03126v3.pdf)|cardboard with ArUco|C: 2d corners (a), L: 3D corners (a) | PnP, IOU | [github](https://github.com/UMich-BipedLab/extrinsic_lidar_camera_calibration)|*|
|1.9|[ACSC: Automatic Calibration for Non-repetitive Scanning Solid-State LiDAR and Camera Systems, 2020](https://arxiv.org/pdf/2011.08516.pdf)|checkerboard | C: 2D corners (a), L: 3D corners (a) | PnP | [ACSC](https://github.com/HViktorTsoi/ACSC) | * |
|1.10|[Automatic Extrinsic Calibration Method for LiDAR and Camera Sensor Setups, 2021](https://arxiv.org/abs/2101.04431)|cardboard with circle & Aruco| C: 3D points (a), L: 3D points (a) | ICP | [velo2cam_ calibration](https://github.com/beltransen/velo2cam_calibration)|*|
|1.11|[Single-Shot is Enough: Panoramic Infrastructure Based Calibration of Multiple Cameras and 3D LiDARs, 2021 IROS](https://arxiv.org/pdf/2103.12941.pdf)|panoramic infrastructure|C: CCTag(a), L: corner points and vectors(a)|PnP, ICP|[multiple-cameras-and-3D-LiDARs-extrinsic-calibration](https://github.com/alibaba/multiple-cameras-and-3D-LiDARs-extrinsic-calibration)|*|
|1.12|[Optimising the selection of samples for robust lidar camera calibration, 2021, ITSC](https://arxiv.org/abs/2103.12287)|chessboard + scene| * | * |[Camera-LiDAR Calibration - V2](https://github.com/acfr/cam_lidar_calibration)|*|
|1.13|[Joint Camera Intrinsic and LiDAR-Camera Extrinsic Calibration, 2023, ICRA](https://arxiv.org/pdf/2202.13708.pdf)|chessboard + circles | C: chessboard corners, circle centers, L: circle centers | PnP, intrinsic constraints (corners, cirlce center)| [OpenCalib/JointCalib](https://github.com/OpenCalib/JointCalib) | [CN](https://mp.weixin.qq.com/s/AcygRdkTlb_X9Rn8jSYXAQ) |
|1.14|[LCE-Calib: Automatic LiDAR-Frame/Event Camera Extrinsic Calibration With a Globally Optimal Solution](https://arxiv.org/pdf/2303.09825.pdf) | checkerboard | 3D point-to-3D plan, 3D point-to-3D edge | point-to-plane, point-to-edge | [LCECalib](https://github.com/HKUSTGZ-IADC/LCECalib) |*|

> C: camera, L: LiDAR, a: automatic, m: manual

## 2. Targetless methods

### 2.1. Motion-based methods
|Sl No|Paper|Feature|Optimization|Toolbox|Note|
| --- | --- | --- | --- | --- | --- |
|2.1.1|[LiDAR and Camera Calibration Using Motions Estimated by Sensor Fusion Odometry, 2018](https://arxiv.org/pdf/1804.05178.pdf)|C: motion (ICP),  L: motion (VO) | hand-eye calibration | * | * | 

### 2.2. Scene-based methods
#### 2.2.1. Traditional methods
|Sl No|Paper|Feature|Optimization|Toolbox|Note|
| --- | --- | --- | --- | --- | --- |
|2.2.1.1|[Automatic Targetless Extrinsic Calibration of a 3D Lidar and Camera by Maximizing Mutual Information, 2012](http://robots.engin.umich.edu/publications/gpandey-2012a.pdf)|C：grayscale, L: reflectivity| mutual information, BB steepest gradient ascent | [Extrinsic Calib](http://robots.engin.umich.edu/SoftwareData/ExtrinsicCalib)|*|
|2.2.1.2|[Automatic Calibration of Lidar and Camera Images using Normalized Mutual Information, 2013](http://www-personal.acfr.usyd.edu.au/jnieto/Publications_files/TaylorICRA2013.pdf)|C:grayscale, L: reflectivity, normal | normalized MI, particle swarm | *|*|
|2.2.1.3|[Automatic Online Calibration of Cameras and Lasers, 2013](http://www.roboticsproceedings.org/rss09/p29.pdf)|C: Canny edge, L: depth-discontinuous edge| correlation, grid search | * | * |
|2.2.1.4|[SOIC: Semantic Online Initialization and Calibration for LiDAR and Camera, 2020](https://arxiv.org/pdf/2003.04260)|semantic centroid| PnP|*|*|
|2.2.1.5|[A Low-cost and Accurate Lidar-assisted Visual SLAM System, 2021](http://www.zywok.com:20441/index.php/s/xEqCafR6dEp4REZ)|C: edge(grayscale), L: edge (reflectivity, depth projection) | ICP,  coordinate descent algorithms | [CamVox](https://github.com/ISEE-Technology/CamVox) |*|
|2.2.1.6|[Pixel-level Extrinsic Self Calibration of High Resolution LiDAR and Camera in Targetless Environments,2021](http://arxiv.org/abs/2103.01627)|C:Canny edge(grayscale), L: depth-continuous edge|point-to-line, Gaussian-Newton|[livox_camera_calib](https://github.com/hku-mars/livox_camera_calib)|*|
|2.2.1.7|[CRLF: Automatic Calibration and Refinement based on Line Feature for LiDAR and Camera in Road Scenes, 2021](https://arxiv.org/pdf/2103.04558v1.pdf)|C:straight line, L: straight line | perspective3-lines (P3L) | * | [CN](https://cloud.tencent.com/developer/article/1805735) |
|2.2.1.8|[Fast and Accurate Extrinsic Calibration for Multiple LiDARs and Cameras,2021](https://arxiv.org/pdf/2109.06550.pdf)|C:Canny edge(grayscale), L: depth-continuous edge|point-to-plane, point-to-edge|[mlcc](https://github.com/hku-mars/mlcc)|*|
|2.2.1.9|[OpenCalib: A Multi-sensor Calibration Toolbox for Autonomous Driving, 2022](https://arxiv.org/abs/2205.14087)| * | target-based, target-less, manual |[SensorsCalibration](https://github.com/PJLab-ADG/SensorsCalibration)|*|
|2.2.1.10|[General, Single-shot, Target-less, and Automatic LiDAR-Camera Extrinsic Calibration Toolbox,ICRA 2023](https://arxiv.org/pdf/2302.05094.pdf)|C:keypoints, L: keypoints on intensity images (by SuperGlue)|reprojection error minimization, RANSAC|[direct_visual_lidar_calibration](https://github.com/koide3/direct_visual_lidar_calibration)|*|
#### 2.2.2. Deep-learning methods
|Sl No|Paper|Feature|Toolbox|Note|
| --- | --- | --- | --- | --- | 
|2.2.2.1|[RegNet: Multimodal sensor registration using deep neural networks, 2017,IV](https://arxiv.org/pdf/1707.03167.pdf)| * |[regnet](https://github.com/aaronlws95/regnet)|*|
|2.2.2.2|[CalibNet: Geometrically supervised extrinsic calibration using 3d spatial transformer networks,2018,IROS](https://arxiv.org/pdf/1803.08181.pdf)| * |[CalibNet](https://github.com/epiception/CalibNet)|*|
|2.2.2.3|[LCCNet: Lidar and Camera Self-Calibration using CostVolume Network,2021,CVPRW](https://openaccess.thecvf.com/content/CVPR2021W/WAD/papers/Lv_LCCNet_LiDAR_and_Camera_Self-Calibration_Using_Cost_Volume_Network_CVPRW_2021_paper.pdf)| * |[LCCNet](https://github.com/IIPCVLAB/LCCNet)|*|
|2.2.2.4|[Calib-Anything: Zero-training LiDAR-Camera Extrinsic Calibration Method Using Segment Anything,2023](https://arxiv.org/pdf/2306.02656.pdf)| C: Segmentation, L: normal estimation, plane fitting & euclidean cluster, intensity normalization|[OpenCalib/CalibAnything](https://github.com/OpenCalib/CalibAnything)|*|

## 3. Other toolboxes
|Sl No|Toolbox|Introduction|Note|
| --- | --- | --- | --- |
|3.1|[Apollo sensor calibration tools](https://github.com/ApolloAuto/apollo/blob/master/docs/quickstart/apollo_2_0_sensor_calibration_guide.md)|targetless method, no source code | [CN](https://blog.csdn.net/learning_tortosie/article/details/82351553?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_baidulandingword-0&spm=1001.2101.3001.4242)|
|3.2|[Autoware camera lidar calibrator](https://github.com/Autoware-AI/utilities/tree/master/autoware_camera_lidar_calibrator)|pick points mannually, PnP|*|
|3.3|[Autoware calibration camera lidar](https://github.com/XidianLemon/calibration_camera_lidar)| checkerboard, similar to [LCCT](http://www.cs.cmu.edu/~ranjith/lcct.html) |[CN](https://adamshan.blog.csdn.net/article/details/81670732)|
|3.4|[livox_camera_lidar_calibration](https://github.com/Livox-SDK/livox_camera_lidar_calibration)|pick points manually, PnP| *|
|3.5|[tier4/CalibrationTools](https://github.com/tier4/CalibrationTools)|target-based, manual|*|
