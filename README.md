# Taccuino — prototipo 0.1.0

Web app installabile su Android e Windows. Le note restano sul dispositivo (IndexedDB).

## Metterla online (una volta sola, gratis)
Serve un indirizzo https perché fotocamera, microfono, posizione e installazione funzionino.
1. Crea un repository su GitHub (es. `taccuino`) e carica tutti i file di questa cartella.
2. Nel repository: Settings > Pages > Branch: main, cartella / (root) > Save.
3. Dopo un minuto l'app è su https://<tuo-utente>.github.io/taccuino/

## Installarla
- Android: apri l'indirizzo con Chrome > menu ⋮ > «Installa app» (o «Aggiungi a schermata Home»).
- Windows: apri l'indirizzo con Chrome o Edge > icona di installazione nella barra dell'indirizzo.

Telefono e PC hanno per ora archivi separati: la sincronizzazione cifrata via Google Drive è il passo successivo.
Per spostare le note: Impostazioni > Avanzate > Esporta un backup, poi Importa un backup sull'altro dispositivo.

## Provarla senza pubblicarla
Nella cartella: `python -m http.server 8000`, poi apri http://localhost:8000 sullo stesso PC.
