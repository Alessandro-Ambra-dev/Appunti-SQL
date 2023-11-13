## OPERATIONS ON SQL

- Ci sono 5 tipi principali di operazioni che possono essere fatte con SQL:

1. DDL: Data Definition Language => E sono tutti gli statement che definiscono lo schema del database;

2. DQL : Data Query Language => E sono tutte le istruzioni che vengono utilzzate per eseguire le query sui dati che vengono chiamati su porzioni specifiche dello schema;

3. DML : Data Manipulation Language => SOno i commandi per manipolare i dati del nostro database, questa classe di operazioni è quella che racchiude il maggior numero di statement di SQL;

4. DCL : Data Control Language => Comandi che trattano i permessi i diritti del server e altri controlli simili sul sistema del database;

5. TCL: Transaction Control Language => Questo è un gruppo che a volte viene escluso da SQL, ma è molto importante poiché si occupa delle transazioni (che sono un particolare tipo di Query) sul database;

## DDL COMMANDS

- DDL => data definition language, sono tutti quei comandi utilizzati per definire lo schema di una tabella di un database;

- Modifichiamo la struttura ma non le righe della tabella stessa;

-Lo schema definisce l'archittetura di un database e quindi come i dati vengono organizzati all'interno di un database relazionale;

- Proprietà dello schema:

  1.Può essere rappresentato tramite uno schema

  2. Definisce una formattazione consistente per tutti i dati (sia valore che chavi )

  3. Definisce delle chiavi uniche per tutti i valori e le tabelle del database;

  4. Definisce le colonne in una table con nomi e diversi tipi di dato;

-List of DDL Commands:

Main commands:

## CREATE:

-Viene utilizzato per creare il database e i suoi oggetti (come una tabella, un index, una funzione etc);

# DROP:

- Viene utilizzato per eliminare ogetti dal database o il database stesso;

# ALTER:

- Viene utilizzato per modificare la struttura del database, incluse i tipi nelle colonne;

# TRUNCATE:

- Viene usato per rimuovere tutti i record da una table, incluso lo spazio fisico che quella tabella occupa;

# COMMENT:

- Utilizzato per aggiungere commenti al dizionario dei dati;

# RENAME:

- Utilizzato per rinominare oggetti esistenti nel database;

-NB: Questi comandi non vengono utilizzati da un utente, ma dall'admin o dal proprietario del database, perché sono operazioni sensibili che potrebbero compromettere i dati di un'azienda;

## SQLite Online

- Questa estensione è utilizzabile per simulare un ambiente in cui abbiamo un database senza dover ricorrere a tools come PostgreSQL o altri;

- Nel tool c'è la possibilità di esercitarsi a scrivere dei componenti database con SQL, è molto utile perché ci sono esempi specifici su come fare;

-Link del sito: "https://sqliteonline.com/"

## PRACTICE DLL COMMANDS:

- Vediamo come creare un database, alterare i dati della tabella ed infine cancellare il database stesso;

- Per creare una nuova tabella bisogna utilizzare la funzione CREATE TABLE; LA sintassi di questo comando è che si può memorizzare la tabella:

La sintassi generica è questa :

CREATE TABLE {name} [{columns}](
KEYS, VALUES;
)

ES:

CREATE TABLE dogs(
id INTEGER PRIMARY KEY,
name TEXT NOT NULL,
gender TEXT VARCHAR 1
)

-SQL creerà quindi questa tabella dogs con 3 chiavi, la prima è ID (fortemente raccomandato per tutte le tabelle, è una primary key, quindi differenzia un item dall'altro e lo rende unico, ed è spesso un numero intero), NAME (un testo che vogliamo sia non nullo), ed un GENDER (anch'esso testo, ma che vogliamo sia una variabile con un singolo valore che può essere M o F);

-Vediamo ora come modificare la struttura di questa tabella:

ALTER TABLE dogs RENAME TO animal => Questo comando cambierà il nome della tabella da dogs ad animals;

ALTER TABLE animal ADD COLUMN category TEXT=> Questo comando aggiungerà una colonna in più alla struttura della tabella, la colonna category che è di tipo testo;

## DQL COMMANDS

- DQL => Data quety language, questi comandi servono a prendere le relazioni di schema basate su una specifica query;

-In realtà questi tipi di comandi contengono solo un comando:

SELECT => Viene usato per prendere o fetchare i dati da un database, con SELECT possiamo prendere delle table intere o singole porzioni di essa; I dati ritornati dalla select vengono conservati in una result table nell'applicazione front-end (Client) connessa al database (Server); => SQL permette al Client di comunicare con il server;

-La funzione select da sola non ha molto senso ma va in coppia con un altro tipo di dato, la DML, che specifica che tipo di table andiamo a interrogare;

## DML COMMANDS

- DML => Data Manipulation Languagem consiste in tutti quei comandi SQL che si occupano della manipolazione delle voci di dati presenti nel database;

-DML manipola le voci stesse:

# Main Commands:

-Comandi che interagiscono con le entries (voci) stesse;

ES:

# INSERT =>

Usato per inserire dati in una table;

# UPDATE =>

Usato per aggiornare dati esistenti in una table;

# DELETE =>

usato per eliminare delle voci da una table di un database;

## Main Commands usati con SELECT:

# SELECT FROM =>

Usato per specificare da quale tabella stiamo prendendo i dati;

# WHERE =>

Usato per definire la condizione (filtro) dei dati che vogliamo ritornare;

## PRACITCE- DML COMMANDS

