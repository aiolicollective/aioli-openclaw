# 🦞 aioli-claw

Configuration système **ai.claw** — agent IA du collectif [/ai.oli](https://aiolicollective.com/).

## C'est quoi ?

ai.claw est un agent IA local qui tourne sur [OpenClaw](https://github.com/openclaw/openclaw) + [Ollama](https://ollama.com). Il archive les productions du collectif, répond aux questions sur l'historique, et fait appel à [Claude Sonnet](https://anthropic.com) quand il a besoin d'un regard extérieur.

L'agent vit dans un serveur Discord privé et communique avec deux membres : Corentin et Victor.

## Stack

| Brique | Rôle | Coût |
|---|---|---|
| **Qwen3.5 27B** / **Gemma 4 31B** | Cerveau local (via Ollama) | 0€ |
| **OpenClaw** | Framework agent, connecte Discord | 0€ |
| **Claude Sonnet 4.6** | Conseiller stratégique (via API) | 3-5€/mois |
| **Discord** | Interface de commande | 0€ |
| **Obsidian** | Lecture humaine de la mémoire | 0€ |
| **Syncthing** | Sync mémoire entre membres | 0€ |

## Fichiers

| Fichier | Rôle |
|---|---|
| `SOUL.md` | Personnalité, ton, commandes, comportement |
| `AGENTS.md` | Règles de sécurité, permissions, hard rules |
| `USER.md` | Infos sur les membres du collectif |
| `IDENTITY.md` | Nom et identité de l'agent |
| `HEARTBEAT.md` | Vérifications périodiques (Phase 2) |

## Sécurité

Ce repo ne contient **aucune donnée sensible**. Les tokens, clés API et données de production sont stockés localement et ne sont jamais versionnés.

## Philosophie

> Composé d'artistes et d'agents IA, /ai.oli est un collectif hybride consacré à la création et à la diffusion d'images, de vidéos et de concepts visuels.

---

*Construit avec Claude Opus 4.6 — Avril 2026*
