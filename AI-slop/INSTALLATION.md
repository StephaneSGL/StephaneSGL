# Installation historique du profil GitHub

> Quarantaine : ce guide décrit l’ancien générateur de métriques, retiré parce qu’il échouait avec le jeton finement limité. Il est conservé uniquement pour traçabilité et ne doit pas servir de procédure actuelle.

## 1. Créer le dépôt de profil

Sur GitHub, crée un dépôt public nommé exactement :

    StephaneSGL

Le propriétaire doit être le compte `StephaneSGL`. Coche l'option permettant d'ajouter un README, ou importe directement les fichiers de ce dossier.

## 2. Copier les fichiers

Place les fichiers ainsi :

    StephaneSGL/
    ├── README.md
    ├── assets/
    │   └── .gitkeep
    └── .github/
        └── workflows/
            ├── metrics.yml
            └── snake.yml

## 3. Créer le secret METRICS_TOKEN

Le générateur `lowlighter/metrics` a besoin d'un jeton GitHub personnel pour lire les statistiques du compte.

Dans GitHub :

    Settings
    → Developer settings
    → Personal access tokens
    → Fine-grained tokens
    → Generate new token

Accorde au minimum un accès en lecture aux métadonnées et aux dépôts que tu souhaites analyser. Pour inclure les dépôts privés dans les calculs, autorise explicitement leur lecture.

Dans le dépôt `StephaneSGL/StephaneSGL` :

    Settings
    → Secrets and variables
    → Actions
    → New repository secret

Nom :

    METRICS_TOKEN

Valeur : le jeton généré.

Ne mets jamais ce jeton directement dans le README ou le workflow.

## 4. Autoriser l'écriture des workflows

Dans le dépôt :

    Settings
    → Actions
    → General
    → Workflow permissions
    → Read and write permissions

Enregistre la modification.

## 5. Lancer les workflows

Ouvre l'onglet Actions, sélectionne successivement :

    Generate profile metrics
    Generate contribution snake

Clique sur `Run workflow`.

Le premier workflow créera `assets/metrics.svg` sur la branche `main`.
Le second publiera les animations sur la branche `output`.

## 6. Actualisation

Les métriques sont régénérées chaque jour à 04:15 UTC.
Le serpent est régénéré chaque jour à 04:35 UTC.

Tu peux aussi les relancer manuellement depuis l'onglet Actions.

## Remarque sur le bloc terminal

Le bloc terminal du README est statique. GitHub ne peut pas lire en direct la RAM, les disques ou l'état de ton ordinateur. Pour afficher de vraies données locales, il faudrait exécuter un script sur ton PC et pousser automatiquement le résultat vers GitHub.
