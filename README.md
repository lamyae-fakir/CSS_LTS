# CCS_LTS – Client-Server & Mutex Access Models

##  Description

Ce projet modélise deux systèmes concurrentiels en utilisant le **Calcul des Communications de Systèmes (CCS)** :
- Un modèle **Client – Serveur** avec gestion d’erreurs et de masquage
- Un modèle **d’accès exclusif** à une ressource critique (exclusion mutuelle)

##  How to Install

1. Faut télécharger et installer **Graphviz** :  
    https://graphviz.org/download/

2. Pendant l’installation, j'ai choisi  :  
   ` Add Graphviz to the system PATH for current user`

3. Vérification de  l'installation avec la commande :


     dot -v
## How to execute 
git clone https://github.com/lamyae-fakir/CSS_LTS.git
cd CSS_LTS

Pour générer l’image du premier LTS (Client-Server) à partir du fichier .dot, exécuter :


    dot -Tpng diagrams/client_server_lts.dot -o diagrams/client_server_lts.png



pour que je génére l’image du second LTS (Mutex Access) :


    dot -Tpng diagrams/mutex_access_lts.dot -o diagrams/mutex_access_lts.png

Les fichiers .png seront générés dans le dossier diagrams/

---

##  CCS Example 1 – Client/Server Model

Client = req.ClientWait + timeout.Client
ClientWait = res.Client + timeout.Client

Server = req̅.ServerWait
ServerWait = res̅.Server + crash.0

System = (Client | Server) \ {req, res}

### LTS 

    Fichier .dot : diagrams/client_server_lts.dot
    Image générée : diagrams/client_server_lts.png

## CCS Example 2 – Mutex Access Model

UserA = reqA.AccessA + waitA.UserA
AccessA = enterA.ExitA
ExitA = exitA.UserA

UserB = reqB.AccessB + waitB.UserB
AccessB = enterB.ExitB
ExitB = exitB.UserB

System = (UserA | UserB) \ {enterA, enterB, exitA, exitB}

Ce modèle illustre l’exclusion mutuelle entre deux processus concurrents qui accèdent à une ressource critique.

### LTS
    Fichier  .dot : diagrams/mutex_access_lts.dot





## Structure de projet 

    CSS_LTS/
    ├── diagrams/
    │   ├── client_server_lts.dot
    │   ├── client_server_lts.png
    │   ├── mutex_access_lts.dot
    │   └── mutex_access_lts.png
    ├── exemple/
    │   ├── client_server.ccs
    │   └── mutex_access.ccs
    ├── README.md

## Summary of Examples
    Exemple 1 : Client/Serveur (communication, masquage, timeout, crash)
    Exemple 2 : Mutex Access (exclusion mutuelle, synchronisation)

