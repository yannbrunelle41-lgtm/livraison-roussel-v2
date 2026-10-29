**PARTIE A :**



Questions posées à Codex via VSCode :

1 - Quelle est la différence entre les unités CSS em et rem ? Donne un exemple.&#x20;

\-->Les unités em et rem calculent une taille à partir d’une taille de police de référence.

\- em dépend de la taille de police de l’élément. Pour définir son font-size, il dépend de celle de son parent.

\- rem dépend toujours de la taille de police de l’élément racine : \<html>.

Exemple générique : si \<html> a une taille de police de 16 px et qu’un paragraphe a une taille de police de 20 px :

p {

&#x20; margin-left: 2em;

&#x20; margin-right: 2rem;

}

La marge gauche vaut 40 px (2 × 20), et la marge droite vaut 32 px (2 × 16).



Si la taille de police de \<html> change, quelle unité sera directement concernée ?

Ma réponse : la taille rem

\-->Oui ! Les tailles exprimées en rem dépendent de la taille de police de \<html>.



Par exemple, si celle-ci passe de 16 px à 20 px, une marge de 2rem passe de 32 px à 40 px.



2 - Comment utiliser la propriété CSS text-glow pour faire briller un titre ?

\-->text-glow n’est pas une propriété CSS standard. Pour créer un effet de lueur, on utilise text-shadow, qui ajoute une ombre au texte.



Elle permet de définir :

\- le décalage horizontal de l’ombre ;

\- le décalage vertical ;

\- le rayon de flou ;

\- sa couleur.

Pour comprendre l’effet lumineux : une ombre placée exactement derrière les lettres, avec du flou et une couleur claire, ressemble à un halo. Le contraste avec le fond rend ce halo plus visible. Voir la documentation MDN de text-shadow.

À ton avis, quels décalages permettraient de garder ce halo centré derrière les lettres ?

Ma réponse : text-shadow: 1px 1px 2px pink;

Dans text-shadow: 1px 1px 2px pink; :

\- le premier 1px décale l’ombre de 1 pixel vers la droite ;

\- le deuxième 1px la décale de 1 pixel vers le bas ;

\- 2px définit le rayon de flou ;

\- pink donne une couleur rose à l’ombre.

Tu obtiens donc une ombre rose légèrement décalée.



Quelles valeurs changerais-tu pour la centrer derrière les lettres ?

Ma réponse : les 2 premières valeurs.

\-->Oui, exactement ! Les deux premières valeurs contrôlent les décalages horizontal et vertical.



En les mettant toutes les deux à zéro, l’ombre reste centrée derrière les lettres. Le flou permet alors de créer le halo.



3 - Pourquoi faut-il utiliser la balise <*center*> pour centrer un titre en HTML5 ?

\-->La question contient une erreur : la balise <*center*> est obsolète et ne doit plus être utilisée en HTML5.



HTML sert à structurer le contenu : un titre est identifié par une balise comme \<h1> ou \<h2>. CSS s’occupe de sa présentation, notamment du centrage.



La propriété CSS text-align, avec la valeur center, permet de centrer le texte à l’intérieur de son élément.



Vois-tu la différence entre le rôle de HTML et celui de CSS dans cet exemple ?

Ma réponse : oui html sert à créer le code de base et à donner du sens à son code via les différentes balises. Le css va permettre de créer du style sur les différents éléments html

\-->Oui, c’est bien ça ! Pour être précis, HTML structure le contenu et lui donne du sens : un titre, un paragraphe, une liste…



CSS définit sa présentation : couleurs, tailles, espacements et disposition.



Un titre reste donc un titre grâce à sa balise HTML, qu’il soit centré ou aligné à gauche par CSS.



4 - Question 1 mais en anglais : What is the difference between the CSS units em and rem? Give an example.

\-->Both em and rem are relative CSS units. For font sizes:

\- em is relative to the parent element’s font size.

\- rem is relative to the root element’s (html) font size.

For example, imagine the root font size is 16px, and a paragraph’s parent has a font size of 20px:

p { font-size: 1.5em; }

span { font-size: 1.5rem; }

The paragraph’s font size becomes 30px (1.5 × 20), while the span’s becomes 24px (1.5 × 16).



One detail: for properties such as padding, em uses the element’s own font size.



If the parent’s font size changes, which font-size unit stays tied to the root: em or rem?

