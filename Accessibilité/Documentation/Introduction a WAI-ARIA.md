# Introduction à WAI ARIA (traduction)
 
L’article qui suit est la traduction de l’article « Introduction to WAI ARIA« , publié parGez Lemon sur Dev Opera, le site d’Opera Software destiné aux développeurs.
Gez Lemon est un expert reconnu de l’accessibilité web. Il est membre du WaSP (Accessibility Task Force ) et travaille pour The Paciello Group, entreprise de conseil spécialisée dans l’accessibilité web.
Cette traduction, comme l’article original, est placée sous licence Creative Commons by-nc-sa 2.5.
Cet article est destiné à des personnes ne connaissant pas ARIA. Vous devriez avoir une bonne connaissance du langage HTML et des problèmes que peuvent rencontrer les personnes handicapées sur le web. Connaître quelques application web « riches » (RIA) d’un point de vue utilisateur serait un plus.
Après avoir lu cet article, vous comprendrez à quoi sert ARIA, comment l’intégrer à vos sites, et comment l’utiliser dès immédiatement et même sur le plus simple des sites pour le rendre plus accessible.

##Introduction
Le langage HTML (HyperText Markup Language) n’a pas été conçu pour créer des applications web. Le nombre de contrôles (bouton, case à cocher, etc.) qu’il propose est limité, et il est basé sur une communication client / serveur séquentielle. Les développeurs d’applications web ont contourné ces limitations en créant leurs propres widgets (contrôles graphiques) associés à Javascript pour leur ajouter le comportement désiré.
Malheureusement, les techniques utilisées pour outrepasser ces limitations ne sont absolument pas accessibles. Bien que ces widgets ressemblent à ceux d’une application bureau classique comme la représentation d’une arborescence (tree view), le rôle (ce que le widget fait), l’état (sa configuration, comme « checked » pour une case à cocher), et d’autres informations importantes ne sont pas disponibles pour les technologies d’assistance (comme les lecteurs d’écran). Ce serait comme styler une ligne de texte pour qu’elle ressemble à un titre, sans utiliser un élément définissant un titre (h1 à h6). Le texte ressemble à un titre, mais les technologies d’assistance n’ont pas accès à cette information.
Les mises à jour sont souvent mal perçues par les personnes utilisant une technologie d’assistance. Ces outils s’attendent à ce que le contenu change lors d’un événement de navigation « classique », comme un clic sur un lien ou un envoi de formulaire. Les applications web utilisent des techniques comme AJAX pour mettre à jour le contenu en arrière plan, ce qui peut passer inaperçu pour les technologies d’assistance. Si elles sont tout de même informées de ces mises à jour, l’utilisateur n’est pas pour autant informé que le contenu à été mis à jour, et n’a aucun moyen de localiser la zone mise à jour.
WAI-ARIA est une spécification qui propose la possibilité de définir une description des rôles, des états et des propriétés pour les widgets personnalisés, de manière à ce qu’ils soient reconnaissables et utilisables par les utilisateurs de technologies d’assistance. WAI-ARIA propose également un système permettant de s’assurer qu’un utilisateur de technologie d’assistance est informé des mises à jour de l’application.
Petit historique du langage HTML
Le langage HTML a été conçu pour être un système hypertexte, permettant de structurer et de partager des documents liés entre eux. Les premiers brouillons de la spécification HTML définissaient des balises comme des titres, des paragraphes, des listes, ou des ancres, pour ajouter une structure à des documents texte. La première proposition d’une spécification HTML par l’IETF incluait l’élément img, permettant d’ajouter des images à l’intérieur du document. La première spécification formelle fût HTML 2, basée sur les premiers brouillons de HTML. Cette spécification a défini les formulaires, ainsi que quelques composants d’interface permettant de créer des zones éditables, des boutons, des cases à cocher, des boutons radio, et des menus déroulants. Le petit ensemble de de contrôles définis dans HTML 2 n’a quasiment pas changé jusqu’à HTML 4.01, que nous utilisons actuellement.
Le modèle de communication de HTML est basé sur un modèle client / serveur : le client envoie des requêtes et reçoit des réponses ; Le serveur web attend les requêtes, les traite, puis renvoie une réponse au client. Puisque HTML ne définit pas de gestion de comportement, la communication est séquentielle : le client demande une page au serveur, le serveur traite la requête et renvoie une page au client.
Applications web
Les applications web essaient d’imiter les applications bureau classiques, mais ces applications web sont elles-mêmes exécutées à l’intérieur d’une application bureau : le navigateur. Il existe deux différences fondamentales entre HTML, avec son modèle de communication, et une application de bureau traditionnelle :
*	Les applications de bureau possèdent une couche de comportement qui ne repose pas sur des requêtes serveur.
*	Les applications de bureau possèdent un nombre bien plus élevé de widgets.

