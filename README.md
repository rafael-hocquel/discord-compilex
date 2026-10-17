# Compilex — Bot Discord pour le BUT Informatique (IUT de Bordeaux)

Bot Discord développé avec **discord.js** pour administrer et animer le serveur de promotion du BUT Informatique. Il regroupe les outils classiques d'administration (modération, tickets, *reaction roles*), des fonctionnalités pour les étudiants (salons de travail de groupe éphémères, alertes de notes, météo du campus) et une couche d'**automatisation grâce à Google Gemini** (auto-modération contextuelle et résumés de discussions).

## Fonctionnalités automatiques (Événements & IA)

Le bot tourne en tâche de fond et réagit aux événements du serveur sans nécessiter de commande :

- **Auto-modération hybride (Regex + Gemini) :** Chaque message envoyé ou édité passe par un premier filtre d'expressions régulières, puis par une analyse via l'API **Gemini** pour détecter les propos problématiques. En cas d'infraction, le message est supprimé et archivé dans les logs.
- **Analyse anti-phishing des liens :** Les URLs partagées sont inspectées par IA afin de bloquer les tentatives de phishing, arnaques ou contenus malveillants.
- **Salons vocaux temporaires (*Join-to-Create*) :** Rejoindre le salon vocal dédié génère automatiquement un salon vocal privé au nom de l'étudiant (dans lequel l'étudiant est automatiquement déplacé), qui s'auto-détruit dès qu'il se vide.
- **Gestion des arrivées et départs :** Message d'accueil personnalisé, attribution automatique du rôle étudiant et mise à jour en temps réel du compteur de membres dans le nom d'un salon.
- **Rôles par réaction & Logs :** Attribution/retrait de rôles à la volée sur les messages configurés, et journalisation systématique de toutes les commandes exécutées dans un salon d'audit.

## Commandes (`/slash`)

### Vie étudiante & Utilitaires

| Commande | Description |
| :--- | :--- |
| `/recap` | Génère un **résumé par IA** des 10 à 100 derniers messages du salon |
| `/setupgroupwork` | Déploie un panneau interactif permettant aux étudiants de créer des **salons privés de travail de groupe** (participants, durée, échéance) |
| `/sondage` | Crée un sondage interactif personnalisé (titre, description, options de vote) |
| `/meteocampus` | Affiche les prévisions météo du campus (par jour et par heure) |
| `/ticket` | Ouvre un salon privé avec l'équipe de modération |
| `/setupTicket` · `/setupReactionRole` | Déploie les messages interactifs d'ouverture de tickets et d'attribution de rôles |
| `/event` · `/note` | Publie des annonces formatées pour les événements de promo ou la sortie de nouvelles notes |
| `/ping` · `/uptime` · `/meme` · `/needhelp` | Latence, temps de fonctionnement, meme d'info aléatoire et liens d'aide |

### Modération

| Commande | Description |
| :--- | :--- |
| `/ban` · `/kick` | Bannir ou expulser un membre du serveur |
| `/mute` · `/tempmute` · `/unmute` | Rendre muet (définitivement ou temporairement) ou lever la sanction |
| `/warn` | Avertir officiellement un membre |
| `/lock` · `/unlock` | Verrouiller ou déverrouiller l'écriture dans le salon courant |
| `/clear` | Supprimer un nombre défini de messages |
| `/clone` · `/close` | Dupliquer un salon à l'identique ou fermer un salon (ex. ticket résolu) |

## Prérequis

- **Node.js 18+**
- Une application Discord avec un bot configuré sur le [Portail Développeur Discord](https://discord.com/developers/applications)
- Les **Privileged Gateway Intents** activés sur le portail : `Server Members Intent` et `Message Content Intent`
- Une clé **API Google Gemini** (pour la commande `/recap` et l'auto-modération)

## Installation et lancement

```bash
git clone https://github.com/rafael-hocquel/discord-compilex.git
cd discord-compilex
npm install
