Responsive & Media Queries
===================


Les **Media Queries** permettent de donner des propriétés spécifique pour chaque tailles d'écrans. 
On peut les utilisées directement dans la page **css** global, ou dans un fichier **css** appart. 

----------
#### <i class="icon-file"></i> Dans la page css globale
```
@media  screen and (min-width: 300px) and (max-width: 600px) {
	.div {
		background-color:red;
		}
	}
```

Dans l'exemple ci-dessus, on dit que si notre taille d'écran est de minimum 300px et de maximum 600px alors la class div aura un background rouge.

-------------  
#### <i class="icon-file"></i> Dans une nouvelle page css

Dans le html :
```
<link rel="stylesheet" type="text/css" media=" screen and (min-width: 300px) and (max-width: 600px)">
```

Dans le css : 
```
.div {
	background-color: red;
	}
```
--------
Les deux codes ci-dessus font exactement la même chose.

--------
##Pour laisser l'OS calculer la taille
dans le HTML :
```
<meta name="viewport" content="initial-scale=1.0" />
<meta name="viewport" content="initial-scale=1.0, user-scalable=yes" />
```
--------
##Pour le posistionnement (entête, pied de page, partie principale, colonne latérale):

```
/* CSS Normal */
*#sidebar {
   float: right;
   width: 200px;
}
*#main {
   margin-right: 200px;
}

@media (max-width: 1024px) {
   /* CSS appliqué aux petits écrans */
   #sidebar {
      float: none;
      width: auto;
   }
   #main {
      margin-right: 0px;
   }
}
```
Pensez à réduire un maximum les marges (margin et padding)
Favoriser les marges latérales, l'aspect aéré sera conservé.
Pensez aussi à faire de l'espace entre les lignes pour une meilleur visibilité sur tout écran.
Sur l’ordi, on pouvait utiliser les effet de survol et de clic pour déclencher des événements en vue d’afficher un menu par exemple. Ceci est plus compliqué sur un écran tactile et parfois mauvais pour l’accessibilité : qu’est-ce qu’un clic sur un smartphone ?

En revanche, il est possible de faire plein de choses nouvelles sur un écran tactile, comme le « swipe » pour passer d’une page à une autre ou utiliser divers actions utilisant le multi-touch. Pensez-y quand vous faites un site mobile !

##Pour les images
Donner la taille dans le HTML pour que l'OS calcule lui même l'adaptation à l'écran.
Dans le html :
```
<img src="image.jpg" alt="lorem ipsum" height="320" width="640">
img {
    max-width: 100%;
    height: auto;
}
```

##Pour les background:

*Avec aucun background-size (l’image est placée telle qu’elle dans le bloc et on découpe ce qui dépasse)
*Avec background-size: contain (on redimetionne l’image pour qu’elle soit entièrement visible)
*Avec background-size: cover (on agrandit l’image en conservant les proportions pour qu’elle recouvre tout, puis on découpe ce qui dépasse en bas)
*Avec background-size: 50px 70px (l’image fait 50px par 70px) 
*Avec background-size: 100% 100% (l’image fait la taille du bloc, quite à perdre ses proportions)
Notez que l’on peut également jouer avec background-position et background-repeat pour obtenir d’autres effets.


##Pour les tableaux

Avec ce code CSS le tableau s'étirera en longueur et créera des sous parti les unes en dessous des autres:
```
table, tbody { 
	display: block; 
	}
tr { 
	display: table; 
	}
td { 
	display: table-row; 
	}
```
Pour que les tableau garde ces paramètres à l'horizontal ce qui donne un travail moins propre mais peut être plus lisible en découpant le tableau en morceaux et les mettre les uns en dessous des autres:
```
@media (max-width: 600px) {
    table tr th:nth-of-type(2),
    table tr td:nth-of-type(2) {
        display: none;
    }
}

@media (max-width: 500px) {
    table tr th:nth-of-type(3),
    table tr td:nth-of-type(3) {
        display: none;
    }
}

@media (max-width: 400px) {
    table tr th:nth-of-type(4),
    table tr td:nth-of-type(4) {
        display: none;
    }
}
```

##Pour gérer les flottants


Ceci n’est pas pratique quand on redimensionne la page : les éléments sortent de leur cadre et masquent le contenu suivant.

Au lieu de faire des float utiliser plutôt en CSS le inline-block:

```
ul.menu {
}

ul.menu li {
    display: inline-block;
    width: 100px;
    height: 40px;
}
Et non :
ul.menu {
    height: 40px;
}

ul.menu li {
    float: left;
    height: 40px;
    width: 100px;
}
```



Dans le CSS:

```
	body { 
		word-wrap: break-word;
		 }
	pre { 
		white-space: pre-wrap; 
		} /* pour firefox et les <pre> */
```

Le texte ne déformera alors plus les blocs, mais sera remis à la ligne.

##La tailles des polices: