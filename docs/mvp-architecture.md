# Architettura MVP

## Frontend
- Single Page Application (React o Vue.js) con routing client-side.
- Autenticazione via JWT e gestione token.
- Interfaccia per CRUD, calendario e moduli clinici.

## Backend
- API RESTful in Node.js/Express o Python/FastAPI.
- Autenticazione e autorizzazioni basate su JWT e RBAC.
- Gestione multi-tenancy a livello di schema o row-based.

## Database
- PostgreSQL con schema separato per tenant o colonna `tenant_id`.
- Migrazioni gestite da ORM (TypeORM, Sequelize o Alembic).

## Multi-tenancy
- Isolamento dati: schema-based o row-based.
- Middleware per identificare tenant da JWT o header HTTP.

## API
- Endpoint versionati (`/api/v1/...`).
- Validazione payload con JSON Schema o Pydantic.

## Autenticazione e Autorizzazioni
- JWT per autenticazione stateless.
- RBAC per controllo accessi granulari.

## Integrazione Retell.ai + Twilio
- Modulo dedicato per orchestrare chiamate vocali.
- Webhook per eventi e aggiornamento dello stato prenotazione.

## Logging
- Log centralizzati (winston, bunyan o loguru).
- Audit log per operazioni sensibili.

## Deployment MVP
- Container Docker per frontend, backend e worker.
- Orchestrazione con Kubernetes o Docker Compose.
- Ambiente staging e production separate.
