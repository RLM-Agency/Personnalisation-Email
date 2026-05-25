# Méthodologie de campagne Cold Email — RLM Agency (Mode CSV uniquement)

> ⚡ **VERSION ÉCONOMIQUE** — Aucune recherche internet. Personnalisation basée uniquement sur les données du CSV Apollo.
> Coût estimé : **1 à 3€ pour 2 000 leads** (API génération uniquement).
>
> Ce fichier définit le workflow complet à suivre pour CHAQUE campagne cold email, quel que soit le client.
> Ces instructions sont universelles et s'appliquent à tous les clients.
> Les informations spécifiques au client (services, cible, ton) se trouvent dans son fichier `client_config.md`.
> En cas de conflit entre ce fichier et un `client_config.md`, le `client_config.md` a priorité.

---

## ÉTAPE 1 — Analyse du CSV

- Utilise la bibliothèque Python **Polars** pour lire et analyser le fichier CSV transmis
- Identifie toutes les colonnes disponibles et retiens celles qui sont exploitables pour la personnalisation :
  - Prénom, nom, poste, entreprise
  - Secteur d'activité, taille d'entreprise, localisation
  - Mots-clés de l'entreprise (colonne `Keywords`)
  - Technologies utilisées (colonne `Technologies`)
  - URL LinkedIn et site web

---

## ÉTAPE 2 — Extraction du contexte depuis le CSV

**Pas de recherche internet.** Pour chaque lead, extrais et interprète les données déjà présentes dans le CSV :

1. **L'entreprise** : déduis le secteur, le positionnement et l'offre principale depuis les colonnes `Industry`, `Keywords` et `Website`
2. **Le rôle de la personne** : interprète ce que le poste (`Title`) implique concrètement au quotidien selon le secteur
3. **L'angle de personnalisation** : choisis parmi les mots-clés du CSV ceux qui résonnent le mieux avec le service du client (consulte le `client_config.md`) et construis l'accroche à partir de là
4. **Le "signal CSV"** : identifie dans les mots-clés un élément spécifique et concret (ex: une spécialisation sectorielle rare, une technologie précise, un positionnement géographique, une niche métier) qui servira d'accroche dans l'email 1

> La colonne `Keywords` Apollo contient souvent des dizaines d'informations exploitables. C'est ta principale source de personnalisation.

---

## ÉTAPE 3 — Rédaction des emails

### Séquence et timing

| Email | Envoi |
|-------|-------|
| Email 1 | Immédiat |
| Email 2 | J+3 (si pas de réponse) |
| Email 3 | J+7 (si toujours pas de réponse) |

---

### Règles absolues (valables pour les 3 emails)

- **Maximum 100 mots** par email
- **Formaté avec des sauts de ligne** adaptés à la lecture mobile (pas de gros blocs de texte)
- **Une salutation simple et humaine** (prénom uniquement, jamais "Monsieur/Madame")
- **La première ligne est la plus importante** — elle doit capturer les 1 à 3 premières secondes d'attention. Elle doit être ultra-spécifique à cette personne, directe, et basée sur un élément concret extrait du CSV

**Ne JAMAIS écrire :**
- "J'espère que cet email vous trouve bien"
- "J'ai vu votre profil LinkedIn, impressionnant"
- "J'admire votre travail"
- Toute phrase générique qui pourrait être envoyée à n'importe qui

---

### L'état d'esprit à adopter

> Imagine que tu croises quelqu'un dans un ascenseur qui a une tache sur sa chemise, et que tu as justement un stylo détachant dans ta poche. Tu dis directement : *"J'ai remarqué cette tache, j'ai justement ce qu'il faut."*
> C'est ça le bon email : **direct, pertinent, utile, sans blabla.**

Tout achat B2B repose sur l'un de ces trois leviers. Chaque email doit en activer **au moins un**, de manière spécifique au contexte du lead :

- ⏱ **Gagner du temps**
- 💰 **Économiser de l'argent**
- 📈 **Gagner plus d'argent**

**L'objectif n'est pas d'aller de cold à close.**
On veut aller de **cold à warm** — piquer suffisamment la curiosité pour que le prospect se demande *"comment ont-ils su ça ?"* et qu'il ait envie d'en savoir plus ou qu'il aille se renseigner de lui-même.

---

### Contenu de chaque email

**Email 1 — Premier contact**
- Première ligne : accroche ultra-spécifique basée sur un élément concret extrait du CSV (spécialisation, secteur, niche, technologie, localisation...)
- Corps : relier le contexte du lead au service du client de manière concrète
- Fin : une seule question douce et ouverte (jamais "Réservez", "Cliquez", "Profitez de")

**Email 2 — Relance J+3**
- Référence courte au premier email
- Nouvel angle ou preuve concrète (résultat client, chiffre, cas similaire)
- Question relancée différemment

**Email 3 — Relance J+7**
- Très court (50 mots maximum)
- Dernier contact, porte ouverte pour l'avenir
- Ton léger, sans pression, mémorable positivement

---

## ÉTAPE 4 — Mode pilote (20 premiers leads)

**Commence TOUJOURS par les 20 premiers leads uniquement.**

1. Génère les emails pour ces 20 leads
2. Crée un fichier **Markdown** lisible avec les 20 séquences générées (pour relecture facile sans ouvrir de CSV)
3. **Attends la validation** avant de continuer sur le reste du fichier

---

## ÉTAPE 5 — Format de sortie final (après validation)

Une fois le feu vert donné :

1. Traite l'ensemble des leads du CSV
2. **Ajoute les données enrichies directement dans le CSV source** avec les colonnes suivantes :
   - `contexte_csv` : l'élément du CSV utilisé comme accroche
   - `email_1` : Email de premier contact
   - `email_2` : Relance J+3
   - `email_3` : Relance J+7

3. **Classe le fichier final** dans la structure suivante :
```
Campagnes Client/
└── [Nom du client]/       ← créer le dossier s'il n'existe pas
    └── [NomClient] - [Mois Année].csv
```

---

## ÉTAPE 6 — Création de la campagne dans Instantly

### Vérification de la clé API

Avant toute chose, vérifie que le fichier `.env` à la racine du projet existe et contient une clé API valide (`INSTANTLY_API_KEY`).

**Si le fichier `.env` est absent ou si la clé est manquante**, arrête-toi et affiche ce message à l'utilisateur :

---

> **Clé API Instantly manquante**
>
> Pour créer la campagne automatiquement, j'ai besoin de ta clé API Instantly.
>
> **Comment la trouver :**
> 1. Connecte-toi à ton compte sur [app.instantly.ai](https://app.instantly.ai)
> 2. Va dans **Settings** (icône engrenage en bas à gauche)
> 3. Clique sur **API Keys**
> 4. Copie ta clé (elle commence généralement par `sk_...`)
>
> **Comment me la donner :**
> - Crée un fichier nommé `.env` à la racine du dossier `ColdEmail/`
> - Colle-y ceci en remplaçant par ta vraie clé :
> ```
> INSTANTLY_API_KEY=sk_ta_cle_ici
> ```
> - Dis-moi quand c'est fait, je reprends automatiquement à cette étape.

---

### Création de la campagne

Une fois la clé API confirmée :

1. Utilise l'**Instantly CLI** pour créer la campagne
2. **Nomme la campagne** avec le même nom que le fichier final (`[NomClient] - [Mois Année]`)
3. Charge les leads dans la campagne
4. Charge les séquences d'emails générées
5. **Montre un aperçu complet** avant tout lancement

> ⚠️ **NE JAMAIS lancer la campagne.** Le lancement se fait toujours manuellement par l'utilisateur.
