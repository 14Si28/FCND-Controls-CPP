## GenerateMotorCommands

From line 57 to line 96, Here we calulated individual motor thrust.
For the same we have a formaula as "Sum of all forces is equal to thrust".

Here `momentCmd` is for getting the moment about each axis, `collThrustCmd` is the collective 
trust. `L` the arm length parameter and the drag/thrust ratio `kappa` is used for calulating
individual motor thrust.


## BodyRateControl

To calulale the 3-axis moment here in the function from line no 114 to 121 we have used desired and
estimated body rate. The simple formula here used is "moment = moment of inertial * angular accelaration"
about the axis.


## RollPitchControl

From line 148 to 176
To calculate a desired pitch and roll angle rates based on a desired global
lateral acceleration, the current attitude of the quad, and desired collective thrust command, 
given hits were more helpful. 

By using rotation matrix, roll/pitch gain and collective thrust, we can use the formula "total thrust force 
is equal to the mass of the body( drone ) * commanded accelaration. Later this can be furture broken down.


## AltitudeControl

From line 202 to 213.

To calculate desired quad thrust based on altitude setpoint, actual altitude,
vertical velocity setpoint, actual vertical velocity, and a vertical 
acceleration feed-forward command. We needed the gain parameters `kpPosZ` and `kpVelZ` to return the collective thrust.
Calculated integrated altitude error with desired virtical accelaration, virtical acce,and dt time, collective trust is
calucalted based on simple mass* acce.

## LateralPositionControl

From line 245 to 266

Here to calculate a desired horizontal acceleration based on 
desired lateral position/velocity/acceleration and current pose, is done by using the gain parameters kpPosXY and kpVelXY,
and by making sure the limit, the maximum horizontal velocity and acceleration
to maxSpeedXY and maxAccelXY.

Here z component is already nil.

## YawControl

From line 282 to 288

To calculate a desired yaw rate to control yaw to yawCmd, 
form commanded yaw and current yaw the agle is calucalted by `fmodf`.
The yaw control gain parameter kpYaw is than multiplied with rad to get the desired output.

 
