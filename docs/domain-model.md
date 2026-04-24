# Modello di Dominio

## Tenant
Rappresenta uno studio dentistico isolato, con configurazioni e dati indipendenti.

## Studio Dentistico
Entità associata al tenant, include metadata come nome, indirizzo e contatti.

## Utenti e Ruoli
- **Utente**: account con credenziali e profilo.
- **Ruoli**: Amministratore, Dentista, Assistente con permessi differenziati.

## Pazienti
Anagrafica pazienti con dati personali e recapiti.

## Appuntamenti
- Data, ora e partecipanti (paziente, dentista, assistente).
- Stato: programmato, confermato, cancellato.

## Anamnesi
Scheda anamnestica iniziale per ciascun paziente.

## Visite
Registro delle visite svolte, con data, orario e note cliniche.

## Note Cliniche
Annotazioni mediche dettagliate collegate a una visita.

## Chiamate Vocali
Log delle interazioni via Retell.ai + Twilio, con esiti e timestamp.

## Audit Log
Tracciamento minimo delle operazioni critiche (creazione, modifica, cancellazione).

## Relazioni
- Tenant 1–N Utenti, Pazienti, Appuntamenti.
- Paziente 1–N Anamnesi, Visite.
- Visita 1–N Note Cliniche.
- Appuntamento N–1 Paziente, N–1 Dentista.
- Chiamata Vocale legata a Appuntamento e Paziente.
