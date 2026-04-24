 # Piano di Implementazione MVP

 | Fase | Priorità | Deliverable | Dipendenze | Criteri di Completamento |
 |------|----------|-------------|------------|--------------------------|
 | 1. Setup Infrastruttura | Alta | Repository, CI/CD, container base | Nessuna | Pipeline CI verde, container avviato |
 | 2. Autenticazione & RBAC | Alta | Endpoints login/logout, gestione ruoli | Fase 1 | Test unitari sicurezza superati |
 | 3. Multi-tenancy dati | Alta | Configurazione schema/row-based | Fase 2 | Verifica isolamento multi-tenant |
 | 4. CRUD Utenti e Ruoli | Media | API e UI gestione utenti | Fase 2 | UI operativa e test end-to-end |
 | 5. Gestione Pazienti | Media | CRUD pazienti, anagrafica | Fase 3, 4 | Operazioni CRUD testate |
 | 6. Appuntamenti | Media | API e calendario frontend | Fase 5 | Calendario mostra gli appuntamenti |
 | 7. Anamnesi e Visite | Bassa | Schede anamnesi, visite e note | Fase 6 | Salvataggio dati e revisione medico |
 | 8. Integrazione Retell/Twilio | Alta | Prenotazione vocale e webhook | Fase 1, 2 | Chiamate di prova riuscite |
 | 9. Audit Log | Bassa | Log operazioni critiche | Fase 2 | Log creati per CUD |
 | 10. Deployment e Monitoraggio | Media | Ambiente production, monitoraggio | Tutte le fasi | Deployment stabile e monitor attivo |
