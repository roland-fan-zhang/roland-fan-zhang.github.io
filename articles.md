---
layout: page
title: work in progress
mermaid: true
---

<div class="mermaid">
graph LR;
    A[Début] --> B{Choix};
    B --> C[Option 1];
    B --> D[Option 2];
    C --> E[Fin];
    D --> E;
</div>

<div class="mermaid">
sequenceDiagram
    Client->>Serveur: GET /api/users
    Serveur->>BDD: SELECT * FROM users
    BDD-->>Serveur: Résultats
    Serveur-->>Client: JSON Response
</div>
