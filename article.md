---
title: |
  "Les expressions régulières en Python"
date: May, 2022
lang: en-EN
urlcolor: blue
geometry: "left=2.5cm,right=2.5cm,top=3cm,bottom=3cm"
documentclass: article
fontfamily: Alegreya
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhf{}
    \rhead{Dakar Institute of Technology}
    \lhead{Patrick Nsukami}
    \rfoot{Page \thepage}
    \hypersetup{pdftex,
            pdfauthor={Patrick Nsukami},
            pdftitle={Introduction to Python programming},
            pdfsubject={Introduction to Python programming},
            pdfkeywords={Python, Programming},
            pdfproducer={Emacs, Pandoc, Latex, Markdown},
            pdfcreator={Emacs, Pandoc, Latex, Markdown}}
    
---

# Les expressions régulières en Python

Un RegEx, ou Regular Expression, est une séquence de caractères qui forme un modèle de recherche. RegEx peut être utilisé pour vérifier si une chaîne contient le modèle de recherche spécifié.

---

# Le module RegEx

Python a un package intégré appelé `re`, qui peut être utilisé pour travailler avec des expressions régulières.

Importez le module `re` :

```python
import re
```

---

Une fois le module `re` importé, vous pouvez commencer à utiliser des expressions régulières :

# Exemple

Savoir si une chaine de caractère commence par "Le" et se termine par "pays":

```python
import re

txt = "Le Sénégal est un bon pays"
x = re.search("^Le.*pays$", txt)
```

---

# Les fonctions RegEx

Le module `re` offre un ensemble de fonctions qui nous permettent de rechercher une correspondance dans une chaîne :

