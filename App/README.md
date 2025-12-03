# 📁 App – Assets et Configurations pour le Déploiement Web

Ce répertoire contient tous les actifs (Assets), les playbooks Ansible spécifiques et les templates de configuration nécessaires pour déployer une application web simple sur deux types de serveurs différents : **Apache** et **Nginx**.

---

## 🚀 Vue d'ensemble

Le répertoire `App` agit comme une bibliothèque de composants de déploiement, permettant de valider l'infrastructure provisionnée par Terraform en y déployant une page de test :
* Le déploiement est géré par des **playbooks Ansible dédiés**.
* Chaque serveur web a son propre répertoire et son template de page web.

---

## 📂 Structure du Répertoire

| Chemin | Type | Description |
| :--- | :--- | :--- |
| `apache/` | Dossier | Contient les actifs pour le déploiement via Apache. |
| `apache/deploy_apache.yml` | Fichier | Le **Playbook Ansible** qui gère l'installation, la configuration et le déploiement du site sur un serveur Apache. |
| `apache/templates/` | Dossier | Contient les templates Jinja2 pour Apache. |
| `apache/templates/index.html.j2` | Template | Template Jinja2 pour la page d'accueil d'Apache. Le suffixe `.j2` indique qu'Ansible le traitera pour y insérer des variables. |
| `nginx/` | Dossier | Contient les actifs pour le déploiement via Nginx. |
| `nginx/deploy_nginx.yml` | Fichier | Le **Playbook Ansible** qui gère l'installation, la configuration et le déploiement du site sur un serveur Nginx. |
| `nginx/templates/` | Dossier | Contient les templates Jinja2 pour Nginx. |
| `nginx/templates/index.html.j2` | Template | Template Jinja2 pour la page d'accueil de Nginx. |

---

## ⚙️ Déploiement Ansible

Chaque playbook de ce répertoire est conçu pour être exécuté séparément, ciblant des groupes d'hôtes spécifiques définis dans le fichier `inventory.ini` global.

### Déploiement sur Apache

Utilisez ce playbook pour configurer les serveurs destinés à Apache :

```bash
ansible-playbook -i ../inventory.ini apache/deploy_apache.yml
