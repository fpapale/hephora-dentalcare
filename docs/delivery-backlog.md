 # Delivery Backlog for DentalCare MVP

 ## 1. Epiche MVP
 - Multi-tenant support (Tenant Management)
 - Gestione Utenti (Registrazione, Login, Profilo)
 - Prenotazioni (Appointment scheduling & management)
 - Cartelle Cliniche (Anamnesis + Clinical Notes)
 - Notifiche e Promemoria (Email/SMS reminders)
 - Integrazione Voce (Retell.ai transcription & Twilio calls)
 - Dashboard e Report (Disponibilità e KPI base)

 ## 2. Task per Backend Lead
 - Configurazione database multi-tenant (schema e partitioning)
 - Implementare servizi: Tenant, Auth, Patient, Appointment, Chart
 - Definire e versionare contratti OpenAPI per tutti i microservizi
 - Sviluppare API CRUD per Appuntamenti e Cartelle Cliniche
 - Implementare layer di integrazione voce con interfacce astratte
 - Configurare notifiche backend via Twilio e Retell.ai
 - Configurare caching Redis per sessioni e code di elaborazione

 ## 3. Task per Frontend Lead
 - Scaffold SPA React con Material/Chakra UI e routing base
 - Creare componenti per Registrazione, Login e gestione profilo
 - Implementare schermate Prenotazione Appuntamenti
 - Realizzare UI Cartelle Cliniche (anamnesi e note cliniche)
 - Integrare notifiche e promemoria nell’interfaccia utente
 - Costruire dashboard base con disponibilità e prossimi appuntamenti
 - Gestire chiamate API e visualizzazione degli errori

 ## 4. Task per Integration Lead
 - Finalizzare contratti OpenAPI e allestire mock server
 - Configurare ambiente Kubernetes di staging e CI/CD (GitHub Actions)
 - Integrare Twilio e Retell.ai (configurazione credenziali e webhooks)
 - Implementare test end-to-end (login → prenotazione → notifica)
 - Monitoraggio e logging centralizzato (ELK/Prometheus)
 - Validare compliance GDPR (crittografia at-rest/in-transit)

 ## 5. Ordine di esecuzione
 1. Finalizzare schema DB e contratti OpenAPI
 2. Configurare multi-tenancy e servizio Auth (Backend)
 3. Scaffold frontend e autenticazione UI (Frontend)
 4. Servizi CRUD Appuntamenti e UI corrispondente
 5. Servizi Cartelle Cliniche e UI corrispondente
 6. Integrazione voce (Backend + Integration) e UI placeholder
 7. Notifiche e Promemoria (Backend e Frontend)
 8. Dashboard e report base
 9. Testing end-to-end e correzioni
 10. Preparazione al lancio (documentazione e training)

 ## 6. Criteri di accettazione
 - Registrazione e login isolati per tenant funzionanti
 - Creazione/modifica/cancellazione appuntamenti via UI e API
 - Visualizzazione e aggiornamento cartella clinica con note
 - Invio corretto di notifiche email/SMS per appuntamenti
 - Trascrizione voce restituita via API da Retell.ai
 - Dashboard mostra dati di disponibilità e KPI base
 - Copertura test end-to-end per flussi critici
 - Rispetto dei contratti OpenAPI per tutti i servizi

 ## 7. Esclusioni dall’MVP
 - Analisi avanzata e reporting complessi
 - Gestione fatturazione e pratiche assicurative
 - Portale paziente con messaggistica diretta
 - Integrazione con gateway di pagamento
 - Funzionalità mobile native
