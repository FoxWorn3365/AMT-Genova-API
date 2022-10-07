# AMT Genova API
Una semplice documentazione per usare le API dell'AMT Genova

**Ringrazio molto [lego11](https://github.com/RAD750) per avermi aiutato molto nella ricerca**

## Introduzione
In questo file andrò a spiegare come utilizzare le API dell'AMT Genova.
Ci tengo a precisare che utilizzeremo le API messe a disposizione dal sito dell'AMT ma non documentate, nella pagina Accessibilità.
Non grantisco che siano le API utilizzate dall'applicazione ufficiale (sto provando a cercarle)

## API in Json
Ho fatto un semplice programma che in base al numero della fermata restituisce i transiti in un comodo Json

**Endpoint:** `https://api.fcosma.it/amt/fermata`<br>
**Tipo di richiesta:** `GET`<br>
**Parametri obbligatori:** `codice (INT)`<br>
**Esempio di una richiesta VALIDA**: `https://api.fcosma.it/amt/fermata?codice=0416`<br>
**Risposta (esempio):**
```json
{
  "status": 200,
  "message": "Autobus per la fermata 0416",
  "aggiornamento": "07/10/2022 - 23:52:44",
  "transiti": {
    "1": {
      "lineNumber": "618",
      "lineDestination": "SAMPIERDARENA",
      "arrivalTime": "00:01:18",
      "waitingTime": "9'"
    },
    "2": {
      "lineNumber": "606",
      "lineDestination": "PRINCIPE FS",
      "arrivalTime": "00:11:10",
      "waitingTime": "18'"
    },
    "3": {
      "lineNumber": "617",
      "lineDestination": "BRIGNOLE FS",
      "arrivalTime": "00:12:34",
      "waitingTime": "20'"
    },
    "4": {
      "lineNumber": "607",
      "lineDestination": "BRIGNOLE FS",
      "arrivalTime": "00:18:16",
      "waitingTime": "26'"
    }
  }
}
```

**Valori:**
  - status: NUMBER INT (200 = success; 204 = nessun transito; 400 = fermata inesistente)
  - message: STRING (Un semplice messaggio del server, anche in caso di errore)
  - aggiornamento STRING (DATA) (La data e ora dell'ultimo aggiornamento degli orari)
  - transiti:
     - 1<br>
       -1 STRING (Numero del bus, sempre a 3 cifre/lettere)<br>
       -2 STRING (Direzione del bus)<br>
       -3 STRING (Ora prevista per il passaggio del bus)<br>
       -4 STRING (Attesa prevista. Se vi da fastidio il ' fate FILTER_SANITIZE_NUMBER_INT)
     - 2<br>
       -1 STRING (Numero del bus, sempre a 3 cifre/lettere)<br>
       -2 STRING (Direzione del bus)<br>
       -3 STRING (Ora prevista per il passaggio del bus)<br>
       -4 STRING (Attesa prevista. Se vi da fastidio il ' fate FILTER_SANITIZE_NUMBER_INT)
       
## API Ufficiali dell'AMT Genova
**Endpoint:** `https://www.amt.genova.it/amt/servizi/passaggitel.php`<br>
**Tipo di richiesta:** `POST`<br>
**Parametri obbligatori:** `CodiceFermata => INT (Codice della fermata); conferma => Conferma`<br>
**Esempio di una richiesta VALIDA**: `https://www.amt.genova.it/amt/servizi/passaggitel.php`<br>
**Risposta (esempio):**
Pagina in HTML con tabella dei passaggi dei Bus
