# CCS_LTS - Client Server Model

## 📘 Description

Ce projet modélise un système **Client - Serveur** en utilisant le **Calcul des Communications de Systèmes (CCS)**.  
Il génère ensuite son **LTS (Labelled Transition System)** avec Graphviz.

---

## 🧠 Définition CCS

```txt
Client = req.ClientWait + timeout.Client
ClientWait = res.Client + timeout.Client

Server = req̅.ServerWait
ServerWait = res̅.Server + crash.0

System = (Client | Server) \ {req, res}
