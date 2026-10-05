Etape 1

1. Le réseau privé permet aux machines virtuelles de pouvoir communiquer entre elles. La passerelle publique permet de se connecter aux machines virtuelles depuis l'extérieur en offrant un point d'entrée.

2. Les différentes catégories permettent d'avoir un outil générique qui s'adapte facilement aux différents cas d'utilisation.

3. Le paquet qui part de l'extérieur passe par le VPN external puis par la passerelle du routerdefault pour rejoindre les machines virtuelles du net-discovery.

Etape 2

1. Autoriser les flux en direction du port 22. Créer une paire de clés SSH. Récupérer la clé privée pour pouvoir se connecter à la vm via ssh. Assigner une adresse IP publique (choisir parmi les adresses ip flotantes) à notre VM. Ensuite se connecter en ssh avec la clé privée et l'ip publique associée à notre vm. 

2. L'adresse IP privée permet de connecter les différentes vm entre elles et avec le routeur. L'IP flottante est une adresse IP qui est attribuable à une VM pour pouvoir y accéder depuis l'extérieur. Les groupes de sécurité correspondent à un firewall, il nous a permit d'autoriser les connexions SSH et les ping via ICMP.  

3. L'objectif des IP flottantes est de combler le manque d'adresses publiques disponibles en pouvant changer la VM associée à l'adresse IP flottante publique. A la différence, une adresse privée est fixée à chaque vm pour maintenir le lien entre les vm.

Etape 3

1. Les security Groups s'appliquent sur l'interface de la VM donc même avec une adresse publique, la dernière règle étant un 'deny_all', il est nécessaire d'ajouter des règles sur le security groups pour ouvrir les ports nécessaires au service. 

2. La requête est envoyée de ma machine vers internet. Elle arrive ensuite sur le routeur via le réseau VPN external qui l'envoie à notre VM via le réseau privé net-discovery. Puis le même chemin est réalisé à l'inverse pour la réponse. 

Etape 4 

1. Un snapshot est une version évoluée d'une image officielle dans laquelle on a par exemple installé des librairies, créé des fichiers… à finir

2. Le redimensionnement permet d'automatiser l'ajustement des ressources sans à avoir à créer un snapshot et recréer une vm à partir de celui-ci. 
On peut ajouter des ressources en cas de besoin sans avoir à réinstaller une VM à partir d'une image et recommencer notre travail. Ou à l'inverse si on a fini de développer un service et que l'on se rend compte qu'on utilise pas toutes les ressources, on peut redimensionner pour économiser des ressources pour d'autres services. 

3. En cas d'améliorations faites par l'admin sur l'image : niveau sécurité, niveau accessibilité … Cela permet de faciliter la duplication de VM sur le même état. 
