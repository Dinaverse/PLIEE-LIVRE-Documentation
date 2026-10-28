# Journaux Supabase / PostgreSQL — PLIEE-LIVRE-TEST

## Capture

La capture ci-dessous provient de la console Supabase du projet `PLIEE-LIVRE-TEST` (`wbkbkygmovuvhagsuixi`), dans **Logs**, avec le filtre `Log Type = postgres`. Elle affiche l’intervalle choisi dans l’interface au moment de la capture.

<p align="center">
  <img width="1366" alt="Logs Supabase filtrés sur PostgreSQL : événements de commandes SQL et checkpoints" src="https://github.com/user-attachments/assets/1f46787f-cd75-42fb-bb42-b5ef1cd1e6b2" />
</p>

## Ce que l’image permet d’affirmer

- La console affiche des événements PostgreSQL horodatés.
- Plusieurs lignes contiennent des messages `statement` avec des paramètres de session et des instructions SQL, notamment des messages commençant par `CREATE OR REPLACE FUNCTION`.
- Des événements `checkpoint starting` et `checkpoint complete` sont visibles.

## Ce que l’image ne prouve pas

- Elle ne suffit pas à valider le contenu, la sécurité ou le résultat d’exécution de chaque fonction SQL : le texte visible est tronqué dans la liste.
- Elle ne démontre pas à elle seule que les politiques RLS sont correctes, que les flux Auth de l’application sont sûrs, ni que les opérations métier sont intégrées de bout en bout.
- Elle représente une fenêtre temporelle et un filtre précis; elle ne constitue pas un export complet des journaux.

## Comment utiliser cette preuve

Traiter l’image comme une **capture d’observation**, à rapprocher des migrations, des définitions SQL, des tests RLS et des tests applicatifs. Pour une investigation, exporter les journaux pertinents depuis Supabase, conserver la plage temporelle et le filtre utilisés, puis documenter séparément les requêtes ou erreurs vérifiées.

Retour à la [documentation principale](../README.md) ou à la [galerie visuelle](11-galerie-prototype.md).