##Reproduction d’applications bureau
Requêtes serveur en arrière plan
Pour simuler les applications bureau classiques, les applications web utilisent Javascript pour la partie comportement. Javascript peut par exemple être utilisé pour ouvrir et refermer un élément de menu lorsque l’utilisateur intéragit avec l’élément. Des données doivent parfois être récupérées sur le serveur : l’application peut par exemple récupérer des enregistrement dans une base de données pour mettre à jour des informations sur la page. Lorsque l’application doit interagir avec le serveur, des techniques comme AJAX ou un élément IFrame masqué sont utilisés pour communiquer de manière transparente avec le serveur.
Reproduire des composants riches (widgets)
Puisque HTML propose très peu de widgets (ndt : dans la suite de l’article, ce mot sera souvent utilisé pour désigner les contrôles d’interface), il est parfois nécessaire de créer des composants plus complexes pour une application web, comme une case à cocher proposant trois états, ou un bouton glissant (slider). Ces composants sont habituellement créés en utilisant des éléments graphiques couplés à Javascript pour qu’ils ressemblent et se comportent comme des composants natifs.

Problèmes d’accessibilité avec la reproduction de composants natifs
Visuellement, créer des contrôles riches et effectuer des requêtes serveur en arrière plan permet de créer une meilleure expérience utilisateur. Malheureusement, ces techniques posent de graves problèmes d’accessibilité pour les utilisateurs de technologies d’assistance, comme les lecteurs d’écran.
*	Les composants créés de cette manière sont rarement accessibles au clavier.
*	Le rôle d’un composant, « ce qu’il fait », n’est pas accessible aux technologies d’assistance.
*	Les états et propriétés d’un composant ne sont pas accessibles aux technologies d’assistance.
*	Les mises à jour ne sont pas signalées aux technologies d’assistance.

## WAI-ARIA à la rescousse
Tous les problèmes listés ci-dessus sont résolus par la specification WAI-ARIA (qui sera abrégée ARIA jusqu’à la fin de cet article) : Web Accessibility Initiative’sAccessible Rich Internet Applications. ARIA est une technologie positive : plutôt que de dire aux développeurs ce qu’ils ne peuvent pas faire, elle leur propose simplement de créer des applications web riches. ARIA est de plus une technologie très facile à implémenter.

## Navigation au clavier
En plus de proposer une alternative aux éléments non-textuels, permettre d’interagir avec les contrôles d’interface à l’aide du clavier fait partie du minimum à mettre en place pour rendre un système plus accessible. Un développeur sensibilisé à l’accessibilité devrait réaliser des widgets dont les éléments permettent de recevoir le focus, tout comme le fait par défaut un élément input de type image (<input type="image" ...>). Malheureusement, la plupart des widgets ne sont pas réalisés de cette manière : ils utilisent plutôt des éléments comme img, ou peuvent être composés de plusieurs éléments placés dans un conteneur div qui ne reçoit pas le focus.
L’attribut tabindex est arrivé avec HTML4, utilisable sur les éléments suivants : a, area, button, input, object, select, et textarea. Cet attribut accepte un nombre positif compris entre 0 et 32767. La navigation commence avec les éléments ayant la plus petite valeur tabindex, et se poursuit jusqu’à l’élément ayant la valeur la plus élevée. Les éléments ayant pour valeur 0 sont visités dans leur ordre naturel d’apparition dans le code. Si le document a une structure logique, l’attribut tabindex n’est pas requis car les éléments d’interface sont naturellement définis dans l’ordre de tabulation.
ARIA étend l’attribut tabindex, lui permettant d’être utilisé sur tous les éléments visibles. ARIA autorise également l’utilisation d’une valeur négative pour les éléments ne devant pas être proposés à la navigation au clavier, mais pouvant recevoir le focus par programmation. Bien que la valeur d’un attribut tabindex négatif n’aie pas d’importance (l’élément ne pourra jamais recevoir le focus au clavier), la valeur -1 est couramment utilisée lorsqu’un élément ne doit pas recevoir le focus au clavier, mais uniquement par programmation.
Par exemple, vous pourriez réaliser un menu dont l’élément conteneur est accessible à l’aide de la tabulation clavier, mais pas les éléments qu’il contient. Ces éléments peuvent alors être programmés pour être parcourus à l’aide des touches fléchées du clavier. Ainsi, les utilisateur n’ont pas à utiliser la touche tabulation sur chacun des éléments du menu, ce qui leur permet de mieux accéder au document. C’est vrai pour tous les widgets ayant une série de composants nécessitant un accès au clavier, comme la représentation d’une arborescence.
Ajouter un élément à l’ordre naturel des tabulations
L’exemple suivant affecte la valeur 0 à l’attribut tabindex pour placer l’élément divdans l’ordre des tabulations, ce qui permettra d’y accéder à l’aide de la navigation clavier.
```
<div tabindex="0">
...
</div>
```
Tabindex négatif
L’exemple suivant utilise un tabindex d’une valeur négative, cet élément pourra alors recevoir le focus par programmation.
```
<div id="progaccess" tabindex="-1">
...
</div>
```
Dans cet exemple, l’élément div n’est pas placé dans l’ordre des tabulations, mais possède un attribut tabindex d’une valeur de -1. Le script qui suit sélectionne l’élément précédemment défini et utilise la méthode focus() pour activer le focus sur cet élément.
```
var objDiv = document.getElementById('progaccess');
// Focus on the element
objDiv.focus();
```

