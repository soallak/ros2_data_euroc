cmake_minimum_required(VERSION 3.8)
project(data_euroc)

# find dependencies
find_package(ament_cmake REQUIRED)

if (EUROC_USE_BAG_FORMAT)

  set(Machine_Hall_01  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_01_easy/MH_01_easy.bag)
  set(Machine_Hall_02  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_02_easy/MH_02_easy.bag)
  set(Machine_Hall_03  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_03_medium/MH_03_medium.bag)
  set(Machine_Hall_04  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_04_difficult/MH_04_difficult.bag)
  set(Machine_Hall_05  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_04_difficult/MH_04_difficult.bag)
  set(Vicon_Room_1_01  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room1/V1_01_easy/V1_01_easy.bag)
  set(Vicon_Room_1_02  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room1/V1_02_medium/V1_02_medium.bag)
  set(Vicon_Room_1_03  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room1/V1_03_difficult/V1_03_difficult.bag)
  set(Vicon_Room_2_01  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room2/V2_01_easy/V2_01_easy.bag)
  set(Vicon_Room_2_02  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room2/V2_02_medium/V2_02_medium.bag)
  set(Vicon_Room_2_03  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room2/V2_03_difficult/V2_03_difficult.bag)
  set(CAMERA_CALIBRATION http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/calibration_datasets/cam_april/cam_april.bag)

else()

  set(Machine_Hall_01  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_01_easy/MH_01_easy.zip)
  set(Machine_Hall_02  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_02_easy/MH_02_easy.zip)
  set(Machine_Hall_03  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_03_medium/MH_03_medium.zip)
  set(Machine_Hall_04  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_04_difficult/MH_04_difficult.zip)
  set(Machine_Hall_05  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/machine_hall/MH_04_difficult/MH_04_difficult.zip)
  set(Vicon_Room_1_01  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room1/V1_01_easy/V1_01_easy.zip)
  set(Vicon_Room_1_02  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room1/V1_02_medium/V1_02_medium.zip)
  set(Vicon_Room_1_03  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room1/V1_03_difficult/V1_03_difficult.zip)
  set(Vicon_Room_2_01  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room2/V2_01_easy/V2_01_easy.zip)
  set(Vicon_Room_2_02  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room2/V2_02_medium/V2_02_medium.zip)
  set(Vicon_Room_2_03  http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/vicon_room2/V2_03_difficult/V2_03_difficult.zip)
  set(CAMERA_CALIBRATION http://robotics.ethz.ch/~asl-datasets/ijrr_euroc_mav_dataset/calibration_datasets/cam_april/cam_april.zip)

endif()


if(NOT DEFINED EUROC_DATASET)
  set(EUROC_DATASET Machine_Hall_01 CACHE STRING "EUROC Dataset")
endif()

if(EUROC_USE_BAG_FORMAT)

  if (NOT EXISTS ${CMAKE_CURRENT_BINARY_DIR}/${EUROC_DATASET}.bag)
    file(DOWNLOAD ${${EUROC_DATASET}} ${EUROC_DATASET}.bag)
  else()
    message(WARNING "${EUROC_DATASET} already exists. Download will be skipped")
  endif()

  if (NOT EXISTS ${CMAKE_CURRENT_BINARY_DIR}/camera_calibration.bag)
    file(DOWNLOAD ${CAMERA_CALIBRATION} camera_calibration.bag)
  else()
    message(WARNING "camera_calibration.bag already exists. Download will be skipped")
  endif()

  install(
    FILES
      ${CMAKE_CURRENT_BINARY_DIR}/${EUROC_DATASET}.bag
      ${CMAKE_CURRENT_BINARY_DIR}/camera_calibration.bag
    DESTINATION
      ${CMAKE_INSTALL_PREFIX}
  )

else()

  set(EUROC_DATASET_URL ${${EUROC_DATASET}})
  include(FetchContent)
  FetchContent_Declare(
    ${EUROC_DATASET}
    URL ${EUROC_DATASET_URL}
    SOURCE_DIR ${CMAKE_CURRENT_BINARY_DIR}/${EUROC_DATASET}
  )
  FetchContent_Declare(
    ${EUROC_DATASET}_calibration
    URL ${CAMERA_CALIBRATION}
    SOURCE_DIR ${CMAKE_CURRENT_BINARY_DIR}/${EUROC_DATASET}_calibration
  )
FetchContent_MakeAvailable(${EUROC_DATASET} ${EUROC_DATASET}_calibration)

endif()


if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # comment the line when a copyright and license is added to all source files
  set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # comment the line when this package is in a git repo and when
  # a copyright and license is added to all source files
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
