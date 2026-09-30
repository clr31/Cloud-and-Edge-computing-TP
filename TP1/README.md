Andrieu Claire / Bos Justin - TP1

Etape 1

1. Une machine virtuelle est une machine virtualisée par un hyperviseur pour donner partager les ressources de la machine hôte. La machine virtuelle contient son propre OS, son propre UserSpace ainsi que les ressources virtuelles qui lui ont été assignées.

2. 	- mutualisation des ressources
	- réduire le nombre de machines physiques

3. La possibilité de créer des snapshots sur une machine virtuelles permet de versionner ses avancements, sauvegarder une machine à un instant donné et gagner en portabilité.

Etape 2

Un conteneur docker permet d'isoler une application sur une machine qui peut être virtuelle. Il contient l'application, ses dépendances, son environnement d'exécution ainsi que ses données applicatives. Il ne contient pas son propre OS mais se base sur celui de la machine hôte. Il fonctionne grâce à un container engine comme Docker  Engine.
Une VM contient son propre OS ce qui la rend plus lourde, lente au démarrage, comparé à un conteneur.
Le container engine permet d'avoir des applications isolées tout en laissant la maintenance de l'OS au fournisseur  Cloud. Cela permet de faciliter la tâche au développeur de l'application.

Etape 3

Cela permet l'automatisation du déploiement des conteneurs ainsi qu'une reproductibilité simplifiée.
Une image est un modèle reproductible de l'environnement alors qu'un conteneur est une application en exécution.

Etape 4

On exécute qu'une commande pour lancer plusieurs conteneurs. Le docker compose permet aussi d'interconnecter les différents conteneurs de manière automatique.
Le yaml décrit les différents conteneurs et donne un port au service qui doit être accéder depuis l'extérieur.
Une limite de docker compose est le fait de ne pas pouvoir couper et relancer un seul service (bug/modification/maintenance…). Cela entraîne une inaccessibilité au service calculator dans notre cas.
De plus, le docker compose est fait pour une topologie simple : pour déployer un grand nombre de conteneurs, la création du yaml peut être redondante.
