# CCS_LTS – Client-Server , Mutex Access Models & Gossiping Girls Models

##  Description

Ce projet modélise 3 systèmes concurrentiels en utilisant le **Calcul des Communications de Systèmes (CCS)** :
- Un modèle **Client – Serveur** avec gestion d’erreurs et de masquage
- Un modèle **d’accès exclusif** à une ressource critique (exclusion mutuelle)
- Un modèle **Gossiping Girls** illustrant la diffusion d'information minimale entre processus

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

Générer les images à partir des fichiers .dot :


    dot -Tpng diagrams/client_server_lts.dot -o diagrams/client_server_lts.png
    dot -Tpng diagrams/mutex_access_lts.dot -o diagrams/mutex_access_lts.png
    dot -Tpng diagrams/gossiping_girls_lts.dot -o diagrams/gossiping_girls_lts.png

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
    Image générée : diagrams/mutex_access_lts.png


## CCS Example 3 – Gossiping Girls Model (n = 4)

Ce modèle représente la propagation minimale d'informations entre 4 filles (A, B, C, D), chacune connaissant une information unique.
Elles s'appellent et partagent leurs informations jusqu’à ce que toutes connaissent tout.

    GirlA = callAB.GirlAB
    GirlB = callBA.GirlAB
    GirlC = callAC.GirlAC
    GirlD = callAD.GirlAD

    GirlAB = callABC.GirlABC
    GirlABC = callABCD.GirlABCD
    GirlABCD = 0

    System = (GirlA | GirlB | GirlC | GirlD) \ {callAB, callBA, callABC, callABCD}
### LTS 
    Fichier .dot : diagrams/gossiping_girls_lts.dot 
    Image générée : diagrams/gossiping_girls_lts.png











## Structure de projet 

    CSS_LTS/
    ├── diagrams/
    │   ├── client_server_lts.dot
    │   ├── client_server_lts.png
    │   ├── mutex_access_lts.dot
    │   ├── mutex_access_lts.png
    │   ├── gossiping_girls_lts.dot
    │   └── gossiping_girls_lts.png
    ├── exemple/
    │   ├── client_server.ccs
    │   ├── mutex_access.ccs
    │   └── gossiping_girls.ccs
    ├── README.md


## Summary of Examples
    Exemple 1 : Client/Serveur (communication, masquage, timeout, crash)
    Exemple 2 : Mutex Access (exclusion mutuelle, synchronisation)
    Exemple 3 : Gossiping Girls (diffusion d'information optimisée)
