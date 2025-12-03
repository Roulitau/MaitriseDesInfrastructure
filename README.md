# 🚧 Séminaire : Maîtrise des Infrastructures 🚧

Ce dépôt contient l'ensemble des configurations, scripts et documentations relatifs à l'infrastructure réseau mise en place dans le cadre du séminaire "Maîtrise des Infrastructures".

L'objectif de ce projet est de concevoir, déployer, configurer et sécuriser une architecture réseau multi-zones intégrant les services d'infrastructure fondamentaux (Routage, DHCP, DNS, Proxy, Serveurs Web).

---

## 🗺️ Architecture et Plan d'Adressage

L'infrastructure est articulée autour d'un **Routeur central** et de **quatre réseaux distincts**, garantissant la segmentation et la sécurité des services.

| Nom du Réseau | CIDR | Plage d'Adresses | Gateway | Rôle Principal |
| :--- | :--- | :--- | :--- |
| **Classe** | `10.0.0.0/24` | `10.0.0.1` à `10.0.0.253`| '10.0.0.254' | Postes clients de cours (zone de travail). |
| **Serv** | `10.0.1.0/24` | `10.0.1.1` à `10.0.1.253` | '10.0.1.254' | Hébergement des services internes critiques (DHCP, DNS, Proxy, Application). |
| **DMZ** | `10.0.2.0/24` | `10.0.2.1` à `10.0.2.253` | '10.0.2.254' |Zone Démilitarisée. Sert de tampon pour les services accessibles depuis l'extérieur (Reverse Proxy). |
| **Net** | `10.0.3.0/24` | `10.0.3.1` à `10.0.3.253` | '10.0.3.254' | Simule le réseau externe (Internet). |

### 🔗 Matériel Clé

* **Routeur :** Machine centrale assurant l'interconnexion et le filtrage (firewalling) entre toutes les zones.
* **Système d'Exploitation Général :** Debian (pour la majorité des serveurs et clients).

---

## 💻 Machines et Services Détaillés

Le tableau ci-dessous liste les machines déployées, leur rôle, leur adresse IP prévue et les responsables de leur configuration.

### 🌐 Routeur (Point Central)

* **Responsable :** **Luc E.**
* **Rôle :** Routage inter-zones, configuration du pare-feu.

### 🖥️ Réseau **Serv** (`10.0.1.0/24`)

| Service | Logiciel | Adresse IP | Responsables |
| :--- | :--- | :--- | :--- |
| **DHCP** (Serveur) | `dhcpd` | `10.0.1.2` | **Killian, Gauthier** |
| **DNS** (Serveur) | `bind9` | `10.0.1.3` | **Luc, Loqman** |
| **Application** (Web) | `Apache` ou `Nginx` | `10.0.1.4` | **Julien** |
| **Proxy** (Forward) | `squid` | `10.0.1.5` | **Cyril** |

### 🛡️ Réseau **DMZ** (`10.0.2.0/24`)

| Service | Logiciel | Responsables |
| :--- | :--- | :--- |
| **Reverse Proxy** | `Nginx` | **Arthur, Gwen** |

### 🧑‍💻 Réseau **Classe** (`10.0.0.0/24`)

| Machine | Système | Responsable |
| :--- | :--- | :--- |
| **PC cours** | Debian | **Luc E.** |

### 🌍 Réseau **Net** (`10.0.3.0/24`)

| Machine | Configuration | Responsable |
| :--- | :--- | :--- |
| **netsoutet** | Linux + IP Forwarding | **Kévin** |

---

## ✅ Objectifs et Livrables

Chaque équipe est responsable de la documentation complète (fichiers de configuration, procédures d'installation, tests de validation) de son service.

### 🎯 Objectifs Clés

1.  **Routage Fonctionnel :** Assurer la communication entre toutes les zones, y compris l'accès au réseau `Net`.
2.  **Sécurité :** Mise en place de règles de firewalling strictes sur le routeur pour isoler les zones (ex: `Classe` ne peut pas accéder directement à `Serv` sauf pour DNS/DHCP/Proxy).
3.  **Accès Web Sécurisé :** Les clients (`Classe`) doivent passer par le Proxy (`10.0.1.5`) pour accéder à l'extérieur (`Net`).
4.  **Application Accessible :** L'application sur `10.0.1.4` doit être accessible de l'extérieur via le Reverse Proxy en DMZ (`10.0.2.x`).

---

## 📂 Structure du Dépôt

* `configs/` : Fichiers de configuration bruts (`dhcpd.conf`, `named.conf`, `squid.conf`, configurations Nginx, règles de firewalling, etc.).
* `docs/` : Documentation détaillée, schémas réseau (à jour), procédures d'installation et de validation des services.
* `scripts/` : Scripts d'automatisation ou de déploiement si utilisés.
* `README.md` : Ce fichier.

---

## 🤝 Équipe et Contacts

| Rôle | Nom(s) |
| :--- | :--- |
| **Routeur/Architecture** | Luc E. |
| **Services Réseau** | Killian, Gauthier (DHCP), Luc, Loqman (DNS), Cyril (Proxy) |
| **Services Applicatifs** | Julien (App), Arthur, Gwen (Rev Proxy) |
| **Internet/Sortie** | Kévin (netsoutet) |
