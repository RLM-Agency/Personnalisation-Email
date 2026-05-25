# Méthodologie de rédaction des emails — RLM Agency

## Objectif
Ce fichier définit les règles universelles de rédaction applicables à TOUTES les campagnes cold email, quel que soit le client. Ces instructions doivent toujours être respectées.

---

## Structure des 3 emails par lead

### Email 1 — Premier contact
- **Objectif** : capter l'attention, créer une connexion personnelle, susciter la curiosité
- **Longueur** : 80–120 mots maximum
- **Structure** :
  1. Accroche personnalisée (fait sur l'entreprise, le secteur, ou le poste du lead)
  2. Une phrase qui relie l'accroche au service/produit du client
  3. Proposition de valeur en 1–2 phrases (résultat concret, pas de jargon)
  4. Call to action doux (ex: "Est-ce que ça vous parlerait d'en discuter 15 min ?")
- **Ne jamais faire** : commencer par "Je m'appelle...", pitcher immédiatement, être trop formel

### Email 2 — Relance J+3 (si pas de réponse)
- **Objectif** : relancer sans paraître insistant, apporter une valeur supplémentaire
- **Longueur** : 50–70 mots maximum
- **Structure** :
  1. Référence courte au premier mail (1 phrase)
  2. Angle différent ou preuve sociale (ex: résultat client, stat, insight)
  3. Call to action doux renouvelé
- **Ton** : décontracté, humain, pas de pression

### Email 3 — Relance J+7 (si toujours pas de réponse)
- **Objectif** : dernier contact, laisser une bonne impression, ouvrir une porte future
- **Longueur** : 30–50 mots maximum
- **Structure** :
  1. Dernière relance très courte
  2. Phrase de sortie positive (ex: "Je ne veux pas être intrusif...")
  3. Call to action minimal (ex: "Un simple oui/non suffit !")
- **Ton** : léger, sans pression, mémorable positivement

---

## Règles générales de rédaction

### Personnalisation
- Toujours utiliser le **prénom** du lead (jamais "Monsieur/Madame")
- Mentionner au moins **1 élément spécifique** au lead ou à son entreprise dans l'email 1
- Adapter le vocabulaire au **secteur d'activité** du lead

### Ton et style
- Écrire comme si on écrivait à **un ami professionnel**, pas à un inconnu
- Phrases **courtes** (15 mots max par phrase)
- Pas de majuscules inutiles, pas d'exclamations excessives
- Éviter le jargon marketing ("synergies", "solution innovante", "best-in-class"...)
- Pas d'emojis dans les emails B2B

### Call to action
- **Un seul** call to action par email
- Formulé comme une **question ouverte et sans pression**
- Jamais : "Cliquez ici", "Réservez maintenant", "Profitez de notre offre"

---

## Format de sortie CSV

Pour chaque lead, générer les colonnes suivantes :
- `email_1_A` : Version A de l'email 1
- `email_1_B` : Version B de l'email 1 (angle différent)
- `email_2` : Relance J+3
- `email_3` : Relance J+7

Les emails doivent être en **texte brut**, sans HTML, sans mise en forme markdown.

---

## Notes importantes
- Ces règles s'appliquent à TOUS les clients
- Les spécificités de chaque client sont dans leur fichier `client_config.md`
- En cas de conflit entre ce fichier et un `client_config.md`, le `client_config.md` a priorité