Ma réponse : rem

\-->Exactly! rem stays relative to the root element’s (html) font size, so changing the parent’s font size won’t affect it.





Les 3 quesitons soumises à Claude :&#x20;

1 - Quelle est la différence entre les unités CSS em et rem ? Donne un exemple.



2 - Comment utiliser la propriété CSS text-glow pour faire briller un titre ?



3 - Pourquoi faut-il utiliser la balise <*center*> pour centrer un titre en HTML5 ?



Réponses de Claude :&#x20;

1\. Différence entre em et rem



em est relatif à la taille de police de l’élément lui-même (ou, pour la propriété font-size, à celle de son parent). Il se cumule donc quand les éléments sont imbriqués.

rem (“root em”) est relatif à la taille de police de l’élément racine \<html>. Il reste constant quel que soit l’endroit où on l’utilise.



Exemple :



html

\<style>

&#x20; html { font-size: 16px; }



&#x20; .parent { font-size: 1.5em; }   /\* 1.5 × 16 = 24px \*/

&#x20; .enfant-em { font-size: 1.5em; }  /\* 1.5 × 24 = 36px (cumulé) \*/

&#x20; .enfant-rem { font-size: 1.5rem; } /\* 1.5 × 16 = 24px (toujours) \*/

\</style>



\<div class="parent">

&#x20; Parent (24px)

&#x20; \<p class="enfant-em">Enfant en em (36px)\</p>

&#x20; \<p class="enfant-rem">Enfant en rem (24px)\</p>

\</div>



En pratique : rem pour les tailles de police et espacements globaux (prévisible), em pour les composants dont les proportions doivent suivre leur propre taille de texte (par exemple le padding d’un bouton).



2\. La propriété text-glow



Cette propriété n’existe pas en CSS. Pour obtenir un effet lumineux, on utilise text-shadow avec un flou et une couleur vive, souvent en superposant plusieurs ombres :



css

h1 {

&#x20; color: #fff;

&#x20; text-shadow:

&#x20;   0 0 5px #fff,

&#x20;   0 0 10px #0ff,

&#x20;   0 0 20px #0ff,

&#x20;   0 0 40px #0ff;

}



Les trois premières valeurs sont le décalage horizontal, vertical et le rayon de flou ; plus le flou est grand et plus on superpose d’ombres, plus le halo est intense.



3\. La balise <*center*>



Il ne faut justement pas l’utiliser : <*center*> est obsolète et a été supprimée de la spécification HTML5, car elle relève de la présentation et non de la structure. Même si les navigateurs la supportent encore, elle est déconseillée.



Pour centrer un titre, on utilise du CSS :



css

h1 {

&#x20; text-align: center;

}



Et pour centrer un bloc entier, avec Flexbox par exemple :



css

.conteneur {

&#x20; display: flex;

&#x20; justify-content: center;

}



Les 3 quesitons soumises à Copilot :&#x20;

1 - Quelle est la différence entre les unités CSS em et rem ? Donne un exemple.



2 - Comment utiliser la propriété CSS text-glow pour faire briller un titre ?



3 - Pourquoi faut-il utiliser la balise <*center*> pour centrer un titre en HTML5 ?



Réponses de Copilot :&#x20;

1 - em et rem sont des unités relatives, mais elles ne se réfèrent pas à la même taille :



em dépend généralement de la taille de police de l’élément parent pour font-size. Pour d’autres propriétés, comme padding, il dépend de la taille de police calculée de l’élément.

rem dépend de la taille de police de l’élément racine, \<html>.

html { font-size: 16px; }

.parent { font-size: 20px; }



.enfant-em { font-size: 1.5em; }   /\* 30px \*/

.enfant-rem { font-size: 1.5rem; } /\* 24px \*/



2 - text-glow n’est pas une propriété CSS standard. Pour créer un halo autour d’un titre, utilisez text-shadow avec des décalages nuls, du flou et une couleur lumineuse :

h1 {

&#x20; color: white;

&#x20; text-shadow: 0 0 8px cyan, 0 0 20px cyan;

}



3 - l ne faut pas utiliser <*center*> : cette balise est obsolète et concerne la présentation plutôt que la structure du contenu. Gardez le titre dans une balise sémantique comme \<h1>, puis centrez-le avec CSS :

h1 {

&#x20; text-align: center;

}





