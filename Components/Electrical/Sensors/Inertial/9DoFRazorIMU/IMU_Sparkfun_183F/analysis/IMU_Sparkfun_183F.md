
IMU Covariance Analysis Report: IMU_Sparkfun_183F
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


Generated on: 2026-08-01 17:36:38

This report provides an analysis of the IMU data, including covariance matrices for orientation, gyroscope, linear acceleration, and magnetometer data. The analysis is based on the provided CSV files containing IMU and magnetic field data.
## IMU Parameters


- name: `IMU_Sparkfun_183F`

- device_name: `/dev/imu_SparkFun_183F`

- description: `Sparkfun 9DoF Razor IMU (MPU-9250)`

- manufacturer: `Sparkfun`

- full_serial_number: `D3CF0EEF514E325437202020FF13183F`
# IMU Analysis


IMU Data Duration: 3635.59 seconds

IMU Data Average Frequency: 79.89 Hz
## Orientation Analysis


Orientation Covariance Matrix:
$$
\begin{bmatrix}
0.00284382 & -0.00010242 & 0.00015077 \\
-0.00010242 & 0.00014203 & -0.00003602 \\
0.00015077 & -0.00003602 & 0.00593072 \\
\end{bmatrix}
$$

![](imu_orientation.png)
## Gyroscope Analysis


Gyroscope Covariance Matrix:
$$
\begin{bmatrix}
1.77738682 & -0.04087697 & -0.10428252 \\
-0.04087697 & 1.95640278 & 0.03071062 \\
-0.10428252 & 0.03071062 & 2.22615955 \\
\end{bmatrix}
$$

![](imu_gyroscope.png)
## Linear Acceleration Analysis


Linear Acceleration Covariance Matrix:
$$
\begin{bmatrix}
0.20434611 & -0.01250318 & -0.05862034 \\
-0.01250318 & 0.37013179 & -0.02434741 \\
-0.05862034 & -0.02434741 & 0.92351966 \\
\end{bmatrix}
$$

![](imu_linear_acceleration.png)
# IMU Magnetometer Analysis


Magnetic Data Duration: 3635.45 seconds

Magnetic Data Average Frequency: 80.49 Hz
## Magnetometer Analysis


Magnetometer Covariance Matrix:
$$
\begin{bmatrix}
0.56097295 & -0.00390156 & -0.02108821 \\
-0.00390156 & 0.57187022 & -0.02220647 \\
-0.02108821 & -0.02220647 & 0.52839862 \\
\end{bmatrix}
$$

![](imu_magnetic_field.png)