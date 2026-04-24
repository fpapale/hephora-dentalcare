# Design del Backend

Questo documento riallinea il design del backend alle specifiche fondative definite nei seguenti documenti di progetto:
- `docs/product-scope.md`
- `docs/domain-model.md`
- `docs/mvp-architecture.md`
- `docs/implementation-plan.md`
- `docs/architecture.md`
- `docs/delivery-backlog.md`

## 1. Responsabilità del backend
- Gestione dei dati persistenti in database relazionali
- Autenticazione e autorizzazione multi-tenant
- Logica di business per appuntamenti, fatturazione e scheda clinica
- API RESTful per interfacce frontend e integrazioni esterne
- Monitoraggio, logging e audit minimo delle operazioni critiche

## 2. Moduli backend principali
- **Auth Service**: login, gestione JWT, ruoli e permessi
- **Tenant Service**: provisioning tenant e isolamento dati
- **Patients Service**: CRUD profili pazienti e anamnesi
- **Providers Service**: CRUD operatori (dentisti, igienisti)
- **Appointments Service**: creazione, modifica e cancellazione appuntamenti
- **ClinicalRecords Service**: gestione scheda clinica e materiali
- **Billing Service**: emissione fatture, pagamenti e richieste assicurative
- **Audit Service**: registrazione e conservazione di log critici

## 3. Modello dati logico
Lo schema dei dati, in linea con `docs/domain-model.md`, include le seguenti entità principali:
- **Tenant**(id, nome, configurazione)
- **User**(id, tenant_id, email, password_hash, ruolo)
- **Patient**(id, tenant_id, nome, cognome, data_nascita, contatti)
- **Provider**(id, tenant_id, nome, specializzazione)
- **Appointment**(id, tenant_id, patient_id, provider_id, start, end, stato)
- **Visit**(id, appointment_id, riepilogo, note, tooth_chart JSON)
- **Invoice**(id, appointment_id, importo, stato, issued_at, paid_at)
- **Claim**(id, invoice_id, dettagli_assicurazione, stato)
- **AuditLog**(id, tenant_id, user_id, entita, entita_id, azione, timestamp)

## 4. Strategia multi-tenant
- Utilizzo di uno schema condiviso con colonna `tenant_id` per ogni tabella
- Filtri a livello di query per garantire l’isolamento dei dati
- Middleware che estrae il contesto tenant dal token JWT

## 5. Autenticazione e autorizzazioni
- Flusso OAuth2 per autenticazione e rilascio token JWT via `/api/auth/login`
- Validazione token JWT ad ogni richiesta
- Controllo accesso basato su ruoli: SysAdmin, AdminTenant, Operatore

## 6. API principali
| Risorsa            | Endpoint                                    | Metodo        | Descrizione                                 |
|--------------------|---------------------------------------------|---------------|---------------------------------------------|
| Auth               | `POST /api/auth/login`                      | POST          | Richiesta JWT                               |
| Pazienti           | `GET/POST/PUT/DELETE /api/patients`         | CRUD          | Gestione profili pazienti                   |
| Appuntamenti       | `GET/POST/PUT/DELETE /api/appointments`     | CRUD          | Gestione appuntamenti                       |
| Visite             | `GET/POST /api/appointments/{id}/visits`    | CRUD          | Gestione visite e note cliniche             |
| Fatture            | `GET/POST /api/appointments/{id}/invoices`  | CRUD          | Emissione fatture e gestione pagamenti      |

## 7. Gestione appuntamenti
- Stato: prenotato, confermato, annullato
- Validazioni di disponibilità orari e risorse
- Possibilità di invio promemoria automatici

## 8. Gestione pazienti
- Anagrafica completa con dati demografici e contatti
- Archiviazione anamnesi e allergie
- Validazione integrità e completezza dei dati

## 9. Gestione scheda clinica
- Registrazione dettagliata di procedure e materiali
- Chart dentale in formato JSON
- Collegamento a visite e appuntamenti

## 10. Gestione anamnesi
- Storico medico e allergie del paziente
- Annotazioni su condizioni croniche
- Collegamento ad entità `Visit` e referto clinico

## 11. Gestione visite e note cliniche
- Creazione e aggiornamento di record di visita
- Inserimento di note, diagnosi e raccomandazioni
- Generazione report sintetici per il paziente

## 12. Data Access Layer
- Pattern Repository con ORM (TypeORM/Sequelize)
- Livello di astrazione per query e transazioni PostgreSQL
- Migrazioni schema definite in `docs/domain-model.md`

## 13. Audit minimo
- Registrazione di modifiche critiche tramite `AuditLog`
- Memorizzazione di utente, azione e timestamp
- Conservazione per requisiti di compliance

## 14. Integrazione backend con Retell.ai e Twilio
- Event Bus (RabbitMQ) per orchestrazione eventi
- Invio SMS/email via Twilio per promemoria
- Elaborazione conversazioni e sintesi vocale via Retell.ai

## 15. Rischi tecnici
- Complessità nella gestione multi-tenant e migrazioni schema
- Latenza ed eventual consistency del bus di eventi
- Disponibilità e tassi di errore delle integrazioni esterne
- Gestione e protezione di dati sensibili (GDPR)

## 16. Piano di implementazione backend
Basato su `docs/implementation-plan.md`:
| Fase | Componenti                   | Deliverables                                |
|------|------------------------------|---------------------------------------------|
| 1    | Core Service e schema DB     | Endpoint CRUD per pazienti e appuntamenti  |
| 2    | Billing Service              | API fatturazione e pagamenti                |
| 3    | Notification & integrazioni  | Reminder automatici (Twilio/Retell.ai)      |
| 4    | Auth Service                 | Endpoint login e controllo ruoli            |
