
IMU Covariance Analysis Report: IMU_Sparkfun_2115
=================================================

Table of Contents
=================

* [Overview](#overview)
	* [IMU Parameters](#imu-parameters)
* [IMU Analysis](#imu-analysis)
	* [Orientation Analysis](#orientation-analysis)
	* [Gyroscope Analysis](#gyroscope-analysis)
	* [Linear Acceleration Analysis](#linear-acceleration-analysis)
* [IMU Magnetometer Analysis](#imu-magnetometer-analysis)
	* [Magnetometer Analysis](#magnetometer-analysis)

# Overview


Generated on: 2026-08-01 21:42:19

This report provides an analysis of the IMU data, including covariance matrices for orientation, gyroscope, linear acceleration, and magnetometer data. The analysis is based on the provided CSV files containing IMU and magnetic field data.
## IMU Parameters


- name: `IMU_Sparkfun_2115`

- device_name: `/dev/imu_SparkFun_2115`

- description: `Sparkfun 9DoF Razor IMU (MPU-9250)`

- manufacturer: `Sparkfun`

- full_serial_number: `A354B24F514E3254374A2020FF062115`
# IMU Analysis


IMU Message Count: 85740

IMU Data Duration: 1015.14 seconds

IMU Data Average Frequency: 84.46 Hz
## Orientation Analysis


Orientation Roll Average: -3.13007167 (rad) Standard Deviation: 0.0920

Orientation Pitch Average: -0.00062996 (rad) Standard Deviation: 0.0125

Orientation Yaw Average: 0.45645585 (rad) Standard Deviation: 0.0524

Orientation Covariance Matrix:
$$
\begin{bmatrix}
0.00845904 & -0.00086688 & -0.00349572 \\
-0.00086688 & 0.00015610 & 0.00057386 \\
-0.00349572 & 0.00057386 & 0.00274070 \\
\end{bmatrix}
$$

![](imu_orientation.png)
## Gyroscope Analysis


Gyroscope X Average: 0.02284772 (rad/s) Standard Deviation: 1.0607

Gyroscope Y Average: 0.01488431 (rad/s) Standard Deviation: 1.1746

Gyroscope Z Average: 0.01955229 (rad/s) Standard Deviation: 1.2536

Gyroscope Covariance Matrix:
$$
\begin{bmatrix}
1.12516210 & -0.00080147 & 0.17067651 \\
-0.00080147 & 1.37958810 & -0.01291881 \\
0.17067651 & -0.01291881 & 1.57149203 \\
\end{bmatrix}
$$

![](imu_gyroscope.png)
## Linear Acceleration Analysis


Linear Acceleration X Average: -0.03671370 (m/s^2) Standard Deviation: 0.3256

Linear Acceleration Y Average: 0.10222011 (m/s^2) Standard Deviation: 0.4754

Linear Acceleration Z Average: -10.25160446 (m/s^2) Standard Deviation: 0.8717

Linear Acceleration Covariance Matrix:
$$
\begin{bmatrix}
0.10599532 & 0.00787056 & 0.09475454 \\
0.00787056 & 0.22598639 & 0.07309878 \\
0.09475454 & 0.07309878 & 0.75979509 \\
\end{bmatrix}
$$

![](imu_linear_acceleration.png)
# IMU Magnetometer Analysis


Magnetic Data Message Count: 85718

Magnetic Data Duration: 1014.89 seconds

Magnetic Data Average Frequency: 84.46 Hz
## Magnetometer Analysis


Magnetometer X Average: 2.80951912 (T) Standard Deviation: 0.7746

Magnetometer Y Average: 23.33400068 (T) Standard Deviation: 0.7714

Magnetometer Z Average: -132.61008213 (T) Standard Deviation: 0.8025

Magnetometer Covariance Matrix:
$$
\begin{bmatrix}
0.60008762 & -0.00065638 & 0.00592694 \\
-0.00065638 & 0.59498957 & -0.00257472 \\
0.00592694 & -0.00257472 & 0.64407098 \\
\end{bmatrix}
$$

![](imu_magnetic_field.png)