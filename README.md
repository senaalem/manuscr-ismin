# _Template_ rapport ISMIN

Ce _template_ est celui que j'utilise pour écrire mes rapports à l'EMSE.
Il utilise le langage Typst et fut grandement inspiré de [celui de Timothé Dupuch](https://github.com/thimotedupuch/Template_Rapport_ISMIN_Typst),
du [_template_ Bubble](https://github.com/hzkonor/bubble-template),
du [_template_ ilm](https://github.com/talal/ilm),
et enfin du [_template_ Diatypst](https://github.com/skriptum/Diatypst).
Beaucoup des règles de typographie ont été tirées du [_Butterick's Practical Typography_](https://practicaltypography.com/).
Je conseille également la lecture de l'ouvrage _Règles françaises de typographie mathématique_ par Alexandre André [ici](http://sgalex.free.fr/typo-maths_fr.pdf).

Le fichier `template_report_ISMIN.pdf` est un apercu en PDF du résultat de la compilation.
J'ai essayé de montrer toutes les possibilités qu'offrait Typst et la fonction manuscr-ismin, le contenu étant évidemment à ajuster à votre guise.

Pour en savoir plus sur les fonctions l'utilisation de Typst, vous pouvez utiliser [la documentation](https://typst.app/docs), elle est très complète.
Le Ctrl+Clic (ou Cmd+Clic) marche aussi sur les fonctions (dans l'éditeur de l'application web).

## Utilisation

Je conseille d'utiliser [l'application Web Typst](https://typst.app/), mais il est possible d'installer le compilateur en CLI sur sa machine.
Une très bonne configuration est Visual Studio Code avec l'extension Tinymist.
- Le fichier `template.typ` contient toutes les règles et fonctions d'affichage,
- le fichier `main.typ` lui contient le contenu que vous souhaitez inclure dans le rapport,
- le fichier `bibs.yaml` contient les références bibliographiques (au format Hayagriva, mais Typst prend aussi en charge le format BibLaTeX, changer le fichier à votre guise),
- le fichier `conf.yaml` sert à régler les différentes polices utilisées dans le document, la couleur principale (par défaut, le violet EMSE) ainsi que la couleur secondaire,
- le répértoire `assets` contient les ressources graphiques pour le thème du _template_,
- le répértoire `images` contient les images inclues dans le document.

### `conf.yaml`

#### Polices

Chaque police est définie par un sous-dictionnaire avec deux champs : `font` (le nom de la police) et `options` (une liste de fonctionnalités OpenType à activer).
Attention au fichier YAML, les noms des polices doivent être corrects.
Par exemple, si on veut un look LaTeX par défaut :

```yml
fonts:
  body:
    font: "New Computer Modern"
    options: []
  code:
    font: "New Computer Modern Mono"
    options: []
  math:
    font: "New Computer Modern Math"
    options: ["ss03"]
  mono:
    font: "New Computer Modern Mono"
    options: []
  sans:
    font: "New Computer Modern Sans"
    options: []
```

#### Couleurs

Deux couleurs sont définies par des chaînes de caractères au format hexadécimal : `main-colour` pour la couleur principale du document, et `other-colour` pour la couleur secondaire (utilisée par exemple pour le triangle décoratif de la page de garde).
Par exemple :
```yml
main-colour: "#FF6347"
other-colour: "#00E81F"
```

### `manuscr-ismin`

Ci-suit une description des paramètres de la fonction `manuscr-ismin` :
- `title` : le titre du document (obligatoire),
- `subtitle` : le sous-titre,
- `school` : informations sur l'école, sous forme de dictionnaire :
  - `name` : le nom de l'école,
  - `subname` : le nom du campus ou de la subdivision ;
- `course` : informations sur l'enseignement, sous forme de dictionnaire :
  - `ue` : le nom de l'unité pédagogique (à l'ISMIN, UE)
  - `ecue` : le nom de l'élement constitutif d'une unité pédagogique (à l'ISMIN, ECUE)
  - `name` : le nom de l'UE,
  - `subname` : le nom de l'ECUE ;
- `authors` : liste des auteurs, chacun sous forme de dictionnaire ; pour n'utiliser qu'un auteur, ne pas oublier de laisser quand même une virgule à la fin :
  - `name` : le nom de l'auteur,
  - `affiliation` : la filière de l'auteur,
  - `email` : son adresse mail ;
- `mentor1`, `mentor2` : encadrants, chacun sous forme de dictionnaire :
  - `role` : le rôle (ex. `"Encadrant"`, `"Co-encadrant"`),
  - `name` : le nom,
  - `email` : l'adresse mail ;
- `date` : la date,
- `academic-year` : l'année scolaire,
- `logo` : le logo que vous voulez utiliser ; par défaut, c'est celui de l'EMSE,
- `header` : le contenu de l'en-tête (contenu Typst libre),
- `show-imt-triangle` : booléen pour afficher ou non le triangle décoratif IMT sur la page de garde (par défaut `true`).

### Les fonctions

- `violet-emse` : la couleur violette de l'EMSE,
- `gray-emse` : la couleur grise de l'EMSE,
- `blue-imt` : la couleur bleue de l'IMT,

- `lining` : pour avoir des nombres en style classique localement ; les chiffres elzéviriens s'intègrent bien au texte minuscule, mais mal à celui en majuscule.
	Par exemple, `#lining[STM32L436RG]` est bien plus élégant que `STM32L476RG`,
- `arcosh` : la fonction arc cosinus hyperbolique pour le mode mathématique (j'en avais besoin),
- `mono` : à utiliser pour retourner rapidement du texte en monospace sans la mise en forme de `raw` ;
	À utiliser pour par exemple indiquer des noms de fichier : `#mono[toto_tigre.png]`,
- `sans` : à utiliser pour retourner rapidement du texte en sans-serif (par exemple `#sans[adder]`),

- `body-font` : la police pour le corps du texte,
- `code-font` : la police utilisée par la fonction `raw`,
- `math-font` : la police utilisée pour les équations mathématiques,
- `mono-font` : la police utilisée pour la fonction `mono`,
- `sans-font` : la police utilisée pour la fonction `sans`,

- `primary-colour` : la couleur par défaut du document,
- `other-colour` : la couleur secondaire du document,
- `block-colour`, `body-colour`, `header-colour`, `fill-colour` : couleurs "éclaircies" dérivées de `primary-colour`.