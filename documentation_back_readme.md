---
agent: agent
---
# Prompt pour Génération de Documentation Automatisée

Utilisez ces prompts séquentiels pour générer la documentation sur d'autres projets similaires (Legacy .NET, Batchs, WinForms).

## Étape 1 : Initialisation du Contexte (Copilot Instructions)

Copiez-collez ce prompt dans le chat pour analyser le projet et créer le fichier d'instructions :

> **Prompt :**
> "Analyse ce codebase pour générer le fichier `.github/copilot-instructions.md`.
> Ce fichier doit aider un agent AI à comprendre rapidement le projet.
>
> Inclure les sections suivantes :
> 1. **Project Overview** : Type d'application (WinForms, Console, .NET Framework version), but principal.
> 2. **Architecture & Patterns** : Points d'entrée (`Program.cs`, `Main`), séparation logique/UI, accès données (ADO.NET, ORM).
> 3. **Critical Constraints** : Version du langage (C# 2.0 vs récents), bibliothèques interdites ou spécifiques, contraintes de déploiement.
> 4. **Conventions** : Langue du code (Français/Anglais), nommage, gestion des configurations (INI, XML, App.config).
> 5. **Key Files** : Liste des 3-5 fichiers les plus importants et leur rôle.
>
> Sois concis et technique."

---

## Étape 2 : Génération de la Documentation des Flux (Workflow)

Une fois l'étape 1 terminée, utilisez ce prompt pour générer la documentation fonctionnelle des étapes :

> **Prompt :**
> "Analyse le fichier `FrmMain.cs` pour identifier le `switch` principal qui orchestre les étapes (souvent basé sur une variable comme `etapeLocal`, `Action` ou `args`).
> Ne documente QUE les étapes présentes dans ce `switch`.
>
> Pour chaque `case` identifié :
> 1. Trouve la méthode appelée (ex: `Traitements.MaFonction()`).
> 2. Analyse le code de cette méthode (souvent dans `Traitements.cs`) pour extraire : Entrées, Logique détaillée, Sorties.
>
> Génère un fichier `README.md` en suivant strictement ce modèle (basé sur `DOC_ETAPES_730.md`).
> Le fichier doit commencer par le titre `# Documentation Synthétique des Étapes`.
>
> ## [NUMERO]. [NOM_DE_L_ETAPE_DANS_LE_CASE]
> **Objectif** : [Description synthétique]
> - **Entrée** : [Fichiers, Tables, Paramètres]
> - **Traitement** :
>   - [Action principale]
>   - [Détail logique précis : conditions `if/else`, boucles importantes, transformations de données]
>   - [Mentionne les méthodes clés appelées (ex: `Manager.Calculer()`) et leur rôle]
>   - [Valeurs en gras, ex: **"VALEUR"** si condition]
>   - [Utilise des blocs de code pour les requêtes SQL, les formats de fichiers générés ou les règles métier complexes]
> - **Sortie** : [Fichiers créés/modifiés, Tables mises à jour]
>
> **Règles de formatage :**
> - Utilise des listes à puces imbriquées pour la lisibilité.
> - Mets en **gras** les noms de champs importants ou les valeurs littérales.
> - Utilise des blocs de code (\`\`\`) pour les requêtes SQL ou les formats spécifiques.
> - Reste concis mais précis.
>
> Exemple :
> ## 1. DOUBLONS
> **Objectif** : Invalidation des doublons en base.
> - **Entrée** : Fichier `.exp`.
> - **Traitement** :
>   - Parcourt les lignes de type **FACTURE**.
>   - Si le statut est **EN_COURS**, appelle `Manager.CheckDoublon()`.
>   - Exécute la mise à jour :
>     \`\`\`sql
>     UPDATE table SET etat='REMPLACEE' WHERE id=...
>     \`\`\`
> - **Sortie** : Base de données mise à jour."
