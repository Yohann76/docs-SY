.. index::
   single: Deploy; 

Outils de déploiement
===================

Processus de déploiement Symfony
-------------------

Déployer: 
-------------------
Utiliser un fichier playbook.yaml
S’assurer de la bonne connexion a MySQL
Utiliser les bonne versions de PHP

processus pour sécuriser le déploiement: 
utiliser composer install --no-dev --optimize-autoloader
s’assurer que le composant Dotenv est présent sur la configuration de prod
s’assurer que le default.conf est supprimer de var/www