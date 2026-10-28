# 1. Architecture

## Vue d'ensemble
```text
Navigateur Web → Next.js/React (port 3000)
                  ├─ pages, layouts, actions serveur
                  ├─ logique métier TypeScript
                  └─ Supabase
                     ├─ Auth
                     ├─ PostgreSQL + migrations
                     ├─ RLS / fonctions SQL
                     └─ Storage (bucket privé attendu : preuves)

Prototype mobile (port 3001) → HTML/CSS/JS autonome + localStorage
                                └─ connexion simulée; pas d'API métier confirmée
```

## Environnements
| Environnement | Fonction |
|---|---|
| Kali Linux, `/home/dina/Desktop/PLIEE-LIVRE` | source Web, dépendances, tests, build et export Docker |
| Supabase `PLIEE-LIVRE-TEST` | Auth et base de test, Canada Central |
| Windows `DESKTOP-IGLRCFT` + WSL2 Ubuntu | hôte Docker de test |
| `http://localhost:3000` | application Web conteneurisée |
| `C:\Users\dinac\PLIEE-LIVRE-test\mobile-app` | prototype mobile actif sur 3001 |

## Stack Web
Next.js 15.5.28 / React / TypeScript; `@supabase/ssr`, `@supabase/supabase-js`; PostgreSQL et SQL versionné; Stripe SDK présent mais flux non certifiés; tests via `tsx --test`; image Docker multi-stage Node 22 slim.

## Structure source connue
- `src/app/`: routes, pages, layouts et composants.
- `src/lib/`: clients, auth et règles métier.
- `supabase/migrations/`: scripts SQL versionnés.
- `supabase/tests/`: tests DB et simulateur local.
- `supabase/seed.sql`: données de départ à examiner avant usage.
- `Dockerfile`, `compose*.yaml`, `export-docker-image.sh`: packaging.
- Les rapports détaillés historiques restent dans le dossier source; ce dépôt est l'index consolidé.

## Flux de confiance
Auth fournit une identité; `profiles.role` détermine l'espace; les pages et actions serveur vérifient les rôles; RLS limite les lignes; Storage exige ses propres politiques. Masquer un bouton n'est jamais un contrôle de sécurité. localStorage et les données de démo ne sont pas une source d'autorité.
