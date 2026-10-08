# eval-git — Site web de l'association étudiante

Évaluation pratique Git & GitHub — Gestion collaborative d'un projet web.


## 1. Identification de l'équipe (obligatoire)

| Pseudonyme GitHub | Nom | Prénom | Rôle |
|---|---|---|---|
| @carabine44 | Hamon | Ilann | [Étudiant 2] |
| @smauroy | Mauroy | Séverine | [Étudiant 3] |
| @DelphinPeltier | Peltier | Delphin | [Étudiant 1] |

**Groupe :** 1
**Dépôt :** https://github.com/carabine44/eval-git
**GitHub Project :** https://github.com/carabine44/eval-git.git

## 2. Présentation du projet

Site web (HTML/CSS, JavaScript optionnel) pour une association étudiante qui organise des événements. Il présente l'association, liste les événements à venir et permet de s'y inscrire. Le but de l'exercice est de démontrer la maîtrise de Git, de GitHub et du travail collaboratif plus que de produire un site complexe.

## 3. Fonctionnalités et responsabilités

| Fonctionnalité | Contenu | Responsable | Issues |
|---|---|---|---|
| A — Présentation et navigation | Identité visuelle, présentation de l'association, navigation entre sections | [@DelphinPeltier] | #1, #7, #8, #9 |
| B — Catalogue d'événements | 3 événements minimum (titre, date, lieu, description, accès à l'inscription) | [@carabine44] | #2, #4, #5, #6 |
| C — Inscription | Formulaire (coordonnées + choix d'un événement), sans backend | [@Smauroy] | #3, #12, #13 |
| Organisation / Project | Création et suivi du GitHub Project | [@Smauroy] | #10 |

## 4. Workflow Git Flow

| Branche | Rôle |
|---|---|
| `main` | Versions stables livrées en production (taguées) |
| `develop` | Intégration des développements en cours |
| `feature/*` | Une branche par fonctionnalité ou amélioration, créée depuis `develop` |
| `fix/*` | Correction d'un bug non urgent, créée depuis `develop` |
| `release/*` | Préparation d'une version stable (vérifications uniquement) |
| `hotfix/*` | Correction urgente de production, créée depuis `main` |

Règles :
- `main` et `develop` sont protégées : aucun push direct.
- Toute intégration passe par une Pull Request avec revue de code ([2 approbations en trinôme / 1 en binôme]).
- Commits explicites, liés aux Issues (`Closes #n`, `Refs #n`).
- Nommage : `feature/<sujet>`, `fix/<sujet>`, `release/1.0`, `hotfix/<sujet>`.
- Limites constatées : [ex. protection de branche indisponible ou limitée sur un dépôt personnel gratuit, règle respectée manuellement — à compléter ou supprimer].

## 5. Planification (GitHub Projects)

- Issues détaillées avec responsable et critères de réalisation : #1 à #13.
- Vues : **Kanban** (suivi d'avancement) et **Roadmap** (ordre prévu et dépendances).
- Lien Project : https://github.com/users/carabine44/projects/2
- Traçabilité : Issue → commits → Pull Request .

## 6. Étapes du développement

| # | Étape | Branche(s) / PR | Responsable |
|---|---|---|---|---|
| 1 | Création du dépôt, des branches et des protections | `main`, `develop` | [@DelphinPeltier] | 
| 2 | Création du Project, des Issues, Kanban et Roadmap | Issues #1–#13 | [tous] |
| 3 | Fonctionnalité A | `feature/[...]`, PR #[n] | [@DelphinPeltier] |
| 4 | Fonctionnalité B | `feature/[...]`, PR #[n] | [@carabine44] |
| 5 | Fonctionnalité C | `feature/[...]`, PR #[n] | [@Smauroy] |
| 6 | Amélioration A (identité visuelle) | `feature/[...]`, PR #[n] | [@DelphinPeltier] |
| 7 | Amélioration B (mobile) | `feature/[...]`, PR #[n] | [@carabine44] |
| 8 | Résolution du conflit | PR #[n] | [@Smauroy] |
| 9 | Correction des cartes d'événements (débordement mobile) | `feature/[...]` ou `bugfix/[...]`, PR #[n] | [@carabine44] |
| 10 | Release 1.0 | `release/1.0`, tag `v1.0` | [@DelphinPeltier] |
| 11 | Hotfix du lien « Événements » | `hotfix/[...]`, tag `v1.0.1` | [@Smauroy] |

## 7. Conflit Git

**Origine :** [@DelphinPeltier] a modifié [fichier / bloc, ex. le `<header>` et la feuille `style.css`] sur `feature/[...]` (identité visuelle : [couleurs, typographie]) pendant que [@carabine44] modifiait la même zone sur `feature/[...]` (adaptation mobile : [navigation, tailles]). Les deux branches touchaient les mêmes lignes, donc Git n'a pas pu fusionner automatiquement lors de la seconde Pull Request.


## 8. Difficultés rencontrées

- mise en place des protections de branche
- onflit : choix de ce qu'il fallait garder
- temps juste obliger de se dépecher

## 9. Questions de synthèse

**1. Quel est l'intérêt de séparer développements en cours et versions stables ?** — *[Auteur : @DelphinPeltier]*
Cela sépare la version stable, prête à être publiée, du travail en cours. Les nouvelles fonctionnalités et les corrections peuvent être préparées dans `develop` sans risquer de perturber `main`.

**2. Pourquoi imposer une revue de code avant intégration ?** — *[Auteur : @Smauroy]*
Pour permettre un second ou plusieurs regards afin de détecter les bugs, les oublis ou les incohérences avec la base commune. Cela permet aussi de garder un historique et de faire une communication indirecte.

**3. Quelles situations provoquent un conflit Git et pourquoi sa résolution n'est-elle pas toujours automatique ?** — *[Auteur : @carabine44]*
Un conflit apparaît quand deux branches modifient les mêmes lignes d'un fichier, ou quand l'une modifie ou supprime un fichier que l'autre a changé. Git ne sait pas quelle intention est la bonne : seule une personne peut décider de garder l'une des versions, l'autre ou un mélange des deux.

**4. Quelle différence entre correction classique et correction urgente de production ?** — *[Auteur : @delphinpeltier]*
Une correction classique suit le cycle normal : branche depuis `develop`, Pull Request, revue, puis livraison avec la prochaine release. Une correction urgente part de `main` (branche `hotfix`), est fusionnée rapidement dans `main` avec un nouveau tag, et n'embarque aucun développement en cours.

**5. Pourquoi répercuter une correction de production dans les développements en cours ?** — *[Auteur : @Smauroy]*
Sans cela, le bug réapparaîtrait à la prochaine release. La répercussion garde les branches cohérentes entre elles.

**6. Quel est le rôle d'une branche de release ?** — *[Auteur : @carabine44]*
Elle isole la préparation d'une version stable : vérifications, petits correctifs et mise à jour des informations de version, sans nouvelle fonctionnalité. Pendant ce temps `develop` peut continuer d'avancer. Elle est ensuite fusionnée dans `main` (avec le tag) puis dans `develop`.

**7. Comment GitHub Projects et les Issues facilitent-ils organisation et traçabilité ?** — *[Auteur : @delphinpeltier]*
Les Issues décrivent le travail, ses critères de réalisation et son responsable. Le Project montre l'avancement, l'ordre prévu. Les références `#n` dans les commits et les Pull Requests relient chaque modification à la demande.

**8. Comment savoir qui a modifié une ligne ?** — *[Auteur : @Smauroy]*
La vue « Blame » indique l'auteur et le commit. Le commit et la Pull Request associée permettent de retrouver le contexte.