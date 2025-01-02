## MCD

![alt](./MCD.png)

## MLD


Livre = (<u>Numero_ID INT</u>, Titre VARCHAR(50), Auteur VARCHAR(50), Genre VARCHAR(50));<br>
Utilisateur = (<u>Id_Utilisateur INT</u>, Nom VARCHAR(50), Prenom VARCHAR(50), Mail VARCHAR(99), Adresse VARCHAR(100));<br>
Bibliotheque = (<u>ID_bibliotheque INT</u>, Telephone INT, Mail VARCHAR(50), Adresse VARCHAR(100), Nom VARCHAR(50));<br>
Emprunter = (<u>#Numero_ID</u>, date_sortie DATE, date_retour DATE,<u>#Id_Utilisateur</u>);<br>
posseder = (<u>#Numero_ID, #ID_bibliotheque</u>);<br>


## SCRIPT SQL

```sql
CREATE TABLE Livre(
   Numero_ID INT,
   Titre VARCHAR(50) NOT NULL,
   Auteur VARCHAR(50) NOT NULL,
   Genre VARCHAR(50),
   PRIMARY KEY(Numero_ID)
);

CREATE TABLE Utilisateur(
   Id_Utilisateur INT,
   Nom VARCHAR(50) NOT NULL,
   Prenom VARCHAR(50) NOT NULL,
   Mail VARCHAR(99),
   Adresse VARCHAR(100),
   PRIMARY KEY(Id_Utilisateur)
);

CREATE TABLE Bibliotheque(
   ID_bibliotheque INT,
   Telephone INT,
   Mail VARCHAR(50),
   Adresse VARCHAR(100),
   Nom VARCHAR(50),
   PRIMARY KEY(ID_bibliotheque)
);

CREATE TABLE Emprunter(
   Numero_ID INT,
   date_sortie DATE,
   date_retour DATE,
   Id_Utilisateur INT NOT NULL,
   PRIMARY KEY(Numero_ID),
   FOREIGN KEY(Numero_ID) REFERENCES Livre(Numero_ID),
   FOREIGN KEY(Id_Utilisateur) REFERENCES Utilisateur(Id_Utilisateur)
);

CREATE TABLE posseder(
   Numero_ID INT,
   ID_bibliotheque INT,
   PRIMARY KEY(Numero_ID, ID_bibliotheque),
   FOREIGN KEY(Numero_ID) REFERENCES Livre(Numero_ID),
   FOREIGN KEY(ID_bibliotheque) REFERENCES Bibliotheque(ID_bibliotheque)
);


```