Que suis-je ?
ARIA propose l’attribut role pour définir les widgets, comme un bouton glissant (slider), ou définir la structure de la page, comme un menu. Un problème majeur des applications web est que n’importe quel élément peut être utilisé pour créer un widget. Les éléments HTML possèdent déjà des rôles prédéfinis. Le rôle d’un élément est « ce qu’il fait » – le rôle qu’il a dans la structure. Par exemple, le rôle des titres est bien compris par les technologies d’assistances. Lorsque des widgets sont réalisés à partir d’éléments existants, le rôle d’un élément est ce que la technologie d’assistance définit plutôt que ce qu’il représente visuellement en tant que widget. Par exemple, si le visuel d’un slider est créé en utilisant un élément img avec un texte alternatif approprié, un lecteur d’écran pourrait annoncer le contrôle comme ceci : « Image d’un slider », plutôt que quelque chose de plus intéressant, comme « Bouton glissant, 16 pour cents ».

Le rôle donné par l’attribut role prend le pas sur le rôle natif de l’élément. Dans l’exemple suivant, un élément input possède un attribut role dont la valeur est slider (nous verrons d’autres propriétés ARIA plus loin dans cet article) — le rôle indiqué à la technologie d’assistance est slider (bouton glissant), plutôt que input(entrée utilisateur).
```
<input type="image" src="thumb.gif"
alt="Effectiveness"
role="slider"
aria-valuemin="0"
aria-valuemax="100"
aria-valuenow="42"
aria-valuetext="42 percent"
aria-labelledby="leffective">
```
Lorsque le focus est placé sur cet élément, un utilisateur de lecteur d’écran comprend ce que fait ce widget. La spécification ARIA propose une liste de rôles.

Rôle des sections du document (document landmark roles)
Les rôles que nous venons de voir permettent de décrire des widgets, mais il existe également des rôles permettant de décrire la structure du document. Les document landmarks (ou description des zones) sont un sous-ensemble des rôles classiques permettant aux utilisateurs de lecteurs d’écran de comprendre le rôle d’une zone pour mieux s’orienter dans le document.
ARIA définit les rôles de document landmarks (zones du document) suivants :
`article`
Contenu ayant du sens par lui-même, comme un article ou un commentaire de blog, un message sur un forum, etc.
`banner`
Contenu à propos du site, comme le titre de la page ou le logo.
`complementary`
Permet éventuellement de définir une partie du contenu principal, mais est plus approprié pour du contenu séparé : la météo sur un portail web par exemple.

