# CTO Project Alignment

## 1. Stato attuale del progetto
- La piattaforma DentalCare Core è nella fase di definizione dell’MVP:
  - **Product Scope** dettagliato in `docs/product-scope.md`
  - **Domain Model** definito in `docs/domain-model.md`
  - **MVP Architecture** specificata in `docs/mvp-architecture.md`
  - **Piano di implementazione** in `docs/implementation-plan.md` è in bozza
  - Configurazioni iniziali di CI/CD e infrastruttura predisposte in `infra/`

## 2. Architettura MVP già definita
- API Gateway layer con autenticazione JWT
- Microservizi: Auth, Patient, Appointment, Billing, Notification
- Storage: PostgreSQL per dati, Redis per cache e sessioni
- Frontend: SPA React con Material/Chakra UI
- Infrastruttura: container Docker, Kubernetes, GitHub Actions CI/CD

## 3. Rischi principali
1. Dipendenze esterne (provider SMS/Email, gateway pagamenti)
2. Compliance GDPR e sicurezza dati sensibili
3. Scalabilità delle code di notifica e dei servizi
4. Allineamento del team su contratti API e versioning
5. Tempi di delivery vs qualità del codice

## 4. Prossimi 5 passi consigliati
1. Finalizzare schema DB e contratti OpenAPI
2. Implementare e testare il servizio Auth (incl. ruoli)
3. Configurare l’ambiente Kubernetes di staging
4. Scaffold del frontend React con login e dashboard
5. Scrivere test end-to-end per flusso login→prenotazione

## 5. Collegamento a GitHub
Il workspace locale è collegato al repository `git@github.com:fpapale/hephora-dentalcare.git` e pronto per commit e push.