[Voir le tableau](https://www.notion.so/576512961ea041c8a411c92760d7c788)
|              Fonction             |             Description           |
| :----------------------------------: | :----------------------------------: |
| findall | Renvoie une liste contenant toutes les correspondances |
| search | Renvoie un objet Match s'il y a une correspondance n'importe où dans la chaîne |
| split | Renvoie une liste où la chaîne a été séparée à chaque correspondance |
| sub | Remplace une ou plusieurs correspondances par une chaîne |

---

# Les métacaractères

Les métacaractères sont des caractères ayant une signification particulière :

[Voir le tableau](https://www.notion.so/05d6464f3cbb4687a56f0273093b501f)
|              Caractère             |             Description           |             Exemple           |
| :----------------------------------: | :----------------------------------: | :----------------------------------: |
| [] | Un ensemble de caractères, | ```[a-z]``` |
| \ | Signale une séquence spéciale (peut également être utilisé pour échapper des caractères spéciaux) | ```\y``` |
| . | N'importe quel caractère (sauf le caractère de nouvelle ligne) | ```bon..soir``` |
| ^ | Commence par | ```^jour``` |
| $ | Se termine par | ```elle$``` |
| * | Zéro ou plusieurs occurrences | ```bon.*soir``` |
| + | Une ou plusieurs occurrences | ```bons.+soir``` |
| ? | Zéro ou une occurrence | ```bon.?soir``` |
| {} | Exactement le nombre d'occurrences spécifié | ```bon.{2}soir``` |
| | | Soit ou | ```oui|non``` |
| () | Obtenir et regrouper |

---

# Les caratères spéciaux

Un caractère spécial est un `\` suivi de l'un des caractères de la liste ci-dessous et a une signification particulière :

[Voir le tableau](https://www.notion.so/d48308b39a1b47a49e726d5f859b413f)
| Caractère | Description| Exemple |
| :----------------------------------: | :----------------------------------: | :----------------------------------: |
| \A | Renvoie une correspondance si les caractères spécifiés sont au début de la chaîne |"\AThe" |
|\b|Renvoie une correspondance où les caractères spécifiés sont au début ou à la fin d'un mot (le "r" au début s'assure que la chaîne est traitée comme une "chaîne brute")|r"\bain"r"ain\b |
|\B|Renvoie une correspondance où les caractères spécifiés sont présents, mais PAS au début (ou à la fin) d'un mot (le "r" au début s'assure que la chaîne est traitée comme une ""chaîne brute"")|r"\Bain"r"ain\B" |
|\d|Renvoie une correspondance où la chaîne contient des chiffres (nombres de 0 à 9)|"\d" |
|\D|Renvoie une correspondance où la chaîne NE contient PAS de chiffres|"\D" |
|\s|Renvoie une correspondance où la chaîne contient un caractère d'espace blanc|"\s" |
|\S|Renvoie une correspondance où la chaîne NE contient PAS d'espace blanc|"\S" |
|\w|Renvoie une correspondance où la chaîne contient des caractères de mot (caractères de a à Z, chiffres de 0 à 9 et la barre de 8 _)|"\w" | 
|\W|Renvoie une correspondance où la chaîne NE contient PAS de caractères de mot|"\W" |
|\Z|Renvoie une correspondance si les caractères spécifiés sont à la fin de la chaîne|"pays\Z" |

---

# Les sets

A set is a set of characters inside a pair of square brackets `[]` with a special meaning:

[Voir le tableau](https://www.notion.so/8eec1670291043aaa4d8627c01200156)
| Set | Description|
| :----------------------------------: | :----------------------------------: |
[mar]|Renvoie une correspondance dans laquelle l'un des caractères spécifiés (m, a, ou r) est présent.|
|[m-r]|Renvoie une correspondance pour tout caractère minuscule, par ordre alphabétique entre m et r|
[^mar]|Renvoie une correspondance pour n'importe quel caractère SAUF m, a et r|
|[0123]|Renvoie une correspondance où l'un des chiffres spécifiés (0, 1, 2 ou 3) est présent|
[0-9]|Renvoie une correspondance pour n'importe quel chiffre entre 0 et 9|
|[0-5][0-9]|Renvoie une correspondance pour tous les nombres à deux chiffres entre 00 et 59|
|[a-zA-Z]|Renvoie une correspondance pour tout caractère par ordre alphabétique entre a et z, minuscule OU majuscule|
|[+]|renvoie une correspondance pour tout + de la chaîne|

---

# La fonction findall()

La fonction `findall()` renvoie une liste contenant toutes les correspondances.

# Exemple

```python
import re

txt = "Le Sénégal est un bon pays"
x = re.findall("pa", txt)
print(x)
```

# La fonction search()

La fonction `search()` recherche une correspondance dans la chaîne et renvoie un **Match object** s'il y a une correspondance.

S'il y a plus d'une correspondance, seule la première occurrence de la correspondance sera renvoyée :

# Exemple

```python
import re

txt = "Le Sénégal est un bon pays"
x = re.search("\pa", txt)

print("Le premier caractère d'espace vide est situé en position :", x.start())
```

# La fonction split()

La fonction `split()` renvoie une liste dans laquelle la chaîne a été divisée à chaque correspondance :

# Exemple

```python
import re

txt = "Le Sénégal est un bon pays"
x = re.split("\e", txt)
print(x)
```

# La fonction sub()

La fonction `sub()` remplace les correspondances par le texte de votre choix :

# Example

```python
import re

txt = "Le Sénégal est un bon pays"
x = re.sub("\e", "7", txt)
print(x)
```

# L’objet Match

Un Match Object est un objet contenant des informations sur la recherche et le résultat.

**Remarque :** S'il n'y a pas de correspondance, la valeur `None` sera renvoyée à la place de l'objet de correspondance.

# Exemple

```python
import re

txt = "Le Sénégal est un bon pays"
x = re.search("pa", txt)
print(x) #un objet sera trouvé
```

# Conclusion

Dans cet article nous avions appris comment une expression régulière(RegEx). Les RegEx nous permettent de vérifier les modèles dans les chaînes de texte. Vous pouvez maintenant définir vos propres critères de recherche pour un modèle adapté à vos besoins.

