# 4. Supabase, migrations et rôles

## Projet cible
- Nom : `PLIEE-LIVRE-TEST`
- Référence : `wbkbkygmovuvhagsuixi`
- URL : `https://wbkbkygmovuvhagsuixi.supabase.co`
- Région : Canada Central (`ca-central-1`).

Ces valeurs identifient le projet, elles ne sont pas des secrets.

## Migrations
Fichiers connus : `0001_schema.sql`, `0002_functions.sql`, `0003_rls.sql`, `0004_fix_admin_profile_visibility_and_partial_refunds.sql`, `0005_subscription_orders.sql`; migrations datées ultérieures pour état de lecture des notifications, restriction du RPC et messages de commande. L'ancienne migration souscriptions 0004 a été archivée après résolution du doublon de préfixe.

Le rapport du 27 octobre indique que 0001–0005 ont été poussées et que le journal local/distant concordait. Inspection rapportée : 27 tables, 48 politiques RLS et 30 routines dans `public`. Ces chiffres sont datés; recontrôler le schéma courant.

## Commandes contrôlées
```bash
npx --yes supabase@latest migration list --linked
npx --yes supabase@latest db push --dry-run
# Après revue et confirmation du projet seulement :
npx --yes supabase@latest db push --linked
npx --yes supabase@latest migration list --linked
```
Arrêter si une migration échoue; ne pas marquer manuellement une migration comme appliquée sans traiter la cause. Examiner `supabase/seed.sql` avant de l'exécuter.

## Rôles et destinations
| Rôle | Route d'accueil |
|---|---|
| client | `/client` |
| pro | `/pro` |
| partenaire | `/partenaire` |
| admin | `/gestion` |
| finance | `/gestion/finances` |

Les quatre comptes de test documentés : `test.admin@pliee-livre.test`, `test.finance@pliee-livre.test`, `test.pro@pliee-livre.test`, `test.client@pliee-livre.test`. Les mots de passe ne sont volontairement pas reproduits.

## État d'auth connu
Des appels directs `signInWithPassword` ont réussi pour ces comptes dans un contrôle antérieur. La navigation E2E avec cookies de session n'a pas été validée. Une modification de `src/app/connexion/actions.ts` a été préparée pour lire le rôle via le même client Supabase après login et limiter la redirection `suite`. Ne pas déclarer le problème résolu avant un test navigateur actuel.

## RLS et Storage
Les contrôles doivent couvrir données client/Pro, finances, remboursements, messages et actions admin. Les rapports indiquent que le bucket privé `preuves` était absent à la dernière inspection; recontrôler et définir les politiques minimales avant d'activer les uploads. La simulation DB locale (47 checks) n'est pas une preuve d'audit RLS distant.

## Inscription et consentement
L'action d'inscription est documentée comme utilisant `createAdminClient()` pour écrire les consentements. La service-role key était vide dans un rapport antérieur. Soit la configurer côté serveur de manière sécurisée, soit refactoriser l'opération avec un privilège moindre. Ne jamais exposer cette clé au navigateur.
