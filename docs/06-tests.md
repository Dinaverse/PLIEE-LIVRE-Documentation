# 6. Tests, preuves et critères de recette

## Résultats consignés
| Contrôle | Résultat historique | Limite |
|---|---|---|
| TypeScript | passé dans rapports antérieurs | relancer après les derniers changements |
| `npm test` | 18/18 | tests de domaine locaux |
| `npm run test:db` | 47/47 | simulation locale, pas audit distant |
| Build | compilé et pages générées; build antérieur noté réussi | recapturer le code de sortie après dernière modification |
| Routes publiques | `/`, `/connexion` en HTTP 200 | disponibilité seulement |
| Routes protégées anonymes | redirections 307 observées | n'évalue pas la session authentifiée |
| API Auth directe | 4 comptes testés en contrôle antérieur | ne prouve pas les cookies SSR ni le navigateur |
| E2E Auth navigateur | non confirmé | banc d'essai antérieur bloqué |
| Mobile 3001 | prototype servi | login simulé |
| Stripe | non validé | paiements réels désactivés |

## Ordre de recette
1. Vérifier diff et secrets.
2. Typecheck, tests de domaine, simulateur DB, build.
3. Routes publiques et routes protégées anonymes.
4. Test navigateur réel pour admin, finance, Pro et client.
5. Tests négatifs croisés entre rôles.
6. RLS distante, Storage, commandes et transitions.
7. Fonctions financières et remboursements.
8. Stripe en mode test, signature webhook et idempotence.
9. Rejouer les tests sur l'image réellement déployée.
10. Enregistrer environnement, commit/build, scénario, résultat, preuve expurgée et limites.

## Matrice négative minimale
- Anonyme → route protégée : refus/redirection.
- Client → commandes d'un autre client : refus.
- Pro → mission non assignée : refus.
- Finance → écran/action admin : refus.
- Client/Pro → gestion/finance : refus.
- Profil manquant ou rôle inconnu : refus sans privilège par défaut.
- Session expirée/déconnexion : accès protégé refusé.
- Fichier de preuve hors périmètre : lecture refusée.
- Webhook invalide/rejoué : rejet ou traitement idempotent.

## Politique de preuve
Un test bloqué n'est pas un échec fonctionnel prouvé, mais ce n'est pas un succès. Une réponse Auth directe ne prouve pas la session navigateur. La simulation locale n'établit pas l'état de la base distante.