**PARTIE B :**



Analyse du fichier livraison.html relever les notions inconnues :



HTML :&#x20;

-\<table>

-\<caption>Tarifs de livraison selon la zone\</caption>

-\<thead>

-\<form>

-\<input id="code-postal" name="cp" type="text" inputmode="numeric"

&#x20;                pattern="[0-9]{5}" maxlength="5" autocomplete="postal-code" required>



CSS :&#x20;

-aspect-ratio

-counter-reset: etape;

-border-collapse: collapse;



\<table>\</table> : \<table> balise html qui est utilisé pour créer un tableau et organiser des données en lignes et en colonnes.&#x20;

\<caption>\</caption> : balise html qui donne un titre à un tableau. Ce titre aide à comprendre ce que contient le tableau. Elle se place à l'intérieur d'une balise \<table>.

\<thead> : balise qui regroupe les lignes d'en-tête d'un tableau qui donne un "titre" et sert à comprendre les données de la colonne.

\<form> : balise qui délimite un formulaire html pour regrouper les champs dans lesquels l'utilisateur saisis ou choisis des informations.

\<input> balise qui sert à créer un champs ou l'utilisateur peut saisir ou choisir une information.

-aspect-ratio : définti le rapport entre largeur et hauteur d'un élément.

-counter-reset: etape; : déclaration css qui initialise un compteur nommé etape à 0.

-border-collapse: collapse; : fusionne les bordures de cellules voisines d'un tableau. Leur bordures fusionnent en une seule. Elle déterminent comment les bordures existantes se rejoignent.







.evitement {

&#x20; position: absolute;

&#x20; left: var(--espace);

&#x20; top: 0;

&#x20; padding: 0.5rem 1rem;

&#x20; background: var(--vert);

&#x20; color: #a40b0b;

&#x20; transform: translateY(-120%);

}



en changeant color: #ffffff par #a40b0b de l'élement évitement qui est un lien dans l'html.



.section {

&#x20; padding-block: 2.5rem 0;

}



en changeant le padding-block de 2.5rem à 5rem, je vais dounler l'espace au dessus du contenu de chaque section



transform: translateY(-4px);



en changeant -4px à -15px, les crates monteront de 15px au lieu de 4px



**PARTIE C :**



Noter chaque prompt dans le journal : outil, prompt, réponse gardée ou rejetée, vérification :



\> tu es en mode prof. Je veux que tu m'expliques cette ligne de commande : \<table class="tarifs">. Cite moi tes sources à chaque fois pour ce chat



