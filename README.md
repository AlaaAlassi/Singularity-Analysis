# Singularity-Analysis
Geometric analysis of some singular configurations for the robotic manipulator KUKA LBR IIWA. (Documantation is still in progress).

# Singularities
For this kinematic solution, there are two serious singular configurations that must be avoided. The first case is when the vector from the base to the wrist is changing direction on X while it has a zero component on Y or vice versa, this moves the first joint instantaneously from 0 to 180 Deg (Check the animation below) or from 90 to -90 Deg, this depends on the input of the atan2 function <a href="https://www.codecogs.com/eqnedit.php?latex=\theta_1&space;=&space;atan2(y,x)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\theta_1&space;=&space;atan2(y,x)" title="\theta_1 = atan2(y,x)" /></a>.



Matlab Plot             |  Simscape
:-------------------------:|:-------------------------:
<img src="https://github.com/AlaaAlassi/Singularity-Analysis/blob/master/Assets/Singularities/ShoulderSing/SigShoulderX.gif?raw=true" width="500">  |   <img src="https://github.com/AlaaAlassi/Singularity-Analysis/blob/master/Assets/Singularities/ShoulderSing/SigShoulderXR.gif?raw=true" width="500">

So if you want to control the robot near a singularly, just avoid to move this vector from -x to x while you have a zero y component or or vice versa as illustrated below. 


Matlab Plot              |  Simscape
:-------------------------:|:-------------------------:
<img src="https://github.com/AlaaAlassi/Singularity-Analysis/blob/master/Assets/Singularities/ShoulderSing/SigShoulderXY.gif?raw=true" width="500">  |  <img src="https://github.com/AlaaAlassi/Singularity-Analysis/blob/master/Assets/Singularities/ShoulderSing/SigShoulderXR3.gif?raw=true" width="500">

This is valid only for simulation, I tried to control the real robot near this singularity, the robot was highly unstable and vibrated with a large amplitude so I ended up pressing the E-Stop, check this [video](https://youtu.be/-SAkOiPgs9U). In this experiment, I was using the inverse kinematics provided by KUKA's software (Sunrise.OS). It looks like this behavior is due to a singularity in the solution. 
