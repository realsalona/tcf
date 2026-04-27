# TCF Canada Platform 🇨🇦🇫🇷

Plateforme SaaS complète de préparation au test TCF Canada (Test de Connaissance du Français).

## ✨ Fonctionnalités

### Pour les utilisateurs:
- **4 épreuves complètes**: Compréhension Orale, Compréhension Écrite, Expression Écrite, Expression Orale
- **Système de quiz réaliste**: Audio player, timer, transition automatique entre questions
- **Correction détaillée**: Résultats instantanés avec explications pour chaque question
- **Suivi de progression**: Statistiques, scores, historique des tentatives
- **Calculateur NCLC**: Estimation du niveau de compétence linguistique
- **Abonnements flexibles**: Packs Bronze (5 jours), Silver (15 jours), Gold (30 jours)
- **Paiement sécurisé**: Intégration Stripe

### Pour les administrateurs:
- **Gestion des questions**: Ajout/modification via base de données
- **Suivi des utilisateurs**: Abonnements, transactions, progression
- **Analytics**: Taux de réussite, engagement des utilisateurs

## 🛠️ Technologies

### Backend:
- Node.js + Express
- PostgreSQL
- JWT Authentication
- Stripe pour les paiements
- bcryptjs pour le hachage des mots de passe

### Frontend:
- React 18 + Vite
- Tailwind CSS
- React Router
- Axios
- Lucide React (icônes)

## 📦 Installation

### Prérequis:
- Node.js 18+
- PostgreSQL 14+
- npm ou yarn

### 1. Cloner le projet:
```bash
cd tcf-canada-platform
```

### 2. Backend:
```bash
cd backend
npm install

# Configurer la base de données
# 1. Créez une database PostgreSQL nommée 'tcf_canada'
# 2. Exécutez le schema
psql -U postgres -d tcf_canada -f ../database/schema.sql

# 3. (Optionnel) Ajoutez des données de test
psql -U postgres -d tcf_canada -f ../database/seed.sql

# 4. Configurez .env
cp .env.example .env
# Éditez .env avec vos credentials

# 5. Lancez le serveur
npm run dev
```

### 3. Frontend:
```bash
cd frontend
npm install

# Configurez .env (optionnel, déjà configuré pour localhost)
# VITE_API_URL=http://localhost:5000/api

# Lancez le serveur de développement
npm run dev
```

## 🚀 Démarrage rapide

```bash
# Terminal 1 - Backend
cd backend
npm install
npm run dev

# Terminal 2 - Frontend
cd frontend
npm install
npm run dev
```

Accédez à l'application: http://localhost:5173

## 📁 Structure du projet

```
tcf-canada-platform/
├── backend/
│   ├── config/
│   │   └── database.js
│   ├── middleware/
│   │   └── auth.js
│   ├── routes/
│   │   ├── auth.js
│   │   ├── quiz.js
│   │   ├── payment.js
│   │   ├── user.js
│   │   └── webhooks.js
│   └── server.js
├── frontend/
│   └── src/
│       ├── components/
│       │   ├── Navbar.jsx
│       │   └── ProtectedRoute.jsx
│       ├── context/
│       │   └── AuthContext.jsx
│       ├── lib/
│       │   └── api.js
│       ├── pages/
│       │   ├── Home.jsx
│       │   ├── Login.jsx
│       │   ├── Register.jsx
│       │   ├── Dashboard.jsx
│       │   ├── QuizPage.jsx
│       │   ├── ResultsPage.jsx
│       │   ├── PricingPage.jsx
│       │   ├── PaymentSuccess.jsx
│       │   ├── PaymentCancel.jsx
│       │   └── ProfilePage.jsx
│       └── App.jsx
└── database/
    ├── schema.sql
    └── seed.sql
```

## 🔑 API Endpoints

### Authentication
- `POST /api/auth/register` - Créer un compte
- `POST /api/auth/login` - Se connecter
- `GET /api/auth/me` - Récupérer le profil
- `PUT /api/auth/profile` - Modifier le profil
- `PUT /api/auth/change-password` - Changer le mot de passe

### Quiz
- `GET /api/quiz/sections` - Liste des épreuves
- `GET /api/quiz/sections/:id/questions` - Questions d'une épreuve
- `POST /api/quiz/attempts/:id/answer` - Soumettre une réponse
- `POST /api/quiz/attempts/:id/complete` - Terminer un test
- `GET /api/quiz/attempts` - Historique des tentatives
- `GET /api/quiz/progress` - Progression de l'utilisateur

### Paiement
- `GET /api/payment/packs` - Liste des abonnements
- `POST /api/payment/create-checkout-session` - Créer un paiement Stripe
- `GET /api/payment/subscription` - Statut de l'abonnement
- `GET /api/payment/transactions` - Historique des transactions

### Utilisateur
- `GET /api/user/dashboard` - Données du tableau de bord
- `POST /api/user/calculate-nclc` - Calculer le niveau NCLC

## 💳 Configuration Stripe

1. Créez un compte sur [Stripe Dashboard](https://dashboard.stripe.com/)
2. Récupérez vos clés API dans **Developers > API keys**
3. Configurez votre `.env` backend:
   ```
   STRIPE_SECRET_KEY=sk_test_...
   STRIPE_PUBLISHABLE_KEY=pk_test_...
   ```
4. Pour les webhooks en local, utilisez Stripe CLI:
   ```bash
   stripe listen --forward-to localhost:5000/api/webhooks/stripe
   ```

## 📝 Notes

- Les fichiers audio et images sont des placeholders (à remplacer par vos propres fichiers)
- La correction IA pour l'expression écrite/orale peut être ajoutée via une API externe
- Le calcul NCLC est une version simplifiée

## 👨‍💻 Développement

### Backend:
```bash
cd backend
npm run dev
```

### Frontend:
```bash
cd frontend
npm run dev
```

### Build de production:
```bash
cd frontend
npm run build
```

## 📄 License

MIT

## 🤝 Support

Pour toute question ou problème, ouvrez une issue sur GitHub.

---

**Développé avec ❤️ pour aider les étudiants à réussir leur TCF Canada**
