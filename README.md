# Viking Transport

Site web de réservation pour la compagnie de transport Viking Transport, réalisé en équipe de 7 pendant la SAÉ 2.4-5-6 de première année de BUT Informatique (IUT de Caen).

## Fonctionnalités

- **Recherche de trajet** : un moteur calcule l'itinéraire entre deux arrêts en modélisant le réseau de lignes sous forme de graphe et en cherchant le plus court chemin avec l'algorithme de Dijkstra
- **Lignes et horaires** : consultation des lignes du réseau et de leurs horaires
- **Réservation et billet** : réservation d'un trajet, paiement, puis billet récapitulatif
- **Espace client** : inscription, connexion, modification du profil et du mot de passe
- **Administration** : gestion des clients et des lignes

## Technologies

PHP · Oracle (via PDO) · HTML · CSS

## Lancer le projet

1. Importer le schéma et les données de `vik.sql` dans une base Oracle.
2. Copier `PHP/param_connexion_etu.example.php` en `PHP/param_connexion_etu.php` et y renseigner les identifiants de la base. Ce fichier est ignoré par git : les identifiants ne sont jamais versionnés.
3. Servir le dossier avec un serveur PHP et ouvrir `PHP/index.php`.

## Avec le recul (sécurité)

La sécurité ne faisait pas partie du sujet de cette SAÉ. En relisant le code avec un œil sécurité, voici ce que j'ai corrigé et ce qui était déjà bien en place :

- **Corrigé : les identifiants de la base étaient écrits en dur** dans le code et publiés sur GitHub. Ils sont maintenant dans un fichier local ignoré par git, avec un modèle sans mot de passe dans le dépôt.
- **Corrigé : une requête SQL était construite en collant des variables dans le texte** (`traitement_modifier_mdp.php`). Elle passe maintenant par une requête préparée, comme le reste du projet, ce qui protège contre les injections SQL.
- **Déjà en place : les mots de passe des clients sont hachés** avec `password_hash` (bcrypt) et vérifiés avec `password_verify`, jamais stockés en clair.
- **Déjà en place : la plupart des requêtes sont préparées.**

## Équipe

- BUCHAILLAT Enzo
- DUMÉNIL Gaëlig
- FONTAINE Louis
- GAUMONT Gabriel
- GUILLAUME Rafaël
- LEGROS Ewenn
- MATHIEU Alix
