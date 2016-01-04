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