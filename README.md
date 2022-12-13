# Mora Clean serveur

Mise en place d'une application de gestion de passage pour les piscinistes.

Pour télécharger le projet

```bash
git clone git@gitlab.com:moraclean/moraclean-serveur.git
```

## Sommaire
- [Stack technique](#stack-technique)
- [Installation](#installation)
- [Tests](#tests)
- [Documentation de l'API](#docs)
- [Déploiement: Scalingo](#deploiement-avec-scalingo)
- [Structure des données](#structure)

## Stack technique

### Version de Ruby: 3.0.4

Si vous utilisez `rbenv`, vous pouvez l'installer avec la commande suivante

```bash
rbenv install 3.0.4
```

### Version de Ruby on Rails: 7.0.4

### SGBD: PostGreSQL

```bash
# MacOS
brew install postgresql
brew services start postgresql
# Linux
sudo apt install -y postgresql postgresql-contrib libpq-dev build-essential
```

### Outil de versionning : Git

La branch de travail par défaut est `develop`. Les branches de dévelopement doivent toutes être tirées de `develop` et préfixées de `feature`.

Afin de ne push aucun commit directement sur master (qui est la branche de production) :

- La correction rapide de bugs, typos etc... en production, se fait par `hotfix`
- La mise à jour de master pour une mise en production (MEP) se fait par `release`

## Installation

Créer un fichier `.env` à la racine du projet et y ajouter

```
DEVISE_JWT_SECRET_KEY=secret_token
```

(vous pouvez aussi générer votre propre secret key avec la commande `rails secret`)

Installer les gems avec

```bash
bundle install
```

Pour installer la base de données

```bash
rails db:drop db:create db:migrate db:seed
```

Démarrer le serveur avec

```bash
bundle exec rails server
```


## Tests

Pour tester avant un commit, les commandes sont les suivantes :

* Pour la suite de tests

```bash
bundle exec rspec
```

* Pour la qualité du code

```bash
bundle exec rubocop
```

## Docs

Excuter la commande

```bash
rake rswag
```

puis démarer le serveur `bundle exec rails s`

et acceder à la doc `api-docs/index.html`

## Deploiement avec Scalingo

Le site est déployé automatiquement avec[Scalingo](https://scalingo.com/).
