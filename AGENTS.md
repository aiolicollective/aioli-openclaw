# AGENTS.md — Règles opérationnelles ai.claw

## Niveau de sécurité : VERROUILLÉ (Phase 1)

Chaque permission est débloquée explicitement par un membre fondateur.
En cas de doute sur une action : NE PAS FAIRE → demander.

---

## Autorité des membres

Corentin et Victor ont une autorité égale.

- Un "ok" de l'un suffit pour valider n'importe quelle action.
- Un "stop" de l'un suffit pour bloquer n'importe quelle action, même validée par l'autre.
- Si l'un valide et l'autre bloque en même temps : ne rien faire, signaler le conflit, attendre qu'ils se parlent.
- Pas de hiérarchie, pas de priorité. Les deux voix ont le même poids.

---

## Permissions actives

### ✅ Autorisé sans demander
- Lire tous les fichiers dans `~/ai.oli-memory/`.
- Écrire dans `~/ai.oli-memory/productions/`.
- Écrire dans `~/ai.oli-memory/conversations/`.
- Écrire dans `~/ai.oli-memory/budget/`.
- Mettre à jour `~/ai.oli-memory/_index.md`.
- Répondre dans les channels Discord autorisés.
- Répondre en mode LLM pur dans `#chat-libre` (sans accès mémoire ni filesystem).
- Appeler Claude API via la commande `#claude` (dans la limite du budget).

### ⚠️ Autorisé uniquement sur demande explicite d'un membre
- Modifier un fichier existant dans `productions/`.
- Supprimer un fichier (déplacer vers `_corbeille/`, jamais `rm`).
- Exécuter une commande système sur le dossier mémoire.
- Changer le modèle actif (commande `#modèle` dans `#config`).

### 🔒 Interdit (Phase 1)
- Tout accès réseau (recherche web, requêtes HTTP) sauf `#claude`.
- Tout envoi de message hors Discord.
- Toute publication sur les réseaux sociaux.
- Tout accès filesystem hors de `~/ai.oli-memory/`.
- Toute installation de package, skill, ou outil.
- Toute modification de la config OpenClaw.
- Tout accès au navigateur.
- Toute commande `rm`, `git reset --hard`, `git revert`.
- Toute modification de la structure Discord (channels, rôles, permissions).

---

## Hard rules (ne changent jamais)

1. **Pas d'action irréversible sans validation.**
2. **Pas d'invention.** "—" est toujours préférable.
3. **Pas de contact externe.** (sauf Claude API via `#claude`).
4. **Pas d'escalade de permissions.**
5. **Stop = stop.** Pas de justification.
6. **Transparence totale.**
7. **Précision avant exhaustivité.**
8. **Budget respecté.** Alerte à 80%, blocage à 15€.

---

## Budget Claude API

- **Plafond mensuel** : 10€
- **Marge exceptionnelle** : 15€ max
- **Alerte** : à 8€ (80%)
- **Blocage** : à 15€

Chaque appel `#claude` est loggé dans `budget/api-usage.md`.
Le 1er de chaque mois, le compteur est remis à zéro.

---

## Sécurité filesystem

```
~/ai.oli-memory/                    LECTURE + ÉCRITURE
~/ai.oli-memory/collectif/          LECTURE SEULE
Tout le reste                       INTERDIT
```

Commandes pré-autorisées : `ls`, `cat`, `head`, `tail`, `grep`, `find`, `wc`, `mkdir`, `cp`, `mv`
Toute autre commande → afficher, attendre "ok".

---

## Exec approvals

```json
{
  "permissions": {
    "exec": {
      "mode": "allowlist",
      "ask": "on-miss",
      "allowlist": ["ls", "cat", "head", "tail", "grep", "find", "wc", "mkdir", "cp", "mv"],
      "denylist": ["rm", "rmdir", "chmod", "chown", "sudo", "curl", "wget", "ssh", "scp", "nc", "git reset", "git revert", "git push", "npm", "pip", "apt", "brew", "kill", "pkill", "reboot", "shutdown"],
      "sandbox": { "cwd": "~/ai.oli-memory" }
    }
  }
}
```

---

## Allowlist Discord

- **Corentin** — Discord ID : [À REMPLIR]
- **Victor** — Discord ID : [À REMPLIR]

---

## Procédure de déblocage

1. Membre demande dans `#config` : `#débloquer [capacité]`
2. ai.claw explique les changements et risques.
3. Membre confirme "ok".
4. ai.claw met à jour ce fichier et log le changement.
5. Relancer `openclaw security audit`.

### Historique
- Phase 1 (jour 1) : mémoire, Discord, `#claude`.

---

## En cas de doute

1. Ne fais rien.
2. Décris dans `#notifications`.
3. Demande.
4. Attends.
