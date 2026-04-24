# Ambito di Prodotto

## Obiettivo del prodotto
Il progetto DentalCare Core Platform mira a fornire una web application SaaS multi-tenant per la gestione completa degli studi dentistici, semplificando processi clinico-amministrativi e favorendo l'efficienza operativa.

## Utenti
- **Amministratore dello studio**: configura tenant, gestisce utenti e ruoli.
- **Dentista**: accede a schede cliniche, visite e note mediche.
- **Assistente**: pianifica appuntamenti e gestisce prenotazioni.
- **Paziente** (self-service limitato in MVP): riceve promemoria vocali.

## Funzionalità MVP
- Gestione multi-tenant per studi dentistici.
- CRUD di utenti, ruoli e profili pazienti.
- Pianificazione e visualizzazione appuntamenti.
- Integrazione prenotazione vocale tramite Retell.ai + Twilio.
- Registrazione di anamnesi, visite e note cliniche.
- Audit log base per operazioni critiche.
- API RESTful e frontend web.

## Esclusioni dall’MVP
- Teleconsulto video in real time.
- Fatturazione e integrazione contabile.
- Reportistica avanzata e dashboard analitici.
- Integrazione con sistemi esterni diversi da Retell/Twilio.

## Valore commerciale
- Riduzione del carico amministrativo.
- Miglioramento della qualità del servizio al paziente.
- Velocizzazione della pianificazione e comunicazione.

## Ipotesi SaaS
- Modello di abbonamento basato sul numero di studi e utenti.
- Pay-per-use per minuti voce Twilio.
- SLA minima garantita e backup automatici.
