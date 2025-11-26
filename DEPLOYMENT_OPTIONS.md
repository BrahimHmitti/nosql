# 🚀 Options de Déploiement en Ligne - Analyse des Dépôts

Ce document analyse tous les dépôts de **BrahimHmitti** et recommande des options de déploiement gratuites pour les rendre accessibles en ligne.

## 📊 Récapitulatif

| Dépôt | Type | Option Recommandée | Statut |
|-------|------|-------------------|--------|
| wordle_py | Jeu Python | ✅ GitHub Pages | Déjà en ligne |
| DEVOPS-jour6 | Dashboard Streamlit | ✅ Streamlit Cloud | Déjà en ligne |
| nosql | Flask App + MongoDB | 🔄 Vercel/Render | À déployer |
| DEVOPS-jour4 | HTML + K8s configs | 🔄 GitHub Pages | À déployer |
| DEVOPS-jour2-Docker | Go WebApp | 🔄 Render/Railway | À déployer |
| DEVOPS-jour3 | K8s scripts | 📚 GitHub Pages (docs) | Documentation seulement |
| DEVOPS-jour5 | K8s security | 📚 GitHub Pages (docs) | Documentation seulement |
| DEVOPS-Terraform | Terraform configs | 📚 N/A | Infra as Code |
| tp_snowflake_dbt | - | ❌ Vide | Dépôt vide |

---

## 🎯 Dépôts Déployables

### 1. 🕵️ nosql - Détecteur de Corruption (CE DÉPÔT)

**Type:** Application Flask avec MongoDB et Google Gemini AI

**Options de déploiement:**

#### Option A: Render (Recommandé) ⭐
Render offre un hébergement gratuit pour les applications Python avec support MongoDB Atlas.

1. Créer un compte sur [render.com](https://render.com)
2. Connecter votre dépôt GitHub
3. Créer un nouveau "Web Service"
4. Configurer les variables d'environnement:
   - `GOOGLE_API_KEY`
   - `MONGO_URI`
   - `DB_NAME`
   - `COLLECTION_NAME`

#### Option B: Vercel
Le fichier `vercel.json` est déjà configuré.

1. Créer un compte sur [vercel.com](https://vercel.com)
2. Importer le dépôt GitHub
3. Configurer les variables d'environnement

#### Option C: Railway
1. Créer un compte sur [railway.app](https://railway.app)
2. Déployer depuis GitHub
3. Ajouter un service MongoDB

**URL potentielle:** `https://nosql-corruption-detector.render.com`

---

### 2. 🎮 DEVOPS-jour4 - Guestbook App

**Type:** Page HTML statique + configurations Kubernetes

**Option recommandée: GitHub Pages** ⭐

Le fichier `index.html` peut être déployé directement sur GitHub Pages.

**Étapes:**
1. Aller dans Settings > Pages
2. Source: Deploy from a branch
3. Branch: main, folder: / (root)
4. Sauvegarder

**URL:** `https://brahimhmitti.github.io/DEVOPS-jour4/`

---

### 3. 🐹 DEVOPS-jour2-Docker - Go WebApp

**Type:** Application Go avec interface web

**Options de déploiement:**

#### Option A: Render (Recommandé) ⭐
1. Créer un Web Service sur Render
2. Build Command: `go build -o app .`
3. Start Command: `./app`

#### Option B: Railway
1. Déployer depuis GitHub
2. Railway détecte automatiquement Go

#### Option C: Fly.io
1. Installer flyctl
2. `fly launch`
3. `fly deploy`

**URL potentielle:** `https://devops-jour2-docker.onrender.com`

---

## 📚 Dépôts Documentation (GitHub Pages)

### 4. DEVOPS-jour3 - Kubernetes Scripts

**Contenu:** Scripts bash, fichiers YAML pour Kubernetes, documentation d'apprentissage

**Option:** GitHub Pages avec Jekyll pour la documentation

**Étapes:**
1. Créer un fichier `index.md` ou `_config.yml`
2. Activer GitHub Pages
3. Choisir un thème Jekyll (ex: minimal)

---

### 5. DEVOPS-jour5 - Kubernetes Security

**Contenu:** Politiques Gatekeeper, configurations réseau, documentation de sécurité

**Option:** GitHub Pages pour la documentation

---

### 6. DEVOPS-Terraform - Infrastructure as Code

**Contenu:** Fichiers Terraform, modules, documentation

**Note:** Ce type de projet n'a généralement pas besoin d'être déployé en ligne car c'est de l'Infrastructure as Code.

---

## 🛠️ Guide de Déploiement Rapide

### Pour GitHub Pages (sites statiques)

```yaml
# .github/workflows/pages.yml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/configure-pages@v4
      - uses: actions/upload-pages-artifact@v3
        with:
          path: '.'
      - uses: actions/deploy-pages@v4
```

### Pour Render (applications Python/Go)

```yaml
# render.yaml
services:
  - type: web
    name: nosql-app
    env: python
    buildCommand: pip install -r requirements.txt
    startCommand: gunicorn app:app
    envVars:
      - key: GOOGLE_API_KEY
        sync: false
      - key: MONGO_URI
        sync: false
```

### Pour Streamlit Cloud

1. Aller sur [share.streamlit.io](https://share.streamlit.io)
2. Connecter votre dépôt GitHub
3. Sélectionner le fichier `.py` principal

---

## 🎁 Bonus: Services Gratuits Recommandés

| Service | Type | Limite Gratuite |
|---------|------|----------------|
| **Render** | Web hosting | 750h/mois |
| **Vercel** | Serverless | Illimité (avec limites) |
| **Railway** | Full stack | $5 crédit/mois |
| **GitHub Pages** | Static sites | Illimité |
| **Streamlit Cloud** | Data apps | 3 apps |
| **MongoDB Atlas** | Database | 512MB |
| **PlanetScale** | MySQL | 1GB |
| **Supabase** | PostgreSQL | 500MB |

---

## 📋 Actions Recommandées

1. **Priorité Haute:**
   - [ ] Déployer `nosql` sur Render ou Vercel
   - [ ] Activer GitHub Pages pour `DEVOPS-jour4`

2. **Priorité Moyenne:**
   - [ ] Déployer `DEVOPS-jour2-Docker` sur Render
   - [ ] Créer documentation GitHub Pages pour `DEVOPS-jour3` et `DEVOPS-jour5`

3. **Optionnel:**
   - [ ] Ajouter des badges de statut aux README
   - [ ] Configurer CI/CD automatique

---

*Document généré automatiquement - Dernière mise à jour: Novembre 2025*
