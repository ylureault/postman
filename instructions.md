## ✍️ MODE 2 : RÉDACTION D'ARTICLE

### Quand utiliser ce mode
Quand on te demande de "rédiger un article", "transformer une idée en article", "écrire depuis _ideas/"

### Process

1. **Scan `_ideas/`** : Liste les fichiers avec statut "À rédiger"
2. **Lis le STYLE_GUIDE.md** en entier
3. **Choisis LA PREMIÈRE idée non traitée** (ordre numérique)
4. **Rédige l'article complet** selon les specs ci-dessous
5. **Sauvegarde en MARKDOWN** dans `_ready/`
6. **Déplace l'idée** vers `_ideas/_done/`
7. **STOP** (un seul article par session)

### Format de sortie MARKDOWN

Fichier : `_ready/2025-11-09-intelligence-collective-pme-blocages.md`
```markdown
---
title: "Intelligence collective en PME : 3 blocages qui tuent vos projets"
slug: intelligence-collective-pme-3-blocages
meta_description: "Les PME échouent avec l'intelligence collective pour 3 raisons invisibles. Décryptage cash et solution avec la Boussole 4C."
keywords:
  - intelligence collective PME
  - facilitation entreprise
  - décision collective
  - transformation organisationnelle
  - Boussole 4C
category: intelligence-collective
date: 2025-11-09
author: Yoan Lureault
status: draft
---

Ta PME a lancé des ateliers participatifs, des réunions « collaboratives », des post-it partout. Résultat ? Rien. Les décisions traînent, les équipes sont frustrées, et tu te demandes si l'intelligence collective c'est pas du bullshit.

Spoiler : c'est pas du bullshit. Mais tu fais 3 erreurs classiques que personne ne voit.

## Blocage 1 : Le contrôle déguisé

Le dirigeant dit "oui" à l'intelligence collective. Il lance des ateliers, demande l'avis des équipes. Mais au final, c'est toujours lui qui tranche. Seul.

Exemple vécu : PME normande 180 salariés, industrie. Le patron organise 6 mois d'ateliers participatifs. Les équipes bossent, proposent, débattent. Résultat ? Aucune décision prise. Pourquoi ? Le patron attendait LA solution parfaite. Celle qui valide ce qu'il pensait déjà.

L'intelligence collective, c'est pas "demander l'avis puis décider seul". C'est **déléguer la décision au bon niveau**. Si tu gardes le contrôle final, t'as juste fait un brainstorming amélioré. Pas de l'intelligence collective.

## Blocage 2 : L'illusion de la méthode

Post-it + paperboard ≠ intelligence collective.

Les entreprises croient qu'organiser un atelier "participatif" suffit. Tu mets 15 personnes dans une salle, distribue des post-it de couleur, hop, intelligence collective. Non.

Sans cadre structuré, tu obtiens :
- Des idées dans tous les sens
- Pas de priorisation claire
- Des débats sans fin
- Zéro décision concrète

L'intelligence collective, c'est une **méthode**. Pas un événement. Chez Insuffle, on utilise la Boussole 4C : Cap (où on va), Contraintes (ce qui bloque), Capacités (ce qu'on peut faire), Cadence (à quelle vitesse). Simple, clair, actionnable.

Sans méthode, tu fais du théâtre participatif. Avec une méthode, tu transformes vraiment.

## Blocage 3 : Le piège du consensus

"On va décider tous ensemble."

Résultat : personne ne décide. Parce que chercher le consensus à 50 personnes, c'est la paralysie garantie.

L'intelligence collective, c'est pas le consensus. C'est la **décision collective structurée**. Différence ?

- Consensus : tout le monde doit être d'accord → ça traîne, ça bloque
- Décision collective : le groupe décide selon un processus clair → ça avance

En 15 ans, j'ai vu des dizaines d'entreprises se planter là-dessus. Elles confondent "impliquer les équipes" avec "tout le monde doit valider". Résultat : des projets qui traînent 18 mois au lieu de 6.

La solution ? Des règles claires de décision dès le départ. Qui décide quoi. Comment. Et dans quel délai.

## FAQ

**Combien de temps pour mettre en place l'intelligence collective ?**

6 à 18 mois pour ancrer les changements. Pas de miracle en 3 mois. C'est un changement de culture, pas un atelier.

**Intelligence collective vs brainstorming : quelle différence ?**

Le brainstorming génère des idées. L'intelligence collective prend des décisions. L'un est un outil, l'autre est une méthode complète.

**Ça marche dans toutes les PME ?**

Oui, si t'as minimum 20-30 personnes et que le dirigeant accepte de lâcher du contrôle. Si le patron veut juste "consulter pour valider ses idées", ça marchera pas.

## Pour aller plus loin

Si tu veux structurer l'intelligence collective dans ta boîte avec une méthode éprouvée, la formation Insuffle Académie sur la facilitation stratégique te donnera les outils concrets. Pas de théorie, que du terrain. 15 ans d'expérience condensés en méthode actionnnable.

[En savoir plus sur la formation](https://insuffle-academie.fr/formations)
```

