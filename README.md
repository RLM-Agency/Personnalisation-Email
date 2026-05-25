# Personnalisation Email — RLM Agency

Système de génération d'emails cold email personnalisés par IA.

---

## Comment utiliser ce projet

### Pour une nouvelle campagne

1. Ouvre Cursor et charge ce dossier
2. Passe en mode **Agent**
3. Envoie ce message :

```
Génère les emails pour [NOM CLIENT], voici le CSV : C:\ColdEmail\clients\[NOM CLIENT]\[fichier].csv
```

L'IA lit automatiquement :
- Les règles globales (`_GLOBAL/email_methodology.md`)
- La fiche client (`clients/[NOM CLIENT]/client_config.md`)
- Le fichier CSV des leads

### Pour un nouveau client

1. Copier le dossier `clients/_TEMPLATE`
2. Le renommer avec le nom du client
3. Remplir `client_config.md`
4. Déposer les fichiers CSV dans le dossier

---

## Structure du projet

```
ColdEmail/
├── _GLOBAL/
│   └── email_methodology.md     ← Règles universelles de rédaction
├── clients/
│   ├── _TEMPLATE/               ← Modèle à copier pour chaque client
│   │   └── client_config.md
│   └── [NomClient]/
│       ├── client_config.md     ← Fiche client
│       └── [leads].csv          ← Fichier de leads (non versionné)
├── .gitignore
└── README.md
```

---

## Sécurité

- Les fichiers CSV (leads) ne sont **pas** synchronisés sur GitHub (données personnelles)
- Les clés API doivent être stockées dans un fichier `.env` local (jamais sur GitHub)
- Ce dépôt est **privé**

---

## Colonnes générées dans le CSV de sortie

| Colonne | Description |
|---------|-------------|
| `email_1_A` | Version A de l'email de premier contact |
| `email_1_B` | Version B de l'email de premier contact |
| `email_2` | Relance J+3 |
| `email_3` | Relance J+7 |
