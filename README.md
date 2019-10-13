# blog
CAHIER DES CHARGES
------------------
objectif
--------
L’objectif de ce blog est de proposer un outil de valorisation de la culture africaine 
pour permettre à terme l’augmentation du nombre de visiteur 
Les cibles de ce blog seront en premier lieu les lecteurs, les passionnées du continents africain. Le contenu doit être adapté aux différentes
cibles :actualités sur la mode pour les passionnés de mode,les évènements qui auront lieu. 

périmètre
---------
Le projet doit se tourner vers la population. Le projet se doit de valoriser les contenus créés
par le blogeur ou la blogeuse.

description fonctionnelle
-------------------------
-Fonction      
 Inciter à la collaboration
-Objectif
 créer des contenus et les mettre en ligne.
 Faciliter la collaboration de tous en proposant un
 contenu et une interface accessibles 
-Niveau de priorité
 Priorité haute (première fonction du blog)

-Fonction
 Hiérarchiser l’information
-Objectif
Catégoriser les contenus afin que les visiteurs
accèdent facilement aux informations recherchées.
Créer plusieurs onglets en fonction des cibles du
blog.

-Fonction
Induire la proximité
-Objectif 
Induire les visiteurs à
commenter 

règles de gestion
-----------------
4 rubriques:art,culture,mode,danse.
barre de recherche ,mot clé 
 Abonnement, Flux RSS,
Commentaires récents (pour valoriser la
participation), Nombre de visites, Réseaux
sociaux

--BASE DE DONNEES BLOG--

admin
------
-id_admin INT PK
-nom_admin VARCHAR(100)
-mot_passe VARCHAR(100)

rubrique
--------
-id_rubrique INT PK
-nom_rubrique VARCHAR(100)

categorie
---------
-id_categorie INT PK
-nom_categorie VARCHAR(100)
-id_rubrique INT FK

article
-------
-id_article INT PK
-titre VARCHAR(100)
-contenu TEXT 
-date_creation DATETIME
-id_admin INT FK
-id_categorie INT FK

image
-----
-id_image INT PK
-lien_image BLOB
-id_article INT FK

commentaire
-----------
-id_commentaire INT PK
-nom_auteur  VARCHAR(100)
-message TEXT 
-date_commentaire DATETIME
-id_article FK

articlecom
----------
-id_artcom INT PK
-id_article INT FK 
-id_commentaire INT FK

newletter
---------
-id_new INT PK
-email  VARCHAR(60)


les requetes
------------
-afficher les rubriques
SELECT nom_rubrique FROM RUBRIQUE;

-afficher les categories dans leur rubriques
SELECT nom_categorie 
FROM categorie 
JOIN rubrique ON rubrique.id_rubrique=categorie.id_rubrique
ORDER BY nom_categorie ASC;

-afficher les articles avec leur images
SELECT lien_image,titre,contenu,date_creation
FROM article
JOIN image ON image.id_article=article.id_article
ORDER BY date_creation ASC;

-afficher les commentaires 
SELECT titre,nom_auteur,message,date_commentaire 
FROM commentaire 
JOIN article ON article.id_article=commentaire.id_article
ORDER BY date_commentaire ASC;



