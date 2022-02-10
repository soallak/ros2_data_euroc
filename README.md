## EuRoC MAV Dataset Downloader

This ROS2 package downloads the specified Bag from [EuRoC MAV Dataset](https://projects.asl.ethz.ch/datasets/doku.php?id=kmavvisualinertialdatasets) along with camera calibration bag.

### Usage

```
colcon build --merge-install --packages-select data_euroc --cmake-args -DEUROC_DATASET=<Name>
```
Refer to the table bellow for the bag name and replace any space with an underscore `_` character.

By default Machine Hall 01 will be downloaded 

```
colcon build --merge-install --packages-select data_euroc
```

### Bags

| Bag              | Link                                                                                                                    |
|------------------|-------------------------------------------------------------------------------------------------------------------------|
| Machine Hall 01  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_01_easy/MH_01_easy.bag  |
| Machine Hall 02  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_02_easy/MH_02_easy.bag  |
| Machine Hall 03  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_03_medium/MH_03_medium.bag |
| Machine Hall 04  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_04_difficult/MH_04_difficult.bag |
| Machine Hall 05  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_04_difficult/MH_04_difficult.bag |
| Vicon Room 1 01  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room1/V1_01_easy/V1_01_easy.bag |
| Vicon Room 1 02  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room1/V1_02_medium/V1_02_medium.bag |
| Vicon Room 1 03  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room1/V1_03_difficult/V1_03_difficult.bag |
| Vicon Room 2 01  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room2/V2_01_easy/V2_01_easy.bag |
| Vicon Room 2 02  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room2/V2_02_medium/V2_02_medium.bag |
| Vicon Room 2 03  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room2/V2_03_difficult/V2_03_difficult.bag |

*Calibration Data*

| Data             | Link                                                                                                                    |
|------------------|-------------------------------------------------------------------------------------------------------------------------|
| cam_checkerboard | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/calibration_datasets/cam_checkerboard/cam_checkerboard.bag |
| cam              | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/calibration_datasets/cam_april/cam_april.bag               |
| imu              | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/calibration_datasets/imu_april/imu_april.bag               |

### Zips

| Zips             | Link                                                                                                                    |
|------------------|-------------------------------------------------------------------------------------------------------------------------|
| Machine Hall 01  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_01_easy/MH_01_easy.zip  |
| Machine Hall 02  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_02_easy/MH_02_easy.zip  |
| Machine Hall 03  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_03_medium/MH_03_medium.zip |
| Machine Hall 04  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_04_difficult/MH_04_difficult.zip |
| Machine Hall 05  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_04_difficult/MH_04_difficult.zip |
| Vicon Room 1 01  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room1/V1_01_easy/V1_01_easy.zip |
| Vicon Room 1 02  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room1/V1_02_medium/V1_02_medium.zip |
| Vicon Room 1 03  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room1/V1_03_difficult/V1_03_difficult.zip |
| Vicon Room 2 01  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room2/V2_01_easy/V2_01_easy.zip |
| Vicon Room 2 02  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room2/V2_02_medium/V2_02_medium.zip |
| Vicon Room 2 03  | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room2/V2_03_difficult/V2_03_difficult.zip |

*Calibration Data*

| Data             | Link                                                                                                                    |
|------------------|-------------------------------------------------------------------------------------------------------------------------|
| cam_checkerboard | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/calibration_datasets/cam_checkerboard/cam_checkerboard.zip |
| cam              | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/calibration_datasets/cam_april/cam_april.zip               |
| imu              | http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/calibration_datasets/imu_april/imu_april.zip               |

### Known issues

Check the home page.
Relevant is that both cameras in have independent exposure control.  
