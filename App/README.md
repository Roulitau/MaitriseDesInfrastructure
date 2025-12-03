# 📁 App – Code Source de l'Application Web

Ce répertoire contient les fichiers sources de l'application web simple destinée à être déployée sur l'infrastructure gérée par Ansible et Terraform dans le cadre du projet **Maitrise Des Infrastructure**.

---

## 🚀 Vue d'ensemble

Cette application sert de page de test (Hello World) pour valider le bon fonctionnement du pipeline de déploiement et de la configuration du serveur web (Apache ou Nginx). Elle est conçue pour être minimaliste et facile à déployer.

---

## 📂 Structure du Répertoire

| Fichier | Description |
| :--- | :--- |
| `app.py` | Le script principal de l'application (probablement une application Python Flask ou équivalente). Il gère le routage et l'affichage de la page web. |
| `index.html` | Le template HTML de la page d'accueil. C'est le contenu web qui est servi aux utilisateurs. |
| `config.py` | Fichier de configuration de l'application. Peut contenir des variables d'environnement, des clés secrètes, ou des paramètres de connexion. |

---

## 🛠️ Prérequis

Pour exécuter cette application localement ou pour la préparer au déploiement, vous aurez besoin de :

* **Python 3.x**
* (Si l'application utilise Flask) Les dépendances listées dans un éventuel fichier `requirements.txt`.

---

## 💻 Exécution Locale

Pour tester l'application avant le déploiement sur l'infrastructure distante :

1.  **Cloner le dépôt et accéder au dossier :**
    ```bash
    git clone [https://github.com/Roulitau/MaitriseDesInfrastructure.git](https://github.com/Roulitau/MaitriseDesInfrastructure.git)
    cd MaitriseDesInfrastructure/App
    ```

2.  **Installer les dépendances (si vous avez un `requirements.txt`) :**
    ```bash
    # pip install -r requirements.txt
    ```

3.  **Lancer l'application :**
    ```bash
    python3 app.py
    ```

> L'application devrait être accessible via votre navigateur à l'adresse `http://127.0.0.1:5000` (ou le port défini dans `app.py`).

---

## ⚙️ Déploiement

Cette application est destinée à être déployée automatiquement sur l'infrastructure cloud/virtuelle gérée par :

1.  **Terraform :** Pour le provisionnement des machines virtuelles.
2.  **Ansible :** Pour la configuration du serveur web, l'installation des dépendances, et la copie des fichiers de ce répertoire vers l'hôte cible.

*Les détails du déploiement se trouvent dans le répertoire racine du projet, notamment dans les playbooks Ansible.*
