# Summary

**INTRO** - Intro

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

4 - Index
- Création d'un index

5 - Commande Mongodb



7 - aggregation

8 - GeoJson

* - Création de l'interface 

* - Connection de l'API a mongoDB
 
 
 
# Intro
Notre project consiste a rassembler les donnée personel de clients et créer par la suite un programme de fidelités pour un restaurant.
- Pour le bien de notre project nous mettons en place une BDD sur mongodb.
- Création des regles permetant la manipulation des données dans mongodb
- Creation d'un Dashboard de visualisation et statistique des données avec une API "en cours(optionel)"

Nous créons une inscription automatique a chaque passage en boutique a un programme de fidelité.<br>
Ce programme de fidélité recuperera : ``Nom``, ``Prenom``, ``Email``, ``Date de naissance``, ``Adresse``, ``Pays``, ``Ville``, ``Sexe``, ``Status social``.<br><br>
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
*Cette collection a été remplacé par la collection clients*
- Import de la collection dans le cluster en shell
La collection db.restaurant contient par ID : ``Adresse``, ``borough``, ``cuisine``, ``grades``, ``name``, ``restaurant_id``
![8](https://user-images.githubusercontent.com/65304878/149128393-f68acd2f-c06e-4c24-a678-ebfc2f4dc99e.JPG)



## IDE 
*Cette collection a été remplacé par le collection clients*
- Affichage de la BDD via Compass
![9](https://user-images.githubusercontent.com/65304878/149128521-ac47c4d6-0445-46ee-9191-89da8a467374.JPG)
- Ajout de l'extention Mongodb et connection a la BDD sur Visual studio code
![10](https://user-images.githubusercontent.com/65304878/149346035-5a9fbb97-71f9-4d76-9eb1-4edc4b19f149.png)


## Index
- Création d'un index
Les index créent une copie d'un segment de votre donnée, parfois dans un ordre spécifique, dans votre base de données. Cela permet à MongoDB de pouvoir les parcourir de manière efficace pour vous retourner le ou les documents recherchés rapidement. *practicalprogramming.fr*<br>
```db.clients.createIndex({"nom":1, "prenom":1})```<br>
![11](https://user-images.githubusercontent.com/65304878/149357573-43149aac-7f50-4f1a-974f-4238ba7db47b.png)


## Commande Mongodb
-Création de notre collection clients
```db.createCollection("clients")```

-Création de documents


```
db.avignon.insertMany([{ 
   "nom": "Palais des Papes", 
   "localisation": { 
       "coordinates": [43.9507, 4.8075], 
       "type": "Point" 
   } 
}, 
{ 
   "nom": "Pont Saint-Bénézet", 
   "localisation": { 
       "coordinates": [43.95397, 4.80478], 
       "type": "Point" 
   } 
}, 
{ 
   "nom": "Collection Lambert", 
   "localisation": { 
       "coordinates": [43.944787, 4.804031], 
       "type": "Point" 
   } 
}])
```













## Opérateur

| Operator          |  Correspondance                         |
| :---------------  |:---------------                         |
| $eq               | éguale à                                |
| $gt               | plus grands que                         |
| $lt               | plus petit que                          |
| $gte              | plus grand ou éguale                    |
| $lte              | plus petit ou éguale                    |
| $in               | est contenue dans l'array suivant       |
| $ne               | different de                            |
| $lt               | n'est pas contenue dans l'array suivant |

```code```
