Mise en place d’un réseau local d’entreprise (Rudy and Theodor Company)

1. Contexte et objectif
Dans le cadre de la SAE 1.02, le projet consiste à concevoir et configurer l’infrastructure réseau d’une succursale de l’entreprise Rudy and Theodor Company. L’objectif est de fournir un réseau local structuré, sécurisé et fonctionnel, capable d’accueillir différents profils d’utilisateurs et de garantir l’accès aux services essentiels de l’entreprise. Ce projet couvre la configuration des équipements réseau (routeur, commutateur), la segmentation logique (VLAN), l’adressage IP, la mise en place d’un serveur Linux et la gestion des accès selon les besoins métiers.

2. Topologie du réseau
La topologie mise en place est la suivante :
    Un routeur Cisco (R1), point de connexion entre la succursale et le réseau de l’entreprise.
    Un commutateur Cisco 2960, centralisant la distribution des connexions filaires et la gestion des VLAN.

    Quatre segments principaux :
        Direction VPC (groupe Direction)
        Utilisateurs VPC (groupe Utilisateurs)
        Administrateur VPC (groupe Administrateur)
        Serveur Linux (hébergement des services réseau internes)

Chaque groupe est connecté à un port spécifique du commutateur, et chaque port est associé à un VLAN dédié pour garantir l’isolation et la sécurité des communications internes.

3. Segmentation logique et VLAN
La segmentation du réseau repose sur quatre VLAN principaux :

    VLAN	  Nom	              Utilisation	              Exemple de poste connecté
    10	    Direction	        Direction/Admin	          Direction VPC
    20	    Utilisateurs	    Employés standards	      Utilisateurs VPC
    30	    Serveurs	        Services réseau	          Serveur Linux
    40	    Administrateur	  Administration réseau	    Administrateur VPC

Chaque VLAN est configuré sur le commutateur avec une plage d’adresses IP adaptée au nombre d’hôtes, selon le plan d’adressage de l’entreprise (ex : 172.20.x.0/24 pour la succursale).

4. Adressage IP
    Direction (VLAN 10) : sous-réseau /29 (jusqu’à 6 hôtes)
    Utilisateurs (VLAN 20) : sous-réseau /26 ou /27 selon le nombre d’utilisateurs
    Serveurs (VLAN 30) : sous-réseau /29
    Administrateur (VLAN 40) : sous-réseau /29

Le serveur Linux reçoit une adresse fixe, tandis que les postes des VLAN Direction et Utilisateurs peuvent obtenir leur adresse par DHCP, initialement fourni par le commutateur puis migré sur le serveur Linux.

5. Configuration des équipements
    Routeur R1 : Configuration des sous-interfaces pour chaque VLAN avec encapsulation dot1Q, routage inter-VLAN, et gestion des passerelles par défaut pour chaque segment.
    Commutateur : Création et attribution des VLAN, configuration des ports en mode access, configuration d’un port trunk pour la liaison avec le routeur, activation du spanning-tree, et mise en place des adresses IP sur les interfaces VLAN pour la gestion locale.
    Serveur Linux : Installation et configuration du service DHCP pour distribuer les adresses dynamiques aux VLAN concernés, hébergement de services réseau internes.

6. Services et fonctionnalités
    DHCP : Attribution automatique des adresses IP pour Direction et Utilisateurs, d’abord via le commutateur puis via le serveur Linux.
    Routage inter-VLAN : Assuré par le routeur, permettant la communication contrôlée entre les différents segments.
    Sécurité : Isolation des VLAN, contrôle des accès selon le profil utilisateur (ex : seuls les administrateurs peuvent accéder à l’ensemble des équipements réseau).

7. Tests et validation
    Connectivité : Vérification de la communication entre les postes d’un même VLAN et entre VLAN différents (ping, traceroute).
    DHCP : Test de l’attribution d’adresses sur les postes Direction et Utilisateurs.
    Routage : Validation du routage inter-VLAN et de la connectivité vers le serveur Linux.
    Sécurité : Vérification de l’isolation des VLAN et des accès selon les droits.

8. Compétences mobilisées
    Conception de topologie physique et logique.
    Configuration avancée des équipements Cisco (routeur, commutateur).
    Mise en œuvre de la segmentation réseau (VLAN, sous-réseaux).
    Installation et administration de services réseau sur Linux.
    Tests de connectivité et validation fonctionnelle.

9. Conclusion
Ce projet illustre la démarche complète de mise en place d’un réseau d’entreprise, de la conception à la validation finale, en passant par la configuration, la sécurisation et la gestion des services essentiels. Il met en avant la capacité à répondre à des besoins concrets en entreprise et à garantir la robustesse et la sécurité de l’infrastructure réseau.
