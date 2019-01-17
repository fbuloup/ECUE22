# Le contenu des séquences
* [Séquence I : Rappels de trigonométrie](https://www.overleaf.com/read/jfxsrwgpqfhm)
* [Séquence II : Rappels sur les nombres complexes](https://www.overleaf.com/read/pddpsqkxtmdk)
* [Séquence III : Signal discret - Aspect temporel](https://www.overleaf.com/read/tyxqvmxvvfwc)
* [Séquence IV : Signal discret - Aspect fréquentiel](https://www.overleaf.com/read/gyybtqwvbtjs)
* [Séquence V : Signal discret - Aspect fréquentiel](https://www.overleaf.com/read/bdnnpcnstbpg)
* [Séquence VI : Introduction au filtrage](https://www.overleaf.com/read/kbhysrdhjjzw)
* [Séquence VII : Contrôle continu final](https://www.overleaf.com/read/xhctcfpcgcqb)

# Les exercices

## Séquence I 
### Exercice II [:open_file_folder:](/S1E2.pdf)
```Matlab
%% Séquence I Exercice II

clear all, close all, clc;

%% Tracer sin et cos
% Création du vecteur angulaire
theta = -6*pi:.001:6*pi;
% Affichage avec titres
plot(theta, cos(theta), 'r', theta, sin(theta), 'b');
title('Fonctions sinus et cosinus');
xlabel('\theta (angle en radian)');
ylabel({'\color{red}cos(\theta)';'\color{blue}sin(\theta)'});
```
![image 1](/S1E2_image1.png "Logo Title Text 1")

```Matlab
%% Sinusoïdes de plusieurs fréquences
% 100 points répartis sur une seconde
Te = 1/100; 
% Création du vecteur temporel
t = 0:Te:1-Te;
% Création des sinusoïdes
s1 = sin(2*pi*1*t);
s2 = sin(2*pi*2*t);
s3 = sin(2*pi*5*t);
% Nouvelle figure
figure;
% Affichage avec titres
plot(t, s1, 'r', t, s2, 'b', t, s3, 'm');
title('Fonctions sinus de plusieurs fréquences');
xlabel('t (temps en seconde)');
ylabel({'\color{red}s1(t)';'\color{blue}s2(t)';'\color{magenta}s3(t)'});
```
![image 2](/S1E2_image2.png "Logo Title Text 1")
