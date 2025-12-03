Pour utiliser le playbook install\_squid il faut créer un dossier puis un fichier comme ceci : 



ansible/
├── install_squid.yml
└── templates/
    └── squid.conf.j2

ansible est un dossier
install\_squid.yml est le playbook 
templates est in dossier
squid.conf.j2 est un fichier template pour squid, si il n'est pas présent dans le répertoire le playbook à l'étape 2 ne pourra pas l'utiliser 


LE PROXY MARCHE SEULEMENT VIA FIREFOX : IL FAUT ALLER DANS LES PARAMETRES DE FIREFOX ET RAJOUTER MANUELLEMENT LE PROXY, vous mettez l'ip de votre serveur proxy + le port 3128
https://support.mozilla.org/fr/kb/parametres-connexion-firefox?redirectslug=parametres-de-connexion-de-firefox\&redirectlocale=fr






