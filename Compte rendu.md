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
### Q1)  
Dan

