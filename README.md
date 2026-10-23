``` mermaid
---
title: MCD Panier Fermier
---
erDiagram
    Client {
        int id PK
        string nom
        string email
        string ville
        string date_inscription
    }

    Producteur {
        int id PK
        string nom
        string ville
        string specialite
    }

    Produit {
        int id PK
        string nom
        float prix_unitaire
        int stock
        int producteur_id FK
    }

    Commande {
        int id PK
        int client_id FK
        string date_commande
        string statut
    }

    Ligne_commande {
        int commande_id PK,FK
        int produit_id PK,FK
        int quantite
    }

    Client ||--o{ Commande : "passe"
    Producteur ||--o{ Produit : "fournit"
    Commande ||--|{ Ligne_commande : "contient"
    Produit ||--o{ Ligne_commande : "figure_dans"
```