## Digital-Signal-Processing--Design-of-Butterworth-Filter---Impulse-Invariant-Method
## AIM:
To design of 2nd order Low Pass Butterworth Filter using using Impulse Invariant Transformation 
## SOFTWARE REQUIRED: 
MAT LAB R2012
## ALGORITHM:
Step 1: Open MAT LAB. Write the program. 

Step 2: Read the values of Ap,As,Pass band frequency,Stop band frequency.

Step 3: Initialise some conditions find out the order (N) value.

Step 4: Find out the transfer function of the filter and magnitude of that filter. 

Step 5: Plot the magnitude spectrum with x-label and y-label with suitable title. 

Step 6: Terminate the program.

## PROGRAM:
```
%Balaji v 212223050008

clc
clear all
close all

Ap=0.7;
As=0.2;
wp=pi/2;
ws=0.7*pi;
T=0.25;

omega_p=(wp/T);
omega_s=(ws/T);
alpha_p=20*log10(Ap);
alpha_s=20*log10(As);

[N wc]=buttord(omega_p,omega_s,alpha_p,alpha_s,'s');
[num den]=butter(N,1,'s');
display('normalised transfer function');
hs=tf(num,den);
[num1 den1]=butter(N,wc,'s')
display('unnormalised transfer function');
hs1=tf(num1,den1);
[numz denz]=impinvar(num1,den1,1/T)
hz=tf(numz,denz,T);
display('digital transfer function');
w=0:pi/16:pi;
y=freqz(numz,denz,w);

%MAGNITUDE SPECTRUM
y1=abs(y);
plot(w,y1);
xlabel('frequency');
ylabel('magnitude');
title('magnitude response butterworth LPF');
```

## OUTPUT:
<img width="1919" height="1019" alt="image" src="https://github.com/user-attachments/assets/f7cfe159-9432-4509-85eb-44f472890f64" />


## RESULT:
![IMG_20260406_193853](https://github.com/user-attachments/assets/193361a3-199e-45ec-9cee-f7bd639039c3)


