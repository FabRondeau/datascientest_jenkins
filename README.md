![alt text](image.png)
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
![alt text](image-1.png)

Tout d'abord, un développeur valide le code dans le référentiel de code source. Pendant ce temps, le Jenkins vérifie le référentiel à intervalles réguliers pour les changements.

Peu de temps après une validation, le serveur Jenkins trouve les modifications qui se sont produites dans le référentiel de code source. Jenkins dessinera ces changements et commencera à préparer une nouvelle version.

Si la construction échoue, l'équipe concernée en sera informée.
Si la construction réussit, le serveur Jenkins déploie la construction dans le serveur de test.

Après les tests, le serveur Jenkins génère un retour d'information, puis informe les développeurs des résultats de la construction et des tests.

Il continuera à vérifier le référentiel de code source pour les modifications apportées au code source et l'ensemble du processus se répète.
![alt text](image-2.png)

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
![alt text](image-3.png)


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

# II - Installation et configuration de Jenkins
## A - Installation de Jenkins
Jenkins est disponible à partir des référentiels Ubuntu et peut être installé directement à l'aide du gestionnaire de packages APT. Nous avons vu que Jenkins est développé en JAVA. Pour vérifier que Java est installé sur notre système, exécutons la commande :
```
java --version
```
Vérifions que Jenkins est bien installé sur notre système et que le service est actif :
```
sudo systemctl status jenkins
```
Vous devriez constater que Jenkins est bien en mode "running". Toutefois, nous vous avons préparé les prochaines étapes pour reproduire l'installation sur votre machine.
### a.1 - Jenkins Master
Puisque Jenkins est basé sur Java, nous devons installer OpenJDK. Pour cela, exécutons la commande :
```
sudo apt update
sudo apt install fontconfig openjdk-17-jre -y
```
Mettre à jour notre machine. Il est recommandé de toujours mettre à jour les packages système.

Exécutons donc la commande :
```
sudo apt update -y
```
Exécutons ensuite :
```
sudo apt upgrade -y
```
Installons à présent Jenkins. Nous ajoutons la clé du référentiel Jenkins à notre système :
```
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins -y
```
Jenkins est démarré lors de l'installation sur notre serveur. Nous pourrons confirmer qu'il est en cours d'exécution en exécutant la commande :
```
sudo systemctl status jenkins
```
À partir de la sortie, nous pouvons voir que Jenkins est opérationnel.

Si Jenkins n'est pas démarré, exécutons la commande ci-dessous pour qu'il soit opérationnel et que le service Jenkins soit activé au démarrage :
```
sudo systemctl enable --now jenkins
```
Jenkins démarrera désormais chaque fois que nous redémarrons ou allumons notre serveur.

## B - Configuration de Jenkins

Connectons-nous au serveur Jenkins à l'aide de notre navigateur, par défaut l'adresse est http://adresseip:8080/, mais si vous êtes sur la machine virtuelle, le port a été changé de 8080 à 9000 pour éviter les conflits, adresseip étant l'adresse IP de votre machine Datascientest, si vous utilisez votre propre machine vous pouvez aller sur localhost.
L'interface Web Jenkins utilise la langue configurée par défaut sur le navigateur du client. Vous pouvez changer ce paramètre à tout moment. Pour simplifier la gestion de nos exercices, nous avons choisi de paramétrer notre navigateur en Anglais.
Nous obtiendrons la première page qui est l'écran "Déverrouiller Jenkins". Afin de configurer Jenkins en toute sécurité, nous devrons coller le mot de passe de l'administrateur.

