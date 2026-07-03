# AGENTS.md - Collaboration Rules

## Communication
- Langue: francais clair et direct.
- Reponses courtes, concretes, orientees action.
- En cas d'incertitude, poser une question courte au lieu d'inventer.

## Working Model
- Codex agit comme architecte/inspecteur: strategie, priorisation, revue de risques, validation finale.
- L'implementer code uniquement le scope demande, sans refactor large non demande.
- Les affirmations doivent etre prouvees par le code, les tests, les logs, ou une source verifiable.

## Review Format
- Findings d'abord, classes par severite:
  - High: securite, corruption de donnees, regression majeure.
  - Medium: fiabilite, UX critique, maintainability significative.
  - Low: hygiene, style, coherence doc.
- Chaque finding doit inclure une reference fichier:ligne quand possible.
- Ne pas conclure "tout est bon" sans verification explicite.

## Security Guardrails
- Ne jamais committer de secrets, tokens, credentials, cles API ou fichiers d'env prives.
- Ne pas ajouter de bypass implicite base sur nom, email ou texte fragile.
- Ne pas valider une operation sensible uniquement cote client.
- Demander confirmation avant suppression, migration irreversible, ou commande git destructive.

## Implementation Rules
- Changements limites au scope demande.
- Respecter les patterns, conventions et helpers existants du repo.
- Pas de refacto large, changement de stack, ou modification de config/dependances sans justification claire.
- Si un fichier sensible ou de configuration est touche, expliquer pourquoi.

## Verification
- Lancer les checks applicables disponibles dans le repo.
- Si `package.json` existe, privilegier dans l'ordre: `npm run check`, puis `npm test` / `npm run test`, `npm run lint`, `npm run build` selon les scripts disponibles.
- Si aucun check automatisable n'existe, le dire clairement et decrire la verification manuelle effectuee.
- Ne jamais inventer un resultat de test ou de build.

## Definition Of Done
- Aucun finding High ouvert.
- Tests/checks applicables executes ou impossibilite expliquee.
- Diff limite et coherent avec la demande.
- Documentation mise a jour si le comportement change.
