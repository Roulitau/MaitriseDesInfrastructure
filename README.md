# MaitriseDesInfrastructure

Séminaire maitrise des infrastructures.

# Machine nécessaire :

Routeur                                                             [Luc E]

Serv (10.0.1.0/24) :
DHCP (dhcpd) 1.2                                        [Killian, Gauthier]
DNS (bind9) 1.3                                            [Luc, Loqman]
Proxy (squid) 1.5                                          [Cyril]
App (Apache ou Ngnix) 1.4                       [Julien]

DMZ (10.0.2.0/24) :
Reverse Proxy (ngnix)                                [Arthur, Gwen]

Classe (10.0.0.0/24) :
PC cours (Debian)                                       [Luc E]

Net (10.0.3.0/24) :
netsoutet (linux + ip forwarding)            [Kévin]
