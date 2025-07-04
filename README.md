[![Partecipa sul canale #anpr](https://img.shields.io/badge/Slack%20channel-%23anpr-blue.svg)](https://developersitalia.slack.com/messages/C7A8NS7RQ)
[![Ricevi un invito a Slack](https://slack.developers.italia.it/badge.svg)](https://slack.developers.italia.it/)
[![Keep a Changelog v1.1.0 badge](https://img.shields.io/badge/changelog-Keep%20a%20Changelog%20v1.1.0-%23E05735)](CHANGELOG.md)

# Client Java di esempio per il test di connessione ad ANPR

⚠️ Attenzione! Questo progetto non è più manutenuto dai suoi autori. Se vuoi contribuire al progetto e diventare maintainer contattaci sul [canale Slack](https://developersitalia.slack.com/archives/C7A8NS7RQ) dedicato.

## Impostare le credenziali

Per rendere il client utilizzabile, è importante impostare, al primo utilizzo, i certificati con le credenziali di test.
Per ottenere delle credenziali di test, è necessario richiederle al comune per conto del quale è in corso l'integrazione software.

Per personalizzare il certificato bisogna:

- Creare il file `src/main/resources/config/TEST_Keystore.properties` partendo dall'esempio `src/main/resources/config/Example_TEST_Keystore.properties` inserendo i riferimenti al proprio ceritficato, al codice della postazione e al PIN del certificato.
- Aggiungere il certificato ottenuto nella cartella `keystore/TEST`

## Installazione

Per l'installazione e l'esecuzione del test di connessione, **dopo aver inserito le credenziali**, eseguire
```
mvn clean install
```
(questo comando esegue tutte le operazioni, compreso l'esecuzione del test di connessione)

**Nota**: è necessario utilizzare un ambiente Java8.
Si può utilizzare la utility `jenv` per impostare il proprio ambiente di sviluppo.
In questo caso, una volta attivata la versione 1.8, richiamare maven con
```
jenv exec mvn clean install
```

Una classe di test della connessione si trova nella cartella `src/test`

## Docker

Per utilizzare Docker invece di installare un ambiente Java sul proprio sistema
eseguire i comandi come segue

```bash
docker build -t anpr-client-app .
docker run -it --rm --name anpr-client-running-app anpr-client-app
```

# Accesso all'applicazione web

Una volta ricevute le credenziali, si potrà accedere all'applicazione web di test per visualizzare e svolgere operazioni con i dati caricati.

Per fare ciò è necessario importare il certificato ricevuto (sbloccandolo con il rispettivo PIN) nel proprio sistema operativo o nel proprio browser. Dopodiché sarà possibile accedere a https://dptest.anpr.interno.it/combas con nome utente e password ricevute via mail.

# Link utili
* [Pagina di ANPR su Developers Italia](https://developers.italia.it/it/anpr)
* [Documentazione di ANPR](https://docs.italia.it/italia/anpr/anpr/it/stabile/index.html)
