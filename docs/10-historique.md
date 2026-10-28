# 10. Historique et décisions

## 2026-10-26
- Projet Web Next.js/React avec Supabase et Stripe.
- Upgrade Next.js 14.2.15 → 15.5.28 rapporté.
- Portage partiel de concepts du prototype Vite vers Next.js; le prototype Vite reste distinct.
- Packaging Docker et procédures Windows/WSL2 documentés.
- Résultats historiques : 18/18 tests applicatifs; tests DB documentés d'abord 45/45 puis 47/47 selon le script et le rapport. Ne pas mélanger les deux suites sans vérifier leur portée.

## 2026-10-27
- Projet Supabase test `PLIEE-LIVRE-TEST`, Canada Central.
- Migrations 0001–0005 appliquées selon le rapport; 27 tables, 48 politiques RLS, 30 routines relevées.
- Quatre comptes de test documentés : admin, finance, pro, client.
- API Auth directe réussie dans un contrôle antérieur; E2E navigateur non confirmé.
- Bucket `preuves` absent à la dernière inspection.
- Paiements réels maintenus désactivés.
- Ajustements UI documentés : sections alternées, page À propos, ordre du hero, hub d'applications, liens et laboratoire de démo par rôle.

## 2026-10-28
- Modification de l'action Web préparée pour lire le rôle avec le même client après connexion et restreindre la redirection `suite`.
- TypeScript et 18 tests signalés passés après cette modification; build final et navigateur à revalider.
- Service actif du port 3001 identifié comme prototype HTML/JS; login non authentifié.
- Décision : préserver l'UI mobile et connecter Auth réelle; ne pas présenter la simulation comme backend opérationnel.

## Décisions durables
- Continuer depuis le projet existant, ne pas reconstruire à zéro.
- Ne pas réinitialiser les mots de passe pour contourner un problème de test.
- Ne pas exposer les secrets.
- Ne jamais annoncer un test bloqué comme réussi.
- Ne pas activer les paiements réels avant la recette.