`contentinfo`
Contenu dépendant d’un autre, comme des notes de bas de page, un copyright, un lien vers la déclaration de confidentialité, un lien vers les paramètres de l’application, etc.`

`main`
Contenu directement lié ou englobant le contenu central du document.

`navigation`
Contient des liens pour naviguer dans ou en dehors du document.

`search`
Cette section contient un formulaire de recherche permettant de chercher sur le site.
Les exemples suivants utilisent les rôles banner, navigation et main pour définir la structure de la page visible sur la figure 4.

```
<div role="banner">
...
</div>
<div role="navigation">
...
</div>
<div role="main">
...
</div>
```

## États et propriétés d’ARIA

Les états (states) et propriétés (properties) d’ARIA permettent de décrire des informations supplémentaires sur les widgets et de les mettre à la disposition des technologies d’assistance, afin d’aider l’utilisateur à comprendre comment intéragir avec le widget. L’état définit une configuration ou une information unique sur un objet. Par exemple, la propriété aria-checked possède trois valeurs pour définir ses états : true, false et mixed.
Dans l’exemple du bouton glissant vu un peu plus haut, nous avons inclus différentes propriétés que nous allons voir ci-dessous, aidant à décrire un widget à une technologie d’assistance.

`aria-valuemin`
Stocke la valeur minimale qu’un bouton glissant peut avoir.

`aria-valuemax`
Stocke la valeur maximale qu’il peut avoir.

`aria-valuenow`
Stocke la valeur actuelle.

`aria-valuetext`
Stocke du texte lisible permettant à l’utilisateur de comprendre le contexte. "30 dollars", par exemple.

`aria-labelledby`
Stocke l’identifiant (attribut id) d’un élément contenant une description appropriée du widget.
Certaines propriétés peuvent être modifiées par programmation. Dans l’exemple suivant, les propriétés arial-valuenow et arial-valuetext de notre widget de bouton glissant sont mises à jour lorsque le bouton change de position :
// Définit les valeurs des propriétés ARIA
// lorsque le bouton change de position

```
objThumb.setAttribute('aria-valuenow', iValue);
objThumb.setAttribute('aria-valuetext', iValue + ' %');
```

Ajouter des rôles et attributs ARIA ne sera pas valide HTML 4.01 ou XHTML1.0, mais rassurez-vous, ARIA ne fait qu’ajouter des informations importantes à des spécifications écrites depuis un bon moment maintenant. Des travaux sont en cours pour définir une DTD pouvant être utilisée avec du XML modulaire, comme XHTML1.1. La spécification ARIA fournit une liste complète des états et propriétés permettant de définir des widgets accessibles.


Les « Live Regions » (zones mises à jour)
Les Live Regions permettent à certains éléments du document d’annoncer qu’ils ont été mis à jour, sans que l’utilisateur ne soit dérangé dans son activité. Cela signifie que les utilisateurs vont pouvoir être informés des mises à jour sans modifier leur position dans le contenu. Par exemple, une application de chat pourrait signaler une réponse de la personne avec qui l’utilisateur est en train de discuter, sans être déplacé en-dehors du champ permettant d’envoyer un nouveau message à la personne.

`aria-live`
Pour un utilisateur de lecteur d’écran, il est très difficile de comprendre ce qui a été mis à jour sur une page. ARIA propose la propriété aria-live, dont la valeur indique l’importance des mises à jour de la région. Voici les différents niveaux d’alerte pouvant être utilisés avec la propriété aria-live :

`off`
Il s’agit de la valeur par défaut, indiquant que la zone ne sera pas mise à jour.
<ul aria-live="off">

`polite`
C’est une notification normale, le comportement généralement attendu d’une Live Region. La valeur polite indique qu’il n’est pas nécessaire d’y répondre tant que l’utilisateur n’a pas terminé ce qu’il est actuellement en train de faire.
```
<ul aria-live="polite">
```

`assertive`
Ce niveau d’alerte est plus élevé que la normale, mais n’interrompt pas nécessairement l’utilisateur.
```
<ul aria-live="assertive">
```

`rude`
Cette valeur est la plus élevée, et interrompt l’utilisateur pour lui notifier la mise à jour. Il peut s’en trouver désorienté, et peut empêcher l’utilisateur de reprendre la tâche qu’il effectuait. Elle ne devrait être utilisée qu’en cas d’absolue nécessité.
```
<ul aria-live="rude">
```

Quelques autres propriétés peuvent être utilisées lorsqu’une Live Region est créée, en voici la liste.

La propriété `aria-atomic`
`aria-atomic` est une propriété optionnelle des Live Regions pouvant prendre comme valeur true ou false (par défaut si la propriété n’est pas définie).
Lorsque la zone est mis à jour, la propriété aria-atomic permet à la technologie d’assistance de savoir si elle doit décrire à l’utilisateur la zone entière ou seulement la partie ayant été mise à jour. Si cette propriété est définie à true, la technologie d’assistance devrait décrire complètement la zone. Si sa valeur est false, seule la partie mise à jour devrait être annoncée.
Dans l’exemple suivant, tous les éléments de la liste non-ordonnée seront annoncés à l’utilisateur, à moins qu’un de ces éléments ne surcharge la propriété aria-atomic.
```
<ul aria-atomic="true"
aria-live="polite">
```

La propriété `aria-busy`
`aria-busy` est une propriété optionnelle des Live Regions pouvant prendre comme valeur true ou false (par défaut si la propriété n’est pas définie). Si plusieurs parties d’une Live Region ont besoin d’être chargées avant que la mise à jour ne soit annoncée à l’utilisateur, la propriété aria-busy peut être définie à true jusqu’à ce que la dernière partie soit chargée, puis à false lorsque la mise à jour est complètement terminée. Cette propriété empêche les technologies d’assistance d’annoncer un changement avant qu’une mise à jour ne soit complétée.
```
<ul aria-atomic="true"
aria-busy="true"
aria-live="polite">
```

La propriété `aria-channel`
`aria-channel` est une propriété optionnelle des Live Regions pouvant prendre comme valeur main (par défaut si la propriété n’est pas définie) ou notify. Les canaux (channels) ont trait au matériel disponible sur le système de l’utilisateur, comme un synthétiseur vocal ou une plage Braille (ndt: lien ajouté). Si un seul canal est disponible, main et notify utiliseront tous deux le même canal. Le canal notify a une priorité plus élevée que le canal main.
```
<ul aria-atomic="true"
aria-channel="notify"
aria-live="polite">
```

La propriété `aria-relevant`
`aria-revelant` est une propriété optionnelle des Live Regions indiquant quels types de changements sont considérés comme significatifs à l’intérieur d’une zone (ajout d’un élément, suppression d’un élément et modification de texte). Cette propriété accepte une ou plusieurs des valeurs suivantes, séparées par des espaces :

* additions
Des noeuds sont ajoutés au DOM à l’intérieur de la zone.
* removals
Des noeuds sont supprimés du DOM à l’intérieur de la zone.
* text
Du texte est ajouté ou supprimé du DOM (modification de texte).
* all
Toutes les valeurs définies précédemment (additions, removals, text) s’appliquent à la zone.
En l’absence de la propriété aria-revelant, le comportement par défaut considère que les modifications significatives sont les modifications de texte et les ajouts de noeuds (aria-revelant="text additions"). L’exemple suivant n’annoncera des changements que si des noeuds sont ajoutés à la région. Si des modifications de texte surviennent ou que des noeuds sont supprimés, l’utilisateur n’en sera pas averti.
```
<ul aria-relevant="additions"
aria-atomic="true"
aria-live="polite">
```


Quand pourrons nous utiliser ARIA ?
L’utilisation d’ARIA ne présente aucun inconvénient, vous pouvez l’utiliser dès à présent. Les quatre principaux navigateurs du marché ont commencé ou prévoient de supporter ARIA. Opera 9.5 et Firefox 1.5+ disposent déjà d’un support ARIA. Internet Explorer 8 beta supporte ARIA, et l’équipe de développement de Webkit, le moteur libre utilisé par Safari (ndt: et Google Chrome), a annoncé que l’intégration d’ARIA avait commencé.
ARIA est également en train d’être largement adopté par les technologies d’assistance. JAWS 7.1+, Window-Eyes 5.5+, NVDA, Zoomtext 9+, et d’autres offrent déjà un support basique d’ARIA, et ce n’est qu’un début.
 
Soyez parmi les premiers à l’utiliser
Puisque nous venons de voir que l’utilisation d’ARIA ne provoque aucun effet de bord et que le support est déjà présent, il n’y a rien à perdre à l’utiliser dès maintenant, et beaucoup à gagner. Même si votre site web est le plus simple du monde, vous pouvez y inclure des document landmarks (rôles des sections) pour aider l’utilisateur à mieux naviguer et à s’orienter à l’intérieur du contenu.
Utilisez les rôles de section (document landmark roles)
Sur mon site web personnel, j’ai utilisé les rôles de zones main, navigation, search, et secondary. Prenons la structure suivante.
```
<div id="ads">
...
</div>
<div id="nav">
<form id="searchform" ...>
...
</form>
...
</div>
<div id="content">
...
</div>
```

Nous pourrions écrire l’attribut role pour nos document landmarks directement dans le code HTML :
```
<div id="ads" role="banner">
...
</div>
<div id="nav" role="navigation">
<form id="searchform" role="search" ...>
...
</form>
...
</div>
<div id="content" role="main">
...
</div>
```

Alternativement, puisque les pages sont structurées de manière à pouvoir être stylées avec CSS, la page a des chances d’être structurée à l’aide d’attributs id pouvant être passés à une fonction Javascript. L’exemple suivant est une fonction Javascript simple acceptant l’attribut id d’un élément et une valeur de role, lui permettant de définir l’attribut role de l’élément correspondant.
```
function addARIARole(strID, strRole)
{
// Find the element to add a role property to
var objElement = document.getElementById(strID);
if (objElement)
{
// Add the role property to the element
objElement.setAttribute('role', strRole);
}
}
```

La fonction peut alors être appelée en passant en paramètre l’attribut id de la section et son rôle dans le document. Considérez la structure de document ci-dessous : nous pourrions utiliser cette fonction Javascript pour insérer un attribut role, plutôt que de l’écrire dans le code HTML.
```
function setupARIA()
{
// Add ARIA roles to the document
addARIARole('content', 'main');
addARIARole('nav', 'navigation');
addARIARole('searchform', 'search');
addARIARole('ads', 'banner');
}