Nous exécuterons la commande suivante afin de révéler le mot de passe :
```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
Affichage en sortie :
```
943eb6a8472b4e929945a5cb65745f24
```
Copions et collons le mot de passe dans le champ de texte « Administrator Password », comme indiqué. Une fois collé, cliquons sur le bouton « Continuer »:
![alt text](image-4.png)

Une fois que nous avons recopié le mot de passe généré, nous arriverons sur la page suivante :
![alt text](image-5.png)

Sélectionnons le bouton « Install suggested plugin »,
![alt text](image-6.png)

Puis remplissons le formulaire avec les informations requises.

L'écran suivant configure la connexion administrateur, remplissons les informations souhaitées :
![alt text](image-7.png)

Vient ensuite la configuration de l'instance de votre URL Jenkins. Nous pouvons laisser la configuration par défaut.
Cliquons sur commencer à utiliser Jenkins. Nous serons alors redirigés vers l'interface Jenkins :
![alt text](image-8.png)

À gauche se trouve le menu principal permettant d'accéder aux différentes fonctionnalités de Jenkins comme la création de projets, la consultation de l'historique. Nous avons également en haut à droite la configuration de Jenkins.
# III - Configuration de GitHub pour Jenkins

## A - Installation du plugin Github Integration
Jenkins est un serveur CI (intégration continue), ce qui signifie qu'il doit extraire le code source d'un référentiel de code source pour créer un projet. Jenkins offre un excellent support pour divers systèmes de gestion de code source tels que Subversion, CVS, etc.

Github est un référentiel de code basé sur le Web qui joue un rôle majeur dans le DevOps. GitHub fournit une plate-forme commune à de nombreux développeurs travaillant sur le même code ou projet pour télécharger et récupérer le code mis à jour, facilitant ainsi l'intégration continue. Jenkins travaille avec Git via le plugin Git.

Cependant, connecter un référentiel privé GitHub à une instance privée de Jenkins peut s'avérer délicat.

Pour effectuer la configuration de GitHub, assurons-nous que la connectivité Internet est présente sur la machine sur laquelle Jenkins est installé.

Dans l'écran d'accueil de Jenkins (tableau de bord Jenkins), cliquons sur l'onglet à gauche Manage Jenkins.
![alt text](image-9.png)

À présent, cliquons sur Manage plugins. Nous remarquons plusieurs onglets, mais nous allons nous intéresser à l'onglet Plugins. Il s'agit d'une fonctionnalité de Jenkins qui permet d'améliorer son usage.
Il y a plus de 1800 plugins pour Jenkins, parmi ceux-ci, on peut notamment citer les intégrations avec les différents systèmes de contrôle de version (Git, Mercurial, SVN), Kubernetes, Docker et même des services de Cloud Computing (AWS, Azure, GCP).
![alt text](image-10.png)


Dans la page suivante, cliquons sur l'onglet Available. Les plugins sont regroupés dans 4 onglets :

* Mises à jour/Updated qui liste les plugins installés pour lesquels des mises à jour sont disponibles.
* Disponibles/Available qui permet de chercher et d'installer les plugins dont nous avons besoin.
* Installés/Installed qui liste l'ensemble des plugins que nous avons installés.
* Avancé/Advanced qui est une interface plus complexe pour installer des plugins manuellement.

Jenkins fourni également un site qui liste les différents plugins existants, sur lequel nous pourrons trouver une documentation plus détaillée.
![alt text](image-11.png)

L'onglet Available nous donne une liste des plugins disponibles au téléchargement. Dans le champ de recherche, entrons github integration et cochons sur la checkbox afin de sélectionner le plugin github integration:
![alt text](image-12.png)

Cliquons sur "install". Le téléchargement du plug-in prendra un certain temps en fonction de notre connexion Internet et sera installé automatiquement.
![alt text](image-13.png)
![alt text](image-14.png)


Une fois terminé, le plugin sera disponible en option lors de la configuration des jobs.
![alt text](image-15.png)


Faisons de même avec le plugin "Pipeline: Stage View" qui est un plugin nous rajoutant un visuel supplémentaire sur les exécutions de pipeline qui nous sera utile pour la suite :
![alt text](image-16.png)


## B - Intégration de Jenkins avec GitHub
### b.1 - Création du dépôt Github
Nous parlerons à présent du processus d'intégration de GitHub à Jenkins. Nous commencerons par créer un nouveau dépôt sur notre compte Github, si vous n'en avez pas, vous pouvez en créer un à l'adresse de GitHub.

Nous allons donc créer un dépôt afin de pouvoir versionner notre code source et le connecter à Jenkins. Allons sur Github créer un nouveau dépôt appelé Jenkins-datascientest, avec une visibilité public:
![alt text](image-17.png)


Nous pouvons à présent créer notre dépôt en cliquant sur le bouton Create repository. Une fois sur l'interface de dépôt, nous pouvons aller sur les réglages du dépôt en cliquant sur settings.
![alt text](image-18.png)


### b.2 - Qu'est-ce qu'un webhook ?
Les Webhooks sont des notifications déclenchées par des événements. Dans la plupart des cas, ils sont utilisés pour la communication entre les systèmes. C'est le moyen le plus simple de recevoir une alerte lorsqu'un évènement (tentative de connexion, mise à jour...) se passe dans un autre système.

Comment fonctionnent les Webhooks ?

Lorsque nous effectuons un retrait à l'aide d'un guichet automatique, la machine vérifie notre solde et nous donne le montant que nous avons demandé. Une fois cette opération effectuée, notre solde est mis à jour et ce changement déclenche une action. Ensuite, un SMS est envoyé avec les détails du retrait.

C'est ainsi que fonctionnent les Webhooks. Une action sert de déclencheur à une autre action. Le reste est une architecture populaire utilisée pour communiquer entre les systèmes. Un cas d'utilisation populaire consiste à connecter des services Web tels que GitHub et Slack.

Un Webhook est une requête HTTP qui transfère des données lorsqu'elle est déclenchée par un événement et transporte un message vers une destination telle qu'un SMS ou une alerte d'appel téléphonique.

Les Webhooks sont utilisés pour les notifications en temps réel, afin que votre système puisse être mis à jour dès que l'événement a lieu. Ce système est très utilisé dans le DevOps afin d'avoir un suivi granulaire de nos systèmes.

En termes plus techniques, la plupart des Webhooks sont configurés en tant que points de rappel HTTP définis par l'utilisateur. Ils nous permettent d'enregistrer une URL http:// ou https:// où les données d'événements peuvent être stockées aux formats JSON ou XML.

Nous pourrons faire ce que nous voulons avec les données que nous récupérons et stockons à partir d'un certain événement.

La mécanique de base des Webhooks consiste à envoyer une requête HTTP à l'URL spécifiée par l'utilisateur, ensuite, un webhook effectue un callback HTTP vers une URL qui doit être configurée par le système qui reçoit les données.

Cette URL de webhook est appelée point de terminaison de webhook. Les points de terminaison Webhook doivent être publics pour être accessibles, et il est important que cette URL appartienne au système récepteur. Le rappel est déclenché chaque fois qu'il y a un événement dont vous souhaitez informer un autre système.

Nous allons donc le mettre en place sur Github afin d'alerter notre instance de Jenkins.

Nous pouvons à présent cliquer sur webhooks.
![alt text](image-19.png)


Nous pouvons cliquer sur Add Webhook.
![alt text](image-20.png)


Dans le formulaire, nous devons remplir le champ Payload URL. Nous allons donc remplir ce champ avec la combinaison suivante :

Votre url Jenkins : http://votreadesseip:8080/
L'endpoint github-webhook
Le contenu complet sera donc http://votreadesseip:8080/github-webhook/. Vous devrez remplacer votreadresseip par l'adresse IP de votre serveur.

Pour le champ Content type, nous choisirons application/json.
![alt text](image-21.png)


À présent, nous devons configurer les évènements qui alerteront Jenkins et déclencheront nos jobs de construction.

Sur la partie Which events would you like to trigger this webhook?, nous choisirons Let me select individual events afin de choisir nous-même les évènements déclencheurs.

Nous cocherons les cases suivantes :

Branch or tag creation

Branch or tag deletion

Packages

Pull request review comments

Pull requests

Pull request reviews

Pushes

Registry packages

Une fois toutes ces cases cochées, nous pouvons enregistrer notre Webhook en cliquant sur le bouton Add Webhook.



Kubernetes et Docker doivent être installés sur votre machine Jenkins DataScientest, les étapes "c" et "d" vous donnent les commandes pour reproduire l'environnement sur votre machine personnelle

Vous pouvez le vérifier avec les commandes suivantes :
```
k3s kubectl get nodes
```
Nous devons ensuite ajouter l'utilisateur Jenkins au groupe Docker afin que Jenkins puisse piloter le Docker engine :
```
sudo usermod -aG docker jenkins
```
Nous créerons ensuite les Namespaces dans lesquelles nous ferons nos déploiements au sein de Kubernetes depuis Jenkins. Nous allons en créer 03, dev, staging et prod :
```
sudo chmod 755 /etc/rancher/k3s/k3s.yaml
kubectl create namespace dev
kubectl create namespace staging
kubectl create namespace prod
```
Si vous utilisez la machine Jenkins de DataScientest et que les commandes ci-dessus fonctionnent, rendez-vous à la section "e - Docker Hub"


## C - Installation de Kubernetes
La mise en œuvre d'un pipeline CI/CD avec les fonctionnalités d'automatisation de Kubernetes présente de nombreux avantages. Les développeurs peuvent facilement corriger les mises à jour, résoudre les problèmes de panne en cas de pic de trafic imprévu et améliorer l'efficacité des ressources.

Kubernetes devenant de plus en plus populaire de jour en jour, tous les fournisseurs d'outils CI/CD matures développent de nouvelles fonctionnalités à intégrer à Kubernetes. Lorsque nous recherchons un outil de pipeline CI/CD Kubernetes, il est essentiel de déterminer des facteurs tels que le type de déploiement (options sur site ou dans le cloud), la facilité d'utilisation et la prise en charge de différents systèmes d'exploitation.

En ce qui concerne la facilité d'utilisation et la mise en œuvre d'une pratique DevOps unique, Jenkins est l'un des meilleurs paris si nous avons besoin d'une intégration et d'une prise en charge avancées pour différentes plates-formes.

Nous utiliserons une version extrêmement légère de Kubernetes appelé k3s dans ce cours. K3s est une distribution Kubernetes développée par Rancher.

En tant que version allégée de Kubernetes, K3s consomme moins de ressources que les distributions traditionnelles, ce qui lui permet de bien fonctionner sur de petites machines individuelles telles que des ordinateurs portables ou des ordinateurs de bureau. K3s est également plus facile que les autres distributions Kubernetes à configurer et à gérer à bien des égards.

Sa capacité à fonctionner sur pratiquement n’importe quel appareil et son processus simple (suffisamment pour fonctionner sur une Raspberry Pi) rendent K3s pratique pour ceux qui découvrent Kubernetes et souhaitent le tester.

Cela dit, K3s n'est pas seulement destiné aux tests et à l'expérimentation. Il peut également servir de distribution Kubernetes prête pour la production qui peut évoluer pour fonctionner sur de grands réseaux d'appareils. Rancher promeut K3s en tant qu'option Kubernetes pour les infrastructures IoT et de périphérie en raison de ses faibles besoins en ressources, ainsi que de sa prise en charge des appareils ARM64 et ARMv7.

Kubernetes est déjà installé sur les machines virtuelles fournies, cette section sert pour ceux qui utilisent leurs ordinateurs personnels. Vous pouvez le vérifier avec la commande sudo kubectl version
Nous pouvons tout installer avec la commande suivante :
```
curl -sfL https://get.k3s.io | sh -s - --write-kubeconfig-mode 644
```
Nous pouvons à présent vérifier l’installation de Kubernetes :
```
sudo kubectl version
```
Affichage en sortie :
```
Client Version: v1.25.4+k3s1
Kustomize Version: v4.5.7
Server Version: v1.25.4+k3s1
```
Nous parlerons de Kustomize dans la suite de ce cours.

K3s nous fournit un nœud sur lequel nous avons l’ensemble des composants d’un cluster, c’est une installation "tout-en-un" sur laquelle nous avons un master et worker en une seule instance.

Pour effectuer cette vérification, nous pouvons exécuter la commande suivante :
```
k3s kubectl get nodes
```
Kubernetes s'est considérablement développé, tout comme l'écosystème qui le soutient. Récemment, Helm a reçu le statut de diplômé de la Cloud Native Computing Foundation (CNCF), ce qui montre sa popularité croissante parmi les utilisateurs. Nous allons l'installer sur notre cluster Kubernetes grâce aux commandes suivantes :
```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```

![alt text](image-22.png)
## D - Installation de Docker
Docker est une plate-forme parfaitement adaptée à l'écosystème DevOps. C'est une solution appropriée pour les éditeurs de logiciels qui ne peuvent pas suivre le rythme de l'évolution de la technologie, des activités et des besoins des clients. Cela fait de Docker un choix évident pour développer et accélérer les opérations dans une entreprise.

La raison du succès de Docker dans l'environnement DevOps est sa capacité à conteneuriser les applications. Cela réduit le temps de développement et de publication d'une solution pour une société de développement de logiciels.

Il est utile pour surmonter les défis de l'environnement "Dev" et "Ops". Il permet à une application de s'exécuter sur n'importe quelle application, quelles que soient les configurations d'hôte. Cela permet à toutes les équipes de collaborer tout en travaillant efficacement.

Docker nous permet de rationaliser et de contrôler les modifications tout au long du cycle de développement. Nous pouvons l'utiliser tout au long des étapes de développement, de production et de publication. Si nous souhaitons revenir à une version précédente, vous pouvez le faire en utilisant Docker.

Nous pouvons également nous assurer qu'une fonctionnalité fonctionne dans l'environnement de production selon qu'elle est opérationnelle ou non dans l'environnement de développement.

Docker est déjà installé sur les machines virtuelles fournies, cette section sert pour ceux qui utilisent leurs ordinateurs personnels. Vous pouvez le vérifier avec la commande docker -v
Nous allons installer Docker à fin que Jenkins puisse être utilisé pour manipuler nos différentes images Docker. Nous installerons Docker en nous servant des commandes suivantes :
```
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
# Add the repository to Apt sources:
echo   "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" |   sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo systemctl enable --now docker
```
Nous devons ensuite ajouter l'utilisateur Jenkins au groupe Docker afin que Jenkins puisse piloter le Docker engine.

Nous le ferons de la façon suivante :
```
sudo usermod -aG docker jenkins
```

## E - Docker Hub
Docker Hub est un registre Docker, une version hébergée dans le cloud, une application côté serveur open-source, évolutive et sans état.

Il peut gérer le partage et le stockage des images Docker. À l'aide de Docker, les développeurs peuvent y accéder en tant que public et créer leur propre espace de référentiels privés et automatiser les fonctions personnalisées de création d'applications, les groupes de travail et les webhooks.

Un développeur formé aux pratiques DevOps peut télécharger l'image officielle du conteneur du système de base de données orienté document MongoDB depuis Docker Hub pour s'entraîner sur une application déployée dans les conteneurs par exemple.

### e.1 - Fonctionnalités du hub Docker
* Référentiels : il contient le processus Push et Pull pour les images de conteneurs.
* Équipes et organisations : il permet au développeur/utilisateur d'accéder à des référentiels privés d'images de conteneurs.
* Images officielles de Docker : il extrait et utilise des images de conteneurs de haute qualité rendues par Docker.
* Images d'éditeur vérifiées par Docker : il extrait et utilise des images de conteneurs de haute qualité rendues par des fournisseurs externes.
* Builds : il fournit les mécanismes qui formulent automatiquement des images de conteneur à partir de Bitbucket et GitHub et les poussent vers Docker Hub.
* Webhooks : il déclenche certaines actions après une poussée réussie vers un conteneur pour combiner Docker Hub avec des services supplémentaires.

Docker implémente un outil Docker Hub CLI qui est actuellement expérimental et une API (Micro-service) qui nous permet de communiquer avec Docker Hub. Nous pouvons parcourir la documentation de l'API Docker Hub pour rechercher les points de terminaison entre accolades.

Vous pouvez créer un compte Dockerhub à l'adresse suivante : https://hub.docker.com/signup. Nous nous en servirons dans la suite de notre cours.