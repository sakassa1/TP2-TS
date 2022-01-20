# TP2- Jeux de mots

# Synthèse et analyse spectrale d’une gamme de musique
-------------------------------------------------------------------
## Objectifs

• Comprendre comment manipuler un signal audio avec Matlab, en effectuant
certaines opérations classiques sur un fichier audio d’une phrase enregistrée via
un smartphone.

• Comprendre la notion des sons purs à travers la synthèse et l’analyse spectrale
d’une gamme de musique.

Commentaires : Il est à remarquer que ce TP traite en principe des signaux continus.
Or, l'utilisation de Matlab suppose l'échantillonnage du signal. Il faudra donc être
vigilant par rapport aux différences de traitement entre le temps continu et le temps
discret.

Tracé des figures : toutes les figures devront être tracées avec les axes et les
légendes des axes appropriés.

Travail demandé : un script Matlab commenté contenant le travail réalisé et des
commentaires sur ce que vous avez compris et pas compris, ou sur ce qui vous a
semblé intéressant ou pas, bref tout commentaire pertinent sur le TP.

## Jeux de mots

« phrase.wave » est un fichier audio enregistré à l’aide d’un smartphone, en
prononçant lentement la phrase : 

            - « Rien ne sert de courir, il faut partir à point ». 

1- Sauvegardez ce fichier sur votre répertoire de travail, puis charger-le dans MATLAB
à l’aide de la commande « audioread ».


2- Tracez le signal enregistré en fonction du temps, puis écoutez-le en utilisant la
commande « sound ».

3- Cette commande permet d’écouter la phrase à sa fréquence d’échantillonnage
d’enregistrement. Ecoutez la phrase en modifiant la fréquence d’échantillonnage à
double ou deux fois plus petite pour vous faire parler comme « Terminator » ou «
Donald Duck ». En effet, modifier la fréquence d’échantillonnage revient à appliquer
un changement d’échelle y(t) = x(at) en fonction de la valeur du facteur d’échelle, cela
revient à opérer une compression ou une dilatation du spectre initial d’où la version
plus grave ou plus aigüe du signal écouté.




```Matlab
%jeux de mots
clear all
close all
clc
file='phrase.wav';

[y,f]=audioread(file);

N=length(y);
te=1/f;
t=(0:N-1)*te;
%sound(y,f);
%sound(y,3*f);
figure(1)
plot(y);

```
![image](https://user-images.githubusercontent.com/85129301/150338715-0548c7e6-f5fa-4198-819f-6d2e5c0230cb.png)


4- Tracez le signal en fonction des indices du vecteur x, puis essayez de repérer les
indices de début et de fin de la phrase « Rien ne sert de »

  ![image](https://user-images.githubusercontent.com/85129301/150339085-104c7819-4136-460a-8a57-7bb39e4daa59.png)


5- Pour segmenter le premier mot, il faut par exemple créer un vecteur « riennesertde »
contenant les n premières valeurs du signal enregistré x qui correspondent à ce
morceau. Créez ce vecteur, puis écoutez le mot segmenté.

```Matlab
figure(2)
riennesertde=y(14770:75390);
subplot(3,1,1);
%soundsc(riennesertde,f);

Nrien=length(riennesertde);
tr=[0:Nrien-1]*1/f;
plot(tr,riennesertde);

```

6- Segmentez cette fois-ci toute la phrase en créant les variables suivantes :
riennesertde, courir, ilfaut, partirapoint.

```Matlab
courir=y(79450:94230);
Ncourir=length(courir);
tc=[0:Ncourir-1]*1/f;
subplot(3,1,2);

plot(tc,courir);

ilfaut=y(98060:121700);
Nilfaut=length(ilfaut);
tf=[0:Nilfaut-1]*1/f;
subplot(3,1,3);

plot(tf,ilfaut);

partir=y(125300:162700);
Npartir=length(partir);
tp=[0:Npartir-1]*1/f;
subplot(3,1,3);
plot(tp,partir);

phrase=[riennesertde,partir,ilfaut,courir];

%sound(phrase,f);

```

  
 ![image](https://user-images.githubusercontent.com/85129301/150338670-5c0d5730-d7fb-4dcf-9123-8c849e596fc3.png)

