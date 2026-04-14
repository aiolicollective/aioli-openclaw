# HEARTBEAT.md — Vérifications périodiques

## Statut : DÉSACTIVÉ (Phase 1)

Les heartbeats seront activés en Phase 2.
Ce fichier est prêt pour quand ce sera le cas.

---

## Phase 2 — toutes les 60 minutes :

- [ ] Budget API Claude → si > 80% du plafond : avertir dans `#notifications`
- [ ] Nouvelles fiches créées aujourd'hui → si > 0, résumé à 18h dans `#notifications`
- [ ] Si rien à signaler : silence total

## Phase 2 — hebdomadaire (lundi 9h) :

- [ ] Vérifier releases Ollama, nouveaux modèles Qwen/Gemma → résumé dans `#veille-modeles`
- [ ] Scanner les sources de prospects configurées → résumé dans `#veille-prospects`

## Phase 3 :

- [ ] Emails urgents non lus
- [ ] Nouveaux appels à projets (CNAP, FRAC, fondations)
- [ ] Rappels calendrier
