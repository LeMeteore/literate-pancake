---
title: |
  Use of python Tkinter GUI to collect, Manage and Visualize data.
date: Jun, 2022
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
    \lhead{Ousséni OUEDRAOGO}
    \rfoot{Page \thepage}
    \hypersetup{pdftex,
            pdfauthor={Ousséni OUEDRAOGO},
            pdftitle={Use of python Tkinter GUI to collect, Manage and Visualize data},
            pdfsubject={Use of python Tkinter GUI to collect, Manage and Visualize data},
            pdfkeywords={Python, Programming},
            pdfproducer={Emacs, Pandoc, Latex, Markdown},
            pdfcreator={Emacs, Pandoc, Latex, Markdown}}
    
---
# Abstracts
# I. Introduction
In the hospital, healthcare pactitioner use a health information system to collect patient data like his identity,
age, higth, weigth and biological informations about his diseases. To have a overview of those information, the statistician
must extract patient data and go to an other system like STATA, R or Python to analyse data and send knowledge to practitioner.
To improve the patient automatic follow up, we need a system which will allow practitoner to follow one patient or many patients
during the collect to detect aberration and take decision quickly. This is our question of reseach.

# II. Aims
## II.1. Main aim

#### Implement a user interface which will help physician to collect and visualize patient data by usin python GUI Tkinter

## II.2. Specifics aims

#### II.2.1. Improve the the taking care of patient by allowing automatique analysing of patient data

#### II.2.2. Reduce the rate of aberration during patient data collection

# III. Methods and materials

## III.1. Methods
The taking care of patients is made by interrogation of patient, physical exam and the proposition of treament.
When the patient arrived to hospital at emercency room, the practitioners will 

<img src="https://github.com/Moeisoft-Business/literate-pancake_Ousseni_OUEDRAOGO/blob/master/img/01.jpg" width="700" height="600">

## III.2. Materials
We use Unified Modeling Language (UML) for describing and design the process of patient taking care by physician in inpatient room.
Mysql will be used to store data which are collected by the system.

### 1 Download XAMP and install it at https://www.apachefriends.org/fr/index.html

### 2 Create
the user "MoeiLab" and passeword "MoeiLab1234"

### 3 launch the Xamps control pannel and connect to the phpmyadmin

### 4 use the sql code below to creat data or create it manually
```
-- phpMyAdmin SQL Dump
-- version 5.2.0
-- https://www.phpmyadmin.net/
--
-- Hôte : 127.0.0.1
-- Généré le : mer. 06 juil. 2022 à 02:31
-- Version du serveur : 10.4.24-MariaDB
-- Version de PHP : 8.1.6

SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
START TRANSACTION;
SET time_zone = "+00:00";

 Base de données : `moeilab`

Structure de la table `constant`

CREATE TABLE `constant` (
  `Id_` int(5) NOT NULL,
  `Temperature_` decimal(3,0) NOT NULL,
  `Age_` int(3) NOT NULL,
  `FC_` int(3) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Déchargement des données de la table `constant`
--

INSERT INTO `constant` (`Id_`, `Temperature_`, `Age_`, `FC_`) VALUES
(1, '38', 25, 85),
(2, '37', 22, 82),
(3, '36', 45, 75),
(4, '36', 45, 75),
(5, '37', 35, 95);

--
-- Index pour les tables déchargées
--
--
-- Index pour la table `constant`
--
ALTER TABLE `constant`
  ADD UNIQUE KEY `Id_` (`Id_`);
COMMIT;

```
### Install the requirements
* mysql.connector using pip
* install pandas using pip
* install matplotlib using pip

