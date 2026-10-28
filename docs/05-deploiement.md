# 5. Déploiement Docker / Windows / WSL2

## Modèle connu
Kali construit l'image; Windows `DESKTOP-IGLRCFT` exécute Docker dans Ubuntu/WSL2. Dossier Windows : `C:\Users\dinac\PLIEE-LIVRE-test`. URL : `http://localhost:3000`. Les rapports citent `pliee-livre` et `pliee-livre-r6`; vérifier le nom réel avec `docker ps`.

## Fichiers
`Dockerfile`, `compose.yaml`, `compose.deploy.yaml`, `export-docker-image.sh`, `README.docker.md`, `README.windows-test.md`, `DEPLOYMENT-AND-TEST-NOTES.md`.

Le Compose Windows utilisait `network_mode: host` pour contourner un problème de port sous WSL2. Ne pas remplacer par la version Kali sans tester les deux côtés du réseau.

## Build/export sur Kali
```bash
cd /home/dina/Desktop/PLIEE-LIVRE
./export-docker-image.sh .env.local pliee-livre-image.tar.gz
sha256sum pliee-livre-image.tar.gz
```
N'exporter que l'image et les fichiers nécessaires. Ne jamais transférer `.env.local`. Les valeurs `NEXT_PUBLIC_*` changées exigent un nouveau build.

## Chargement et démarrage Windows
```powershell
Set-Location 'C:\Users\dinac\PLIEE-LIVRE-test'
Get-FileHash .\pliee-livre-image.tar.gz -Algorithm SHA256
wsl -d Ubuntu -- docker load -i /mnt/c/Users/dinac/PLIEE-LIVRE-test/pliee-livre-image.tar.gz
wsl -d Ubuntu --cd /mnt/c/Users/dinac/PLIEE-LIVRE-test -- docker compose --env-file .env.production -f compose.deploy.yaml config --quiet
wsl -d Ubuntu --cd /mnt/c/Users/dinac/PLIEE-LIVRE-test -- docker compose --env-file .env.production -f compose.deploy.yaml up -d
```
Comparer les empreintes SHA-256 avant chargement. Vérifier le fichier Compose et l'environnement sans afficher de secrets.

## Smoke tests et opérations
```powershell
curl.exe -I http://localhost:3000/
curl.exe -I http://localhost:3000/connexion
wsl -d Ubuntu -- docker ps -a
wsl -d Ubuntu -- docker logs --tail 100 pliee-livre
```
Commandes opérationnelles possibles après vérification du nom/contexte :
```powershell
wsl -d Ubuntu -- docker inspect pliee-livre --format '{{.State.Status}} {{.State.Health.Status}}'
wsl -d Ubuntu -- docker logs -f pliee-livre
```
Ne pas utiliser de commande supprimant des volumes sans inspection préalable. HTTP 200/healthy = UI répond; cela ne prouve pas Auth, DB, Storage ou Stripe.
