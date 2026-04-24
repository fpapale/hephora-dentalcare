 # Frontend Design for DentalCare MVP
 This document outlines the frontend structure, user flows, and implementation plan for the DentalCare MVP.

 ## 1. Obiettivi Frontend dell’MVP
 - Offrire interfaccia chiara e veloce per gestione appuntamenti.
 - Supportare pazienti e dentisti con UX mobile-first.
 - Integrare in modo sicuro con le API backend.
 - Assicurare accessibilità e performance.

 ## 2. Utenti e Ruoli
 - **Paziente**: prenotazione, visualizzazione e modifica appuntamenti.
 - **Dentista**: gestione agenda, conferma e ripianificazione.
 - **Supporto/Amministratore**: monitoraggio e risoluzione ticket.

 ## 3. Mappa delle Schermate Principali
 | Pagina                   | Descrizione                                            |
 |--------------------------|--------------------------------------------------------|
 | Login/Registrazione      | Accesso e creazione account                            |
 | Dashboard Paziente       | Elenco appuntamenti e azione “Prenota”                 |
 | Dashboard Dentista       | Agenda giornaliera con conferma/rifiuto                |
 | Prenota Appuntamento     | Selezione data, orario e dentista                      |
 | Dettaglio Appuntamento   | Info appuntamento e stato                              |
 | Profilo Utente           | Modifica dati personali e professionali                |
 | Gestione Pazienti        | Elenco pazienti recenti con accesso alla scheda clinica|
 | Scheda Clinica Paziente  | Anamnesi, visite e note cliniche                       |
 | Supporto e Contatti      | Form invio messaggio                                   |

 ## 4. Flussi Utente Principali
 - Login → Dashboard
 - Paziente: prenota → conferma → reminder email
 - Dentista: filtra giorno → conferma/rifiuta
 - Modifica profilo → salva
 - Invia richiesta supporto → conferma invio

 ## 5. Dashboard Studio Dentistico
 - Vista giornaliera con `AppointmentCard` e azioni rapide
 - Filtri per stato e ricerca pazienti

 ## 6. Gestione Appuntamenti
 - Elenco completo con paginazione
 - Modal per gestione stato e note

 ## 7. Gestione Pazienti
 - Lista sintetica con nome, ultima visita, stato
 - Accesso rapido a `Scheda Clinica Paziente`

 ## 8. Scheda Clinica Paziente
 - Tab: Anamnesi, Visite, Note Cliniche
 - Aggiunta/modifica inline dei record

 ## 9. Anamnesi
 - Form anamnestico strutturato con check-list
 - Storico anamnesi in ordine cronologico

 ## 10. Visite e Note Cliniche
 - Elenco visite con sintesi e prescrizioni
 - Editor semplificato per note, caricamento file

 ## 11. Integrazione con Backend/API
 - Consumo RESTful API con autenticazione JWT
 - Gestione token e rinnovo automatico
 - Error handling e retry limitato

 ## 12. Principi UX per MVP Semplice
 - Design responsive mobile-first
 - Riduzione degli step e smart defaults
 - Feedback visivo immediato (loader, toast)

 ## 13. Rischi Frontend
 - Connessioni lente o intermittenti
 - Stato offline non supportato
 - Carichi elevati in dashboard

 ## 14. Primo Piano di Implementazione Frontend
 | Fase                      | Attività principale                                |
 |---------------------------|----------------------------------------------------|
 | Setup progetto e tooling  | Configurazione librerie, linting, styling          |
 | Layout e navigazione      | Navbar, routing, container responsive              |
 | Autenticazione            | Login, registrazione, protezione rotte             |
 | Dashboard Paziente        | Vista appuntamenti e prenotazione                  |
 | Dashboard Dentista       | Agenda giorno e gestione richieste                 |
 | Profilo e Supporto        | Moduli profilo e form supporto                     |
 | Schede cliniche           | Anamnesi, visite e note                            |
 | Test e QA                 | Unit test, end-to-end, revisione UX                |
