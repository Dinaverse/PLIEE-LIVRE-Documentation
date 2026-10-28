# Galerie visuelle — prototype mobile PLIEE-LIVRE

> Captures réelles de la maquette locale, prises le 28 octobre 2026 dans Microsoft Edge en format mobile (390 × 844). Les espaces utilisent des données de démonstration : ces captures illustrent l'interface, pas une preuve d'authentification, de paiement ou de traitement en production.

## Parcours de connexion

![Écran de connexion et choix de l'espace](assets/prototype-screenshots/00-connexion.png)

## Espace Client

| Accueil | Création de commande |
|---|---|
| ![Accueil Client](assets/prototype-screenshots/02-client-home.png) | ![Commander](assets/prototype-screenshots/03-client-order.png) |

| Suivi de commande | Abonnement |
|---|---|
| ![Suivi](assets/prototype-screenshots/04-client-track.png) | ![Abonnement](assets/prototype-screenshots/05-client-sub.png) |

![Profil Client](assets/prototype-screenshots/06-client-profile.png)

## Espace Pro

| Missions disponibles | Mes courses |
|---|---|
| ![Missions Pro](assets/prototype-screenshots/02-pro-missions.png) | ![Mes courses](assets/prototype-screenshots/03-pro-mine.png) |

| Gains | Profil Pro |
|---|---|
| ![Gains Pro](assets/prototype-screenshots/04-pro-earn.png) | ![Profil Pro](assets/prototype-screenshots/05-pro-profile.png) |

## Espace Gestion

| Tableau de bord | Liste prioritaire de fin de mois |
|---|---|
| ![Tableau de bord Gestion](assets/prototype-screenshots/02-gestion-dash.png) | ![Fin de mois](assets/prototype-screenshots/03-gestion-prio.png) |

![Gestion des commandes](assets/prototype-screenshots/04-gestion-orders.png)

## Assistant intégré

![Chatbot d'aide dans l'espace Client](assets/prototype-screenshots/20-client-assistant-chatbot.png)

## Infrastructure — Supabase / PostgreSQL

Cette capture de la console Supabase est une preuve opérationnelle distincte des écrans du prototype mobile. Elle montre les journaux PostgreSQL du projet de test, avec des messages SQL et des checkpoints; elle ne certifie pas à elle seule la sécurité ni le bon fonctionnement de l’application.

<p align="center">
  <img width="1366" alt="Logs Supabase PostgreSQL du projet PLIEE-LIVRE-TEST" src="https://github.com/user-attachments/assets/1f46787f-cd75-42fb-bb42-b5ef1cd1e6b2" />
</p>

Lire le [détail de la capture et ses limites](12-supabase-logs.md).

## Inventaire complet

Toutes les captures PNG sont conservées dans [`assets/prototype-screenshots/`](assets/prototype-screenshots/). L'index détaillé des fichiers se trouve dans le [README des captures](assets/prototype-screenshots/README.md). Le fichier `clipboard-capture.png` conserve également l'image qui se trouvait dans le presse-papiers lors de la capture.

## Périmètre et limites

- Les captures montrent les écrans principaux des espaces Client, Pro et Gestion, ainsi que la connexion et le chatbot.
- Les captures sont des images statiques; les interactions, états d'erreur, confirmations et toutes les fenêtres modales ne sont pas exhaustivement documentés.
- Le prototype mobile est une maquette front-end : la connexion est simulée et les données sont locales. Ne pas interpréter les données affichées comme des données de production.
