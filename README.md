# Summary

Intro

1 - MongoDB sur Atlas
- Création de l'espace /création des droits
- Création de la Database
- Choix des serveur d'herbergemt
- Choix du pays du serveur
- Création d'un acces utilisateur / Création d'un white list IP
- Création d'un cluster
- Choix de Connection au cluster 

2 - BDD
- Import de la BDD dans le cluster via le shell

3 - IDE
- Affichage de la BDD via Compass
- Ajout de l'extention Mongodb et connection a la BDD sur Visual studio code

2 - Index
- Création d'un index

6 - Operateur

7 - aggregation

8 - GeoJson

* - Création de l'interface 

* - Connection de l'API a mongoDB
 
 
 
# Intro
Notre project consiste a rassembler les donnée personel de clients et créer par la suite un programme de fidelités pour un restaurant.
- Pour le bien de notre project nous mettons en place une BDD sur mongodb.
- Création des regles permetant la manipulation des données dans mongodb
- Creation d'un Dashboard de visualisation et statistique des données avec une API "en cours(optionel)"

Nous créons une inscription automatic a chaque achat a un programme de fidelité.<br>
Ce programme de fidélité recuperera : ``Nom``, ``Prenom``, ``Email``, ``Date de naissance``, ``Adresse``, ``Pays``, ``Ville``, ``Sexe``, ``Status social``.<br>
Nous Stockerons dans notre BDD, chaque donnée de passage en boutique.<br>
Les Passages en boutique recuperera : ``Date``, ``Articles achetés``, ``Prix total``, ``Categorie de produit``, ``Nombre de point généré``.


## Création d'un espace MongoDB sur Atlas
- Création de l'espace / création des droits
![1](https://user-images.githubusercontent.com/65304878/149127230-9d180b9a-3d0f-4ea5-8da3-21fc9a6b531f.JPG)

- Création de la Database
![2](https://user-images.githubusercontent.com/65304878/149127792-abf0261d-e05c-4b5a-b53b-bcd211f03ea8.JPG)

- Choix des serveur d'hebergement
![3](https://user-images.githubusercontent.com/65304878/149127896-79a69376-409c-4ebf-b68d-753d880f903e.JPG)

- Choix du pays du serveur
![4](https://user-images.githubusercontent.com/65304878/149128004-4804eb43-577e-400b-b526-6b0432caba71.JPG)

- Création d'un acces utilisateur / Création d'un white list IP
![5](https://user-images.githubusercontent.com/65304878/149128211-d5f33875-9aad-4e5d-8935-aafc174c3c29.JPG)

- Création d'un cluster
![6](https://user-images.githubusercontent.com/65304878/149128257-e78086f3-94f9-4ea4-8e5c-61a83968a011.JPG)

- Choix de Connection au cluster 
![7](https://user-images.githubusercontent.com/65304878/149128326-0fed2726-b53a-4320-9523-ce6fd93f198a.JPG)



## BDD
- Import de la BDD dans le cluster en shell
La collection db.restaurant contient par ID : ``Adresse``, ``borough``, ``cuisine``, ``grades``, ``name``, ``restaurant_id``
![8](https://user-images.githubusercontent.com/65304878/149128393-f68acd2f-c06e-4c24-a678-ebfc2f4dc99e.JPG)



## IDE 
- Affichage de la BDD via Compass
![9](https://user-images.githubusercontent.com/65304878/149128521-ac47c4d6-0445-46ee-9191-89da8a467374.JPG)
- Ajout de l'extention Mongodb et connection a la BDD sur Visual studio code
![10](https://user-images.githubusercontent.com/65304878/149346035-5a9fbb97-71f9-4d76-9eb1-4edc4b19f149.png)


## Index
- Création d'un index
L'index permetra d'acroitre la rapidité des requetes sur la BDD



| Operator          |  Correspondance                         |
| :---------------  |:---------------                         |

```code```
