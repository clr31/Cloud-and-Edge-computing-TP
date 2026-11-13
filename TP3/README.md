Etape 1

1. La VM-K8s est les master du cluster Kubernetes. Il permet de relier les autres machines depuis l'extérieur car il a une IP flottante publique. Son rôle est de maintenir l'état du cluster, prendre les décisions de déploiement et de monitorer le cluster. 

2. Les labels permettent d'identifier facilement les workers.

3. Configuration du réseau : Création du bridge et initalisation des règles pour nous permettre d'utiliser les services des workers
Initialisation du cluster : création du groupe master+workers 
Installation du réseau de pods : permet de créer des pods sur chaque worker 

Etape 2

1. Un Deployment Kubernetes décrit ce que Kubernetes doit exécuter : quelle image conteneur utiliser, combien de replicas (Pods) créer, comment les identifier, où les exécuter... Le Deployment permet d'automatiser de déploiement des pods en pouvant préciser le nombre de répliques (utile pour edge-1 et 2). Il est donc préférable de ne pas déployer chaque pod un par un.

2. Le targetPort correspond au port du pod. Le port du service est celui qui permet de communiquer avec le worker depuis l'intérieur du cluster.

3. Une ressource Service permet de donner un accès stable au pod dans le cluster, elle garantit l'accès au pod même s'il est supprimé puis recréé sur une autre machine virtuelle du cluster. La ressource Ingress permet quant à elle d'accéder aux services depuis l'extérieur du cluster.

4. Une requête pour l'application envoyée depuis l'extérieur utilise le port 30080 avec l'adresse IP flottante attribuée au master. L'Ingress controller du master redirige ensuite cette requête vers l'IP privée de la machine accueillant le worker son port de type clusterIP (80). Enfin, la requête est envoyée au pod sur le port 5000 (targetPort) qui contient le conteneur sur lequel l'application écoute sur un port (containerPort).

Etape 3
