
# Paradoxe de Simpson et analyse de données de randonnée

## Présentation

Ce projet présente une étude statistique construite autour d’un cas fictif mais réaliste de randonnée en montagne, visant à illustrer de manière concrète le paradoxe de Simpson. Il s’appuie sur la génération de données simulées, l'exploration de différentes hypothèses explicatives et une démonstration progressive des effets d’agrégation non contrôlés.

Cette étude a donné lieu à une publication LinkedIn destinée à la vulgarisation de ce phénomène statistique.

## Contexte

Un département de montagne souhaite valoriser ses sentiers. Dans cette optique, il s'équipe (capteurs, données GPS, collecte des retours utilisateurs) afin de mieux valoriser et adapter son offre.

L’analyse des données récoltées révèle une tendance surprenante :

> Plus les randonneurs passent de temps sur les sentiers, moins ils semblent effectuer de dénivelé.

Ce résultat, contre-intuitif, suggère qu’une randonnée de 3h peut ne représenter que 300m de D+ tandis qu’un itinéraire de 1h30 peut facilement dépasser les 1000m de D+. Plusieurs hypothèses sont alors testées pour expliquer ce paradoxe apparent, notamment la distance linéaire, sans succès.

C’est en segmentant les randonneurs selon leur niveau (de Loisirs à Elite) que la clé apparaît : les tendances observées à l’intérieur de chaque sous-groupe sont inversées par rapport à la tendance globale. C’est le cœur du paradoxe de Simpson.

## Objectifs

- Simuler un jeu de données cohérent représentant différents profils de randonneurs.
- Visualiser les relations entre temps de randonnée, dénivelé et distance parcourue.
- Identifier les effets de confusion liés à l’agrégation des données.
- Montrer comment la segmentation révèle des dynamiques contraires au niveau global.

## Le paradoxe de Simpson

Le paradoxe de Simpson désigne une situation où une tendance observée globalement est inversée lorsqu’on segmente les données en sous-groupes.

Dans ce projet :
- À l’intérieur de chaque profil de randonneur, la relation entre le temps et le dénivelé est positive et logique : plus le dénivelé est important, plus la randonnée prend du temps,
- Lorsque l’on regroupe tous les profils sans distinction, la tendance s’inverse : on observe une corrélation négative entre la durée de la randonnée et le dénivelé.

Cette inversion est causée par un facteur de confusion : le niveau du randonneur, qui influence à la fois la vitesse et les performances, et biaise ainsi les conclusions si l’on ne le prend pas en compte.

## Structure du projet

Le projet se compose d’un notebook Python contenant :

1. La simulation des données pour plusieurs profils (Loisirs, Intermédiaire, Sportif, Avancé, Elite) avec distributions spécifiques de dénivelé et de vitesse ascensionnelle.
2. Un filtrage réaliste des données incohérentes (garde-fous).
3. La génération de distances linéaires plausibles.
4. Trois visualisations principales :
   - **Graphe 1** : relation globale temps / dénivelé, contre-intuitive.
   - **Graphe 2** : test de l’effet distance comme variable confondante.
   - **Graphe 3** : visualisation par profil, révélant le paradoxe de Simpson.

Chaque graphique est enrichi d’une régression linéaire (globale et par sous-groupe) et de commentaires d’analyse.

## Technologies utilisées

- Python 3.10+
- Librairies :
  - `numpy`, `pandas` pour la simulation et la gestion des données
  - `matplotlib`, `seaborn` pour la visualisation
  - `scipy.stats` pour les distributions normales
  - `scikit-learn` pour la régression linéaire

## Enseignements

Cette étude rappelle qu’il ne suffit pas d’avoir un volume important de données pour obtenir des résultats fiables. Il est essentiel de :
- Segmenter les données selon des critères pertinents,
- Identifier les variables de confusion potentielles,
- Interroger les tendances globales, surtout si elles contredisent l’intuition.

Le paradoxe de Simpson, bien que connu, reste un piège courant dans l’interprétation des données agrégées.

## Auteur

**Pierrick Girard**  
MontBlanc Data  
[LinkedIn](https://www.linkedin.com/in/pierrick-g-4721a2190/) • [GitHub](https://github.com/montblancdata)

## Licence
Projet distribué sous licence libre.
