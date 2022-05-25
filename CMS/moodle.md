## Moodle

LMS ( Learning Platform or course management system )
[Moodle docs](https://docs.moodle.org/4x/fr/Installation_de_Moodle)


[Instalation Serveur](https://docs.moodle.org/4x/fr/Installation_de_Moodle#Mettre_en_place_votre_serveur)


1. $ git clone -b MOODLE_33_STABLE git://git.moodle.org/moodle.git 

Database : 

dbhost - le nom de l'hôte du serveur de base de données. Probablement localhost si la base de données et le serveur web sont la même machine, auquel cas, le nom du serveur de base de données

dbname - le nom de la base de données. Peu importe son nom, par ex. moodle

dbuser - le nom d'utilisateur pour la base de données. Peu importe son nom, par ex. moodleuser - n'utilisez jamais le compte du root/super-utilisateur, mais créez un compte propre à cette base de données avec le minimum de permissions.

dbpass - le mot de passe de l'utilisateur ci-dessus

