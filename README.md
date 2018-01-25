# Extended Kalman Filter Project Starter Code
Self-Driving Car Engineer Nanodegree Program

In this project I implemented kalman filter to estimate the state of a moving object of interest with noisy lidar and radar measurements. 

My RMSE = [.9, .8, .45, .43] on Dataset 1 are lower that the tolerance outlined in the project rubric. 

On the beginning I use first measurements to initialize the state vectors and covariance matrices (FusionEKF.cpp, lines: 68-97).

Upon receiving a measurement after the first, the algorithm predicts object position to the current timestep and then update the prediction using the new measurement. (FusionEKF.cpp, lines: 104-148)

I set up the appropriate matrices given the type of measurement and calls the correct measurement function for a given sensor type. (FusionEKF.cpp, lines: 129-142). For updating data from lidar I call method KalmanFilter::UpdateLidar(const VectorXd &z) (kalman_filter.cpp, lines: 33-48), for radar - KalmanFilter::UpdateRadar(const VectorXd &z) (kalman_filter.cpp, lines: 51-100).
Also for calculating Jacobian Matrix I created method Tools::CalculateJacobian(const VectorXd& x_state) (tools.cpp, lines: 48-75)

To increase accuracy of the algorithm, I check dividing by zero when px and px are equal (or close) to zero. Also I normalize angles when use atan2() method to convert data from radar to polar coordinates.



