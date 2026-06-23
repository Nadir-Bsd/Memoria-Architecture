# 🚀 Memoria - AI-Powered Web Application & Infrastructure

<img width="1447" height="736" alt="Gemini_Generated_Image_b99fgyb99fgyb99f" src="https://github.com/user-attachments/assets/86fe409a-798f-4835-9560-134763b4573a" />
<img width="266" height="520" alt="Capture d&#39;écran 2026-06-22 115506" src="https://github.com/user-attachments/assets/53bd4594-82ba-4438-aee8-2b9fc6611e2b" />

> **À propos** : **Memoria** est un projet full-stack conçu et réalisé de A à Z dans le cadre de ma 3ème année (Bac+3). Mon objectif principal avec ce projet était de sortir de ma zone de confort et de me confronter aux réalités de la production : **l'architecture, la conteneurisation globale via Docker et le déploiement sur un VPS dédié ont été entièrement réalisés en auto-formation**. 
> 
> Ce projet de bout en bout illustre ma capacité d'adaptation technologique, ma rigueur, et ma détermination à évoluer vers le **Machine Learning Engineering (MLE)** pour mon Bac+5.

## ✨ Fonctionnalités Principales & Approche MLOps/DevOps

Ce projet n'est pas qu'un simple site web, c'est une infrastructure complète pensée pour l'intégration de modèles d'Intelligence Artificielle :

* **🌍 Déploiement Indépendant :** Hébergement complet sur un VPS personnel.
* **🐳 Conteneurisation (Docker) :** Tous les services (Frontend, Backend Symfony, API IA FastAPI, Base de données) sont isolés et orchestrés via Docker pour garantir la reproductibilité.
* **🧠 IA Locale (Privacy-First) :** Déploiement d'un modèle d'IA en local sur le VPS via **Ollama**, interfacé avec un wrapper **FastAPI**, garantissant le contrôle total des données (pas de fuite vers des API tierces en production).
* **⚙️ API Hybride :** En environnement de développement local, utilisation de l'API Mistral pour la rapidité d'itération, switchable avec l'IA locale (Ollama) en production.
* **🚦 Reverse Proxy :** Utilisation de **NGINX** pour router proprement les requêtes entre le frontend, le backend classique et le microservice IA.

## 🏗️ Architecture du Projet

L'architecture est divisée en deux environnements distincts pour séparer le développement de la production :

### 1. Environnement de Production (VPS)
* **Frontend** : Application cliente (image Docker).
* **Backend Core** : API métier développée en **Symfony** avec sa base de données.
* **Backend AI** : Microservice en **FastAPI** qui sert de pont (wrapper).
* **Inférence** : Moteur **Ollama** hébergeant le modèle d'IA (AI_LOCAL).
* **Passerelle** : **NGINX** gère le trafic entrant et le distribue aux bons conteneurs.

### 2. Environnement de Développement Local
* Séparation claire des environnements.
* Utilisation d'appels API externes (Mistral API) via FastAPI pour ne pas surcharger la machine de développement local pendant le code du front/back.

## 🛡️ Assurance Qualité (Code Quality)

Une attention particulière a été portée à la qualité et à la maintenabilité du code, une compétence essentielle en Software Engineering et MLOps. Avant chaque build d'image, le code passe par plusieurs vérifications :
* **Python (FastAPI / IA) :** `pytest` (Tests), `pylint` & `ruff` (Linting/Formatting).
* **PHP (Symfony) :** `phpstan` (Analyse statique niveau 6), `phpcbf` (Formatage), `phpunit` (Tests).
* **Frontend :** `ESLint`.

## 🛠️ Installation et Lancement

Pour simplifier les manipulations, les commandes complexes ont été automatisées via un `Makefile`.

```bash
# 1. Cloner les différents dépôts (ou le monorepo)
git clone [URL_DE_TON_REPO]

# 2. Utiliser le Makefile pour lancer l'environnement complet via Docker
make build
make up

# 3. Lancer les vérifications de qualité de code
make check-quality
