# Galeries visuelles — les deux prototypes Web PLIEE-LIVRE

> Deux applications distinctes sont documentées ici. Ne pas confondre les captures, les routes ou le niveau d'intégration.

## 1. Application Web Next.js — version principale

Adresse locale documentée : `http://localhost:3000`.

Cette version porte le parcours public et les espaces métier reliés à l'architecture applicative. Sa galerie contient des captures réelles du navigateur pour les pages publiques, puis un inventaire des parcours protégés et de leurs routes.

![Page d’accueil de l’application Web Next.js](assets/web-screenshots/01-accueil.png)

**Galerie détaillée :** [Galerie visuelle — application Web Next.js](13-galerie-web.md)

**Captures actuellement disponibles :**

| Domaine | Captures / contenu |
|---|---|
| Public | Accueil, À propos, Connexion, Inscription, récupération d'accès, Conditions, Confidentialité |
| Découverte | Laboratoire public `/demo`, Devenir Pro, Devenir partenaire |
| Client | Tableau de bord, commande, suivi, abonnement, profil, notifications — routes et fonctions documentées; captures authentifiées à compléter |
| Pro | Missions, courses, gains, profil — routes et fonctions documentées; captures authentifiées à compléter |
| Gestion | Tableau de bord, commandes, professionnels, tarifs, finances, fin de mois, applications, laboratoire — routes et fonctions documentées; captures authentifiées à compléter |
| Partenaire | Tableau de bord et redevances — routes et fonctions documentées; captures authentifiées à compléter |

## 2. Prototype Web original — Vite

Adresse locale de référence : `http://localhost:4173` sur le PC Windows.

Cette version est le prototype UI/UX original conservé comme référence visuelle pendant le portage vers Next.js. Sa source est documentée dans `PROTOTYPE-FEATURE-MAP.md` sur la machine de développement, et non dans le dépôt de documentation. Au moment de la mise à jour de cette galerie, le service sur le port 4173 n'est pas joignable depuis l'environnement de capture et le PC Windows n'est pas connecté à l'outil de travail. **Aucune nouvelle capture directe de Vite n'est donc présentée comme si elle venait du navigateur.**

### Carte des concepts UI du prototype Vite

| Fonction / composant original | Intention visuelle ou interaction | État documenté du portage Next.js |
|---|---|---|
| `HeroSection`, `HowItWorksSection` | Présentation du service et étapes de collecte/lavage/livraison | Présents dans l'accueil Next.js |
| `DoorDashLaundryOnDemand` | Choix d'un parcours de service à la demande | Partiel; pas de promesse express non configurée |
| `SubscriptionPlansSection` | Offres et parcours d'abonnement | Point d'entrée et espace abonnement présents; dépend des règles/configurations |
| `BalancedPricingSection` | Devis interactif et transparence des prix | Portage interactif initial dans `PricingWorkspace` |
| `CoverageTerritoriesSection` | Vérification de couverture | Partiel; dépend des zones configurées |
| `DynamicBagsAndProductsGallery`, `OfficialBagsShowcase` | Présentation des sacs et options | Partiel; pas de catalogue complet |
| `SoapCatalogSection`, `ServiceCatalog` | Catalogue de produits et services | Options et conditions partiellement portées |
| `FabricCareSection`, `AiFabricDoctorModal`, `ArtOfFoldingSection` | Entretien textile et conseils | Guide local à règles fixes; pas de diagnostic photo IA |
| `OrderWizardModal`, `OrderTrackerModal`, `OrderHistoryModal` | Commander, suivre et consulter l'historique | Parcours correspondants présents dans les routes Client |
| `ProfessionalRatingCard` | Évaluer le professionnel | Formulaire lié à une commande livrée; pas de nom client demandé dans ce formulaire |
| `ChatModal`, `SmsMessengerModal`, `EmailInboxModal` | Aperçus de communication | Simulations locales dans `/demo`; aucun envoi réel annoncé |
| `NotificationDrawer`, `NotificationToast` | Notifications et compteur non lu | Démo locale; centre global relié au backend à compléter |
| `InvoiceModal`, `invoiceService` | Facture dédiée | À intégrer; pas de facture persistée dédiée confirmée |
| `PaymentGateway`, `stripeService` | Paiement | Le backend existe, mais le fournisseur doit être configuré et testé avant tout paiement réel |
| `AdminDashboard`, `DriverPortal`, `LaundromatPartnerPortal`, `WorkshopPortal` | Espaces Gestion, Pro, partenaire et atelier | Portails métier présents à des degrés différents; atelier dans `/demo` reste local/fictif |
| `BuildingAccessPortal`, `SosSecurityModal`, `SecurityCenterModal` | Accès bâtiment et sécurité | Simulations locales pour certains parcours; aucun contrôle physique ni alerte externe réelle |

**Référence fonctionnelle :** [carte de migration Vite → Next.js](../README.md#état-exécutif-2026-10-28) et fichier `PROTOTYPE-FEATURE-MAP.md` dans le dépôt source. Le tableau ci-dessus décrit le portage et n'est pas une capture du prototype Vite.

### À faire pour compléter la galerie Vite avec des images réelles

1. Réactiver le projet original sur le PC Windows depuis `C:\Users\dinac\Downloads\pli-livr-26-oct-2026-19-58-18`.
2. Vérifier que `http://localhost:4173/` répond.
3. Capturer les écrans directement dans le navigateur : accueil, tarification, abonnement, sacs/options, entretien textile, évaluations, chat/notifications et portails simulés disponibles.
4. Ranger les captures dans `docs/assets/web-vite-screenshots/` et remplacer ce tableau par une galerie illustrée, sans fabriquer de captures ni mélanger les images Next.js.

## Règles communes de lecture

- Les captures du navigateur sont des preuves du rendu à un instant donné, pas la preuve qu'une intégration réseau ou une action métier fonctionne.
- Les captures des parcours Client, Pro, Gestion et Partenaire doivent utiliser des sessions de test autorisées et des données fictives.
- Les simulations locales (chat, SMS, courriel, accès, SOS, atelier) doivent être étiquetées comme simulations.
- L'application mobile sur le port 3001 dispose d'une [galerie distincte](11-galerie-prototype.md).
