# 🚀 Oracle 19c avec Docker Compose

## 📌 Description

Ce projet permet de lancer une base de données Oracle 19c avec Docker Compose, avec :

* ✔️ Données persistantes
* ✔️ Scripts SQL auto-exécutés
* ✔️ Configuration via `.env`
* ✔️ Compatible VS Code

---

## 📂 Structure du projet

```
oracle-project/
│
├── docker-compose.yml
├── .env
└── README.md
```

📁 Scripts SQL (en dehors du projet) :

```
/Users/mac/oracle-scripts/
├── init.sql
├── schema.sql
└── data.sql
```

---

## ⚙️ Configuration

Modifier le fichier `.env` :

```env
ORACLE_PWD=Oracle123
ORACLE_SCRIPTS_PATH=/Users/mac/oracle-scripts
```

---

## ▶️ Lancer Oracle

```bash
docker compose up -d
```

📌 La première fois : 10 à 20 minutes

---

## 📊 Vérifier

```bash
docker ps
```

Tu dois voir :

```
oracle19c   Up (healthy)
```

---

## 🔌 Connexion

### SQLPlus

```bash
docker exec -it oracle19c sqlplus system/Oracle123@ORCLPDB1
```

### SQL Developer

* Host: localhost
* Port: 1521
* Service: ORCLPDB1

---

## 📜 Scripts SQL automatiques

Tous les fichiers dans :

```
/Users/mac/oracle-scripts/
```

seront exécutés automatiquement au démarrage.

---

## 💾 Persistance des données

Les données sont stockées dans :

```
oracle-data (Docker volume)
```

➡️ Même si tu supprimes le conteneur, les données restent ([Oracle Docs][1])

---

## 🛑 Arrêter

```bash
docker compose down
```

---

## 🔥 Recommandations

* Ne pas utiliser `SYS` pour travailler
* Utiliser `SYSTEM` ou un utilisateur dédié
* Toujours faire `COMMIT`

---

## 👨‍💻 Auteur

Abdoulaye Wade CISSE
UADB Bambey — Sénégal 🇸🇳

[1]: https://docs.oracle.com/en/database/oracle/oracle-database/21/deeck/oracle-database-enterprise-edition-installation-guide-docker-containers-oracle-linux.pdf?utm_source=chatgpt.com "Oracle® Database"
