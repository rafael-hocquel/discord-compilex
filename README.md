# Compilex - Bot Discord pour la promotion BUT Informatique (IUT Bordeaux)

Bot **Discord** en discord.js qui gère la vie d'un serveur de promo : modération,
tickets, sondages, salons de travail de groupe, accueil des nouveaux et
**automatisation par IA** (filtrage des messages et des liens, résumé de
conversation).

**Équipe :** Rafaël HOCQUEL · Nolan MAILLARD-GOUAS  
**Version :** 1.0 - septembre-novembre 2025

## Ce que fait le bot

### Modération

| Commande | Effet |
|----------|-------|
| `/ban` · `/kick` | Bannir ou expulser un membre |
| `/mute` · `/tempmute` · `/unmute` | Rendre muet pour une durée, indéfiniment, ou lever la sanction |
| `/warn` | Donner un avertissement |
| `/lock` · `/unlock` | Fermer ou rouvrir l'écriture dans un salon |
| `/clear` | Effacer des messages |
| `/clone` · `/close` | Recréer un salon à l'identique, ou le fermer |

### Vie du serveur

| Commande | Effet |
|----------|-------|
| `/recap` | **Résumé IA** des 10 à 100 derniers messages du salon |
| `/ticket` | Ouvrir un salon privé avec l'équipe de modération |
| `/sondage` | Créer un sondage interactif (nom, description, réponses, vote) |
| `/setupgroupwork` | Message interactif : créer un salon de **travail de groupe** privé (participants, durée, échéance) |
| `/setupTicket` · `/setupReactionRole` · `/event` · `/note` | Messages d'installation : support, rôles par réaction, événements, nouvelles notes |
| `/meteocampus` | Météo du campus, par jour et par heure |
| `/ping` · `/uptime` · `/meme` · `/needhelp` | Latence, disponibilité, meme informatique aléatoire, lien d'aide |

### Automatique, sans commande

| Déclencheur | Réaction |
|-------------|----------|
| Nouveau message, ou message édité | **Double filtre** : liste d'expressions régulières puis vérification par **Gemini** → suppression et log si le message est non conforme |
| Message contenant un lien | Analyse par IA des liens (phishing, arnaques, contenu illégal) → suppression et log |
| Arrivée d'un membre | Message de bienvenue, ajout automatique du rôle étudiant, mise à jour du compteur de membres dans un salon |
| Départ d'un membre | Message d'au revoir, mise à jour du compteur |
| Réaction ajoutée ou retirée | Attribution ou retrait du rôle correspondant |
| Arrivée dans le salon vocal dédié | Création d'un **salon vocal privé** au nom du membre, supprimé quand il se vide |
| Chaque commande utilisée | Log dans un salon dédié |

## Prérequis

- **Node.js 18 ou plus**
- Une **application Discord** avec un bot, sur le [portail développeur](https://discord.com/developers/applications)
- Les **intents privilégiés** activés pour le bot : *Server Members Intent* et *Message Content Intent*
- Une clé **API Google Gemini** (résumé et modération)

## Installation

```
bash
git clone https://github.com/rafael-hocquel/compilex.git
cd compilex
npm install
```