window.onload = setupARIA;
```

Indiquer les champs requis
Si certains de vos formulaires contiennent des champs requis, vous pouvez utiliser la propriété `aria-required`. Cette propriété indique qu’une entrée utilisateur est requise pour envoyer le formulaire. L’exemple suivant ajoute la propriété `aria-required` à un élément input classique.
```
<label for="contactname">Name</label>
<input type="text"
id="contactname"
name="contactname"
size="30"
aria-required="true">
```

Le système de blog WordPress a déjà commencé à utiliser l’attribut aria-requiredpour les champs requis du formulaire d’envoi de commentaire.

Ajouter d’autres propriétés pertinentes
Beaucoup de propriétés ARIA peuvent être utilisées sur des sites web très simples, comme `aria-labelledby` et `aria-describedby`. La propriété aria-labelledby pointe sur un ou plusieurs éléments considérés comme le libellé de l’élément, tandis que l’attribut aria-describedby pointe sur un ou plusieurs éléments considérés comme la description de l’élément.
```
<h2 id="limg">Paragliding</h2>
<p id="dimg">
A long description of our paragliding trip ...
</p>

<div>
<img src="takeoff.png"
alt="Getting ready to take off"
aria-labelledby="limg"
aria-describedby="dimg">
</div>
```

Priorité des attributs HTML

Les attributs ARIA ont la priorité sur le code HTML de base. C’est à dire que si aria-labelledby est utilisé parallèlement à `<label for="">`, seul l’attribut aria-labelledby sera pris en compte. L’élément label est toujours encouragé pour les anciens navigateurs ne supportant pas ARIA. Une technique simple pour éviter les conflits est d’utiliser l’attribut aria-labelledby pour faire référence à l’élément
label, ce qui permet d’être sûr que le libellé est lisible, quel que soit le support d’ARIA.
```
<label id="lblef" for="effectiveness">Effectiveness</label>
<input type="image"
role="slider"
id="effectiveness"
aria-labelledby="lblef"
...>
```

Parcourez la liste complète des états et propriétés pour en apprendre plus sur la manière dont ARIA peut vous aider à rendre votre contenu plus accessible.

Ensemble, maintenant
HTML n’a pas été conçu dans le but de créer des applications web, mais les développeurs les ont créées en dessinant leurs propres widgets, et en leur ajoutant des comportements avec Javascript. Le problème est que le rôle, l’état et les propriétés des widgets et du contenu mis à jour sur ces pages n’est pas correctement transmis aux technologies d’assistance. La spécification ARIA résoud ce problème en permettant aux développeurs de décrire précisément leurs éléments d’interface, leur structure de document, et les zones de la page qui seront modifiées.
Que vous développiez une application web complète avec de nombreux wigets et mises à jour dynamiques, ou le plus simple des sites web, vous pouvez commencer à utiliser ARIA dès maintenant pour vos utilisateurs handicapés.
