# Méthodologie de campagne Cold Email — RLM Agency

> Ce fichier définit le workflow complet à suivre pour CHAQUE campagne cold email, quel que soit le client.
> Ces instructions sont universelles et s'appliquent à tous les clients.
> Les informations spécifiques au client (services, cible, ton) se trouvent dans son fichier `client_config.md`.
> En cas de conflit entre ce fichier et un `client_config.md`, le `client_config.md` a priorité.

---

## ÉTAPE 1 — Analyse du CSV

- Utilise la bibliothèque Python **Polars** pour lire et analyser le fichier CSV transmis
- Le CSV contient pour chaque lead : nom, entreprise, poste, et potentiellement d'autres informations utiles
- Identifie toutes les colonnes disponibles pour les exploiter pendant la recherche et la rédaction

---

## ÉTAPE 2 — Recherche de chaque lead

**Lance des agents de recherche en parallèle en arrière-plan pour maximiser la vitesse.**

Pour chaque lead, tu dois trouver :

1. **L'entreprise** : secteur d'activité, offre principale, positionnement sur le marché
2. **Le rôle de la personne** : ce que son poste implique concrètement au quotidien, ses responsabilités, ses enjeux
3. **Un signal** *(information absente du CSV — à découvrir pendant la recherche)* :
   - Funding récent
   - Nouveau recrutement clé
   - Lancement de produit ou nouvelle offre
   - Expansion géographique ou sectorielle
   - Changement de direction
   - Publication récente, interview, prise de parole publique
   - Tout événement récent et spécifique à cette entreprise ou cette personne

4. **L'angle de personnalisation** : consulte le `client_config.md` du client concerné et détermine comment ses services sont pertinents pour ce lead spécifiquement, en t'appuyant sur ce que tu as découvert

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
- **La première ligne est la plus importante** — elle doit capturer les 1 à 3 premières secondes d'attention. Elle doit être ultra-spécifique à cette personne, directe, et basée sur un fait concret découvert pendant la recherche

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
- Première ligne : accroche ultra-spécifique basée sur le signal ou le contexte découvert
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
   - `signal` : le signal découvert pendant la recherche
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

1. Crée la campagne via `POST /api/v2/campaigns` avec le nom `[NomClient] - [Mois Année]`
2. Configure la séquence d'emails (3 étapes : Email 1 immédiat, Email 2 J+3, Email 3 J+7)
3. Importe les leads via `POST /api/v2/leads/add` avec le mapping ci-dessous
4. **Montre un aperçu complet** avant tout lancement

> ⚠️ **NE JAMAIS lancer la campagne.** Le lancement se fait toujours manuellement par l'utilisateur.

---

### Mapping des champs CSV → Instantly

À chaque import, analyse les colonnes du CSV et applique la correspondance suivante de manière **sémantique** (le nom exact de la colonne peut varier d'un fichier à l'autre) :

| Colonne CSV (ou équivalent) | Champ Instantly | Via API |
|---|---|---|
| First Name | First Name | `first_name` *(natif)* |
| Last Name | Last Name | `last_name` *(natif)* |
| Title / Job Title / Poste | Job Title | `job_title` *(natif)* |
| Company Name | Company Name | `company_name` *(natif)* |
| Email | Email | `email` *(natif, obligatoire)* |
| Website | Website | `website` *(natif)* |
| Person Linkedin Url / LinkedIn | LinkedIn | `custom_variables.linkedin` |
| Company Address / Adresse entreprise | Location | `custom_variables.location` |
| Company City / Ville entreprise | Custom Variable | `custom_variables.company_city` |
| Company State / Région entreprise | Custom Variable | `custom_variables.company_state` |
| Company Country / Pays entreprise | Custom Variable | `custom_variables.company_country` |
| Toutes les autres colonnes | Do not import | — |

> **Note technique :** L'UI Instantly affiche "LinkedIn" et "Location" comme des options nommées lors d'un import CSV manuel. Via l'API v2, ces champs n'existent pas au niveau natif — ils sont envoyés en `custom_variables` avec les clés `linkedin` et `location`, ce qui produit un résultat identique dans Instantly.

**Règles d'interprétation :**
- Si le CSV contient plusieurs colonnes d'adresse (ex. adresse du lead ET adresse de l'entreprise), toujours privilégier l'**adresse de l'entreprise**
- La correspondance est sémantique : `Person Linkedin Url`, `linkedin_url`, `LinkedIn` → même champ
- Si une colonne attendue est absente du CSV, **ne pas bloquer l'import** — continuer avec les champs disponibles

**Après l'import**, si une ou plusieurs variables attendues étaient absentes du CSV, afficher ce message :

> ⚠️ Variables non trouvées dans ce CSV et non importées : `[liste des champs manquants]`
