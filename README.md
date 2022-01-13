# Summary

**INTRO** - Intro

**1 - MongoDB sur Atlas**
- Création de l'espace /création des droits
- Création de la Database
- Choix des serveur d'herbergemt
- Choix du pays du serveur
- Création d'un acces utilisateur / Création d'un white list IP
- Création d'un cluster
- Choix de Connection au cluster 

***2 - BDD**
- Import de la BDD dans le cluster via le shell

**3 - IDE**
- Affichage de la BDD via Compass
- Ajout de l'extention Mongodb et connection a la BDD sur Visual studio code

**4 - Index**
- Création d'un index

**5 - Commande Mongodb**
- Opérateurs
- Création de notre collection clients
- Création de documents
- Find
- Update

**6 - Aggrégation**
- Triage des ville
- Calcule du prix des paniers en moyenne
- Création d'une promotion si un clients viens le jour de son anniversaire

**7 - GeoJson**
- Forme Possible

**8- Création de l'interface**

**9 - Connection de l'API a mongoDB**
 
 
 
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

- Opérateur

| Operator          |  Correspondance                             |
| :---------------  |:---------------                             |
| $eq               | éguale à                                    |
| $gt               | plus grands que                             |
| $lt               | plus petit que                              |
| $gte              | plus grand ou éguale                        |
| $lte              | plus petit ou éguale                        |
| $in               | est contenue dans l'array suivant           |
| $ne               | different de                                |
| $lt               | n'est pas contenue dans l'array suivant     |

| Commande          |  Correspondance                             |
| :---------------  |:---------------                             |
| .find             | rechercher dans un document                 |
| .insert           | ajout dans un document                      |
| .drop             | suprimer une collection                     |
| .update           | actualiser les données d'un document        |
| .updateMany       | actualiser les données de tous les documents|
| .distinc          | rechercher une valeurs distinct             |
| .count            | Compter le nombre d'éléments                |



- Création de notre collection clients
```db.createCollection("clients")```

- Création de documents
```
db.client.insertMany([{ 
   "nom": "Danon", 
   "prenom": "Arthur"
}, 
{ 
   "nom": "Le moine seronie", 
   "prenom": "Adrien"
}, 
{ 
   "nom": "Klein", 
   "prenom": "Nicolas"
}])
```

- Update<br>
*Cela ajoute le field ```age``` : 20 a tous les documents*
```
db.client.updateMany({}, {$set: {"age":20}})
```

- Find <br>
*Cela permet de rechercher dans notre collection* ``$eq`` = ``===``
```
db.client.find({"prenom" : { $eq : "Arthur" }})
```

```
{ _id: ObjectId("61e0474e97d888e7415d5505"),
  nom: 'Danon',
  prenom: 'Arthur',
  age: 20 }
```

## Aggregation
- Triage des ville
Dans notre project nous utiliserons les liens d'agragation de mongodb pour regrouper le nombre de clients par ville, pour savoir quel dans quelle ville nos boutique sont les plus rentable/ou pas.<br><<br>
Pour cela nous additionons le nombre de points de fidelité des clients par ville.<br><br>
Avec cela nous pouvons deduire le prix des panier moyen des clients par ville.<br>
```
db.client.aggregate([{
  $group :{
  _id: "$city",
  countSmaller: { $sum : {$cond: [{ $lte : ["$points" , 250000]}, 1 , 0]}},
  countBigger: { $sum : { $cond :[{$gt: ["points", 250000]}, 1,0]}}
  }}])
  
```
```
{ _id: 'Lyon', countSmaller: 9172, countBigger: 36124 }
{ _id: 'Paris', countSmaller: 9043, countBigger: 35876 }
{ _id: 'Marseille', countSmaller: 8961, countBigger: 35735 }
```

- Calcule du prix des paniers en moyenne
Ils nous est interessants de savoir le prix moyen pour cibler plus precisement nos prix et notre communication selon nos boutique.
```
db.clients.aggregate(
   [
     {
       $project:
         {
           _id: "$idClient",
           moyenPanier: { $avg: "$panier"  },
         }
     }, {
         $group: {
             _id: "_id",
             moyenne : { $avg: "$moyenPanier"},
         }
     }
   ]
)
```
```
[
  {
    "_id": "_id",
    "moyenne": 46.66666666666667
  }
]
```

- Fidelistation
Pour fideliser nos clients nous pouvons leurs emmetre un bon cadeau apres un nombre de passage depassé dans nos boutique.
```
db.clients.aggregate(
   [
     {
       $project:
         {
           _id: "$idClient",
           Nombreachat: { $size: "$panier"  },
         }
     }
   ]
)
```

```
[
  {
    "_id": 656565,
    "Nombreachat": 3
  },
  {
    "_id": 606060,
    "Nombreachat": 3
  }
]
```

- Création d'une promotion si un clients viens le jour de son anniversaire
```
db.clients.find({
   "$expr": { 
       "$and": [
            { "$eq": [ { "$dayOfMonth": "$dob" }, { "$dayOfMonth": new Date() } ] },
            { "$eq": [ { "$month"     : "$dob" }, { "$month"     : new Date() } ] }
       ]
    }
})
```



## GeoJson
Nous aurons besoin de GeoJson dans notre project pour afficher une carte avec toute nos boutique, mais aussi a etablir un plan de route pour des livreur ex *ubereat*.<br>
Des études de marchés peuvent etre faite suivant les zone geographique des boutiques.

```
db.boutique.insertMany([{ 
   "nom": "boutique1", 
   "localisation": { 
       "coordinates": [43.9507, 4.8075], 
       "type": "Point" 
   } 
}, 
{ 
   "nom": "Boutique2", 
   "localisation": { 
       "coordinates": [43.95397, 4.80478], 
       "type": "Point" 
   } 
}, 
{ 
   "nom": "Boutique3", 
   "localisation": { 
       "coordinates": [43.944787, 4.804031], 
       "type": "Point" 
   } 
}])
```
![12](https://user-images.githubusercontent.com/65304878/149370589-15d1aeb2-a1d9-4e02-b719-dc70a2cd8a43.png)

- Forme possible

*Point*<br>
```
{
   "type": "Point",   
   "coordinates": [75, 15]
}
```
*Ligne*<br>
```
{
   "type": "LineString",    
   "coordinates":
   [
       [10, 40], [10, 30], [20, 20]   
   ]
}
```
*Polygone*<br>
```
{
  "type": "Polygon", 
  "coordinates": 
   [
        [
          [40, 20], [55, 75], [25, 20], [90, 10], [25, 40]  
        ],
        [
          [30, 20], [55, 65], [10, 30], [10, 30] 
        ]
   ] 
}
```



## Création de l'interface
Pour notre project nous aurons besoin d'une interface web permettant de resistituer les données des clients et des boutiques.
Cette interface serait utile pour créer des statistique en forme de graphique et pout tous simplement faire des requete simple/complexe avec un basic bouton sur une interface.

Exemple:
*rechercher tous les john et sortir leurs fiche de coohordoné*
```
db.clients.find({"prenom":"John"})
```


