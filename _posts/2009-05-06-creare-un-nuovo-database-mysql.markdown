---
title: Creare un nuovo database MySQL
layout: post
---

[createdb]: http://dev.mysql.com/doc/refman/5.1/en/create-database.html
[createuser]: http://dev.mysql.com/doc/refman/5.1/en/create-user.html
[grant]: http://dev.mysql.com/doc/refman/5.1/en/grant.html

Una delle **operazioni più comuni** nella **gestione di un server** per hosting web è la **creazione di database**.
Ormai praticamente ogni sito di media grandezza nel web è costruito e mantenuto grazie a sistemi di gestione dei contenuti (come ad esempio Drupal o WordPress) che hanno necessariamente bisogno dell’accesso ad un database per funzionare.

Una buona pratica per la sicurezza dell’intero sistema è **assegnare ad ogni progetto un proprio database** e **creare un nuovo utente per la gestione di ogni nuovo database**.
In questo modo se dovesse esserci un exploit per uno qualsiasi dei siti residenti nella macchina server, la sicurezza degli altri siti non ne risentirebbe.

**4 semplici passi** per creare da riga di comando un nuovo database e un nuovo utente associato in MySQL (versione 5):

1. accedere alla console mysql come utente root

        mysql -u root -p

1. creare il nuovo database

        CREATE DATABASE <db_name>;

1. creare un nuovo utente

        CREATE USER '<user_name>'@'localhost' IDENTIFIED BY '<user_password>';

1. garantire tutti i permessi all’utente appena creato per il database `<db_name>`

        GRANT ALL PRIVILEGES ON <db_name>.* TO '<user_name>'@'localhost';

Dove:

* `<db_name>` è il nome del nuovo database
* `<user_name>` è il nome del nuovo utente
* `<user_password>` è la password di accesso per il nuovo utente

A questo punto usciamo dalla console con il comando `<Ctrl+D>` e proviamo ad accedere al database appena creato con il nuovo utente per verificare l’effettiva riuscita delle operazioni.

    mysql -u <user_name> -p <db_name>

Per approfondire l’argomento:

* [MySQL 5 Manual – CREATE DATABASE syntax][createdb]
* [MySQL 5 Manual – CREATE USER syntax][createuser]
* [MySQL 5 Manual – GRANT syntax][grant]
