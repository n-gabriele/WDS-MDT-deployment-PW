# 💻 Déploiement Automatisé de Windows avec WDS & MDT  
📂 TP Réalisé par : Ventre & Gabriele – BTS SIO SISR

---

## 🎯 Objectif du TP

Le but de ce TP est clair :  
**Automatiser l’installation de Windows 10 Entreprise 64 bits** sur une vingtaine de nouveaux postes **sans intervention manuelle**, grâce aux outils professionnels **WDS** (Windows Deployment Services) et **MDT** (Microsoft Deployment Toolkit).

En entreprise, un déploiement manuel prend du temps, génère des erreurs, et est difficilement reproductible. Ici, on met en place **une solution centralisée, rapide, homogène et évolutive**.

---

## 🧱 Contexte professionnel

🏢 **Stadium Company** renouvelle ses postes administratifs.  
🖥️ Les nouveaux ordinateurs arrivent sans système installé.  
📦 Objectif : les rendre 100 % opérationnels via une installation réseau automatisée.

---

## 🛠️ Les technologies utilisées

| Outil | Rôle |
|------|------|
| **Windows Server 2019** | Serveur principal pour l’hébergement WDS + MDT |
| **WDS** | Démarrage PXE + déploiement d’images système |
| **MDT** | Création des séquences de tâches + automatisation |
| **Active Directory** | Organisation et rattachement automatique des postes |
| **Windows PE (WinPE)** | Système de boot réseau allégé |
| **ADK** | Kit Microsoft pour créer les environnements d’installation |
| **VMware** | Virtualisation des serveurs et clients pour tests |

---

## 🧩 Étapes principales du projet

### 1. 🧮 Préparation du serveur
- Ajout d’un disque dur dédié (G:) pour stocker les images
- Formatage, nommage et partage sécurisé du disque
- Création d’un utilisateur dédié (`MDTuser`) avec droits limités
- Création d’une OU spécifique (`MDTdeploy`) dans l’AD

### 2. 🏗️ Installation de l’environnement de déploiement
- Ajout du rôle **WDS** sur Windows Server
- Configuration du PXE, TFTP, DHCP, sécurité réseau
- Téléchargement et installation de **l’ADK** et de **MDT**

### 3. 🧪 Création de l’image & séquence de tâches
- Import d’une image `.WIM` personnalisée de Windows 10
- Création d’une **séquence de tâches complète** (paramètres, nom machine, langue, admin…)
- Génération d’une image de démarrage **LiteTouchPE_x64.wim**
- Ajout de cette image dans WDS

### 4. 🚀 Déploiement automatisé sur poste client
- Démarrage PXE
- Connexion automatique au domaine
- Exécution sans erreurs de la séquence de tâches
- Vérification dans l’AD que le poste est bien intégré

---

## 🧠 Pourquoi ce TP est important ?

- ✅ Automatisation = gain de temps énorme
- ✅ Standardisation = moins d’erreurs humaines
- ✅ Reproductibilité = facile à maintenir et à mettre à l’échelle
- ✅ Sécurité = comptes dédiés + délégation contrôlée
- ✅ Réalisme = mise en œuvre concrète d’une architecture pro

---

## 🧪 Points techniques et subtilités

- 💡 *Pourquoi utiliser MDTuser au lieu d’un admin ?*  
  ➜ Pour **séparer les rôles**, sécuriser le domaine, et **limiter les risques** en cas de compromission.

- 💡 *Pourquoi convertir le disque en dynamique ?*  
  ➜ Pour **bénéficier de plus de flexibilité** dans la gestion des volumes de stockage.

- 💡 *Et le PXE ?*  
  ➜ Il permet aux clients de **booter directement depuis le réseau**, sans clé USB ni DVD. Hyper pratique !

---

## 📈 Résultat final

- 2 machines virtuelles entièrement déployées via le réseau
- Intégration automatique dans Active Directory
- Zéro interaction utilisateur après le démarrage
- Une infrastructure **propre, efficace, et prête à être réutilisée**

---

## 📚 Compétences mises en œuvre

- Installation & configuration d’un serveur Windows
- Manipulation Active Directory (OU, comptes, délégations)
- Déploiement via MDT et gestion de séquences
- Utilisation de WinPE, ADK, TFTP, PXE
- Sécurité, performances, et bonnes pratiques pro

---

## 🔗 Webographie utile

- [💬 Installation WDS & MDT](https://neptunet.fr/mdt-deploy/)
- [📘 Documentation officielle MDT](https://learn.microsoft.com/fr-fr/windows/deployment/deploy-windows-mdt/)
- [🧰 Installation de l’ADK](https://learn.microsoft.com/fr-fr/windows-hardware/get-started/adk-install)
- [🛡️ Délégation dans l’AD](https://www.it-connect.fr/active-directory-deleguer-lajout-dordinateurs-au-domaine/)

---

## 👋 Pour aller plus loin

Ce projet peut être :
- **étendu à Windows 11**
- **déployé en environnement réel** (école, PME, mairie…)
- relié à un outil de supervision comme **Zabbix** pour surveiller les installations

---

## 🧑‍💻 Auteurs

- **Ventre**
- **Nathan Gabriele**
- 📬 Contact : [ton.email@domaine.com]

---
