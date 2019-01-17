# Le contenu des séquences
* [Séquence I : Rappels de trigonométrie](https://www.overleaf.com/read/jfxsrwgpqfhm)
* [Séquence II : Rappels sur les nombres complexes](https://www.overleaf.com/read/pddpsqkxtmdk)
* [Séquence III : Signal discret - Aspect temporel](https://www.overleaf.com/read/tyxqvmxvvfwc)
* [Séquence IV : Signal discret - Aspect fréquentiel](https://www.overleaf.com/read/gyybtqwvbtjs)
* [Séquence V : Signal discret - Aspect fréquentiel](https://www.overleaf.com/read/bdnnpcnstbpg)
* [Séquence VI : Introduction au filtrage](https://www.overleaf.com/read/kbhysrdhjjzw)
* [Séquence VII : Contrôle continu final](https://www.overleaf.com/read/xhctcfpcgcqb)


```matlab
%% SÈquence I Exercice II

clear all, close all, clc;

%% Tracer sin et cos
% CrÈation du vecteur angulaire
theta = -6*pi:.001:6*pi;
% Affichage avec titres
plot(theta, cos(theta), 'r', theta, sin(theta), 'b');
title('Fonctions sinus et cosinus');
xlabel('\theta (angle en radian)');
ylabel({'\color{red}cos(\theta)';'\color{blue}sin(\theta)'});

%% SinusoÔdes de plusieurs frÈquences
% 100 points rÈpartis sur une seconde
Te = 1/100; 
% CrÈation du vecteur temporel
t = 0:Te:1-Te;
% CrÈation des sinusoÔdes
s1 = sin(2*pi*1*t);
s2 = sin(2*pi*2*t);
s3 = sin(2*pi*5*t);
% Nouvelle figure
figure;
% Affichage avec titres
plot(t, s1, 'r', t, s2, 'b', t, s3, 'm');
title('Fonctions sinus de plusieurs frÈquences');
xlabel('t (temps en seconde)');
ylabel({'\color{red}s1(t)';'\color{blue}s2(t)';'\color{magenta}s3(t)'});

```
