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

---

# Les métacaractères

Les métacaractères sont des caractères ayant une signification particulière :

[Voir le tableau](https://www.notion.so/05d6464f3cbb4687a56f0273093b501f)

---

# Séquences spéciales

Une séquence spéciale est un `\` suivi de l'un des caractères de la liste ci-dessous et a une signification particulière :

[Voir le tableau](https://www.notion.so/d48308b39a1b47a49e726d5f859b413f)

---

# Les sets

A set is a set of characters inside a pair of square brackets `[]` with a special meaning:

[Voir le tableau](https://www.notion.so/8eec1670291043aaa4d8627c01200156)

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

