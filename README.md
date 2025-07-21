# KERVENTZcontacts - Système de Gestion de Contacts WhatsApp

Une application complète de gestion de contacts pour WhatsApp avec interface publique et dashboard administrateur.

## 🚀 Lancement de l'Application

### Sur Replit
1. Cliquer sur le bouton "Run" 
2. L'application sera accessible sur le port 5000

### URLs d'Accès

#### 🔵 Site Public (Enregistrement)
- **URL**: `/` (page d'accueil)
- **Fonction**: Formulaire d'enregistrement pour les utilisateurs
- **Caractéristiques**:
  - Sélection de pays avec drapeaux (195+ pays)
  - Ajout automatique du suffixe "k.1🔥"
  - Détection de doublons (nom et numéro)
  - Page de remerciement avec lien WhatsApp

#### 🟠 Dashboard Admin (Privé)
- **URL**: `/admin`
- **Mot de passe**: `kerventz2000`
- **Fonction**: Gestion complète des contacts
- **Caractéristiques**:
  - Liste de tous les contacts
  - Modification/suppression de contacts
  - Téléchargement fichier .vcf
  - Gestion du lien WhatsApp
  - Suppression en masse

## 📱 Comment Tester les Deux Sites

### Méthode 1: Deux Onglets
1. **Onglet 1**: Ouvrir l'URL de base pour le site public
2. **Onglet 2**: Ajouter `/admin` à l'URL pour le dashboard admin

### Méthode 2: Nouvelle Fenêtre
1. **Fenêtre actuelle**: Site public (/)
2. **Nouvelle fenêtre**: Copier l'URL et ajouter `/admin`

## 🔧 Fonctionnalités Testées

### Site Public ✅
- ✅ Formulaire avec tous les pays du monde
- ✅ Validation anti-doublons
- ✅ Ajout automatique "k.1🔥"
- ✅ Page de succès avec bouton WhatsApp
- ✅ Bouton retour à l'accueil

### Dashboard Admin ✅
- ✅ Authentification sécurisée
- ✅ Affichage du nombre total de contacts
- ✅ Liste complète des contacts
- ✅ Édition de contacts
- ✅ Suppression individuelle et en masse
- ✅ Export .vcf de tous les contacts
- ✅ Gestion du lien WhatsApp

## 🛠 Technologies Utilisées

- **Frontend**: React + TypeScript + Vite
- **Backend**: Express.js + TypeScript
- **UI**: Tailwind CSS + Radix UI (shadcn/ui)
- **Stockage**: Mémoire (MemStorage) pour le développement
- **Validation**: Zod + React Hook Form
- **État**: TanStack Query (React Query)

## 📦 Structure du Projet

```
├── client/src/
│   ├── pages/
│   │   ├── public-home.tsx      # Page d'accueil publique
│   │   ├── public-success.tsx   # Page de remerciement
│   │   ├── admin-login.tsx      # Connexion admin
│   │   └── admin-dashboard.tsx  # Dashboard admin
│   └── lib/
│       └── countries.ts         # Liste de tous les pays
├── server/
│   ├── index.ts                 # Serveur principal
│   ├── routes.ts                # Routes API
│   └── storage.ts               # Gestion des données
└── shared/
    └── schema.ts                # Schémas de validation
```

## 🔑 Identifiants Admin

- **Mot de passe**: `kerventz2000`
- **Route**: `/admin`

## 📝 Notes Importantes

- Les données sont stockées en mémoire pour le développement
- Le suffixe "k.1🔥" est ajouté automatiquement aux noms
- Les doublons sont détectés par nom ET numéro de téléphone
- Le fichier .vcf contient tous les contacts au format vCard
- Le lien WhatsApp est configurable via le dashboard admin

## 🚀 Déploiement

L'application est prête pour le déploiement sur Replit ou toute plateforme supportant Node.js.
