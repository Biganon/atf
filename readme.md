# ATF de 1954 à 2019, au format JSON

## Définitions

Le **Tribunal fédéral** est l'instance judiciaire suprême de la Suisse. Il siège à Lausanne. Il est compétent pour connaître, en dernière instance, de la plupart des litiges de droit privé, pénal, administratif ou fiscal.

Le Tribunal fédéral rend actuellement plus de 7'500 **arrêts** (jugements) par année.

Environ 2 à 3% de ces arrêts (entre 200 et 400, environ) sont considérés comme particulièrement importants, et sont publiés depuis 1874 dans un recueil annuel, appelé **recueil ATF**. Par extension, on appelle "un ATF" un arrêt publié dans ce recueil. Les arrêts ainsi promus sont généralement expurgés d'une partie de leur contenu, afin de se limiter à des extraits qui rendent comptent de leur importance. 

Les différences entre les arrêts publiés aux ATF et ceux qui ne le sont pas sont de plusieurs ordres :

* les arrêts publiés aux ATF ont un contenu matériellement plus significatif ;
* les arrêts publiés aux ATF doivent en principe être connus des avocates et avocats ; un manquement à cette exigence peut, en cas de dommage, engager la responsabilité civile de l'avocate ou de l'avocat ;
* les arrêts publiés aux ATF étaient, pendant longtemps, plus facilement accessibles que les autres. Cela n'est plus le cas depuis 2000, année depuis laquelle ces arrêts sont également mis à disposition gratuitement sur internet, que ce soit sur le site du Tribunal fédéral ou sur celui de l'Université de Berne.

## Source des données

Le recueil ATF est disponible en version reliée, par volume annuel.

