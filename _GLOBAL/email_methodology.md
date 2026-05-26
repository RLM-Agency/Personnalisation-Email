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

### Création de la ligne d'objet

> L'objectif est d'optimiser pour les **RÉPONSES**, pas pour les ouvertures. Une ligne d'objet qui génère des ouvertures sans réponses est un échec. Cible : dépasser 10% de taux de réponse.

#### Règle fondamentale

La ligne d'objet doit sonner comme quelque chose qu'un collègue écrirait à un autre collègue dans un email interne.

Elle doit passer deux tests :
- **Colleague Test** : est-ce qu'un employé pourrait envoyer cet objet à un collègue en interne sans que ça semble bizarre ? Si oui : valide.
- **So What Test** : un VP occupé peut-il comprendre immédiatement pourquoi il devrait s'en préoccuper ? Si oui : valide.

#### Règles mécaniques obligatoires

**Longueur :**
- Entre 2 et 6 mots (idéal)
- Entre 36 et 50 caractères idéalement
- Minimum absolu : 21 caractères / Maximum absolu : 60 caractères
- Raison : 61% des emails sont ouverts sur mobile. Au-delà de 60 caractères, l'objet est tronqué et le taux de réponse chute de 25% ou plus.

**Capitalisation :**
- Toujours minuscules ou sentence case (première lettre du premier mot en majuscule, reste en minuscules)
- Jamais le Title Case (Each Word Capitalized) : signal marketing
- Jamais les MAJUSCULES : détruit la délivrabilité, augmente les plaintes spam de 50%
- Modèle mental : écrire comme un SMS à un collègue que l'on respecte

**Ton :**
- Neutre, direct, humain
- Zéro jeu de mots, zéro exclamation, zéro emoji
- Zéro buzzwords ("transform", "revolutionize", "game-changing", "incredible opportunity")
- Zéro vague ("our new offer", "something exciting")

#### Les 4 frameworks (par ordre de priorité)

