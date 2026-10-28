# 9. Problèmes ouverts et feuille de route

Mise à jour de référence : 2026-10-28. Confirmer les statuts par de nouveaux tests avant de les fermer.

## P0 — Avant de déclarer l'intégration terminée
### Auth Web E2E
**Constat :** API Auth directe passée dans un contrôle antérieur; navigateur a affiché une erreur générique et test avec cookies SSR incomplet. **Action :** tester dans un vrai navigateur, comparer config build/runtime, vérifier profil, cookies et logs expurgés. **Sortie :** quatre rôles réussissent et les accès croisés sont refusés.

### Auth mobile
**Constat :** port 3001 = prototype, login simulé. **Action :** brancher Auth réelle, rôle, session et déconnexion sans changer le design. **Sortie :** tests positifs/négatifs et aucun secret privé dans le code.

### Storage `preuves`
**Constat :** bucket absent à la dernière inspection. **Action :** recontrôler, créer privé si nécessaire, politiques minimales et tests. **Sortie :** accès autorisé uniquement aux identités pertinentes.

### Consentement d'inscription
**Constat :** action utilise un client admin; service-role vide dans un rapport. **Action :** config server-side sécurisée ou refactorisation de moindre privilège. **Sortie :** inscription/consentement testés.

## P1 — Recette métier
- Auditer RLS distante pour profils, commandes, paiements, gains, remboursements et messages.
- Vérifier le seed avant exécution.
- Tester commandes et transitions avec plusieurs rôles.
- Tester finance, paie, redevances et remboursements.
- Tester Stripe en mode test, webhook inclus; paiements réels désactivés.
- Vérifier notifications/RPC.
- Rebuild et test de l'image avec configuration publique actuelle.

## P2 — Qualité produit
- Revalider les éléments notés « à intégrer » : i18n, courriel, Gemini, facturation et autres connecteurs.
- Automatiser les tests E2E dans un runtime navigateur fonctionnel.
- CI typecheck/tests/build et scan de secrets/dépendances.
- Définir et tester sauvegarde/restauration.
- Documenter les contrats API et événements métier.

## Journal des risques
| Risque | État |
|---|---|
| E2E auth navigateur non terminé | ouvert |
| Erreur de connexion Web non diagnostiquée | ouvert |
| Mobile sans Auth réelle | ouvert |
| Bucket Storage `preuves` | à revérifier |
| Service-role pour consentement | à revérifier |
| Stripe non validé | ouvert |
| Build après dernière modification Auth | à revalider |
| Répertoire source Kali sans `.git` à la vérification | versionnement source à traiter séparément |

## Définition de prêt
Ne pas déclarer le produit prêt pour données/utilisateurs réels avant E2E Auth, RLS distante, Storage, flux métier, sauvegarde/restauration, observabilité et sécurité secrets; paiement uniquement après recette Stripe complète.
