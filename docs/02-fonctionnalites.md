# 2. Fonctionnalités et périmètre

## Espaces
| Espace | Route | Rôle attendu |
|---|---|---|
| Client | `/client` | `client` |
| Professionnel | `/pro` | `pro` |
| Partenaire | `/partenaire` | `partenaire` |
| Gestion | `/gestion` | `admin` |
| Finances | `/gestion/finances` | `admin` ou `finance`, selon l'action |
| Démo publique | `/demo` | démonstration sans données réelles |

## Concepts UI documentés
Page d'accueil enrichie : commande ponctuelle/abonnement, options de collecte, transparence des coûts, sacs et préférences, espaces Client/Pro/Partenaire/Gestion et conseils textiles. Chatbot conservé. Notation du Pro liée à une commande livrée et ne demandant pas le nom du client dans la démo.

Le laboratoire de démonstration présente des simulations de chatbot, SMS/courriel, aperçu de facture, guide d'entretien, notifications locales, pass/SOS fictif et file d'atelier locale. Ces éléments ne doivent pas être présentés comme des intégrations réseau réelles.

## État par domaine
| Domaine | État connu | Limite |
|---|---|---|
| Pages Web | plusieurs routes répondent HTTP | ne prouve pas les parcours complets |
| Prix et règles métier | tests locaux présents | ne valide pas les opérations distantes |
| Supabase | migrations appliquées selon rapport | RLS et flux applicatifs à retester |
| Auth | appels directs validés auparavant | session navigateur E2E incomplète |
| Preuves photo Pro | dépend du bucket privé `preuves` | bucket absent lors de la dernière inspection |
| Inscription/consentement | action utilise un client admin | service-role requis côté serveur ou refactorisation |
| Stripe | dépendance installée | clés/webhooks et flux non certifiés |
| Courriel/SMS/Gemini/i18n/facturation | certaines intégrations étaient notées « à intégrer » | vérifier le code actuel avant de reclasser |
| Mobile | interface de prototype | login simulé, données locales |

## Définition d'une fonctionnalité terminée
Documenter la route, l'action, la source de données, les contrôles d'accès, les dépendances, les tests positifs et négatifs et les limites. Une maquette interactive n'est pas une fonctionnalité métier intégrée.