**Caractéristiques du format :**

✅ **Front matter YAML** :
- Métadonnées pour WordPress (titre, slug, meta, etc.)
- Compatible plugins SEO (Yoast, RankMath)
- Status: draft (tu décides quand publier)

✅ **Markdown pur** :
- Directement importable WordPress
- Titres avec #, ##
- Gras avec **texte**
- Listes avec - ou 1.
- Liens avec [texte](url)

✅ **Prêt à l'emploi** :
- Tu copies/colles dans WordPress
- Ou tu importes via plugin markdown
- Ou n8n crée le brouillon automatiquement

---

## **WORKFLOW N8N SIMPLIFIÉ**
```
[Schedule Trigger] → Tous les 2 jours (ou webhook manuel)
↓
[FTP/SFTP Read] → Lit _ready/
↓
[IF Node] → Y a-t-il un fichier .md ?
   ├─ NON → Stop
   └─ OUI ↓
[Read File Content]
↓
[Parse Front Matter] → Extrait métadonnées YAML
↓
[Convert Markdown to HTML] (optionnel si WordPress accepte markdown)
↓
[WordPress Node]
  - title: {{frontmatter.title}}
  - content: {{markdown ou html}}
  - status: draft (TU décides de la publication)
  - slug: {{frontmatter.slug}}
  - excerpt: {{frontmatter.meta_description}}
  - categories: [{{frontmatter.category}}]
  - tags: {{frontmatter.keywords}}
↓
[FTP Move File] → _ready/ vers _published/
↓
[Notification] → "✅ Article en brouillon WordPress : [titre]"
```

**Avantages :**
- Article créé en **brouillon** WordPress
- **TU gères le calendrier** éditorial manuellement
- n8n te notifie juste qu'un brouillon est dispo

---

## **CHECKLIST ARTICLE**

Remplace aussi cette section :
```markdown
### Checklist article

Avant de sauvegarder le MARKDOWN, vérifier :

**Front matter :**
- [ ] title (50-60 chars)
- [ ] slug (3-5 mots, tirets)
- [ ] meta_description (140-155 chars)
- [ ] keywords (5 max)
- [ ] category (intelligible)
- [ ] status: draft

**Contenu :**
- [ ] 800-1200 mots
- [ ] Mot-clé principal dans premier paragraphe
- [ ] 3 H2 minimum (## en markdown)
- [ ] Au moins 1 exemple terrain anonymisé
- [ ] FAQ (2-3 questions)
- [ ] CTA naturel en fin d'article

**Style Yoan :**
- [ ] Phrases < 25 mots
- [ ] Zéro jargon corporate
- [ ] Ton cash mais pas agressif
- [ ] Actionnable
- [ ] "Je dirais ça en séminaire ?"

**Markdown propre :**
- [ ] # pour H1 (jamais utilisé, déjà dans title)
- [ ] ## pour H2
- [ ] **gras** pour emphase
- [ ] [liens](url) pour CTA
- [ ] Listes avec - ou 1.
```

---

**Résumé des modifs :**

1. ✅ Format **markdown pur** avec front matter YAML
2. ✅ Fichier `.md` dans `_ready/`
3. ✅ n8n crée brouillon WordPress (status: draft)
4. ✅ **Toi tu gères le calendrier** éditorial manuellement dans WordPress

**Je push les modifs dans INSTRUCTIONS.md ?**