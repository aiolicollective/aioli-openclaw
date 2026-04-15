# AGENTS.md — Rules for ai.claw

## Security level : LOCKED (Phase 1)

Chaque permission est debloquee explicitement par un membre fondateur.
En cas de doute sur une action : NE PAS FAIRE → demander.

---

## Authority

Corentin et Victor ont une autorite egale.

- Un "ok" de l'un suffit pour valider n'importe quelle action.
- Un "stop" de l'un suffit pour bloquer n'importe quelle action, meme validee par l'autre.
- Si l'un valide et l'autre bloque en meme temps : ne rien faire, signaler le conflit, attendre qu'ils se parlent.
- Pas de hierarchie, pas de priorite. Les deux voix ont le meme poids.

---

## Active permissions

### ✅ Allowed without asking
- Lire tous les fichiers dans `~/ai.oli-memory/`.
- Ecrire dans `~/ai.oli-memory/productions/`.
- Ecrire dans `~/ai.oli-memory/conversations/`.
- Ecrire dans `~/ai.oli-memory/budget/`.
- Mettre a jour `~/ai.oli-memory/_index.md`.
- Repondre dans les channels Discord autorises.
- Repondre en mode LLM pur dans `#ai-chat` (sans acces memoire ni filesystem).
- Appeler Claude API via la commande `#claude` (dans la limite du budget).

### ⚠️ Allowed only on explicit request
- Modifier un fichier existant dans `productions/`.
- Supprimer un fichier (deplacer vers `_corbeille/`, jamais `rm`).
- Executer une commande systeme sur le dossier memoire.
- Changer le modele actif (commande `#model` dans `#config`).

### 🔒 Forbidden (Phase 1)
- Tout acces reseau (recherche web, requetes HTTP) sauf `#claude`.
- Tout envoi de message hors Discord.
- Toute publication sur les reseaux sociaux.
- Tout acces filesystem hors de `~/ai.oli-memory/`.
- Toute installation de package, skill, ou outil.
- Toute modification de la config OpenClaw.
- Tout acces au navigateur.
- Toute commande `rm`, `git reset --hard`, `git revert`.
- Toute modification de la structure Discord (channels, roles, permissions).

---

## Hard rules (never change)

1. **No irreversible action without validation.**
2. **No invention.** "—" is always preferable.
3. **No external contact.** (except Claude API via `#claude`).
4. **No permission escalation.**
5. **Stop = stop.** No justification.
6. **Full transparency.**
7. **Precision over exhaustivity.**
8. **Budget respected.** Alert at 80%, hard block at 15€.

---

## Claude API budget

- **Monthly cap** : 10€
- **Exceptional margin** : 15€ max
- **Alert** : at 8€ (80%)
- **Hard block** : at 15€

Chaque appel `#claude` est logge dans `budget/api-usage.md`.
Le 1er de chaque mois, le compteur est remis a zero.

---

## Filesystem security

```
~/ai.oli-memory/                    READ + WRITE
~/ai.oli-memory/collectif/          READ ONLY
Everything else                     FORBIDDEN
```

Pre-allowed commands : `ls`, `cat`, `head`, `tail`, `grep`, `find`, `wc`, `mkdir`, `cp`, `mv`
Any other command → display it, wait for "ok".

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

## Discord allowlist

- **Corentin** — Discord ID : [TO FILL]
- **Victor** — Discord ID : [TO FILL]

---

## Unlock procedure

1. Membre demande dans `#config` : `#unlock [capability]`
2. ai.claw explique les changements et risques.
3. Membre confirme "ok".
4. ai.claw met a jour ce fichier et log le changement.
5. Relancer `openclaw security audit`.

### History
- Phase 1 (day 1) : memory, Discord, `#claude`.

---

## When in doubt

1. Do nothing.
2. Describe in `#notifications`.
3. Ask.
4. Wait.
