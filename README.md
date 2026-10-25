Guide de Déploiement sur MacBook (macOS)

L'archive autonome du projet Veille Tech Agent a été assemblée et optimisée pour un déploiement instantané sur macOS (Apple Silicon M1/M2/M3/M4 & Intel).

📦 Fichiers Archives Disponibles
Format ZIP (Recommandé macOS / Finder) :
Chemin : /Users/romainrouzaud/.gemini/antigravity/scratch/veille_tech_agent_macbook.zip
Poids : 1.7 Mo (100% anonymisé : aucune clé API, aucun mot de passe, aucun log ni donnée personnelle n'est embarqué).
Format Tarball (Terminal) :
Chemin : /Users/romainrouzaud/.gemini/antigravity/scratch/veille_tech_agent_macbook.tar.gz
🚀 Procédure de Déploiement en 3 Étapes
Étape 1 : Décompresser l'archive

Dans le Terminal de votre MacBook (ou par double-clic dans le Finder) :

bash
# Exemple dans votre dossier personnel ou Projets
unzip veille_tech_agent_macbook.zip -d ~/Projets/
cd ~/Projets/veille_tech_agent
Étape 2 : Lancer l'installation automatique

Exécutez le script d'installation dédié :

bash
./install.sh

Ce script automatisé :

Détecte votre installation Python 3 macOS.
Crée un environnement virtuel propre (./venv) adapté à l'architecture de votre processeur (ARM64 ou x86_64).
Installe toutes les dépendances (requirements.txt).
Initialise les dossiers data/raw, data/summaries, data/newsletters.
Prépare le fichier .env avec vos accès.
Étape 3 : Exécution & Utilisation

Le script wrapper ./run.sh évite d'avoir à activer manuellement le virtualenv :

bash
# Lancer la collecte et l'évaluation quotidienne
./run.sh daily
# Générer la newsletter hebdomadaire (Markdown prêt à être partagé)
./run.sh weekly
# Générer et envoyer directement par email
./run.sh weekly --send-email
# Modifier la configuration des modèles (Gemini, Ollama, WatsonX)
./run.sh configure
🕒 Automatisation sur macOS (Crontab)

Pour que la veille s'exécute de façon autonome en arrière-plan sans intervention manuelle :

Tous les jours à 06h00 : Collecte des flux RSS et synthèse IA des articles pertinents.
Tous les dimanches à 19h00 : Génération de la newsletter hebdomadaire avec l'infographie prioritaire IBM Cloud / GCP et la Wardley Map.

Exécutez simplement l'assistant interactif :

bash
./setup_cron.sh

L'assistant configure automatiquement les chemins absolus adaptés à l'emplacement où vous avez extrait l'archive.

📂 Contenu du Package
Moteur Multi-Agents :
collector.py : Ingestion RSS, détection GCP/IBM Cloud, extraction et filtrage d'infographies authentiques.
evaluator.py : Scoring d'architecture (>= 7/10) et structuration d'impacts.
writer.py : Rédaction hebdomadaire (3 piliers, infographie IBM/GCP, Wardley Map, 4 projets pilotes).
mailer.py : Distribution SMTP HTML/Markdown.
llm_client.py : Connecteur LLM unifié (Gemini / WatsonX / Ollama).
Configurations & Sources :
sources.yaml : Plus de 20 flux majeurs (AWS, Azure, Google Cloud, IBM watsonx, Netflix, Fowler, Hohpe, Wardley, etc.).
email_config.yaml : Paramètres d'envoi SMTP et destinataires.
llm_config.yaml : Configuration du provider actif.
Scripts Prêts à l'Emploi :
install.sh, run.sh, setup_cron.sh, cron_daily.sh, cron_weekly.sh.
