Responsive & MediaQueries
=======================


Ceci est un tutoriel sur le Responsive et les MediaQueries. Ce tutoriel va montrer comment les MediaQueries vont permettre de faire un site internet Responsive.

----------

#Qu'est ce que le responsive design et les medias queries?
----------

##Le responsive design
----------
Le responsive design permet d'afficher un site internet sur différents supports tels que les desktop, les laptops, les tablettes et les smartphones. Le site modifie son apparence en fonction de la taille de l'écran sur lequel il est lu.

![Alt text] (http://jmgraphcom.com/wp-content/uploads/2016/01/responsive-design.png)

----------


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

--------

Pour les tailles de polices, on connaît les pixels, les em, les en ou les %. Mais il y en a maintenant des nouvelles. Une d’elles permet de faire en sorte que la taille de police soit proportionnelle à la taille de l’écran : ce sont les unités vw, vh, vmin et vmax (v comme viewport, w pour la largeur, h pour la hauteur).

10vw correspond à une taille de 10% de la largeur de la fenêtre du navigateur. Si la fenêtre fait 1600px de large, c’est comme une taille de police de 160px. Si la fenêtre est ramenée à 500px de large, alors la police sera équivalente à 50px.
10vh est l’équivalent, mais pour la hauteur de la fenêtre.
10vmax correspond au maximum de 10vw et 10vh : si l’écran est plus large que haut, alors ce sera la valeur de 10vw qui sera retenu.
10vmin correspond au minimum de 10vw et 10vh.
L’avantage avec ça, c’est que le texte aura toujours la même proportion par rapport à la taille de l’écran, sans glisser sur plusieurs lignes.

##Pour les hauteur dynamique
Si vous avez un bloc de texte dont vous réduisez la largeur, c’est sa hauteur qui s’agrandira pour contenir tout le texte. Il ne faut donc jamais donner une hauteur fixe à un bloc de texte en responsive-design, sous peine de voir le contenu sortir de son cadre.

Utilisez plutôt une hauteur minimale : la hauteur sera alors au moins de cette valeur, mais augmentera pour tout contenir quand le texte aura subitement besoin de plusieurs lignes pour s’afficher. Ceci est particulièrement vrai pour les titres et les menus auxquelles on a toujours tendance à appliquer une hauteur fixe.

##Le pixel-ratio et les images
Si vous utilisez des images de fond en CSS, il faudra tenir compte du pixel ratio aussi : si votre écran a un pixel ratio de 2, une icône de 16 pixels sera étirée jusqu’à 32 pixels. C’est bien, car sinon les icônes sont bien trop petites, mais l’image s’en retrouve pixelisée.
*sur l’ordinateur avec un pixel-ratio de 1
*sur un mobile avec un pixel-ratio de 2
On voit tout de suite que l’icône sur mobile est bien plus jolie : elle est plus nette. C’est normale car en réalité elle fait 32 pixels (par exemple) et est du coup affichée sans être étirée. Sur l’ordinateur, elle est rétrécie, mais ceci n’altère pas la qualité de l’image de façon visible.
Afin d’arriver à ce résultat, il faut évidemment utiliser une icône plus grande dès le départ : 32 pixels, dans notre exemple.
Ensuite, on utilise très simplement du CSS pour la réduire à la taille de l’icône :

```
#bouton-16 {
    width: 16px;
    height: 16px;
    background: transparent url(icon32.png) no-repeat;
    background-position: 0px 0px;
    background-size: 16px 16px;
}
```
Que l’on peut condenser en :
```
#bouton-16 {
    width: 16px;
    height: 16px;
    background: transparent url(icon32.png) no-repeat 0px 0px / 16px 16px;
}
```
(attention, avec ça, la position et le size doivent se suivre et être séparés par un slash)

L’icône, le fichier, mesure bien 32 pixels, mais avec background-size on la rapporte à 16 pixels : le pixel-ratio de l’image sera alors de 2 et elle restera nette même sur les mobiles. Si vous prévoyez d’utiliser l’application web sur des écrans avec un pixel-ratio encore plus grand, prévoyez des images 3 voire 4 fois plus grande (donc 48px ou 64px).
Faites gaffe cependant : l’image sera plus grande et donc aussi plus lourde. Mais je pense qu’il est préférable de charger une seule image pour tous les appareils plutôt que spécifier des images différentes selon les appareils : dans la plupart des cas, la taille des fichiers ne sera pas beaucoup plus grande (perso je suis passé de 9 ko à 13 ko, ce qui est négligeable devant l’intérêt de l’astuce).

Cette méthode fonctionne aussi avec la méthode des portes coulissantes pour les images avec plusieurs icônes dedans. Si votre image avec les sprites mesure par exemple 100px sur 32px, déclarez une size de 50px par 16px. La position doit être effectuée comme si l’image mesurée réellement 50×16px, donc comme la taille en CSS, pas la taille du fichier-image.

##L'effet du :hover sur un mobile

Sur un navigateur mobile, que ce soit Firefox Mobile ou Opera, ou même les autres, un effet de « :hover » est déclenché avec le tapotement sur l’écran. Si vous avez un menu déroulant, il est possible de dérouler en tapant dessus, tout simplement.

Il y cependant un petit bug qui apparaît : si le menu contient des liens ou des boutons cliquables, alors le « tapotement » pour le :hover peut accidentellement se propager sur un lien de la liste, ce qui n’est pas pratique pour naviguer.

Il y a une petite astuce cependant : délayer le déroulement du menu. On peut le faire en JS, perso je le fais en CSS avec les transitions.

Si vous utilisez un effet d’affichage basé sur le display: none/block, ceci ne marchera pas. En revanche, si vous utilisez quelque chose basé sur le right: -9999, alors ça marchera !

Il suffit d’appliquer une transition de durée 0s sur le right, mais délayée d’une petite durée :
```
#nav:hover ul {
  transition: 0s linear .05s;
}
```