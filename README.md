# _Template_ rapport ISMIN

Ce _template_ est celui que j'utilise pour écrire mes rapports à l'EMSE.
Il utilise le langage Typst et fut grandement inspiré de [celui de Timothé Dupuch](https://github.com/thimotedupuch/Template_Rapport_ISMIN_Typst),
du [_template_ Bubble](https://github.com/hzkonor/bubble-template),
du [_template_ ilm](https://github.com/talal/ilm),
et enfin du [_template_ Diatypst](https://github.com/skriptum/Diatypst).
Beaucoup des règles de typographie ont été tirées du [_Butterick's Practical Typography_](https://practicaltypography.com/).
Je conseille également la lecture de l'ouvrage _Règles françaises de typographie mathématique_ par Alexandre André [ici](http://sgalex.free.fr/typo-maths_fr.pdf).

Le fichier `template_report_ISMIN.pdf` est un aperçu en PDF du résultat de la compilation.
J'ai essayé de montrer toutes les possibilités qu'offrait Typst et la fonction `manuscr-ismin`, le contenu étant évidemment à ajuster à votre guise.

Pour en savoir plus sur l'utilisation de Typst, vous pouvez consulter [la documentation](https://typst.app/docs), elle est très complète.
Le Ctrl+Clic (ou Cmd+Clic) marche aussi sur les fonctions dans l'éditeur de l'application web.

## Utilisation

Je conseille d'utiliser [l'application Web Typst](https://typst.app/), mais il est possible d'installer le compilateur en CLI sur sa machine.
Une très bonne configuration est Visual Studio Code avec l'extension Tinymist.
- Le fichier `template.typ` contient toutes les règles et fonctions d'affichage,
- le fichier `main.typ` contient le contenu que vous souhaitez inclure dans le rapport,
- le fichier `bibs.yaml` contient les références bibliographiques (au format Hayagriva, mais Typst prend aussi en charge le format BibLaTeX, changez le fichier à votre guise),
- le répertoire `assets` contient les ressources graphiques pour le thème du _template_,
- le répertoire `images` contient les images incluses dans le document.

### `manuscr-ismin`

Toute la configuration se fait directement via les paramètres de la fonction `manuscr-ismin` dans `main.typ`.
Ci-suit une description de ses paramètres :

- `title` : le titre du document (obligatoire),
- `subtitle` : le sous-titre,
- `school` : informations sur l'école, sous forme de dictionnaire :
  - `name` : le nom de l'école,
  - `subname` : le nom du campus ou de la subdivision ;
- `course` : informations sur l'enseignement, sous forme de dictionnaire :
  - `ue` : le label affiché pour l'unité pédagogique (ex. `"UE"`),
  - `ecue` : le label affiché pour l'élément constitutif (ex. `"ECUE"`),
  - `name` : le nom de l'unité pédagogique,
  - `subname` : le nom de l'élément constitutif ;
- `authors` : liste des auteurs, chacun sous forme de dictionnaire ; pour n'utiliser qu'un seul auteur, ne pas oublier de laisser une virgule à la fin :
  - `name` : le nom de l'auteur,
  - `affiliation` : la filière de l'auteur,
  - `email` : son adresse mail ;
- `mentor1`, `mentor2` : encadrants, chacun sous forme de dictionnaire :
  - `role` : le rôle (ex. `"Encadrant"`, `"Co-encadrant"`),
  - `name` : le nom,
  - `email` : l'adresse mail ;
- `date` : la date,
- `academic-year` : l'année scolaire,
- `logo` : le logo à utiliser ; par défaut, celui de l'EMSE,
- `header` : le contenu de l'en-tête (contenu Typst libre),
- `show-imt-triangle` : booléen pour afficher ou non le triangle décoratif IMT sur la page de garde (par défaut `true`),
- `latex-look` : booléen pour utiliser les polices _Computer Modern_ à la place des polices par défaut, pour un rendu proche de LaTeX (par défaut `false`),
- `main-colour` : la couleur principale du document ; par défaut, le violet EMSE (`violet-emse`),
- `other-colour` : la couleur secondaire du document, utilisée notamment pour le triangle décoratif ; par défaut, le bleu IMT (`blue-imt`).

### Les fonctions et couleurs

- `violet-emse` : la couleur violette de l'EMSE,
- `gray-emse` : la couleur grise de l'EMSE,
- `blue-imt` : la couleur bleue de l'IMT,

- `lining` : pour avoir des chiffres en style classique (_lining_) localement ; les chiffres elzéviriens s'intègrent bien au texte minuscule, mais mal à celui en majuscules.
	Par exemple, `#lining[STM32L436RG]` est bien plus élégant que `STM32L476RG`,
- `arcosh` : la fonction arc cosinus hyperbolique pour le mode mathématique.