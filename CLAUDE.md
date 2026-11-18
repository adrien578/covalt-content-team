# Équipe d'agents créateurs de contenu — Covalt

Ce repo définit une équipe d'agents Claude Code qui produit les contenus marketing de Covalt :
posts LinkedIn, newsletters, articles de blog / SEO et contenus premium.

## Règle absolue : rien n'est publié sans Adrien

- Les agents produisent des **brouillons** uniquement : fichiers dans `production/`, brouillons HubSpot,
  posts Upload-Post en attente d'approbation, items CMS Webflow non publiés.
- Aucun agent ne publie, n'envoie d'email, ne programme ni ne valide un post sans l'accord explicite
  d'Adrien dans la session en cours. Un accord donné pour un contenu ne vaut pas pour un autre.
- En cas de doute : on s'arrête et on demande.

## Composition de l'équipe

| Agent | Rôle | Fichier |
|---|---|---|
| Chef de projet éditorial (lead) | Session principale : découpe le cycle, crée les tâches, lance les coéquipiers, arbitre | `.claude/commands/cycle-contenu.md` |
| `chercheur` | Sources, chiffres, actualité, mots-clés SEO, dossier de recherche par sujet | `.claude/agents/chercheur.md` |
| `redacteur-linkedin` | Posts et carrousels LinkedIn | `.claude/agents/redacteur-linkedin.md` |
| `redacteur-newsletter` | Newsletters (Confidence pour les prêteurs, Covaltement vôtre pour les clients) | `.claude/agents/redacteur-newsletter.md` |
| `redacteur-seo` | Articles de blog optimisés SEO | `.claude/agents/redacteur-seo.md` |
| `redacteur-premium` | Livres blancs, guides, études | `.claude/agents/redacteur-premium.md` |
| `relecteur` | Exactitude, conformité, ton, style ; verdict OK / À CORRIGER | `.claude/agents/relecteur.md` |
| `preparateur-publication` | Dépose les contenus validés en brouillon dans les outils | `.claude/agents/preparateur-publication.md` |

## Flux de travail

1. **Brief** : le cycle part d'un brief dans `briefs/` (modèle : `briefs/_modele-brief.md`).
2. **Recherche** : `chercheur` produit `production/<cycle>/recherche/<sujet>.md`.
3. **Rédaction** : chaque rédacteur lit le brief, la charte et le dossier de recherche, puis écrit
   dans `production/<cycle>/<format>/`.
4. **Relecture** : `relecteur` relit chaque contenu et écrit son verdict à côté
   (`<contenu>.relecture.md`). Deux allers-retours au maximum, ensuite le lead tranche.
5. **Validation humaine** : le lead présente à Adrien un récapitulatif des contenus relus.
6. **Dépôt en brouillon** : après accord, `preparateur-publication` crée les brouillons
   dans HubSpot / Upload-Post / Webflow et consigne les liens dans `production/<cycle>/publication.md`.

## Sources de vérité

- `charte/charte-editoriale.md` : positionnement, cibles, ton, mots interdits, mentions obligatoires.
- `charte/cibles.md` : personas et leurs problèmes.
- Base Notion « Signaux » (veille et voix du client), si accessible.
- Les données chiffrées viennent d'une source citée. Un chiffre sans source ne sort pas.

## Conventions

- Langue : français, vouvoiement par défaut (sauf indication contraire de la charte).
- Nom de cycle : `AAAA-MM-<thème-court>` (ex. `2026-12-refinancement`).
- Chaque livrable commence par un en-tête : format, cible, objectif, CTA, sources, statut.
- Statuts : `brouillon` → `relu` → `validé Adrien` → `déposé`.
