# AMT Genova API
Una semplice documentazione per usare le API dell'AMT Genova

**Ringrazio molto [lego11](https://github.com/RAD750) per avermi aiutato molto nella ricerca**

## Introduzione
In questo file andrò a spiegare come utilizzare le API dell'AMT Genova.
Ci tengo a precisare che utilizzeremo le API messe a disposizione dal sito dell'AMT ma non documentate, nella pagina Accessibilità.
Non grantisco che siano le API utilizzate dall'applicazione ufficiale (sto provando a cercarle)

## API in Json
Ho fatto un semplice programma che in base al numero della fermata restituisce i transiti in un comodo Json

**Endpoint:** `https://api.fcosma.it/amt/fermata`
**Tipo di richiesta:** `GET`
**Parametri obbligatori:** `codice (INT)`
**Esempio di una richiesta VALIDA**: `https://api.fcosma.it/amt/fermata?codice=0001`
**Risposta (esempio):**
```json
{"status":200, "message":"Autobus per la fermata 0001", "aggiornamento":"05/03/2022 - 12:19:43", "transiti":{"1":["032","S.F. DA PAOLA","12:31:54","12'"],"2":["032","S.F. DA PAOLA","12:46:14","27'"]}}
```
**Valori:**
  - status: NUMBER INT (200 = success; 204 = nessun transito; 400 = fermata inesistente)
  - message: STRING (Un semplice messaggio del server, anche in caso di errore)
  - aggiornamento STRING (DATA) (La data e ora dell'ultimo aggiornamento degli orari)
  - transiti:
     - 1
       -1 STRING (Numero del bus, sempre a 3 cifre/lettere)<br>
       -2 STRING (Direzione del bus)<br>
       -3 STRING (Ora prevista per il passaggio del bus)<br>
       -4 STRING (Attesa prevista. Se vi da fastidio il ' fate FILTER_SANITIZE_NUMBER_INT)
     - 2
       -1 STRING (Numero del bus, sempre a 3 cifre/lettere)<br>
       -2 STRING (Direzione del bus)<br>
       -3 STRING (Ora prevista per il passaggio del bus)<br>
       -4 STRING (Attesa prevista. Se vi da fastidio il ' fate FILTER_SANITIZE_NUMBER_INT)
       
## API Ufficiali dell'AMT Genova

