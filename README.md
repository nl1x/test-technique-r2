# Test Technique - Agence R2

## Utilisation
1. Cloner le repository
```bash
git clone https://github.com/nl1x/test-technique-r2
```

2. Démarrer WordPress avec Docker
```bash
cd test-tecnique-r2 && sudo docker-compose up -d
```

3. Configurer WordPress depuis l'url suivante : http://localhost:8000

4. Importer l'archive localhost-20240701-190630-fssl21.wpress à l'aide de l'extension `All-In-One Migration`.
> [!note]
> En cas de problème d'importation dû à une limite d'upload limitée, suivez les explications ci-dessous.

## En cas de problèmes d'importation

1. Ouvrez un shell intéractif du Docker
```bash
sudo docker exec -it ttr2clone-wordpress-1 /bin/bash
```

2. Copiez/Collez l'archive de l'extension `/tmp/wordpress-test-technique/all-in-one-wp-migration-6.7.zip` dans le dossier `/var/www/html/wp-content/plugins`
```bash
cp /tmp/wordpress-test-technique/all-in-one-wp-migration-6.7.zip /var/www/html/wp-content/plugins
```

3. Supprimez le dossier actuelle de l'extension `All-In-One Migration` présent dans `/var/www/html/wp-content/plugins`
```bash
rm -r /var/www/html/wp-content/plugins/all-in-one-wp-migration
```

4. Dézippez l'archive de l'ancienne version de `All-In-One Migration`
```bash
cd /var/www/html/wp-content/plugins && unzip all-in-one-wp-migration-6.7.zip
```

5. Créez le fichier `storage/index.php` dans le dossier de l'extension
```bash
cd /var/www/html/wp-content/plugins/all-in-one-wp-migration && mkdir storage && touch storage/index.php 
```

6. Copiez/Collez l'archive du site dans le dossier `wp-content/ai1wm-backups`
```bash
cp /tmp/wordpress-test-technique/localhost-20240701-190630-fssl21.wpress /var/www/html/wp-content/ai1wm-backups
```

7. Sur l'interface WordPress, dans la catégorie `Sauvegardes` de l'extension `All-In-One Migration`, restaurez la sauvegarde appelée `localhost-20240701-190630-fssl21.wpress`
![image](https://github.com/nl1x/test-technique-r2/assets/83085376/d9f57551-ea42-4ce1-9c6d-d5237c9ab6a5)

8. Suivez les étapes de restauration.
