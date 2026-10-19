# 🚀 TP : Redistribution de Routes (OSPF / EIGRP / RIPv2) sous GNS3

Ce projet présente la configuration, l'optimisation et la validation d'une architecture réseau multi-domaines interconnectant les protocoles de routage dynamique **OSPF**, **EIGRP** et **RIPv2** au sein d'une topologie simulée sous **GNS3**.

---

## 📌 Topologie du Réseau
La topologie est composée de **6 routeurs Cisco 7200** répartis en trois zones de routage distinctes :
* **Domaine OSPF (Area 0) :** Routeurs `R1`, `R2`, `R3`
* **Domaine EIGRP (AS 1) :** Routeurs `R2`, `R3`, `R4`, `R5`
* **Domaine RIPv2 :** Routeurs `R5`, `R6`

---

## ⚙️ Points Clés de la Configuration

1. **Interfaces et Adressage :** 
   - Utilisation de liaisons série sur les ports `Serial1/X` (slots modifiés pour le routeur Cisco 7200) et d'interfaces `Loopback` pour simuler les réseaux locaux de chaque routeur.
2. **Redistribution Bidirectionnelle :**
   - Sur les routeurs frontières **R2** et **R3** (redistribution entre OSPF et EIGRP).
   - Sur le routeur frontière **R5** (redistribution entre EIGRP et RIPv2).
3. **Optimisation du Routage :**
   - Ajustement de la Distance Administrative d'EIGRP sur **R3** (`distance eigrp 90 105`) afin d'éviter le routage sous-optimal et de privilégier le chemin le plus court via EIGRP.

---

## 🔍 Commandes de Vérification et Démonstration

Pour valider le bon fonctionnement de la redistribution et de la connectivité de bout en bout, les commandes suivantes sont utilisées :

* **Vérification de la table de routage (sur R3) :**
  ```cisco
  show ip route
