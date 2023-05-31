
# Project Gestion_Paiement
 Ce projet a pour objectif de mettre en place une solution de gestion des paiements dans une entreprise. Il inclut la création de plusieurs tables pour stocker les informations relatives aux diplômes, grades, salaires de base, cotisations, employés, fonctions, indemnisations, paiements, détails des paiements, congés payés et congés non payés.

 ## STRUCTURE DE LA BASE DE DONNEES
 Table "Diplome":
Cette table contient les informations sur les diplômes disponibles. Chaque diplôme a un identifiant unique (id_diplome) et un nom spécifique (nom). Par exemple, les diplômes peuvent être "Baccalauréat", "Master", "Doctorat", etc. Le champ "nom" garantit que chaque diplôme a un nom unique dans la table.

Table "Grade":
La table "Grade" stocke les informations sur les grades disponibles. Chaque grade a un identifiant unique (id_grade) et un nom spécifique (nom). Par exemple, les grades peuvent être "Assistant", "Ingénieur", "Directeur", etc. Le champ "nom" garantit que chaque grade a un nom unique dans la table.

Table "Diplo_Grade":
Cette table sert de lien entre les diplômes et les grades. Elle enregistre les combinaisons possibles entre un diplôme et un grade, ainsi que leur état et leur date. Chaque combinaison diplôme-grade a un identifiant unique (id_diplo_grade). Le champ "etat" peut prendre la valeur '0' pour indiquer que la combinaison est expirée ou '1' pour indiquer qu'elle est non expirée. Par défaut, l'état est '1'. La date représente la date à laquelle la combinaison a été établie. Les champs "id_diplome" et "id_grade" sont des clés étrangères qui référencent respectivement les tables "Diplome" et "Grade".

Table "Salaire_de_base":
Cette table enregistre les salaires de base associés aux combinaisons diplôme-grade. Chaque salaire de base a un identifiant unique (id_SB) et un montant spécifique (Somme). La date_db représente la date de début de validité du salaire de base. La date_fin peut être nulle si la date de fin n'est pas connue. Le champ "id_diplo_grade" est une clé étrangère qui référence la table "Diplo_Grade", permettant ainsi d'associer le salaire de base à une combinaison diplôme-grade spécifique.

Table "Type_Cotisation":
Cette table stocke les différents types de cotisations possibles. Chaque type de cotisation a un identifiant unique (id_type_cot) et un nom spécifique (nom). Par exemple, les types de cotisations peuvent être "Sécurité sociale", "Retraite", "Mutuelle", etc. Le champ "nom" garantit que chaque type de cotisation a un nom unique dans la table.

Table "Cotisation":
La table "Cotisation" associe les cotisations aux salaires de base. Chaque cotisation a un identifiant unique (id_cotisation) et un pourcentage (pourcent_SB) qui représente le pourcentage du salaire de base à prélever pour cette cotisation. Le champ "id_SB" est une clé étrangère qui référence la table "Salaire_de_base", permettant d'associer la cotisation à un salaire de base spécifique. Le champ "id_type_cot" est une clé étrangère qui référence la table "Type_Cotisation", permettant ainsi de spécifier le type de cotisation.

Table "Employe":
La table "Employe" stocke les informations sur les employés de l'entreprise. Chaque employé a un identifiant unique (id_employe), un nom et un prénom. Par exemple, les champs "nom" et "prenom" peuvent contenir les valeurs "Dupont" et "Jean" respectivement pour un employé spécifique.

Table "SB_Empl":
Cette table sert de lien entre les salaires de base et les employés. Elle enregistre les dates de validité pour chaque liaison salaire de base-employé. Chaque liaison a un identifiant unique (id_SB_empl). La date_db représente la date de début de validité de la liaison. La date_fin peut être nulle si la date de fin n'est pas connue. Les champs "id_SB" et "id_employe" sont des clés étrangères qui référencent respectivement les tables "Salaire_de_base" et "Employe", permettant ainsi d'associer un salaire de base à un employé spécifique.