**FRAMEWORK 1 — Le Problème Douloureux** *(Priorité MAXIMALE — taux d'ouverture moyen : 82%)*

Nommer exactement la douleur que le prospect ressent en ce moment. Pas la solution, pas l'offre. Juste leur problème, formulé avec précision chirurgicale, comme si on avait assisté à leurs réunions. Les douleurs génériques sont ignorées, les douleurs ultra-spécifiques à leur rôle/secteur/situation sont ouvertes.

Formule : `[Problème spécifique qu'ils vivent au quotidien]`
Exemples : "not interested" (sales managers), "unverified lead data" (ops managers), "43% of SDRs miss quota"

---

**FRAMEWORK 2 — Le Trigger Event / Référence Directe** *(Priorité HAUTE — boost d'ouverture : +45%, taux de réponse x3)*

Référencer quelque chose de spécifique et récent sur leur entreprise ou activité. Cela transforme un cold email en quelque chose qui ressemble à un email warm. Prendre l'événement et le retourner pour révéler un angle mort ou une conséquence qu'ils n'ont pas encore considérée.

Sources par ordre de priorité : levée de fonds, offre d'emploi active, post LinkedIn récent, lancement de produit, expansion, recrutement massif.

A ne pas faire : "congrats on the funding" (trop évident, ressemble à du spam)
A faire : "funding concerns" (crée de la curiosité)

Formule : `[Référence à l'événement] + [implication/question implicite]`
Exemples : "saw you're hiring three SDRs, quick thought", "funding concerns", "your Q3 expansion"

---

**FRAMEWORK 3 — La Stat ou Résultat Chiffré** *(Priorité HAUTE — taux d'ouverture moyen : 66%, boost avec chiffres : +45%)*

Les chiffres attirent l'attention, surtout quand ils sont liés au secteur ou au rôle. Le chiffre doit représenter soit leur plus grande peur, soit leur plus grand désir. Si le chiffre vient de leurs propres données (site web, rapport annuel), l'utiliser : ça prouve que la recherche a été faite.

A ne pas faire : "500% revenue increase" (trop vague, crie au spam)
A faire : "100% uptime in Q3" (data center managers), "43% of SDRs miss quota" (sales managers)

Formule : `[Chiffre spécifique] + [résultat/contexte lié à leur rôle]`
Exemples : "47 qualified leads in 30 days", "43% of SDRs miss quota"

---

**FRAMEWORK 4 — La Question Courte** *(Priorité MOYENNE — 4 à 6 mots)*

Le cerveau ne peut pas résister à une question sans réponse. La question doit être pertinente et liée à quelque chose de spécifique à leur situation. Ne jamais écrire juste "quick question" sans contexte.

Formule : `[Question de 4-6 mots liée à leur réalité spécifique]`
Exemples : "still struggling with deliverability?", "are you scaling outbound this quarter?"

---

#### Processus de sélection du framework

1. Y a-t-il un événement récent identifiable (funding, offre d'emploi, post LinkedIn, lancement) ? Si oui : considérer Framework 2 en priorité.
2. Y a-t-il un problème douloureux ultra-spécifique identifiable pour ce rôle/secteur ? Si oui : considérer Framework 1 en priorité.
3. Y a-t-il une stat ou un chiffre pertinent pour leur réalité ? Si oui : considérer Framework 3.
4. Sinon : Framework 4.

Règle de priorité : **Problème douloureux > Trigger event > Stat pertinente > Question courte**

Après génération, valider chaque point :
- Entre 2 et 6 mots ?
- Entre 21 et 60 caractères ?
- Minuscules ou sentence case uniquement ?
- Zéro buzzword marketing ?
- Passe le Colleague Test ?
- Passe le So What Test ?
- Centré sur EUX, pas sur l'offre ?

#### Ce qu'il faut absolument éviter

- Tout ce qui ressemble à du marketing : "Transform your business", "Incredible opportunity", "Don't miss out"
- Tout ce qui est trop vague : "Quick question" (sans contexte), "Following up", "Partnership opportunity"
- Tout ce qui semble trop vendeur : "500% ROI", "Triple your revenue"
- Title Case, MAJUSCULES, points d'exclamation, emojis, plus de 60 caractères

#### Format de sortie dans le CSV

Pour chaque lead, ajouter 4 colonnes supplémentaires avec exactement ces noms :

| Colonne | Description |
|---|---|
| `Objet` | La ligne d'objet générée |
| `Framework` | Le framework utilisé (ex. "Framework 1 - Problème Douloureux") |
| `Nombre de mots` | Nombre de mots de l'objet |
| `Nombre de caractères` | Nombre de caractères de l'objet |

---

### Règles absolues (valables pour les 3 emails)

- **Maximum 100 mots** par email
- **Formaté avec des sauts de ligne** adaptés à la lecture mobile (pas de gros blocs de texte)
- **Une salutation simple et humaine** (prénom uniquement, jamais "Monsieur/Madame")
- **La première ligne est la plus importante** — elle doit capturer les 1 à 3 premières secondes d'attention. Elle doit être ultra-spécifique à cette personne, directe, et basée sur un fait concret découvert pendant la recherche
- **Orthographe irréprochable** : l’orthographe doit être absolument parfaite ! Aucune faute ne peut être tolérée. Un mail contenant des fautes est un mail qui ne sera ni lu ni pris au sérieux.

**Ne JAMAIS écrire :**
- "J'espère que cet email vous trouve bien"
- "J'ai vu votre profil LinkedIn, impressionnant"
- "J'admire votre travail"
- Toute phrase générique qui pourrait être envoyée à n'importe qui

**Règles typographiques obligatoires :**
- **Toujours mettre les accents** : à â æ ç é è ê ë î ï ô œ ù û ü ÿ (et leurs majuscules À Â Æ Ç É È Ê Ë Î Ï Ô Œ Ù Û Ü Ÿ). Un email sans accent est un email non professionnel.
- **Ne jamais utiliser le tiret long "—"** pour séparer des bouts de phrase. Ce signe est caractéristique des textes générés par IA et rend les emails non humains. Utiliser une virgule, un point, ou reformuler la phrase.

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
2. **Ajoute les données enrichies directement dans le CSV source** avec exactement ces noms de colonnes :

| Colonne | Description |
|---|---|
| `signal` | Le signal découvert pendant la recherche |
| `email_1` | Email de premier contact |
| `email_2` | Relance J+3 |
| `email_3` | Relance J+7 |
| `Objet` | La ligne d'objet générée |
| `Framework` | Le framework utilisé |
| `Nombre de mots` | Nombre de mots de l'objet |
| `Nombre de caractères` | Nombre de caractères de l'objet |

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

**Si le fichier `.env` est absent ou si la clé est manquante**, demande simplement à l'utilisateur dans le chat :

> J'ai besoin de ta clé API Instantly pour créer la campagne. Tu peux la trouver dans **Settings → API Keys** sur [app.instantly.ai](https://app.instantly.ai). Colle-la ici directement.

Une fois la clé reçue, crée le fichier `.env` à la racine du projet avec le contenu suivant, puis continue :
```
INSTANTLY_API_KEY=la_cle_recue
```

---

### Création de la campagne

Une fois la clé API confirmée :

1. Crée la campagne via `POST /api/v2/campaigns` avec le nom `[NomClient] - [Mois Année]`
2. Configure la séquence d'emails (3 étapes) avec les sujets suivants :
   - Email 1 (immédiat) : sujet = `{{Objet}}`
   - Email 2 (J+3) : sujet = `Re: {{Objet}}`
   - Email 3 (J+7) : sujet = `Re: {{Objet}}`
   > Le `Re:` sur les relances donne l'impression d'une continuation de thread, ce qui augmente les taux d'ouverture. La valeur de `{{Objet}}` est injectée automatiquement depuis la custom variable de chaque lead — aucune colonne supplémentaire n'est nécessaire.
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
| `signal` | Custom Variable | `custom_variables.signal` |
| `email_1` | Custom Variable | `custom_variables.email_1` |
| `email_2` | Custom Variable | `custom_variables.email_2` |
| `email_3` | Custom Variable | `custom_variables.email_3` |
| `Objet` | Custom Variable | `custom_variables.Objet` *(utilisé comme sujet de séquence via `{{Objet}}`)* |
| `Framework` | Custom Variable | `custom_variables.Framework` |
| `Nombre de mots` | Custom Variable | `custom_variables.Nombre de mots` |
| `Nombre de caractères` | Custom Variable | `custom_variables.Nombre de caractères` |
| Toutes les autres colonnes | Do not import | — |

> **Note technique :** L'UI Instantly affiche "LinkedIn" et "Location" comme des options nommées lors d'un import CSV manuel. Via l'API v2, ces champs n'existent pas au niveau natif — ils sont envoyés en `custom_variables` avec les clés `linkedin` et `location`, ce qui produit un résultat identique dans Instantly.

**Règles d'interprétation :**
- Si le CSV contient plusieurs colonnes d'adresse (ex. adresse du lead ET adresse de l'entreprise), toujours privilégier l'**adresse de l'entreprise**
- La correspondance est sémantique : `Person Linkedin Url`, `linkedin_url`, `LinkedIn` → même champ
- Si une colonne attendue est absente du CSV, **ne pas bloquer l'import** — continuer avec les champs disponibles

**Après l'import**, si une ou plusieurs variables attendues étaient absentes du CSV, afficher ce message :

> ⚠️ Variables non trouvées dans ce CSV et non importées : `[liste des champs manquants]`
