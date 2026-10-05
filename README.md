# SMART-ERA Data Platform Hub – Traduzioni (i18n)

Repository indipendente contenente i file di traduzione (`*.json`) usati da
[SMART-ERA_Data_Platform_Hub](https://github.com/<org>/SMART-ERA_Data_Platform_Hub).

I file vengono caricati **a runtime via HTTP** dall'applicazione Angular (tramite
`@ngx-translate/http-loader`), e **non sono inclusi nella build** dell'app. Questo
permette di aggiornare le traduzioni con un semplice push su questo repository,
senza dover ricompilare/ridistribuire l'intera applicazione.

## Struttura

Un file JSON per lingua, con chiave piatta `"chiave": "testo tradotto"`.
Nessun markup HTML o classe grafica deve comparire nei valori: il layout
grafico vive esclusivamente nel template Angular (`homepage.component.html`
e simili); qui va inserito **solo il testo da tradurre**.

| File | Lingua |
|---|---|
| en.json | Inglese (sorgente di riferimento) |
| it.json | Italiano |
| de.json | Tedesco |
| fr.json | Francese |
| gr.json | Greco |
| lt.json | Lituano |
| sp.json | Spagnolo |
| pt.json | Portoghese |
| bg.json | Bulgaro |
| bs.json | Bosniaco |
| fi.json | Finlandese |
| sl.json | Sloveno |

## Workflow di aggiornamento

1. Clona questo repository.
2. Modifica il/i file JSON interessati (mantieni la validità JSON: puoi
   verificarla con `node -e "JSON.parse(require('fs').readFileSync('it.json','utf8'))"`
   oppure con un validatore JSON online).
3. Committa e fai push su questo repository.
4. Sul server dove gira l'app (vedi `docker-compose.yml` del progetto principale),
   aggiorna la cartella montata come volume (es. `git pull` nella cartella
   `./i18n` usata dal `docker-compose.yml`). **Non serve rebuildare né
   ridistribuire l'applicazione**: nginx serve i file aggiornati alla
   richiesta successiva.

## Sviluppo locale del progetto principale

Per eseguire `ng serve` in locale, clona questo repository nella cartella
`src/assets/i18n` del progetto `SMART-ERA_Data_Platform_Hub` (quella cartella
è ignorata da git nel progetto principale, proprio per ospitare questo
contenuto durante lo sviluppo):

```bash
git clone <url-di-questo-repo> SMART-ERA_Data_Platform_Hub/src/assets/i18n
```
