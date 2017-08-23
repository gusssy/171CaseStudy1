# 171CaseStudy1

%Case Study 1, Exercise 1
%Hauling a sled up an incline with a cable
%Using Newton's method and graphical method to solve for V

clear
clc

%Sled mass (kg)
m = 1000;
%Gravitational constant 
g = 9.81;
%slope gradient (degrees)
gradient = 45;
%Coefficient of friction
Cf = 0.2;
%alpha constant (w.s^2/rad^2)
a = 1;
%Beta constant (rad/s)
B = pi;
%Pulley radius (m)
R = 0.5;
%gearbox ratio
rgb = 20;

%Defining function for the power output of the motor (W)
P = @(V) a*((B*rgb)/R - (rgb^2*V^2)/R^2); 

%Defining function for the friction power (W)
F = @(V) V*Cf*m*g*(cos(gradient));

%Defining function for resistive/weight power (W) 
W = @(V) V*m*g*sin(gradient);

%final function which gives speed at which power output matches power
%demand
f = @(V) V*m*g*sin(gradient) + V*Cf*m*g*cos(gradient) - a*((B*rgb)/R - (rgb^2*V^2)/R^2);

%Derivitave of final function
d = @(V) m*g*sin(gradient) + Cf*m*g*cos(gradient) - a*((B*rgb)/R - (2*rgb^2*V)/r^2);
