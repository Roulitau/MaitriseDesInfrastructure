Pour utiliser le playbook install\_squid il faut créer un dossier puis un fichier comme ceci : 

ansible 
-> install\_squid.yml
-> templates
      -> squid.conf.j2 

ansible est un dossier
install\_squid.yml est le playbook 
templates est in dossier
squid.conf.j2 est un fichier template pour squid, si il n'est pas présent dans le répertoire le playbook à l'étape 2 ne pourra pas l'utiliser 

Dans le fichier squid.conf.j2 : 

# templates/squid.conf.j2

\# Port d'écoute par défaut

http\_port 3128



\# ----------------- 1. DÉCLARATION DE TOUTES LES ACLs -----------------



\# ACL 1: Liste des domaines à bloquer

acl domains\_bloques dstdomain .amazon.fr .amazon.com



\# ACL 2: Identification de la méthode de connexion chiffrée

acl CONNECT method CONNECT



\# ACL 3: Définition des ports SSL/sécurisés

acl SSL\_ports port 443 563



\# ACL 4: Accès pour le réseau du proxy (VMs)

acl vm\_lan src 192.168.190.0/24



\# ACL 5: Accès spécifique pour le PC client

acl client\_pc src 10.213.119.200





\# ----------------- RÈGLES D'ACCÈS (http\_access) - L'ORDRE est CRUCIAL -----------------



\# 1. RÈGLE D'INTERDICTION HTTPS : Bloquer les requêtes CONNECT vers Amazon

http\_access deny CONNECT domains\_bloques



\# 2. RÈGLE D'INTERDICTION HTTP : Bloquer les requêtes HTTP standard vers Amazon

http\_access deny domains\_bloques



\# 3. RÈGLE D'INTERDICTION DE BASE : Bloquer les requêtes CONNECT vers des ports non sécurisés (bonne pratique)

http\_access deny CONNECT !SSL\_ports





\# 4. RÈGLES D'AUTORISATION : Autoriser les réseaux définis pour le trafic restant

http\_access allow vm\_lan

http\_access allow client\_pc



\# 5. RÈGLE DE SÉCURITÉ : Refuser tout le reste

http\_access deny all



\# Option de caching

cache\_dir ufs /var/spool/squid 100 16 256



LE PROXY MARCHE SEULEMENT VIA FIREFOX : IL FAUT ALLER DANS LES PARAMETRES DE FIREFOX ET RAJOUTER MANUELLEMENT LE PROXY, vous mettez l'ip de votre serveur proxy + le port 3128
https://support.mozilla.org/fr/kb/parametres-connexion-firefox?redirectslug=parametres-de-connexion-de-firefox\&redirectlocale=fr


