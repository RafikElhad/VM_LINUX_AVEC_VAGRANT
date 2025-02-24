Création de VM Linux avec Vagrant


<img width="621" alt="vagrant file" src="https://github.com/user-attachments/assets/ea4c5f97-5d81-423c-b253-19ff5c7caba3" />


Un Vagrantfile est un fichier de configuration écrit en Ruby qui permet de créer et gérer une machine virtuelle (VM) avec Vagrant. Ici, on définit une VM nommée "server", basée sur Ubuntu 14.04 LTS (Trusty 64 bits). On désactive la mise à jour automatique de la box et on configure deux types de réseau : port forwarding (8080 dans la VM accessible via 8082 sur l’hôte) et une IP fixe privée (192.168.0.10). Un dossier local (./tomcatwebapps) est synchronisé avec /opt/tomcat/webapps dans la VM pour faciliter le partage de fichiers. La VM tourne sous VirtualBox avec les paramètres suivants : pas d’interface graphique, nom "webserver-tomcat", 1 Go de RAM. 

- Objectif : créer un environnement de développement automatisé pour héberger une application web.
  

<img width="573" alt="validate" src="https://github.com/user-attachments/assets/7ff39f07-db8f-49e1-a39f-763c01be241b" />


La commande vagrant validate vérifie la syntaxe et la configuration du fichier Vagrantfile se trouvant dans le répertoire actuel (D:\Cours M2GL ISI\Devops\vagrant\install-jdk-tomcat-on-ubuntu).
Le résultat nous montre que le fichier Vagrantfile a été validé avec succès : "Vagrantfile validated successfully."
Cette commande garantit que le fichier de configuration utilisé par Vagrant (Vagrantfile) est correct, sans erreurs de syntaxe ou de configuration. C'est une étape importante avant d'utiliser des commandes comme vagrant up pour démarrer une machine virtuelle.
Cette capture est utile pour montrer que l'environnement de développement est correctement configuré et que le fichier Vagrantfile est prêt à être utilisé.


<img width="641" alt="vagrant up" src="https://github.com/user-attachments/assets/374887cd-116c-4fee-b2b3-8b31b2a89f7a" />


La commande vagrant up démarre une machine virtuelle (VM) "server" avec VirtualBox.

- Configuration réseau : Un adaptateur NAT (Internet) et un adaptateur Hostonly (accès depuis l’hôte).
- Redirection des ports : 8080 (VM) → 8082 (hôte) et 22 (SSH) → 2222 (hôte).
- Connexion SSH : Après quelques tentatives, la connexion réussit.
- Dossiers partagés : /vagrant synchronisé avec un dossier local, et /opt/tomcat/webapps également partagé.
- Provisioning : Des scripts/configurations ont été exécutés au démarrage, et peuvent être relancés avec vagrant provision.

  Objectif : Automatiser le déploiement d’un environnement de développement avec Vagrant.


<img width="504" alt="ssh" src="https://github.com/user-attachments/assets/fb190499-b810-4772-8857-64ac479681d5" />



La commande vagrant ssh nous permet de se connecter en SSH à la machine virtuelle Ubuntu 14.04 LTS sans authentification manuelle.

- Informations système : Noyau Linux 3.13.0-170 (64 bits).
- Documentation et mises à jour : Un lien vers la doc Ubuntu est fourni. ESM non activé, aucune mise à jour disponible, et une nouvelle version (16.04 LTS) est proposée.
- Commande pwd : Affiche le répertoire courant /home/vagrant, qui est celui de l’utilisateur par défaut.
- Objectif : Accéder à la VM pour effectuer des configurations et exécuter des commandes. 🚀

