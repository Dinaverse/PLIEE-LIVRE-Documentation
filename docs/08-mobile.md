# 8. Prototype mobile — port 3001

## État confirmé dans le code inspecté
Source active : `C:\Users\dinac\PLIEE-LIVRE-test\mobile-app\index.html`; serveur minimal `server.js`; écoute sur `127.0.0.1:3001`. Le README du prototype décrit l'absence d'authentification réelle, d'API métier, de base distante et de paiement réel. L'écran indique que les identifiants ne sont pas vérifiés.

## Comportement
Espaces Client/Pro/Gestion simulés, état local/localStorage et chatbot FAQ de démo. Aucune connexion Supabase confirmée. La CSP du serveur est documentée comme limitant `connect-src 'self'`; tout appel direct à Supabase exige une mise à jour ciblée de la CSP.

## Plan d'intégration
1. Inspecter les gestionnaires existants avant de modifier.
2. Garder l'UI et les flux de démo; remplacer uniquement le login simulé.
3. Utiliser l'URL et la clé publique du même projet de test; jamais la service-role key.
4. Authentifier avec Supabase, lire `profiles.role`, refuser profil absent ou rôle inconnu.
5. Mapper les rôles exactement; finance ne doit pas avoir les privilèges admin.
6. Gérer session, déconnexion, rechargement et expiration.
7. Mettre à jour la CSP pour les seuls domaines requis.
8. Tester les refus inter-rôles et les erreurs; ne pas prétendre que les données métier sont réelles tant que les API ne sont pas intégrées.

## Limite
Un contrôle JavaScript peut être contourné. Il ne protège pas des données réelles. Toute opération métier doit être autorisée par le serveur et/ou RLS.

## Critères de sortie
Les quatre comptes se connectent et arrivent au bon espace; accès croisés refusés; aucun secret privé dans le bundle; UI existante préservée; les simulations sont identifiées comme telles.
## Captures d’écran du prototype

La galerie illustrée des écrans est disponible dans [Galerie visuelle — prototype mobile](11-galerie-prototype.md). Elle comprend les parcours de connexion, Client, Pro, Gestion et le chatbot. Les captures sont statiques et issues de données de démonstration; elles ne prouvent pas une intégration de production.
