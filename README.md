# Objectif Pédagogique
Cette formation sur Jenkins vise à doter les participants des compétences nécessaires pour installer, configurer et gérer des pipelines CI/CD avec Jenkins. L'approche de cette formation inclut l'intégration d'outils clés tels que Jenkins, Docker et Kubernetes, formant ainsi une chaîne complète d'intégration et de déploiement continus.

Cette formation s'adresse principalement aux ingénieurs DevOps en formation ainsi qu'à toute personne souhaitant acquérir une compréhension approfondie de la mise en place de pipelines CI/CD avec Jenkins.

## Compétences Acquises
À l'issue de cette formation, les participants seront capables de :

Installer et configurer Jenkins : Maîtriser les étapes nécessaires à une installation réussie de Jenkins et à sa configuration initiale.
Intégrer Docker à Jenkins : Utiliser Docker pour automatiser la phase de build des applications.
Installer et configurer des plugins : Élargir les fonctionnalités de Jenkins grâce à l'installation de plugins adaptés aux besoins spécifiques.
Rédiger un Jenkinsfile : Créer des fichiers de configuration pour définir les pipelines CI/CD.
Connecter Jenkins à l'API Kubernetes : Utiliser des fichiers de configuration kubeconfig pour permettre à Jenkins d'interagir avec un cluster Kubernetes.
Configurer des alertes par email : Paramétrer des notifications par email pour les événements critiques dans le pipeline.
Prérequis
Les participants doivent posséder des connaissances de base en Docker, Docker Hub, Kubernetes, Git et GitHub.

# I - Introduction
Pour une bonne compréhension des concepts Jenkins et CI/CD, nous vous recommandons d'avoir complété au préalable le cours Docker & Kubernetes.
La machine utilisée pour ce cours est dédiée à Jenkins.

## A - Présentation
Jenkins est un outil d'automatisation open source écrit en Java utilisé pour construire et implémenter les principes d'intégration continue.

Jenkins construit et teste nos projets logiciels, ce qui facilite en permanence l'intégration des modifications du projet par les développeurs et facilite l'obtention d'une nouvelle version par les utilisateurs.

Cela nous permet également de fournir en continu notre logiciel en s'intégrant à un grand nombre de technologies de test et de déploiement.

Jenkins offre un moyen simple de configurer un environnement d'intégration continue ou de livraison continue pour presque tous les langages et les référentiels de code source (comme GitHub, GitLab...) à l'aide de pipelines, ainsi que d'automatiser la plupart des tâches de développement.

Avec l'aide de Jenkins, les organisations peuvent accélérer le processus de développement logiciel grâce à l'automatisation. Jenkins ajoute des processus de cycle de vie de développement de toutes sortes, y compris la construction, la documentation, le test, le package, la mise en scène, le déploiement d'analyses statiques et bien plus encore.

Jenkins réalise la phase d'intégration continue (CI) à l'aide de plugins. Les plugins sont utilisés pour permettre l'intégration de différentes étapes DevOps. Si nous souhaitons intégrer un outil particulier, nous devons installer les plugins dédiés pour cet outil. Par exemple : Maven 2 Project, Git, HTML Publisher, Amazon EC2, etc.

Si une organisation développe un projet, Jenkins testera en permanence les versions de notre projet et mettra en lumière les erreurs dans les premières étapes de notre développement.

Les étapes possibles exécutées par Jenkins sont par exemple :

Effectuer une construction de logiciel à l'aide d'un système de construction comme Gradle ou Maven Apache

Exécuter un script shell

Archiver un résultat de génération

Exécution de tests logiciels

## B - Histoire de Jenkins
En 2011, Oracle qui possédait la société Sun Microsystems a eu un différend avec la communauté open source d'Hudson. Hudson avait une vision bien différente d'Oracle en terme d'engineering et a décidé de bifurquer le projet et d'inaugurer Jenkins.

Hudson et Jenkins ont continué à fonctionner de manière indépendante. Mais en peu de temps, Jenkins a acquis beaucoup de contributeurs et de projets, tandis qu'Hudson n'a conservé que 32 projets. Puis avec le temps, Jenkins est devenu plus populaire, et Hudson n'est depuis plus maintenu.

