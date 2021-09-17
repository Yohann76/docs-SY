## Amazon Web Service :

[Site Officiel Ansistranos](https://us-east-2.console.aws.amazon.com/console/home?region=us-east-2)


## Lancer un serveur MC2 ( machine linux )

Configuration ( obligatoire ) :
Dans service/MC2, lancer une instance
Choisir une image ( ex Ubuntu Server ) ou un AMI déjà pré-configuré comme
LAMP with PHP 7.1 Certified by Bitnami ( conseillé )
Choisir une instance T2.micro ( gratuit )

A partir de maintenant , deux options :
Lancer le serveur
Configurer en profondeur ( suite )

## Configuration suite :

Configurer instance ( autoscaling..) : rien toucher faire suivant
Ajouter le stockage , gérer le stockage, laisser par défaut ( 10 )
Ajouter Balise : Tagger le serveur pour le retrouver facilement ( laisser default )
Groupe sécurité : config Firewall ( pare feu ) ( régle d’entré serveur ) ( laisser default )
Lancement du serveur

Authentification par Clé
Fichier a telecharger a la fin en choisissant “new paire de clé”
Surtout ne pas le perdre, non re-téléchargeable, si perdu serveur mort

## Se connecter au Serveur

En SSH :
Mettre la clé sur le bureau ( plus simple )
chmod 400 Yohann-dev.pem ( donner les droit au clé )
ssh -i "Yohann-dev.pem" ubuntu@ec2-15-188-47-112.eu-west-3.compute.amazonaws.com
Aller dans l’onglet “connexion” pour avoir la commande SSH
FTP ( FileZilla )
hote : ec2-15-188-47-112.eu-west-3.compute.amazonaws.com
Protocole : sftp
type d’authentification : clé
identifiant : ubuntu
fichier de clé : lien du fichier de clé

## Adresse Ip-Élastique ( qui ne change pas )

Aller dans réseau et sécurité
Allouer une nouvelle adresse
Action -> Associer une adresse
Choisir instance du serveur sur liste déroulante et cliquer sur associé

## Sauvegarde

EC2, puis Actions > Image > Créer l'image
Donner un nom à l’image et cliquer sur Créer
    - Restauration
Images" > AMI >Lancer (ne pas oublier de associé ip Élastique)


## Suppression des vieux AMI

Actions" > "Annuler l'inscription" pour supprimer l'AMI
supprimé EBS ( elastic block store ) -> Actions" > "Supprimer"
Sauvegarde avec un instantané EBS
Elastic Block Store" > Volume -> Donner un nom et “Créer”


Lancer un serveur RDS ( Gestion BDD )
Lancement d'une instance DB/ Créer une bdd ( dans service RDS )
Suivre les étapes
Faire Easy pour plus de facilité
Prendre Mysql pour  version gratuite

## Restauration RDS

“Action d’instance” -> “ prendre un instantané ( fait automatiquement toute les semaines )
Cliquez sur instantané
"Restaurer l'instantané". ( pour le restaurer )
“Restaurer à un moment donnée” ( plus précis )

## Lié avec EC2

Vérifier que l’instance RDS est publique
Sinon : Sélectionner l’instance et modifier
Vérifier Que le groupe de sécurité RDS utilisé autorise MySQL sur le port 3306 depuis votre IP.
configurés dans l'interface EC2 d'AWS.

## Connection WorkBench

Requiert une accessibilité public
cliquer sur Manage connection
Standart TCP/IP
hostname: yohannrds.cp2q9efssabn.eu-west-3.rds.amazonaws.com ( point de terminaison de rsd
username : yohannrRDS ( identifiant PRINCIPALE )
Indiqué également le password dans Store in vault
Configurer également un groupe de sécurité pour EC2 en entrant 3306 sql

## Pour se connecter à rds sur EC2 :

$bdd = new PDO('mysql:host=dbinstance.cmo5fnknxzqh.us-east-2.rds.amazonaws.com;
dbname=test;
charset=utf8',
 'mateo',
'VOTRE_MOT_DE_PASSE_ICI');


Lancer un serveur S3 ( Stockage fichier )
Lien du cours

Gestion de droit par users :

1 : User policy
définit ce qu'un utilisateur a le droit de faire.

2 :Resource-based policy :
définit ce qu'on a le droit de faire sur un bucket ou un fichier.

Le cloud Uploader ( Service d’upload via site)  :

Faire pointer Sur un nom de domaine
