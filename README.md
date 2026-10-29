# Taccuino 0.3.0

Web app installabile su Android e Windows. Le note stanno sul dispositivo; se attivi la
sincronizzazione, una copia cifrata va nella cartella nascosta dell'app sul tuo Google Drive.

## 1. Metterla online (una volta sola, gratis)
Serve un indirizzo https perché fotocamera, microfono, posizione, installazione e accesso a Google funzionino.
1. Crea un repository su GitHub (es. `taccuino`) e carica tutti i file di questa cartella.
2. Nel repository: Settings > Pages > Source «Deploy from a branch», Branch: main, cartella / (root) > Save.
3. Dopo un minuto l'app è su https://<tuo-utente>.github.io/taccuino/
Per aggiornare l'app in futuro basta sostituire i file nel repository (config.js compreso, se non l'hai modificato lì).

## 2. Installarla
- Android: apri l'indirizzo con Chrome > menu ⋮ > «Installa app» (o «Aggiungi a schermata Home»).
- Windows: apri l'indirizzo con Chrome o Edge > icona di installazione nella barra dell'indirizzo.

## 3. Sincronizzazione con Google Drive (facoltativa)
L'app usa solo la sua cartella nascosta su Drive (permesso «drive.appdata»): non vede gli altri tuoi file.
Tutto viene cifrato sul dispositivo con una frase segreta che solo tu conosci.

Una volta sola, nella Google Cloud Console (console.cloud.google.com), con il tuo account Google:
1. Crea un progetto (es. «Taccuino»).
2. Abilita l'API: menu APIs & Services > Library > «Google Drive API» > Enable.
3. Configura la schermata di consenso (Google Auth Platform / OAuth consent screen):
   nome app «Taccuino», la tua email come contatto; pubblico «External»;
   lascia l'app in modalità «Testing» e aggiungi la tua email tra i «Test users».
   Tra gli scope (Data access) aggiungi `.../auth/drive.appdata`.
4. Crea le credenziali: Clients (o Credentials) > Create client > tipo «Web application».
   In «Authorized JavaScript origins» aggiungi `https://<tuo-utente>.github.io` (senza / finale e senza /taccuino).
5. Copia l'«ID client» (finisce con .apps.googleusercontent.com) e incollalo in `config.js`
   nel repository GitHub, tra le virgolette di googleClientId. Salva (commit).

Poi, nell'app: Impostazioni > Google Drive, cifrato > attiva.
- Sul primo dispositivo crei la frase segreta e ricevi una chiave di recupero: conservala fuori dal telefono.
- Sugli altri dispositivi attivi lo stesso interruttore e inserisci la stessa frase.
Google mostrerà l'avviso «app non verificata»: è normale per un'app personale in modalità Testing; scegli Continua.
L'accesso web a Google dura circa un'ora: quando scade, il pallino arancione sul pulsante di sincronizzazione
in alto indica che basta un tocco per rinnovarlo.

## 4. Spostare le note senza Drive
Impostazioni > Avanzate > Esporta un backup, poi Importa un backup sull'altro dispositivo.

## Provarla senza pubblicarla
Nella cartella: `python -m http.server 8000`, poi apri http://localhost:8000 sullo stesso PC (senza Drive).
