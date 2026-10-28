# 7. Sécurité et secrets

## Interdits Git
Ne jamais commiter `.env.local`, `.env.production`, mots de passe, service-role key, PAT, clés Stripe, secrets webhook, cookies, bearer/refresh tokens, sauvegardes de comptes, données clients ou photos de preuve.

Une clé publique `NEXT_PUBLIC_*` est conçue pour le client, mais exige des politiques RLS correctes. Le dépôt documentaire ne reproduit pas ces valeurs.

## Contrôle avant publication
```bash
git status --short
git diff --check
git diff --stat
git check-ignore -v .env.local .env.production
```
Inspecter aussi les fichiers déjà suivis et l'historique Git. Si un secret a été commité, supprimer le fichier ne suffit pas : révoquer/renouveler le secret et examiner son usage.

## Contrôles applicatifs
- Moindre privilège pour les rôles et RLS.
- Autorisation dans chaque action serveur sensible, pas seulement dans l'UI.
- Validation des entrées et des transitions d'état.
- Limites d'upload (type, taille, propriétaire, contexte métier).
- Vérification de signature des webhooks et idempotence.
- Messages d'erreur d'auth génériques.
- Logs expurgés des tokens et données personnelles.
- Ne jamais exposer la service-role key côté client.

## Paiements et données
Le rapport d'environnement indique que Stripe secret/webhook étaient absents et que `STRIPE_LIVE_PAYMENTS_ENABLED=false`. Maintenir les paiements réels désactivés jusqu'à validation complète en mode test. Ne pas importer de données clients réelles dans la démo.

## GitHub
Dépôt privé par précaution, accès restreint, MFA recommandé. La confidentialité du dépôt n'autorise pas à y stocker des secrets.