- INSERT INTO animals VALUES (1, 'Rex', 'm', 'dog') => In questo modo stiamo inserendo i valori che mettiamo nelle parentesi tonde per i rispettivi campi (id, name, gender, category), quando vogliamo inserire tutti i fields della nostra table non dobbiamo specificare i campi, poiché SQL sa già che vogliamo aggiornarli tutti;

- Possiamo inserire più elementi nella stessa tabella andando a ripetere il comando =>

INSERT INTO animal VALUES (2, 'Joe', 'f', 'dog');
INSERT INTO animal VALUES (3, 'Max', 'm', 'cat');

=> Se runniamo il comando vedremo che SQL inserirà i valori nella tabella creando 3 elementi (seguendo l'id che è la primary key);

-Per vedere i valori nella tabella runneremo il comando:

SELECT \* FROM animal => Questo comando ci restituirà tutti i valori di tutti gli elementi della table selezionata;

-Ora andremo a modificare il valore di uno degli elementi della table:

UPDATE animal SET name='Toby', gender='f' WHERE id=1; => Con questo comando andrò a modificare i campi selezionati (name e gender)
con i valori nuovi, solo nell'elemento 1 della tabella (poiché ho utilizzato la keyword WHERE specificando il filtro che è id= 1);

- Possiamo anche selezionare condizionalmente un elemento della nostra tabella utilizzando sempre la keyword WHERE:

SELECT id,name,gender FROM animal WHERE category="dog" => Prenderò i campi selezionati nella tabella animal e solo per gli elementi che presentano il valore DOG per il field category;

## DCL COMMANDS

- Tutti i comando che hanno a che fare con i diritti e i permessi del database sono i DCL => Data control commands;

# GRANT:

- Viene usato per dare agli user l'accesso privilegiato ad un database

# REVOKE:

- Viene utilizzato per revocare i permessi speciali dati ad uno user (che si danno col GRANT);

# PRACTICE DCL COMMANDS:

-Vediamo come utilizzare il grant ed il revoke permission in un database;

-Useremo questi comandi solo se siamo gli amministratori del database;

GRANT <command list> ON <tablename> TO <user>;

-Command list=> Ovvero i comandi che stiamo permettendo di utilizzare (come SELECT; UPDATE, DELETE etc;)

GRANT SELECT, INSERT, DELETE ON animal TO user

-la sintassi dello user nei database è la seguente:

username@ip-server => ip server è dove risiede il server ovviamente;

ES: 'Alessandro'@localhost;

-Pensiamo di voler revocare qualche azione allo user a cui abbiamo fatto il grant, la sinstassi è la stessa:

REVOKE DELETE ON animal TO 'Alessandro'@localhost => In questo modo stiamo togliendo allo user Alessandro il permesso di eliminare i dati dal database;

-Ora andiamo a vedere un case study molto più azeindale; Spesso i permessi sono dati in base al ruolo che lo user ricopre all'intrerno dell'azienda:

-Per simularlo facciamo ciò=>

-Creiamo un ruolo nel nostro database;

CREATE ROLE data_analyst; => Questo comando creerà un ruolo all'interno del nostro database con la chiave 'data_analyst'

-Per attribuire dei permessi ad un ruolo occorre utilizzare la sintassi di prima;

GRANT SELECT ON animal TO data-analyst; => Questo permetterà a tutti gli utenti che hanno quel ruolo di interrogare l'api e di usare il comando select;

-Per attribuire un ruolo ad uno user basterà fare così:

# GRANT data_analyst TO 'Alessandro'@localhost =>

- Ora lo user specifico avrà quel ruolo con quelle grant che abbiamo assegnato in precendenza al ruolo specifico;

## TCL COMMANDS

- TCL => Transaction Control Language, sono tutti quei comandi che hanno a che fare con operazioni e query transazionali che possono essere fatte con il database;

- Una transazione in SQL è un gruppo di task che vengono eseguiti insieme automaticamente;

- Le transazioni hanno solo 2 tipi di risultati: successo o fallimento;

COMANDI PRINCIPALI PER I TCL:

# BEGIN TRANSACTION =>

- Usato per indicare lo starting point di una transazione

# SET TRANSACTION =>

- Usato per specificare le caratteristiche di una transazione

# COMMIT=>

- Usato per committare una transazione e quindi runnarla nel database;

# ROLLBACK =>

- Usato per cancellare una transazione nel caso di errori;

## PRACTICE TCL COMMANDS

-Vediamo ora come settare e runnare una transazione in SQL;

BEGIN TRANSACTION;
DELETE FROM animal WHERE id=1;
COMMIT;

-Dopo aver runnato la transazione possiamo vedere come andando a interrogare il database viene tolto ciò che abbiamo chiesto;

-Proviamo a utilizzare il rollback

BEGIN TRANSACTION;
DELETE FROM animal WHERE id=2;
ROLLBACK;

-Ora se runno la transazione vedrò come la transazione viene annullata e quindi l'elemento specifico non viene eliminato proprio per la prensenza del rollback;

-Vediamo ora come utilizzare i save-point per eseguire un rollback di una transaction solo in specifici punti:

-I savepoint sono dei punti di salvataggio che vengono memorizzati dal server:

Per crearne uno:

# SAVEPOINT SP1;

-Proviamo a inserirlo in una transazione;

BEGIN TRANSACTION;
DELETE FROM animal WHERE id=4;
SAVEPOINT SP1;
DELETE FROM animal WHERE id=5;
ROLLBACK TO SP1;
DELETE FROM animal WHERE id=6;
COMMIT;

-Il risultato di questa transazione sarà che le colonne 4 e 6 della nostra table animal non ci sono più => Questo perché dopo aver fatto il rollback viene cancellato il delete sull'id 5 ma viene mantenuto il delete sull'id 6;


