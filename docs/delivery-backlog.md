# Delivery Backlog MVP

## Epiche MVP
- **User Management**  
  - Registrazione, autenticazione e profilazione dei pazienti  
- **Appointment Booking**  
  - Programmazione, visualizzazione e modifica degli appuntamenti  
- **Clinical Record Management**  
  - Creazione, aggiornamento e consultazione delle cartelle cliniche  
- **Notifications & Alerts**  
  - Promemoria via email e SMS per appuntamenti e follow-up  
- **Integration Layer**  
  - Connessione con sistemi esterni: Payment Gateway, CRM, servizi di notifica

## Task per Backend Lead
1. **Schema dati**  
   Progettare e versionare il modello dati (visti in `docs/domain-model.md`).  
2. **Auth Service**  
   Implementare autenticazione JWT e OAuth2 (allineato a `docs/cto-project-alignment.md`).  
3. **API Pazienti & Cliniche**  
   Endpoint CRUD per pazienti, cartelle, note cliniche (`docs/implementation-plan.md`).  
4. **API Appuntamenti**  
   Endpoint per creare, leggere, aggiornare e cancellare appuntamenti.  
5. **Servizi Notifiche**  
   Microservizio per invio email/SMS (configurazione su `docs/mvp-architecture.md`).  
6. **Middleware di integrazione**  
   Adattatori per Payment Gateway e CRM esterni (`docs/architecture.md`).

## Task per Frontend Lead
1. **Wireframe & UI Kit**  
   Mockup di tutte le schermate chiave (Product Scope).  
2. **Login & Profilo**  
   Pagine di registrazione, login e gestione profilo utente.  
3. **Dashboard Appuntamenti**  
   Calendario interattivo e lista prenotazioni.  
4. **Cartella Clinica**  
   Visualizzazione e modifica dei dati clinici.  
5. **Notifiche in-app**  
   Popup e banner per alert e promemoria.  
6. **Integrazione API**  
   Chiamate REST ai servizi backend, gestione errori e loading.

## Task per Integration Lead
1. **Autenticazione tra moduli**  
   Validazione token e propagazione credenziali.  
2. **Payment Gateway**  
   Setup sandbox e integrazione flusso di pagamento (CTO Alignment).  
3. **CRM Esterno**  
   Sincronizzazione dati pazienti e appuntamenti.  
4. **Orchestrazione Flussi**  
   Definizione processi end-to-end con microservizi.  
5. **Test E2E**  
   Scenario booking completo con tutte le integrazioni.

## Ordine di esecuzione
1. Schema dati & wireframe UI  
2. Auth Service + UI autenticazione  
3. API Appointment + UI calendario  
4. API Cliniche + UI cartella clinica  
5. Servizi notifiche + UI alerts  
6. Middleware integrazioni esterne  
7. Test e QA end-to-end

## Dipendenze
- Database schema → API core  
- Auth Service → UI autenticazione  
- API Appointment → UI calendario  
- Payment Gateway → Conferma booking  
- CRM sync → Reportistica futura

## Criteri di accettazione
- Test automatici ≥ 90% coverage sui servizi core  
- UI responsive e compatibile con Chrome/Firefox/Safari  
- End-to-end booking flow documentato e verificato  
- Notifiche inviate in max 5 minuti dallo scheduler  
- Integrazioni stub-based presenti per demo

## Esclusioni dall’MVP
- Report avanzati e analytics  
- Portale admin multi-tenant e RBAC  
- Mobile app nativa (solo web responsive)  
- Fatturazione e pagamenti ricorrenti

## Piano operativo per MVP dimostrabile
- **Sprint 1 (2 settimane)**: Schema dati, Auth API + UI  
- **Sprint 2 (2 settimane)**: Booking API + UI calendario  
- **Sprint 3 (2 settimane)**: Clinica API + UI cartella  
- **Sprint 4 (2 settimane)**: Notifiche e integrazioni esterne  
- **Demo interna** e raccolta feedback  
- **Bugfix & polish** per demo cliente
