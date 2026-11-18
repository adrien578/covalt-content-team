# Covalt — équipe d'agents créateurs de contenu

Une équipe d'agents Claude Code qui produit, à partir d'un brief, les posts LinkedIn, newsletters,
articles de blog / SEO et contenus premium de Covalt, jusqu'au dépôt en brouillon dans les outils.
**Rien n'est publié sans la validation d'Adrien.**

## L'équipe

```
                    Chef de projet éditorial (lead, /cycle-contenu)
                                     │
             ┌──────────────────────┼─────────────────────────┐
         chercheur          rédacteurs (×4)                relecteur
      dossier sourcé  ──▶  linkedin · newsletter  ──▶  verdict OK / À CORRIGER
                           seo · premium                       │
                                                               ▼
                                              validation d'Adrien (humaine)
                                                               │
                                                               ▼
                                                  preparateur-publication
                                          brouillons HubSpot · Upload-Post · Webflow
```

Les définitions sont dans `.claude/agents/`, le déroulé du cycle dans
`.claude/commands/cycle-contenu.md`, les règles communes dans `CLAUDE.md`.

## Démarrage

1. **Compléter la charte** : `charte/charte-editoriale.md` et `charte/cibles.md`.
   C'est l'étape qui a le plus d'effet sur la qualité.
2. **Écrire un brief** : copier `briefs/_modele-brief.md` en `briefs/2026-12-<theme>.md`.
3. **Lancer le cycle** dans une session Claude Code ouverte sur ce repo :
   ```
   /cycle-contenu briefs/2026-12-<theme>.md
   ```
4. Le lead planifie, lance les coéquipiers, puis vous présente `production/<cycle>/recap.md`.
   Vous validez contenu par contenu ; seuls les contenus validés sont déposés en brouillon.

## Mode équipe et mode simple

`.claude/settings.json` active les *agent teams* de Claude Code
(`CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1`, fonctionnalité expérimentale) : les coéquipiers
travaillent en parallèle, partagent une liste de tâches et s'envoient des messages
(le relecteur répond directement au rédacteur, par exemple).

Si la fonctionnalité n'est pas disponible dans votre version, les mêmes fichiers marchent
comme **sous-agents** classiques : le lead les appelle un par un. C'est plus lent mais le
résultat est le même.

## Connecteurs utilisés

| Outil | Usage | Agent |
|---|---|---|
| Recherche web | sources, SEO | chercheur, rédacteurs SEO / premium |
| HubSpot | brouillons de newsletters, articles, landing pages | preparateur-publication |
| Upload-Post | posts LinkedIn en attente d'approbation | preparateur-publication |
| Webflow | items CMS non publiés (optionnel) | preparateur-publication |
| Notion (base Signaux) | veille et voix du client (optionnel) | chercheur |

## Structure

```
CLAUDE.md                    règles communes de l'équipe
.claude/settings.json        active les agent teams
.claude/agents/              les 7 coéquipiers
.claude/commands/            /cycle-contenu (le lead)
charte/                      charte éditoriale et personas (à compléter)
briefs/                      un brief par cycle
production/<cycle>/          recherche, contenus, relectures, récap, liens des brouillons
```
