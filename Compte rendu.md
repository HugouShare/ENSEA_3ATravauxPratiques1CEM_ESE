# Travaux pratiques CEM : utilisation de la méthode DF pour la simulation CEM

## Contexte global
### Objectifs :  
- Calcul du potentiel électrique par la méthode des différences finies (potentiel scalaire)
- Calcul des grandeurs dérivées (champ électrique et capacité) illustratives sur un cas CEM
### Compétences visées :  
- Connaitre les éléments constitutifs d’un modèle électromagnétique : domaine de calcul, source, conditions initiales, conditions aux limites, convergence
- Utilisation d’un outil de simulation & développement numérique (sous environnement Matlab / Octave)
- Post-traitement des données & sensibilisation aux grandeurs CEM (capacité)
### Contrôle des connaissances :  
- Rendu d’un compte-rendu des travaux suite à la séance présentielle

## A. Introduction   
L'équation de Laplace sert à modéliser divers phénomènes physiques comme le potentiel gravitationnel, les champs électriques, la diffusion de la chaleur et les ondes sonores, en utilisant des conditions aux limites pour résoudre des problèmes en physique et en ingénierie.  

Dans le cas de la CEM, il est alors parfois nécessaire de résoudre cette équation appliquée au potentiel V dans le vide.  
On obtient alors l'équation :  

$$
\Delta V = 0
$$
  
Pour se faire, nous pouvons alors utiliser la méthode des différences finies (DF) afin de résoudre numériquement et en 2D l'équation de Laplace.  
La méthode des DF permet de trouver une solution à une équation aux dérivées partielles (EDP) en approximant le calcul d'une dérivée en un point par sa tangente.  
Dans le cas particulier de la résolution de l'équation de Laplace dans le vide on obtient (extrait du cours) : 
<img width="480" height="361" alt="image" src="https://github.com/user-attachments/assets/e4ecd982-828f-4e1f-9b46-952cece513e9" />  
Qui dans le cas particulier où dx=dy=1 devient : 

$$
V_{i,j} = 1/4*(V_{i+1,j}+V_{i-1,j}+V_{i,j+1}+V_{i,j-1})
$$  

## B. Durant la séance  
### Q1) Modélisation du problème  
Dans un premier temps, nous commençons par modéliser le problème en 2D à l'aide des conditions initiales.  
Nous modélisons deux conducteurs l'un à côté de l'autre, avec les conditions suivantes :  
- le conducteur rouge a un potentiel initial de V=+100V
- le conducteur bleu a un potentiel initial de V=-100V
- le reste est à V=0V
- l'espace considéré est de Nx=Ny=40 (nombre de cellules)

On obtient alors le résultat suivant :  

<img width="633" height="483" alt="image" src="https://github.com/user-attachments/assets/59b18a3a-9f40-4317-903f-9ffebdaf0f9d" />  

### Q2) Itération du calcul par DF pour k = 20, 50 et 200
Après avoir modélisé le problème, nous nous proposons maintenant d'exécuter itérativement 200 fois le calcul, par méthode des différences finies, du potentiel sur notre problème.  
Nous obtenons alors : 
<p align="left">
  <img width="609" height="482" alt="image" src="https://github.com/user-attachments/assets/cea66ccf-9345-4755-b84c-d15398b03221" />
  <br>
  <em>Résultat pour k = 20 itérations</em>
</p>
<p align="left">
  <img width="607" height="489" alt="image" src="https://github.com/user-attachments/assets/352a1942-7577-4e5a-ba81-fdd11062910f" />
  <br>
  <em>Résultat pour k = 50 itérations</em>
</p>
<p align="left">
  <img width="637" height="484" alt="image" src="https://github.com/user-attachments/assets/11e26412-947e-4ffd-9312-56e687597c36" />  
  <br>
  <em>Résultat pour k = 200 itérations</em>
</p>  

Nous obtenons un résultat convenable cependant, il vient assez naturellement la question : _combien d'itérations doit-on faire avant d'obtenir un résultat convenable ?_  
De fait, selon que l'on réalise 20, 50 ou 200 itérations, nous obtenons des résultats très différents.  
=> Il faut donc définir un seuil d'itération à partir duquel le résultat obtenu sera satisfaisant. 

### Q3) Définition de la notion de convergence, ainsi que d'un seuil  
Afin de s'assurer que le résultat obtenu converge bien vers le résultat souhaité, nous allons définir un seuil et comparer l'écart de potentiel entre deux valeurs successives pour un même point donné. Puis nous allons, à chaque itération, comparer la valeur maximum de cet écart sur tous les points du plan au seuil fixé.  
Nous obtenons alors les résultats suivants :  
- seuil = 1e-2 & Nx=40 Ny=40 : nb iteration = 284
- seuil = 1e-3 & Nx=40 Ny=40 : nb iteration = 491
- seuil = 1e-4 & Nx=40 Ny=40 : nb iteration = 699
- seuil = 1e-2 & Nx=100 Ny=100 : nb iteration = 1276
- seuil = 1e-3 & Nx=100 Ny=100 : nb iteration = 4670
- seuil = 1e-4 & Nx=100 Ny=100 : nb iteration = 8555
De 