Les ATF dès 1954 sont également transcrits et accessibles gratuitement sur le [site du Tribunal fédéral](https://www.bger.ch/ext/eurospider/live/fr/php/clir/http/index_atf.php?lang=fr).

Les ATF antérieurs à 1954 sont disponibles sur le [site de l'Université de Berne](https://www.servat.unibe.ch/dfr/dfr_bge14.html). 

Les arrêts non publiés dans le recueil ATF sont disponibles (depuis 2000) sur le [site du Tribunal fédéral](https://www.bger.ch/ext/eurospider/live/fr/php/aza/http/index.php?lang=fr) ainsi que sur le [site de l'Université de Berne](https://www.servat.unibe.ch/dfr/dfr_bger2020.html).

## Limitations

Premièrement, j'ai exclu de ce projet les ATF antérieurs à 1954. Bien que disponibles sur le site de l'Université de Berne, la grande majorité d'entre eux n'a pas été transcrite, et se présente donc sous forme de fichiers PDF contenant le scan de l'arrêt, imprimé pour les plus anciens en écriture [Fraktur](https://fr.wikipedia.org/wiki/Fraktur). Il serait intéressant de transcrire ces arrêts anciens. Pour éviter un "mitage" des données, même les arrêts transcrits ont été exclus du projet.

Deuxièmement, les arrêts non publiés au recueil ATF ont été exclus, parce qu'ils ne présentent qu'un intérêt matériel limité, et parce qu'ils auraient multiplié par près de 50 la quantité de données traitées, et avec cela la durée des différents traitements.

## Pertinence

Le projet a été motivé par mon travail d'assistant à l'Université de Genève. Dans le cadre de la mise à jour d'un ouvrage de référence, j'ai eu (entre autres choses) à mettre à jour les très nombreuses références jurisprudentielles de l'ouvrage. Le procédé, s'appuyant massivement sur le site internet de référence Swisslex, se décomposait en plusieurs étapes, répétées de façon quasi-mécanique :

1. repérer l'identifiant de l'ATF ("l'ATF de base") dans le corps du texte ou dans les notes de bas de page ;
1. rechercher cette référence dans le moteur de recherche de Swisslex ;
1. retrouver le considérant pertinent, lorsque celui-ci n'était pas clairement indiqué dans l'ouvrage ;
1. utiliser la fonction "Cité par" de Swisslex, pour lister tous les ATF faisant référence à l'ATF de base ;
1. parmi ces ATF, ne garder que ceux postérieurs à 2013 (la précédente version de l'ouvrage datant de 2013, je suis parti de l'idée que si un ATF existait déjà à ce moment-là mais avait été ignoré, je n'avais pas à le prendre en compte aujourd'hui) ;
1. dans chacun des ATF postérieurs à 2013, rechercher toutes les références à l'ATF de base (Swisslex met en évidence la première de ces références, mais il y en a souvent plusieurs) ;
1. pour chacune des références en question, vérifier si le considérant précis auquel elle fait référence est celui cité (ou auquel il est fait allusion) dans l'ouvrage, et ne garder la référence qu'à cette condition ;
1. lire (et souvent traduire) la phrase précédent la référence, et estimer à partir de là si l'ATF récent représente, dans son ensemble, un apport significatif pour la nouvelle édition de l'ouvrage.

Si cette méthode fonctionne, elle est extrêmement lente, et peut être massivement automatisée, à condition toutefois de disposer de l'ensemble des ATF dans un format exploitable. C'est ce qui a motivé ce projet, ainsi que l'accent mis sur l'aspect "citations croisées" (quels arrêts sont cités par tel arrêt, et quels arrêts le citent lui).

En outre, le site internet du Tribunal fédéral est de piètre qualité. La navigation est peu agréable, et les arrêts eux-mêmes sont souvent mal structurés :

* certains arrêts contiennent des balises HTML orphelines, ou (par exemple) la totalité du chapeau à l'intérieur d'une balise servant normalement à indiquer une référence à une base légale ;
* certains arrêts ont manifestement été mal scannés, ou ont fait l'objet de fautes de frappe, ce qui rend notamment difficile l'extraction des dates (cf. l'ATF 100 II 92 et le mois de "geunaio", l'ATF 86 II 106 et le mois de "Februer", l'ATF 98 Ia 175 et le mois de "févier", et j'en passe).

Ainsi, ce projet permet à d'autres personnes de disposer d'une base de travail (plus) propre.

## Structure

Un ATF peut se composer des sections suivantes, parfois répétées en plusieurs occurrences :

* **chapeau** : date et code d'identification du ou des arrêt(s) à l'origine de l'ATF, ainsi qu'un titre qui indique en général les parties en cause ;
* **regeste(s)** : résumé(s) de l'ATF ;
* **faits** : faits de la cause ;
* **considérants** : raisonnement juridique opéré par le Tribunal.

Il y a toujours un seul chapeau, et une seule section "considérants". Il y a en général un seul regeste, mais environ 1.5% des ATF en contiennent plusieurs (jusqu'à 8 pour l'ATF 137 V 210). Il y a en général une section "faits", mais environ 12% des ATF n'en contiennent pas.

Cette structure est reflétée dans les fichiers JSON. Le reste des champs est trivial à comprendre.

Note : les changements de page sont indiqués par le nouveau numéro de page, entre deux caractères "tube" (`|`).

## Avenir

Les ATF à venir seront ajoutés au fur et à mesure de leur publication sur le site internet du Tribunal fédéral.

Un script simple reprenant la méthodologie détaillée ci-dessus sera peut-être créé, ainsi qu'un outil permettant de passer d'obtenir la ou les pages à partir d'un numéro de considérant, et vice-versa.

## Trivia

Quelques infos diverses :

* 19'537 ATF ont été pris en compte.
* ATF le plus long : ATF 126 II 522 (190'059 octets, 79 pages)
* ATF le plus court : ATF 97 I 608 (682 octets, 1 phrase)
* La date la plus fréquente pour un ATF est le 19 décembre, avec 97 ATF.
* Les dates les moins fréquentes sont le 25 décembre et le 1er janvier, avec aucun ATF, puis le 26 décembre et le 2 janvier, avec 1 ATF chacune.
* L'année la plus prolifique fut 1991, avec 420 arrêts.
* L'année la moins prolifique fut 1962, avec 183 arrêts.
* Environ 77% des ATF sont en allemand, 19% en français, 4% en italien, et 2 arrêts sont en romanche (ATF 122 I 93 et ATF 139 II 145).
* Un seul ATF (ATF 91 II 25) contient le mot "framboise", et il est en allemand.