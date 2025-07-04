# MathCAT #

* Auteur : Neil Soiffer
* Compatibilité NVDA : 2018.1 ou version ultérieure (non testée dans les
  versions antérieures)
* Télécharger [version stable][1]

MathCAT est conçu pour finalement remplacer MathPlayer, car ce dernier n'est
plus pris en charge. MathCAT génère la parole et le braille à partir de
MathML. La parole produite par MathCAT pour les mathématiques est améliorée
avec intonation afin qu'elle semble plus naturelle. Vous pouvez naviguer
dans la parole de trois façons en utilisant les mêmes commandes que dans
MathPlayer. De plus, le nœud de navigation est indiqué sur l'afficheur
braille. les codes Nemeth et UEB technique sont pris en charge.

MathCAT a un certain nombre d'options de configuration qui contrôlent la
parole, la navigation et le braille. Beaucoup d'entre eux peuvent être
définis dans la boîte de dialogue des paramètres MathCAT (qui se trouve dans
le menu Préférences de NVDA). Pour plus d'informations sur ces paramètres,
consultez la [documentation
MathCAT](https://nsoiffer.github.io/mathcat/users.html). La documentation
comprend un lien vers [une table répertoriant toutes les commandes de
navigation dans
MathCAT](https://nsoiffer.github.io/MathCAT/nav-commands.html).

Remarque : MathCAT est une bibliothèque générale pour générer la parole et
le braille à partir de MathML. Il est utilisé par d'autres dans des projets
en plus de NVDA. Pour plus d'informations sur le projet MathCAT en général,
consultez la principale [page de documentation de
MathCAT](https://nsoiffer.github.io/MathCAT).


Qui devrait utiliser MathCAT :

* Ceux qui ont besoin de Nemeth Braille de haute qualité (Nemeth de
  MathPlayer est basé sur la génération Nemeth de liblouis qui a un certain
  nombre de bogues importants qui sont techniquement difficiles à corriger).
* Those who need UEB technical braille, CMU (Spanish/Portuguese), German
  LaTeX, ASCIIMath, or Vietnamese braille
* Ceux qui veulent essayer les dernières technologies et sont prêts à aider
  en signalant des bogues
* Ceux qui utilisent Eloquence comme voix

Qui ne devrait pas utiliser MathCAT :

* Toute personne utilisant MathPlayer avec une langue pas encore prise en
  charge par Mathcat (des traductions existent pour le chinois
  (traditionnel), l'espagnol, l'indonésien et le vietnamien; d'autres
  traductions doivent arriver dans un futur proche) et qui ne se sent pas à
  l'aise avec la parole dans les langues prises en charge.
* Quiconque préfère Access8Math à MathPlayer (pour la parole ou d'autres
  fonctionnalités)

Les règles de la parole de MathCAT ne sont pas encore aussi étendues que
celles de MathPlayer - cela peut être une autre raison de continuer avec
MathPlayer. MathCAT est utilisé comme banque de test pour MathML 4, ce qui
permet aux auteurs d'exprimer leur intention afin que les notations ambiguës
soient verbalisées correctement sans avoir à les deviner. J'ai attendu avant
d'ajouter de nombreuses règles, car l'architecture de MathCAT se concentre
sur l'utilisation et la déduction de l'intention de l'auteur, et ce n'est
pas encore complètement établi.

## Mise à jour du Journal de MathCAT

### Version 0.6.3

* Tous les fichiers de règles de langue et de braille sont zippés par
  répertoire et décompressés à la demande.

	* Cela économise actuellement environ 5 Mo lorsque les règles.zip sont
	  décompressées et économisera encore plus lorsque plus de langues et de
	  codes braille seront ajoutés.
	* Ceci est en préparation pour l'intégration de Mathcat dans NVDA 2024.3

* Ajout d'une nouvelle préférence `Decimalseparator`.

	* La valeur par défaut est `Auto`, les autres valeurs étant ".", "," et
	  "Custom". Les trois premières valeurs définissent `Decimalseparators` et
	  `Blockseparators`.
	* `Auto` définit ces préférences en fonction de la valeur de pref
	  `Language`. Pour certaines langue comme l'espagnol, `,`,est utilisée dans
	  certains pays et `.` est utilisée dans d'autres. Dans ce cas, il est
	  préférable de définir la langue pour inclure également le code du pays
	  (par exemple, `es-es` ou `es-mx`) pour s'assurer que la bonne valeur est
	  utilisée.

* Ajout du suédois aux langues prises en charge.
* Added more Unicode chars to include both all Unicode chars marked as "Sm"
  and those with a mathclass (except Alphabetic and Glyph classes) in the
  Unicode standard.
* Après avoir changé le fonctionnement des préfes dans une version
  précédente, j'ai oublié de modifier `Mathrate` et `Pausefactor` afin
  qu'ils soient des nombres, pas des chaînes.
* Fixed bug in the braille Rules (missed change from earlier) where a third
  argument should have been given to say to look in the _Braille_
  `definitions.yaml` files and not the speech ones when looking up the value
  of a definition.
* Nettoyage de l'utilisation de `definitions.yaml`.
* Correction de bugs dans le nettoyage du MathML pour les séparateurs
  décimaux ",".
* Found a bug in braille highlighting when nothing is highlighted (maybe
  never happens which is why I didn't see it in practice?)
* Correction du mode "Décrire" pour qu'il fonctionne -- il est encore très
  minimaliste et probablement pas encore utile
* Correction de la version minimale prise en charge

### Version 0.5.6
* Ajout de Copier en tant que... au dialogue MathCAT (dans le volet
  "Navigation").
* Correction d'un bug où la langue retournait à l'anglais lors de la
  modification des styles de parole.
* Correction d'un bug relatif à la navigation et au braille
* Correction de problèmes d'espacement Asciimath.
* Reconnaissance améliorée de la chimie
* Mise à jour de Mathcat pour les nouvelles spécifications de chimie Bana
  Nemeth (toujours seulement pour les lignes simples, cas spéciaux de
  changement de style ou de police non pris en charge)
* Correction d'un plantage lorsque des chiffres non ASCII (par exemple, des
  chiffres en gras) sont utilisés dans les nombres
* Pas d'utilisation d'indicateurs italiques dans les codes braille lorsque
  les caractères italiques alphanumériques mathématiques sont utilisés
* Quelques autres corrections de bogues plus petites qui n'ont pas été
  rapportées par les utilisateurs

### Version 0.5.0
* Ajout du code braille LaTeX allemand. Contrairement à d'autres codes
  braille, celui-ci génère des caractères ASCII et utilise la table de
  sortie braille actuelle pour traduire les caractères en braille.
* Ajout du code braille ASCIIMath (expérimental). Comme le code braille
  LaTeX, celui-ci génère des caractères ASCII et utilise la table de sortie
  braille actuelle pour traduire les caractères en braille.
* Ajout de la préférence "CopyAs" qui prend en charge la copie au format
  MathML, LaTeX ou ASCIIMath en utilisant contrôle+C lorsque le focus sur du
  MathML (comme auparavant). Le nœud ayant le focus est copié. Remarque :
  cette option n'est listée que dans le fichier prefs.yaml et n'est pas
  (encore) exposé dans la boîte de dialogue Préférences MathCAT.

### Version 0.4.2
* Correctif pour le changement de langue lorsque la voix change et que la
  langue MathCAT est "Auto"
* Ajout de plus de contrôles de $Impairments afin d'améliorer la lecture
  lorsqu'elle n'est pas définie pour les personnes aveugles
* Nemeth : correction de "~" lorsqu'il ne fait pas partie d'un mrow
* UEB : ajouts de caractères, correction de l'espacement de "~" avec un
  préfixe, correction de xor,
* Nettoyage MathML pour les voyelles accentuées (principalement pour le
  vietnamien)
* Réécriture majeure du code de lecture/mise à jour des préférences avec une
  grande accélération -- ajout de la préférence `CheckRuleFiles` pour
  contrôler quels fichiers sont vérifiés pour les mises à jour
* Ajout de deux nouveaux appels d'interface -- permet de définir
  l'emplacement de navigation à partir du curseur braille (ne fait pas
  encore partie de l'extension MathCAT)

### Version 0.3.11
* Mise à niveau vers python 3.11 et vérification du fonctionnement avec NVDA
  2024.1
* Correction de bugs dans le braille vietnamien et également dans la parole,
  principalement pour la chimie.
* Correction du dysfonctionnement du braille lorsque le code braille et la
  langue dépendante ne correspondent pas (en particulier le braille
  vietnamien et la parole vietnamienne)
* Correction d'un bug d'espacement en HTML à l'intérieur des élements
* Amélioration de la détection des chiffres romains


### Version 0.3.9
* Ajout de la traduction en chinois traditionnel (remerciements à Hon-Jang
  Yang)
* Correction d'un bug lors de la navigation dans la base d'une expression
  scriptée comportant des parenthèses
* Modification significative de la façon dont les espaces sont gérés. Cela
  affecte principalement la sortie braille (détection des espaces et des
  "omissions").
* Reconnaissance améliorée de la chimie
* Corrections du braille UEB résultant de l'ajout d'exemples de chimie
* Corrections UEB pour l'ajout de parenthèses auxiliaires dans certains cas


### Version 0.3.8

Braille :

* Les dialogues ont été internationalisé pour plusieurs langues (un grand
  merci aux traducteurs !)
* Implémentation initiale du CMU -- le code braille utilisé dans les pays
  hispanophones et lusophones
* Correction de quelques bugs de l'UEB et ajout de quelques caractères pour
  l'UEB
* Améliorations significatives du braille Vietnamien

Autres correctifs :

* Modifiez le curseur de la boîte de dialogue de débit relatif pour avoir
  une valeur maximale de 100 % (permet désormais uniquement de définir des
  débits  plus lents). En outre, des tailles de pas ont été ajoutées pour
  qu'il soit plus facile d'augmenter/diminuer le débit de manière
  significative.
* Correction d'un bug d'eSpeak qui coupait parfois la parole lorsque le
  débit relatif était modifié
* Améliorations de la parole en Vietnamien
* Correction d'un bug avec les voix OneCore disant "a"
* Correction de quelques bugs de navigation lorsque `AutoZoomOut` est False
  (pas la valeur par défaut)
* Correction de la mise à jour autour des changements de langue et de
  certains autres changements de boîte de dialogue afin qu'ils prennent
  effet immédiatement après avoir cliqué sur "Appliquer" ou "OK".
* Ajout d'une option "Utiliser la langue de la voix" afin que MathCAT parle
  immédiatement dans la bonne langue (s'il existe une traduction)
* Plusieurs améliorations de nettoyage de mauvais code MathML

### Version 0.3.3
Cette version contient un certain nombre de corrections de bogues. Les
nouvelles fonctionnalités et correctifs de bogues sont :

* Ajout de la traduction en espagnol (grâce à Noelia Ruiz et María Allo
  Roldán)
* Navigation modifiée afin qu'elle démarre le zoom sur un niveau
* Ajout de ctrl+alt+flèche comme moyen de naviguer sur les structures
  tabulaires. Ces touches doivent être plus mémorables car elles sont
  utilisées pour la navigation de tableau dans NVDA.
* Travaillé autour du bogue de NVDA pour les voix eSpeak qui les ont amenés
  à ralentir lorsque le relatif MathRate  a été mis plus lentement que le
  débit de la parole de texte.
* Travaillé autour d'un problème de la voix OneCore afin qu'ils parlent le
  son long "a".

Il y a beaucoup de petits ajustements dans la parole et quelques corrections
de bogues pour Nemeth et UEB.

Remarque : il y a maintenant une option pour obtenir la norme en braille
Vietnamien comme sortie braille. Il s'agit toujours d'un travail en cours et
il y a trop de bogues pour être utilisé autrement que pour les tests. Je
m'attends à ce que la prochaine version de MathCAT contienne une
implémentation fiable.

### Version 0.2.5
* Plus d'améliorations chimique
* Correction pour Nemeth :

	* Ajout de règles "omission"
	* Ajout de quelques règles pour les indicateurs de langue anglaise
	* Ajout de plus de cas où l'indicateur polyvalent est nécessaire
	* Correctifs liés au code Nemeth et à la ponctuation

### Version 0.2
* Beaucoup de correctifs de bogues
* Améliorations de la parole
* Un paramètre de préférence pour contrôler la durée de la pause (fonctionne
  avec le changement du débit relatif de la parole pour les mathématiques)
* Prise en charge de la reconnaissance de la notation chimique et à la
  verbaliser de manière appropriée
* Traductions vers indonésien et vietnamien

[[!tag dev stable]]

[1]: https://www.nvaccess.org/addonStore/legacy?file=mathcat