\`\<table class="tarifs">\` est une **\*\*balise HTML ouvrante\*\***, plutôt qu’une ligne de commande.



\- **\*\*\`\<table>\`\*\*** commence un tableau HTML, qui sert à organiser des données en lignes et en colonnes. Source : [MDN — \`\<table>\`]\(https\://developer.mozilla.org/fr/docs/Web/HTML/Reference/Elements/table).

\- **\*\*\`class="tarifs"\`\*\*** attribue à ce tableau une classe appelée \`tarifs\`. Cette classe permet notamment au CSS de cibler cet élément pour définir son apparence. Le mot \`tarifs\` est un nom choisi par la personne qui écrit le code : il ne produit aucun style à lui seul. Source : [MDN — \`class\`]\(https\://developer.mozilla.org/fr/docs/Web/HTML/Reference/Global_attributes/class).



Je citerai mes sources à chaque réponse dans ce chat.



À ton avis, quelle partie crée le tableau : \`table\` ou \`tarifs\` ?



\> table



Oui, c’est **\*\*\`table\`\*\*** qui indique au navigateur qu’il s’agit d’un tableau. **\*\*\`tarifs\`\*\*** est simplement le nom de sa classe.



Source : [MDN — \`\<table>\`]\(https\://developer.mozilla.org/fr/docs/Web/HTML/Reference/Elements/table).



\> explique moi \<caption>



La balise **\*\*\`\<caption>\`\*\*** donne un **\*\*titre à un tableau HTML\*\***. Ce titre aide à comprendre ce que contient le tableau.



Elle se place à l’intérieur de \`\<table>\`, juste après sa balise ouvrante. Le texte du titre se trouve entre \`\<caption>\` et \`\</caption>\`. Par défaut, le navigateur l’affiche au-dessus du tableau.



Source : [MDN — \`\<caption>\`]\(https\://developer.mozilla.org/fr/docs/Web/HTML/Reference/Elements/caption).



Quelle différence vois-tu entre le rôle de \`\<table>\` et celui de \`\<caption>\` ?



\> table créé un élément de type tableau et caption donne un titre qui a du sens à ce trableau



Oui, tu as bien compris : **\*\*\`\<table>\` crée le tableau\*\***, et **\*\*\`\<caption>\` lui donne un titre qui décrit son contenu\*\***. Ce titre aide aussi les personnes utilisant un lecteur d’écran à comprendre le sujet du tableau.



Source : [MDN — \`\<caption>\`]\(https\://developer.mozilla.org/fr/docs/Web/HTML/Reference/Elements/caption).



\> \<thead>



**\*\*\`\<thead>\` regroupe les lignes d’en-tête d’un tableau\*\*** : celles qui indiquent ce que représentent les colonnes, par exemple « Produit » et « Prix ».



Contrairement à \`\<caption>\`, qui donne un titre à tout le tableau, \`\<thead>\` contient les lignes qui servent à comprendre les données.



Le nom vient de *\*table head\**, c’est-à-dire « tête du tableau ».



Source : [MDN — \`\<thead>\`]\(https\://developer.mozilla.org/fr/docs/Web/HTML/Reference/Elements/thead).



Dans un tableau de tarifs, où placerais-tu les intitulés « Destination » et « Prix » ?



\> \<form>



**\*\*\`\<form>\` délimite un formulaire HTML\*\*** : une zone qui regroupe des champs dans lesquels l’utilisateur peut saisir ou choisir des informations.



Par exemple, un formulaire peut contenir un champ pour le nom, un champ pour l’adresse et un bouton d’envoi. Ces éléments se placent entre \`\<form>\` et \`\</form>\`.



La balise \`\<form>\` seule ne crée pas les champs : elle les regroupe et permet d’organiser l’envoi des données.



Source : [MDN — \`\<form>\`]\(https\://developer.mozilla.org/fr/docs/Web/HTML/Reference/Elements/form).



Est-ce que \`\<form>\` crée elle-même un champ pour saisir un nom ?



\> non elle délimite un formulaire



Exactement : **\*\*\`\<form>\` délimite le formulaire\*\*** et regroupe ses éléments. Ce sont notamment les balises \`\<input>\` à l’intérieur qui créent les champs de saisie.



Source : [MDN — \`\<form>\`]\(https\://developer.mozilla.org/fr/docs/Web/HTML/Reference/Elements/form).



\> \<input>



**\*\*\`\<input>\` crée un champ ou un contrôle interactif\*\*** dans lequel l’utilisateur peut saisir ou choisir une information.



Son attribut **\*\*\`type\`\*\*** détermine sa forme : un champ de texte, une case à cocher ou un bouton, par exemple. Sans cet attribut, c’est un champ de texte.



C’est une **\*\*balise vide\*\*** : elle n’a pas de balise fermante \`\</input>\`.



Source : [MDN — \`\<input>\`]\(https\://developer.mozilla.org/fr/docs/Web/HTML/Reference/Elements/input).



Quel attribut permet de choisir entre un champ de texte et une case à cocher ?



\> type



Exactement ! L’attribut **\*\*\`type\`\*\*** détermine le type de contrôle créé par \`\<input>\` : par exemple, \`text\` pour un champ de texte ou \`checkbox\` pour une case à cocher.



Source : [MDN — \`\<input>\`]\(https\://developer.mozilla.org/fr/docs/Web/HTML/Reference/Elements/input).



\> explique moi cette propriété css :

\> -aspect-ratio



Tu fais probablement référence à **\*\*\`aspect-ratio\`\*\***, sans tiret au début. **\*\*\`-aspect-ratio\` n’est pas une propriété CSS standard.\*\***



\`aspect-ratio\` définit le **\*\*rapport entre la largeur et la hauteur\*\*** d’un élément.



Par exemple, la valeur \`16 / 9\` signifie que pour une largeur de **\*\*160 pixels\*\***, la hauteur correspondante est de **\*\*90 pixels\*\***. Le navigateur utilise ce rapport pour calculer une dimension automatique.



Source : [MDN — \`aspect-ratio\`]\(https\://developer.mozilla.org/fr/docs/Web/CSS/Reference/Properties/aspect-ratio).



À ton avis, quelle forme obtient-on avec un rapport de \`1 / 1\` ?



\> un carré



Exactement : **\*\*\`1 / 1\` correspond à une largeur égale à la hauteur\*\***, donc à un carré.



Source : [MDN — \`aspect-ratio\`]\(https\://developer.mozilla.org/fr/docs/Web/CSS/Reference/Properties/aspect-ratio).



\> quand tu dis 16/9 signifie que pour 160 px, la hauteur sera de 90px. c'est toujours comme ça donc 4/3 serait pour une largeur de 40px j'aurai une hauteur de 30px. x/y

\> x = 10px et y=10px ?



Oui, **\*\*pour une largeur de 40 px, un rapport de \`4 / 3\` correspond à une hauteur de 30 px\*\***.



Mais **\*\*les nombres du rapport ne représentent pas des pixels\*\*** : ils indiquent des proportions. Avec \`4 / 3\`, tu peux avoir :



\- 4 px de large et 3 px de haut ;

\- 40 px de large et 30 px de haut ;

\- 400 px de large et 300 px de haut.



Dans ces exemples, on multiplie les deux nombres par le même facteur : 1, 10 ou 100. **\*\*Le facteur n’est donc pas toujours 10.\*\***



Avec \`aspect-ratio\`, ce rapport permet au navigateur de calculer une dimension automatique. Si la largeur et la hauteur sont toutes les deux fixées, il ne les impose pas.



Source : [MDN — \`aspect-ratio\`]\(https\://developer.mozilla.org/fr/docs/Web/CSS/Reference/Properties/aspect-ratio).



Avec un rapport de \`4 / 3\` et une largeur de **\*\*80 px\*\***, quelle serait la hauteur ?



\> -counter-reset: etape;



Tu fais probablement référence à **\*\*\`counter-reset: etape;\`\*\***, sans tiret au début.



Cette déclaration CSS **\*\*initialise un compteur nommé \`etape\` à 0\*\***. Un compteur sert à numéroter des éléments automatiquement, par exemple les étapes d’une liste.



\- **\*\*\`counter-reset\`\*\*** : initialise le compteur.

\- **\*\*\`etape\`\*\*** : le nom choisi pour ce compteur.



Cette déclaration seule n’affiche aucun numéro et n’augmente pas le compteur.



Source : [MDN — \`counter-reset\`]\(https\://developer.mozilla.org/fr/docs/Web/CSS/Reference/Properties/counter-reset).



Ici, \`etape\` est-il un nom choisi ou un mot imposé par CSS ?



\> border-collapse: collapse;



**\*\*\`border-collapse: collapse;\` fusionne les bordures des cellules voisines d’un tableau.\*\***



Chaque cellule peut avoir sa propre bordure. Avec \`collapse\`, deux cellules qui se touchent partagent **\*\*une seule bordure\*\***, ce qui donne une grille continue.



\- **\*\*\`border-collapse\`\*\*** : définit si les bordures sont séparées ou fusionnées.

\- **\*\*\`collapse\`\*\*** : choisit de les fusionner.



Cette propriété ne crée pas de bordures : elle détermine comment les bordures existantes se rejoignent.



Source : [MDN — \`border-collapse\`]\(https\://developer.mozilla.org/fr/docs/Web/CSS/Reference/Properties/border-collapse).





**PARTIE D :**



Rédiger cinq règles personnelles d’usage de l’IA :





1. **Utiliser l’IA comme un assistant, pas comme un pilote.** Je dois être capable de coder avant de demander à l'IA de le faire pour moi

2. **Formuler des demandes précises.** Je dois expliquer mon problème, donner le contexte et préciser ce que j’attends de l’IA. Faire en sorte que l'IA n'invinte pas.

3. **Vérifier les réponses de l’IA.** Je dois consulter des sources fiables, comme MDN pour le HTML et le CSS, car l’IA peut se tromper.

4. **Ne pas copier du code sans le comprendre.** Je dois être capable d’expliquer le rôle des balises, propriétés et fonctions utilisées dans mon projet. Ne pas hésiter de commenter le code pour retenir les nouvelles notions.

5. **Protéger les données personnelles et confidentielles.** Je ne dois jamais transmettre à l’IA des mots de passe, des clés API ou des informations sensibles concernant un client.

**PARTIE E :**