### Section du code python
```python
# Python Code section
# importation of library required
import tkinter
import mysql.connector
import time
import datetime
import tkinter as tk
import pandas
from pandas import DataFrame
import matplotlib.pyplot as plt
from matplotlib.backends.backend_tkagg import FigureCanvasTkAgg


# definition of the main panel
Pane = tk.Tk()
Pane.config(bg="green")
Pane.geometry("500x300")
Pane.title("Patient Follow Up")#attribution de titre à la fenetre

# creating a Fra, e which can expand according
# to the size of the window
Main_Fen = tkinter.Frame(Pane)
Main_Fen.pack(fill = tkinter.BOTH, expand = True)

#time managment
aujourdhui = datetime.date.today()
aujourdhui
datetime.date(2011, 2, 14)
datetime.date.fromtimestamp(time.time()) # Équivalent à date.today
datetime.date(2011, 2, 14)
Lab_time=tkinter.Label(Main_Fen,text=aujourdhui,bg="green",fg="white")
Lab_time.pack(side = tk.TOP, fill = tkinter.BOTH, expand = True)


Id_1 = tkinter.Label(Main_Fen, text = "Patient Id")
Id_1.pack(side= tkinter.TOP, fill = tkinter.BOTH, expand = True)
Id_1 = tk.Entry(Main_Fen, bd =5)
Id_1.pack(side = tk.TOP, fill = tkinter.BOTH, expand = True)

Patient_Temperature = tkinter.Label(Main_Fen, text = "Patient Temperature")
Patient_Temperature.pack(side= tkinter.TOP, fill = tkinter.BOTH, expand = True)
Patient_Temperature = tk.Entry(Main_Fen, bd =5)
Patient_Temperature.pack(side = tk.TOP, fill = tkinter.BOTH, expand = True)

Patient_FC = tkinter.Label(Main_Fen, text = "Patient Cardiac Rate")
Patient_FC.pack(side= tkinter.TOP, fill = tkinter.BOTH, expand = True)
Patient_FC = tk.Entry(Main_Fen, bd =5)
Patient_FC.pack(side = tk.TOP, fill = tkinter.BOTH, expand = True)

Patient_Age = tkinter.Label(Main_Fen, text = "Patient Age")
Patient_Age.pack(side= tkinter.TOP, fill = tkinter.BOTH, expand = True)
Patient_Age = tk.Entry(Main_Fen, bd =5)
Patient_Age.pack(side = tk.TOP, fill = tkinter.BOTH, expand = True)


# Cette fonction va permettre de sauvegarder les enregistrement dans une base données sql
def Save_to_sql():
    Temperature = Patient_Temperature.get()
    Age = Patient_Age.get()
    FC = Patient_FC.get()
    Id = Id_1.get()
    cnx = mysql.connector.connect(user='MoeiLab', password='MoeiLab@1234', host='127.0.0.1', database='moeilab')
    cursor = cnx.cursor()
    add_constant = ("INSERT INTO constant " "(Id_,Temperature_, Age_, FC_)" "VALUES (%(Id_)s,%(Temperature_)s, %(Age_)s, %(FC_)s)")

    Data_constant = {'Id_': Id,'Temperature_': Temperature, 'Age_': Age, 'FC_': FC, }
    cursor.execute(add_constant, Data_constant)
    # Make sure data is committed to the database
    cnx.commit()

    # Renitialisation de la table de saisie
    Patient_Age.delete(0, tkinter.END)
    Patient_FC.delete(0, tkinter.END)
    Id_1.delete(0, tkinter.END)
    Patient_Temperature.delete(0, tkinter.END)


def Save() :
    Save_to_sql()
Sauvergarde =tkinter.Button(Main_Fen,text="Sauvegarder",bg="green",fg="white",command=Save)
Sauvergarde.pack(side=tkinter.TOP, fill = tkinter.BOTH, expand = True)


def Afficher() :
    cnx = mysql.connector.connect(user='MoeiLab', password='MoeiLab@1234', host='127.0.0.1', database='moeilab')
    cursor = cnx.cursor()
    cursor.execute("SELECT * FROM constant ")
    table_rows = cursor.fetchall()
    df3 = pandas.DataFrame(table_rows, columns=['Id_', 'Temperature_','Age_','FC_'])

    #df3 = pandas.DataFrame(data, columns=['1', '3'])
    #df3 = data['Temperature_C', 'FC_C']
    #print(df3)

    root = tk.Tk()
    root.title("Report Graph")
    figure3 = plt.Figure(figsize=(5, 4), dpi=100)
    ax3 = figure3.add_subplot(111)
    ax3.scatter(df3['Temperature_'], df3['FC_'], color='g')
    scatter3 = FigureCanvasTkAgg(figure3, root)
    scatter3.get_tk_widget().pack(side=tk.LEFT, fill=tk.BOTH)
    ax3.legend(['FC_'])
    ax3.set_xlabel('Temperature_')
    ax3.set_title('Temperature_ Vs. FC_')
    root.mainloop()


# cette fonction va permettre d'afficher la courbe de suivi
def Print_report():
    Afficher()
Buton_Print_report=tkinter.Button(Main_Fen,text="Print a Report",bg="green",fg="white",command=Print_report)
Buton_Print_report.pack(side=tkinter.TOP, fill = tkinter.BOTH, expand = True)

# Pour la fenetre principale
Main_Fen.mainloop()

```
# IV. Results
### The user interface
<img src="https://github.com/Moeisoft-Business/literate-pancake_Ousseni_OUEDRAOGO/blob/master/img/02.jpg" width="500" height="400">

### While collecting data
<img src="https://github.com/Moeisoft-Business/literate-pancake_Ousseni_OUEDRAOGO/blob/master/img/03.jpg" width="500" height="400">

### Data store in Mysql database
<img src="https://github.com/Moeisoft-Business/literate-pancake_Ousseni_OUEDRAOGO/blob/master/img/04.jpg" width="700" height="600">

### Printing a report of temperature Vs heart rate
<img src="https://github.com/Moeisoft-Business/literate-pancake_Ousseni_OUEDRAOGO/blob/master/img/05.jpg" width="700" height="600">

# Conclusion
This is a set of healthcare user interface. It can be improve for later use.

# Bibliography
* [1]. https://www.tutorialspoint.com/python/tk_entry.htm
* [2]. https://dev.mysql.com/doc/connector-python/en/connector-python-example-cursor-select.html
* [3]. https://stackoverflow.com/questions/58263034/mysql-pythonusing-auto-increment-primary-key
* [4]. https://www.delftstack.com/fr/howto/python-pandas/select-multiple-columns-pandas/
