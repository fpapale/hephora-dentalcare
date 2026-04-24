<!--
  Backend Design per DentalCare MVP
-->

# Backend Design

## 1. Responsabilità del backend
- Gestione dati persistenti (DB relazionale)
- Autenticazione e autorizzazione multi-tenant
- Logica di business: scheduling, fatturazione, record clinici
- API RESTful per frontend e integrazioni esterne
- Monitoraggio, logging e auditing minimale

## 2. Moduli backend principali
- **Auth**: login, token JWT, gestione ruoli
- **Tenant**: provisioning, isolamento dati
- **Patients**: CRUD profili paziente e anamnesi
- **Providers**: CRUD operatori (dentisti, igienisti)
- **Appointments**: prenotazione, modifica, cancellazione
- **ClinicalRecords**: visite, note, chart dentale
- **Billing**: creazione fatture, pagamenti
- **Audit**: registrazione modifiche critiche

## 3. API principali
| Risorsa       | Endpoint                                  | Metodo | Descrizione                  |
|---------------|-------------------------------------------|--------|------------------------------|
| Auth          | POST /api/auth/login                      | POST   | Ottieni JWT                  |
| Pazienti      | GET/POST/PUT/DELETE /api/patients         | CRUD   | Gestione profili pazienti    |
| Appuntamenti  | GET/POST/PUT    /api/appointments         | CRUD   | Scheduling                   |
| Visite        | GET/POST        /api/appointments/:id/visits    | CRUD   | Record clinici               |
| Fatture       | GET/POST        /api/appointments/:id/invoices  | CRUD   | Gestione fatturazione        |

## 4. Schema dati logico
- **Tenant**(id, name, config)
- **User**(id, tenant_id, email, password_hash, role)
- **Patient**(id, tenant_id, first_name, last_name, dob, contact)
- **Provider**(id, tenant_id, name, specialty)
- **Appointment**(id, tenant_id, patient_id, provider_id, start, end, status)
- **Visit**(id, appointment_id, summary, notes, tooth_chart JSON)
- **Invoice**(id, appointment_id, amount, status, issued_at, paid_at)
- **AuditLog**(id, tenant_id, user_id, entity, entity_id, action, timestamp)

## 5. Strategia multi-tenant
- Schema condiviso con colonna `tenant_id` per ogni entità
- Filtri a livello di query per isolamento dati
- Middleware per validare contesto tenant da token JWT

## 6. Utenti e ruoli
- **SysAdmin**: crea tenant, gestisce configurazioni globali
- **AdminTenant**: gestisce utenti e provider nel tenant
- **Provider**: accesso alle proprie agende e record clinici
- **Staff**: creazione e modifica appuntamenti e pazienti

## 7. Appuntamenti
- Flusso: verifica disponibilità → prenotazione → conferma via email
- Stati: pending, confirmed, cancelled, completed
- Regole: no prenotazioni sovrapposte, policy di cancellazione

## 8. Pazienti
- Profilo: anagrafica, contatti, preferenze
- Associazione anamnesi e visite precedenti
- Campi obbligatori: nome, cognome, data di nascita

## 9. Anamnesi
- Tabella anamnesi con JSON per domande/risposte
- Versioning con timestamped updates
- FK verso Patient

## 10. Visite e note cliniche
- Record associato ad Appointment
- Campi: diagnosi, procedure, note libere, tooth_chart JSON
- Possibilità di link a immagini o file esterni

## 11. Audit minimo
- Log operazioni CRUD critiche (utente, paziente, appuntamento)
- Tabella AuditLog con user, azione, dettagli, timestamp

## 12. Rischi tecnici backend
- Scalabilità DB con crescita dati
- Concorrenza in prenotazioni real-time
- Sicurezza JWT e isolamento tenant
- Evoluzione schema e migrazioni
- Backup e disaster recovery

## 13. Primo piano di implementazione
1. Setup progetto e connessione DB
2. Modelli Tenant + Auth con JWT
3. Entity Patient/Provider + CRUD
4. Scheduling Appointments + regole business
5. ClinicalRecords e AuditLog
6. Billing e Invoice
7. Test end-to-end e documentazione API
