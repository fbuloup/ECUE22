# Le contenu des séquences
* [Séquence I : Rappels de trigonométrie](https://www.overleaf.com/read/jfxsrwgpqfhm)
* [Séquence II : Rappels sur les nombres complexes](https://www.overleaf.com/read/pddpsqkxtmdk)
* [Séquence III : Signal discret - Aspect temporel](https://www.overleaf.com/read/tyxqvmxvvfwc)
* [Séquence IV : Signal discret - Aspect fréquentiel](https://www.overleaf.com/read/gyybtqwvbtjs)
* [Séquence V : Signal discret - Aspect fréquentiel](https://www.overleaf.com/read/bdnnpcnstbpg)
* [Séquence VI : Introduction au filtrage](SEQUENCE_VI.pdf)
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
Te = 1/100; % C'est la période d'échantillonnage
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

## Séquence V
### Spectre bilatéral de la note MI
```matlab
%% Tracé du spectre bilateral de la note
clear all, close all, clc;

[signal, Fe] = audioread('note.wav');
% Nombre d'échantillons
nbSamples = length(signal);

% FFT du signal
fftSignal = fftshift(fft(signal))/nbSamples; % On utilise fftshift puisque spectre bilatéral
modFFTSignal = abs(fftSignal);
phaseFFTSignal = angle(fftSignal);

% Contruction du vecteur frequentiel en bilatéral
df = Fe/nbSamples;
if(mod(nbSamples, 2) == 0)
    % Pair
    f = -Fe/2 : df : Fe/2 - df;
    N =  nbSamples; % Le nb echantillons pour affichage n'est pas modifié
else
    % Impair
    f = -Fe/2 + df/2 : df : Fe/2 - df + df/2;
    N =  nbSamples; % Le nb echantillons pour affichage n'est pas modifié
end
    
% Affichage 
subplot(2,1,1);
stem(f, modFFTSignal);
xlabel('f');
ylabel('Amplitude');
title('Spectre d''amplitude');
subplot(2,1,2);
stem(f, phaseFFTSignal);
xlabel('f');
ylabel('Phase');
title('Spectre de phase');
```
### Spectre monolatérale de la note MI
```matlab
%% Tracé du spectre monolateral de la note
clear all, close all, clc;

[signal, Fe] = audioread('note.wav');
% Nombre d'échantillons
nbSamples = length(signal);

% FFT du signal
fftSignal = fft(signal)/nbSamples; % Inutile d'utiliser fftshift
modFFTSignal = abs(fftSignal);
phaseFFTSignal = angle(fftSignal);

% Contruction du vecteur frequentiel en monolateral
df = Fe/nbSamples;
if(mod(nbSamples, 2) == 0)
    % Pair
    f = 0 : df : Fe/2 - df;
    N =  nbSamples/2; % Modification du nb echantillons pour affichage
else
    % Impair
    f = 0 : df : Fe/2 - df + df/2;
    N =  (nbSamples + 1)/2; % Modification du nb echantillons pour affichage
end
    
% Affichage 
subplot(2,1,1);
stem(f, [modFFTSignal(1); 2*modFFTSignal(2:N)]);
xlabel('f');
ylabel('Amplitude');
title('Spectre d''amplitude');
subplot(2,1,2);
stem(f, phaseFFTSignal(1:N));
xlabel('f');
ylabel('Phase');
title('Spectre de phase');
```

## Séquence VI
```matlab
% Séquence VI Exercice I
clear all, close all, clc;

% Création du vecteur temporel
Fe = 4;
Te = 1/Fe;
t = 0:Te:10;

% Signal
e = 3 + sin(2*pi*t);

% Affichage du signal
plot(t, e);
title('Signal en fonction du temps');
xlabel('t (s)');
ylabel('Amplitude');

% Définition des vecteurs a et b pour le filtre moyenneur sur 4 points
b = [1/4, 1/4, 1/4, 1/4];
a = [1];

% Filtrage
s_moyenne = filter(b, a, e);

% Affichage du signal filtré
hold on
plot(t, s_moyenne);

% Filtre dérivateur
a = [1];
b = [1/Te, -1/Te];
s_derive = filter(b, a, e);
plot(t, s_derive);
```
