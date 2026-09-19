# Architecture — CivicOS

## Vue système

```mermaid
flowchart TB
 U[Usager] --> WEB[Portail Web / Mobile]
 WEB --> IAM[Identité & contrôle d'accès]
 WEB --> API[API Gateway]
 API --> SVC[Services métier]
 SVC --> DOC[Documents]
 SVC --> NOTIF[Notifications]
 SVC --> PAY[Paiements]
 SVC --> AUDIT[Audit]
 API --> EXT[Services externes]
```

## Principes techniques

- API-first et contrats versionnés.
- PostgreSQL pour les données transactionnelles.
- File/object storage pour les documents avec chiffrement.
- Observabilité et journal d'audit.
- Mode dégradé pour les zones à faible connectivité.
- Permissions minimales et séparation des responsabilités.

## Données sensibles

L'identité, les documents et les journaux nécessitent minimisation, chiffrement, contrôle d'accès et politique de rétention documentée.

## Évolution

Le MVP doit rester modulaire afin que chaque service public puisse intégrer uniquement les briques dont il a besoin.