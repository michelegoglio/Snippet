#Améliorer l’accessibilité d’un formulaire

L’information ne doit jamais être véhiculée par la couleur seulement.
	Penser aux daltoniens, aux personnes qui ont sur-contrasté leur écran, désactivant de ce fait les couleurs web.


**Il faut tout  de même ajouter des effets visuels pour tout utilisateur :**
* Ajouter une bordure rouge au champ lorsque non valide
* Ajouter un effet visuel au survol du champ (ne pas supprimer l’outline)

**Contrôler les couleurs, les contrastes**

SC 1.4.3 Contraste (minimum) : la présentation visuelle du texte et du texte sous forme d’image a un rapport de contraste d’au moins 4,5:1, sauf dans les cas suivants : (Niveau AA) Texte agrandi : le texte agrandi et le texte agrandi sous forme d’image ont un rapport de contraste d’au moins 3:1[…].

SC 1.4.6 Contraste (amélioré) : la présentation visuelle du texte et du texte sous forme d’image a un rapport de contraste d’au moins 7:1, sauf dans les cas suivants : (Niveau AAA) Texte agrandi : le texte agrandi et le texte agrandi sous forme d’image ont un rapport de contraste d’au moins 4,5:1 […].
Outil : [Contrast Analyser](http://paciellogroup.com/resources/contrastAnalyser)


**Utiliser les labels**
	Un utilisateur de lecteur d’écran aura l’information pertinente 
Par exemple mettre le focus sur le champ identifiant nous permettra d’entendre **« Identifiant : “toto” ; champ texte ».**
````
	<label for="login">Identifiant</label>
	<input type="text" name="login" id="login" value="">
````
L’attribut `for` du label pointe vers l’attribut `id` du champ texte.

The HTML `<label>` element is appropriate for form-related elements, but many form controls are implemented as a dynamic JavaScript widget, using `<div>`s or `<span>`s.

WAI-ARIA provides the `aria-labelledby` attribute for these cases.

The example below shows a radio button group implemented using an unordered list. The `<ul`> element sets the `aria-labelledby` attribute to `"rg1_label,"` the id of the `<h3>` which is the label for the radio group.
````
<h3 id="rg1_label">Lunch Options</h3>
<ul class="radiogroup" id="rg1"  role="radiogroup" aria-labelledby="rg1_label">
  <li id="r1"  tabindex="-1" role="radio" aria-checked="false">
    <img role="presentation" src="radio-unchecked.gif" /> Thai
  </li>
  <li id="r2"  tabindex="-1" role="radio"  aria-checked="false">
    <img role="presentation" src="radio-unchecked.gif" /> Subway
  </li>
</ul>
````

**Valider les champs avec ARIA**

ARIA permet d’enrichir les éléments d’un formulaire pour permettre à un utlisateur d’écran d’avoir les mêmes informations, le même feedback qu’un utlisateur n’ayant aucune déficience.

* Alerter l’utilisateur sur les champs non renseignés
Sur perte de focus ou sur validation, rajouter un `role="alert"` sur le tooltip ou message qui va notifier à l’utilisateur que quelquechose d’important requiert son attention

````
<div role="alert" class="info-required">Indiquez votre identifiant</div>
````

* Indiquer les champs obligatoires
Déclarer le champ obligatoire avec l’attribut `aria-required`

````
<input type="text" aria-required="true" value="" id="login" name="login">
````

Le lecteur d’écran va annoncer à l’utilisateur, le caractère obligatoire du champ : `« Identifiant : champ texte, vide, obligatoire ».`

* Indiquer un champ invalide
Sur perte de focus ou sur validation, ajouter dynamiquement l’attribut `aria-invalid` (vrai/faux)

````
<input type="text" aria-required="true" value="" id="login" name="login" aria-invalid="true">
````


* Describing with ARIA

ARIA provides the `aria-describedby` attribute to directly associate the description with a control.
The example below shows a `<button>` element that is described by a sentence in a separate `<div>` element. The aria-describedby attribute on the `<button>` references the id of the `<div>`.

````
<button aria-describedby="descriptionRevert">Revert</button>
<div id="descriptionRevert">Reverting will undo any changes that have been made since the last save.</div>
````

**`role="tooltip"`**
````
<label for="username">Your username</label>
<input type="text" id="username" aria-describedby="username-tip" required />
<div role="tooltip" id="username-tip">Your username is your email address</div>

input:focus + [role="tooltip"] {
	display: block;
	position: absolute;
	top: 100%;
}
````

**`role="alert"`**

````
<label for="number">Current value</label>
<input type="text" role="alert" aria-live="assertive" readonly value="0" id="number" />
<button type="button" title="add 10" aria-controls="number">Add</button>
<button type="button" title="subtract 10" aria-controls="number">Subtract</button>
````

## 2. Incrementer & decrementer 

````
$('[aria-controls="number"]').on('click', function() {
var button = $(this);
  $('#number').val(function(i, oldval) {
    return button.is('[title*="add"]') ? 
     parseInt(oldval, 10) + 10 : 
     parseInt(oldval, 10) - 10;
  });
});
````

The `aria-live="assertive"` attribute means that the value of the text field will be spoken whenever it changes.
The `aria-controls` attribute just confirms that each button controls the input. Different screen readers identify this accessible relationship in different ways, but it helps to know what you are affecting.


**Collapsible content sections**
````
<button aria-expanded="false" aria-controls="collapsible-0">What is this all about?</button>
<div id="collapsible-0" aria-hidden="true">
<p>Lorem ipsum</p>
</div>
````

A click function just toggles the aria-expanded and aria-hidden states.

**`role="tablist"`**
````
<ul role="tablist">
<li role="presentation"><a href="#section1" tabindex="0" role="tab" aria-controls="panel1" aria-selected="true">Section 1</a></li>
<li role="presentation"><a href="#section2" tabindex="-1" role="tab" aria-controls="panel2">Section 2</a></li>
<li role="presentation"><a href="#section3" tabindex="-1" role="tab" aria-controls="panel2">Section 3</a></li>
</ul>
<section id="section1" role="tabpanel">...</section>
<section id="section2" role="tabpanel" aria-hidden="true">...</section>
<section id="section3" role="tabpanel" aria-hidden="true">...</section>
````

**`role="alertdialog"`**
<dialog role="alertdialog" aria-describedby="d-message">
<div role="document">
<p id="d-message" >I really do not like you pressing that</p>
</div>
</dialog>
alertdialog role reserved for warning and error dialogs
document role reinstates predictable key bindings if the dialog is in a role="application"
Associates the message with the dialog element itself with aria-labelledby

**`role="toolbar"`**
<div role="toolbar" aria-label="sorting options" aria-controls="sortable">
  <button type="button" aria-pressed="true" data-sort="ascending">A to Z</button>
  <button type="button" aria-pressed="false" data-sort="descending">Z to A</button>
</div>
<ul id="sortable" tabindex="-1">
  <li>Fiddler crab</li>
  <li>Hermit crab</li>
</ul>
button with aria-pressed="true" will be appended with the word "pressed" when announced.

**`role="navigation"`**
a 	<nav role="navigation" aria-label="example with dropdowns" >
	<	ul class="with-dropdowns">
			<li><a href="#">Home</a></li>
			<li>
				<a href="/about" aria-haspopup="true">About</a>
				<ul aria-hidden="true" aria-label="submenu">
					<li><a href="/about/#who-we-are">Who we are</a></li>
					<li><a href="/about/#what-we-do">What we do</a></li>
					<li><a href="/about/#why">Why</a></li>
				</ul>
			</li>
			<li><a href="#">Blog</a></li>
			<li><a href="#">Contact</a></li>
	<		</ul>
<	</nav>
/* 9. Simple dropdowns
-----------------------------------------------------------------------------------------
*/

$('[role="navigation"] ul ul').prev('a')
  .attr('aria-haspopup', 'true')
  .append('<span aria-hidden="true"> &#x25be;</span>');

var showSubmenu = function(dropdown) {
  dropdown.attr('aria-hidden', 'false');
};

var hideSubmenu = function(dropdown) {
  dropdown.attr('aria-hidden', 'true');
};

$('.with-dropdowns > li > a').on('focus', function(e) {
  hideSubmenu($('[aria-label="submenu"]'));
});

$('[aria-haspopup]').on('click', function(e) {
  var submenu = $(this).next();
  showSubmenu(submenu);
  $(submenu).find('li:first-child a').focus();
  return false;
});

$('[aria-haspopup]').hover(function() {
  showSubmenu($(this).next());
  $(this).off('click');
});

$('[aria-haspopup]').parents('li').mouseleave(function() {
  hideSubmenu($(this).find('[aria-label="submenu"]'));
});
The aria-haspopup alerts you to the presence of a submenu.
The addition of an aria-label with a value of "submenu" just confirms it is a submenu you are entering as the first item is focused.
The submenu is an enhancement, so aria-haspopup is only added when javascript runs, allowing you to reveal the submenu on click. If javascript does not run, the about link takes you to the top of the about page.
