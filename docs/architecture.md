# Architettura Generale

DentalCare Core Platform adotta un'architettura modulare con i seguenti livelli:

- **Presentazione**: SPA Web (React/Vue) che interagisce con le API backend.
- **API Layer**: Routing, autenticazione, validazione e orchestrazione dei servizi.
- **Business Logic**: Moduli per utenti, pazienti, appuntamenti e integrazioni esterne.
- **Data Access**: ORM per PostgreSQL con supporto multi-tenant.
- **Integrazione Esterna**: Gestione delle chiamate vocali tramite Retell.ai e Twilio.
- **Infrastruttura**: Container Docker, orchestrazione Kubernetes/Compose, CI/CD.

La separazione in moduli facilita scalabilità, manutenzione e sicurezza. Le componenti comunicano via API versionate e, in futuro, tramite code/message bus per processi asincroni. L'uso di JWT e RBAC garantisce isolamento e controllo degli accessi per tenant multipli.
