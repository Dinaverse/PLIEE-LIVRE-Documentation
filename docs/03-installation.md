# 3. Installation et développement

## Prérequis
Node.js/npm compatibles avec `package.json`; accès au code source; variables d'environnement de test; environnement DB requis pour `supabase/tests/run_local.sh`; Docker pour reproduire le packaging.

## Démarrage Web
```bash
cd /home/dina/Desktop/PLIEE-LIVRE
npm install
npm run dev
```
Le port Next.js par défaut est 3000; confirmer le port dans la sortie de démarrage.

## Validation
```bash
npm run typecheck
npm test
npm run test:db
npm run build
``
- `typecheck`: TypeScript.
- `test`: tests de règles métier sous `src/lib/domain/*.test.ts`.
- `test:db`: simulation locale définie par `supabase/tests/run_local.sh`.
- `build`: build optimisé Next.js.

Toujours capturer le code de sortie final. Un processus bloqué ou dont la sortie finale manque = non confirmé, pas réussi.

## Environnement
1. Copier `.env.example` vers `.env.local`.
2. Configurer uniquement les valeurs de test requises.
3. Vérifier l'exclusion Git; ne pas afficher les valeurs.
4. Les variables `NEXT_PUBLIC_*` peuvent être intégrées au bundle : reconstruire l'image si elles changent.
5. La service-role key doit rester côté serveur.

## Mobile
Le prototype actif connu est dans `C:\Users\dinac\PLIEE-LIVRE-test\mobile-app`; serveur sur `127.0.0.1:3001`. Voir [le document mobile](08-mobile.md).

## Dépannage
- Port occupé : identifier le processus avant arrêt.
- Page inaccessible : vérifier port, logs, santé du conteneur.
- Connexion refusée : vérifier URL/key du même projet, confirmation Auth, profil, cookies SSR et version réellement exécutée.
- Démo : déterminer si la donnée vient du localStorage ou d'une API.
