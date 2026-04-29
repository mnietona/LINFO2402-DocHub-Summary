# LINFO2402 - Open Source Development : Résumé de Contribution

**Étudiant :** Matias Nieto Navarrete  
**Projet soutenu :** [DocHub](https://github.com/DocHub-ULB/DocHub)  

---

## 1. Le projet : DocHub

**DocHub** est une plateforme étudiante indépendante, créée et gérée par des passionnés d'informatique pour les étudiants de l'ULB. Contrairement aux outils institutionnels, ce projet repose entièrement sur l'auto-hébergement et l'entraide communautaire.

*   **Objectif :** Centraliser et faciliter le partage de ressources éducatives (résumés, notes de cours, anciens examens) de manière instantanée, sans les barrières d'accès habituelles des dossiers partagés (type Google Drive).
*   **La communauté :** Le code est maintenu par un développeur principal bénévole. Cependant, les acteurs clés de la communauté gravitent autour du Cercle Informatique (CI) et d'UrLab, qui récoltent les besoins des utilisateurs et conseillent la plateforme aux nouveaux étudiants.

---

## 2. Mes contributions

Mon travail s'est divisé en trois axes principaux pour aider à consolider le projet et améliorer l'expérience des utilisateurs et des futurs développeurs.

### A. Amélioration de l'expérience développeur (Infrastructure)
Pour faciliter l'arrivée de nouveaux contributeurs étudiants (et réduire la dépendance à un seul développeur), j'ai modernisé la configuration de base :
*   **[PR #368](https://github.com/DocHub-ULB/DocHub/pull/368) & [PR #381](https://github.com/DocHub-ULB/DocHub/pull/381) :** Mise à jour du `Makefile` (intégration du gestionnaire rapide `uv`, ajout de commandes de confort pour les tests locaux).
*   **[PR #363](https://github.com/DocHub-ULB/DocHub/pull/363) :** Remplacement des anciens `print()` par un véritable système de `logging` Python pour faciliter le débogage.

### B. Corrections et robustesse
*   **[PR #377](https://github.com/DocHub-ULB/DocHub/pull/377) (Correction critique) :** Résolution d'un bug majeur lors de l'envoi massif de documents (Bulk Upload) causé par un conflit avec le framework *Hotwire Turbo*. J'ai implémenté le design pattern **PRG (Post/Redirect/Get)** pour stabiliser le flux.
*   **[PR #372](https://github.com/DocHub-ULB/DocHub/pull/372) :** Ajout d'un message d'information sur la page d'accueil pour rappeler le caractère étudiant et non officiel de la plateforme, accompagné d'une invitation ouverte à rejoindre l'équipe pour apprendre et contribuer.

### C. Fonctionnalité majeure : Le système de modération
*   **[PR #379](https://github.com/DocHub-ULB/DocHub/pull/379) :** Création complète d'une interface de modération sécurisée (hors du panel d'administration natif de Django). 
    *   Création de vues protégées (`@moderator_required`).
    *   Mise en place de formulaires stricts (obligation de justifier un refus de demande de modération).
    *   Développement d'un journal public garantissant la transparence des actions, avec des requêtes SQL optimisées (`select_related`, `prefetch_related`) pour éviter les problèmes de performances (N+1 Query).

---

## 3. Aspect méthodologique de l'Open Source : Le consensus avant le code

Au cours de mon implication, j'ai pris l'initiative de développer une refonte visuelle complète de l'interface du site ([PR #364](https://github.com/DocHub-ULB/DocHub/pull/364)), suite à des discussions informelles avec des étudiants. J'ai réagi comme je l'aurais fait pour un projet étudiant classique : j'ai vu un problème, j'ai codé la solution dans mon coin, puis j'ai soumis le résultat.

**L'apprentissage :** J'ai réalisé que dans un véritable écosystème Open Source, cette approche ne fonctionne pas. Une refonte majeure impacte les habitudes de milliers d'utilisateurs, nécessite de mettre à jour la documentation, et demande au mainteneur de vérifier énormément de fichiers. 

Cette expérience m'a appris une règle d'or de la méthodologie Open Source : **la communication est prioritaire sur le code**. Une bonne contribution architecturale ne doit pas être soumise sans une discussion préalable (*Issue* ou *Request for Comments*) avec les mainteneurs pour s'assurer qu'elle s'inscrit bien dans la feuille de route du projet.