Jenkins est l'un des outils DevOps CI/CD open source les plus utilisés. Il permet aux développeurs d'implémenter des pipelines CI/CD dans l'environnement de développement de manière complète.
## C - Intégration continue - Livraison continue - Déploiement continu
Le CI/CD (intégration continue/livraison continue) est un processus DevOps holistique (qui s'intéresse à son objet dans sa globalité) et se concentre sur la création d'un mélange compatible entre le cycle de développement et le processus d'exploitation.

Cela se fait en automatisant les flux de travail et en déployant des mises à jour automatiques pour améliorer le retour sur investissement. La mise en œuvre du pipeline CI/CD est l'épine dorsale de l'ensemble des principes DevOps et facilite le processus d'introduction du produit sur le marché plus rapidement que jamais.

### c.1 - Qu'est-ce que l'intégration continue ?
CI pour Continue Integration n'est pas entièrement une condition préalable essentielle requise pour créer un produit logiciel stable. Cependant, il joue certainement un rôle important lors du développement de produits logiciels ou de composants nécessitant des modifications fréquentes. De plus, cela garantit également que tous les composants d'une application sont correctement intégrés.

L'intégration continue est une pratique de développement dans laquelle les développeurs doivent valider les modifications apportées au code source dans un référentiel partagé à intervalles réguliers. Chaque commit effectué dans le référentiel est ensuite construit. Cela permet aux équipes de développement de détecter les problèmes en amont.

L'intégration continue nécessite que les développeurs aient des versions régulières. La pratique générale est que chaque fois qu'une validation de code se produit, une génération doit être déclenchée.

L'intégration continue, qui a d'abord été proposée comme terme par Gary Booch, intègre le code source au référentiel. Cela permet aux développeurs de mener à bien le processus de développement de manière rapide et sophistiquée.
Dans le SDLC (Software Development Life Cycle ou Cycle de vie de développement), CI couvre principalement les phases Source et Build.

Un pipeline CI implique généralement ces étapes :

1 - Détecter les changements dans le code
2 - Analyser la qualité du code source
3 - Construire le code
4 - Exécuter tous les tests unitaires
5 - Exécuter tous les tests d'intégration
6 - Générer des artefacts déployables
7 - État du rapport

Si l'une des étapes ci-dessus échoue, l'intégration s'arrête immédiatement et l'équipe est informée du résultat.

### c.2 - Qu'est-ce que la livraison continue ?
La livraison continue, quant à elle, est un ensemble de pratiques de développement logiciel qui garantit le déploiement du code en production tout en effectuant des tests efficaces au cours du processus. Plus précisément, CD commence là où CI se termine. La livraison continue est chargée de pousser le code vers l'environnement de test où différents tests tels que les tests système, les tests unitaires et les tests d'intégration sont effectués.

Un pipeline CI/CD typique fonctionne en 4 phases répertoriées ci-dessous :

Phase 1 : Commit - il s'agit de la phase réelle au cours de laquelle les développeurs valident les modifications apportées au code.
Phase 2 : Build - dans cette phase, le code source est intégré dans la build à partir du référentiel.
Phase 3 : Automatisation des tests - cette étape fait partie intégrante de tout pipeline CI/CD. Le code source préalablement intégré dans le build est soumis à un cycle de test systématique.
Phase 4 : Déploiement - la version testée est finalement envoyée pour déploiement dans cette phase.

Alors que l'intégration continue couvre les étapes de validation et de construction, la livraison continue, quant à elle, assure l'automatisation des processus ainsi que les tests jusqu'à la phase de déploiement en environnement de développement, de test et de qualité.

La livraison en production quant à elle doit être validé de façon manuelle par un humain dans le processus de livraison continue.

### c.3 - Qu'est-ce que le déploiement continue ?
Le déploiement continu est une méthode qui comprend les mêmes phases que la livraison continue, à la différence qu'elle permet le déploiement automatisé jusqu'à l'environnement de production sans validation humaine. Une entreprise utilisera pour un processus CI/CD le déploiement continue ou alors une livraison continue.

## D - Intégration continu avec Jenkins
Considérons un scénario où le code source complet de l'application a été créé puis déployé sur le serveur de test pour les tests. Cela semble être un moyen parfait de développer des logiciels, bien que ce processus présente de nombreux problèmes :

Les équipes de développeurs doivent attendre que le logiciel complet soit développé pour les résultats des tests.

Il y a de fortes chances que les résultats des tests montrent plusieurs bugs. Il était difficile pour les développeurs de localiser ces bugs, car ils devaient vérifier l'intégralité du code source de l'application.

Cela ralentit le processus de livraison du logiciel.

Les commentaires continus concernant des éléments tels que les problèmes d'architecture ou de codage, les échecs de construction, l'état des tests et les téléchargements de versions de fichiers manquaient, ce qui pouvait entraîner une baisse de la qualité du logiciel.

L'ensemble du processus était manuel, ce qui augmente le risque d'échecs fréquents.

Il ressort clairement des problèmes mentionnés ci-dessus que non seulement le processus de livraison du logiciel est devenu lent, mais que la qualité du logiciel a également diminué. Cela conduit à l'insatisfaction des clients.

Donc, pour corriger ce problème, il était nécessaire d'avoir un système où les développeurs peuvent déclencher en permanence une construction et tester chaque modification apportée au code source.

Jenkins permettra donc de résoudre ce problème. Jenkins est un outil d'intégration continue très mature, alors voyons comment l'intégration continue avec Jenkins a surmonté les lacunes ci-dessus.

Tout d'abord, un développeur valide le code dans le référentiel de code source. Pendant ce temps, le Jenkins vérifie le référentiel à intervalles réguliers pour les changements.

Peu de temps après une validation, le serveur Jenkins trouve les modifications qui se sont produites dans le référentiel de code source. Jenkins dessinera ces changements et commencera à préparer une nouvelle version.

Si la construction échoue, l'équipe concernée en sera informée.
Si la construction réussit, le serveur Jenkins déploie la construction dans le serveur de test.

Après les tests, le serveur Jenkins génère un retour d'information, puis informe les développeurs des résultats de la construction et des tests.

Il continuera à vérifier le référentiel de code source pour les modifications apportées au code source et l'ensemble du processus se répète.

La publication (release) d'un logiciel passe par de nombreuses étapes. La première étape est bien sûr de développer le logiciel en question, ou les nouvelles fonctionnalités. Il faut ensuite souvent passer par une étape de build, qui permet de créer une version exécutable du logiciel à partir du code source. Après le build, des tests sont réalisés. En cas de succès, le logiciel est publié ou déployé.

En cas d'échec, il faudra analyser ce qui a provoqué les erreurs et modifier le code en conséquence pour résoudre les bugs. Toutes ces étapes doivent être réalisées avant chaque release, ce qui peut devenir très lourd, surtout si les releases sont fréquentes.

C'est là qu'intervient Jenkins, qui permet d'automatiser les étapes. En effet, nous modifions les fichiers sources de notre projet et Jenkins nous notifie si les transformations sont un succès ou un échec.

De même, nous pouvons aussi déployer une nouvelle version d'un logiciel sans difficultés. Ainsi les développeurs disposent de plus de temps pour se concentrer sur les phases demandant plus de réflexion.

Jenkins se démocratise de plus en plus, d'une part grâce à son installation qui s'est simplifiée avec le temps et d'autre part, par son association avec divers logiciels importants comme Kubernetes, Docker et Git. De plus, disposant d'une interface graphique depuis le navigateur, son utilisation s'est facilitée.

Enfin, puisqu'il s'agit d'un outil open-source, il est régulièrement mis à jour, comme vous pourrez le constater en allant sur leur GitHub ou leur Docker Hub.

## E - Avantages et inconvénients de l'utilisation de Jenkins
### e.1 - Avantages de Jenkins
C'est un outil open source et gratuit.

Il ne nécessite pas de composants ou dépendances supplémentaires. Cela signifie qu'il est facile à installer.
Il prend en charge 1000 plugins ou plus pour faciliter notre travail. Si un plugin n'existe pas, nous pouvons écrire le script correspondant et le partager avec la communauté.
Il est construit en Java et est donc portable.
Il est indépendant de la plate-forme et est disponible pour toutes les plates-formes et différents systèmes d'exploitation. Comme OS X, Windows ou Linux.

Jenkins prend également en charge l'architecture basée sur le cloud afin que nous puissions déployer Jenkins sur des plates-formes basées sur le cloud.

### e.2 - Inconvénients de Jenkins

Son interface est obsolète et peu conviviale par rapport aux tendances actuelles de l'interface utilisateur.

Pas facile à maintenir car il tourne sur un serveur et nécessite quelques compétences en tant qu'administrateur de serveur pour surveiller son activité.

CI se casse régulièrement en raison de quelques petits changements de réglage. CI sera mis en pause et nécessite donc l'attention de l'équipe de développeurs.

## F - Architecture Jenkins
Jenkins suit l'architecture maître-esclave pour gérer les builds distribués. Dans cette architecture, l'esclave et le maître communiquent via le protocole TCP/IP.

L'architecture Jenkins comporte deux composants :

Jenkins Master
Jenkins Worker


### f.1 - Jenkins Master
Le serveur principal de Jenkins est le Jenkins Master. Il s'agit d'un tableau de bord Web alimenté par un fichier war.

Par défaut, celui-ci fonctionne sur le port 8080. Avec l'aide du Dashboard, nous pouvons configurer les travaux ou/et projets mais la construction de ces travaux a lieu sur les Jenkins Worker. Par défaut, un nœud esclave est configuré et exécuté sur le serveur Jenkins. Nous pouvons ajouter plus de nœuds en utilisant l'adresse IP, le nom d'utilisateur et le mot de passe en utilisant les méthodes ssh, jnlp ou webstart.

Le travail du serveur ou le travail du Master consiste à gérer :

Planification des travaux de construction.

Envoi des builds aux nœuds/esclaves pour l'exécution.

Surveiller les nœuds/esclaves (éventuellement en les mettant en ligne et hors ligne selon les besoins).

Enregistrement et présentation des résultats de construction.

Une instance maître/serveur de Jenkins peut également exécuter directement des tâches de build.

### f.2 - Jenkins Worker
Le Jenkins Worker est utilisé pour exécuter les tâches de build envoyées par le Master. Nous pouvons configurer un projet pour qu'il s'exécute toujours sur une machine esclave particulière, ou un type particulier de machine esclave, ou simplement laisser Jenkins choisir le prochain esclave (nœud) disponible.

Comme nous le savons, Jenkins est développé à l'aide de Java et est indépendant de la plate-forme utilisée. Ainsi, les Jenkins Master et Worker peuvent être configurés sur n'importe quel serveur, y compris Linux, Windows et Mac.
