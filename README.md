# Full Stack FastAPI Payment Template

[![Test](https://github.com/fastapi/full-stack-fastapi-template/workflows/Test/badge.svg)](https://github.com/fastapi/full-stack-fastapi-template/actions?query=workflow%3ATest)
[![Coverage](https://coverage-badge.samuelcolvin.workers.dev/fastapi/full-stack-fastapi-template.svg)](https://coverage-badge.samuelcolvin.workers.dev/redirect/fastapi/full-stack-fastapi-template)

A **production-ready Full Stack FastAPI template** with integrated **Razorpay payment gateway**, ready-to-use checkout pages, payment analytics, and complete payment flow management.

> 🚀 **Bootstrap your monetized app in minutes** - Everything you need for payments is already integrated!

## ✨ Features

### 💳 Complete Payment Integration
- **Razorpay Gateway Integration** - One-time payments with secure signature verification
- **Webhook Handling** - Real-time payment status updates
- **Payment Analytics Dashboard** - Track payments, success rates, and revenue
- **Checkout UI** - Beautiful, responsive checkout page with Razorpay modal
- **Payment History** - Complete order and payment tracking in database

### 🎨 Modern Tech Stack
- **Backend**: FastAPI + SQLModel + PostgreSQL
- **Frontend**: React + TypeScript + Chakra UI
- **DevOps**: Docker Compose with hot-reload
- **Testing**: Pytest + Playwright E2E tests
- **Deployment**: Production-ready with Traefik & HTTPS

### 🔐 Security & Authentication
- JWT authentication
- Secure password hashing
- Email-based password recovery
- Role-based access control
- Payment signature verification

## 📸 Screenshots

### Payment Checkout Dashboard

![Payment Checkout](img/checkout.png)

Complete payment dashboard with integrated checkout form and payment analytics. Users can make payments and view their payment history all in one place.

### Razorpay Integration

![Razorpay Integration](img/razorpay.png)

Seamless Razorpay checkout modal integration with secure payment processing.

### Dashboard Features

<details>
<summary>View all dashboard screenshots</summary>

![Login](img/login.png)
![Dashboard](img/dashboard.png)
![Create User](img/dashboard-create.png)
![Items](img/dashboard-items.png)
![User Settings](img/dashboard-user-settings.png)
![Dark Mode](img/dashboard-dark.png)
![API Docs](img/docs.png)

</details>

## 🚀 Quick Start

### Prerequisites

- [Docker](https://www.docker.com/) and Docker Compose
- [Git](https://git-scm.com/)

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/full-stack-fastapi-payment-template.git
cd full-stack-fastapi-payment-template
```

### 2. Configure Environment Variables

Copy `.env` and update the following:

```bash
# Security Keys (generate with: python -c "import secrets; print(secrets.token_urlsafe(32))")
SECRET_KEY=your-secret-key-here
POSTGRES_PASSWORD=your-db-password
FIRST_SUPERUSER_PASSWORD=admin-password

# Razorpay Payment Gateway
RAZORPAY_KEY_ID=rzp_test_xxxxxxxxxxxxx
RAZORPAY_KEY_SECRET=your-razorpay-key-secret
RAZORPAY_WEBHOOK_SECRET=your-webhook-secret  # For production webhooks
```

### 3. Start the Application

```bash
docker compose watch
```

This will:
- Start all services (backend, frontend, database)
- Run database migrations automatically
- Enable hot-reload for development

### 4. Access the Application

- **Frontend**: http://localhost:5173
- **Backend API**: http://localhost:8000
- **API Documentation**: http://localhost:8000/docs
- **Checkout Page**: http://localhost:5173/checkout

### 5. Create Your First User

1. Go to http://localhost:5173/signup
2. Create an account
3. Navigate to `/checkout` to test payments

## 💳 Razorpay Setup

### Get Your API Keys

1. **Sign Up**: Visit [Razorpay Dashboard](https://dashboard.razorpay.com/signup)
2. **Get Test Keys** (no KYC required):
   - Log in to [Razorpay Dashboard](https://dashboard.razorpay.com/)
   - Go to **Settings** → **API Keys**
   - Copy your **Key ID** (starts with `rzp_test_`) and **Key Secret**
3. **Add to `.env`**:
   ```bash
   RAZORPAY_KEY_ID=rzp_test_your_key_id
   RAZORPAY_KEY_SECRET=your_key_secret
   ```

### Test Payments

Use Razorpay test cards:
- **Success**: `4111 1111 1111 1111` (any CVV, any future expiry)
- **Failure**: `4000 0000 0000 0002`
- See [Razorpay Test Cards](https://razorpay.com/docs/payments/test-cards/) for more options

### Production Setup

1. Complete KYC verification in Razorpay Dashboard
2. Switch to **Live Mode**
3. Generate Live API keys
4. Update `.env` with live keys
5. Configure webhooks (see [backend/README.md](./backend/README.md#webhook-setup-for-local-development))

## 📚 Documentation

### Core Documentation
- **[Development Guide](./development.md)** - Local development with Docker Compose
- **[Deployment Guide](./deployment.md)** - Production deployment instructions
- **[Backend README](./backend/README.md)** - Backend development, migrations, and payment API details
- **[Frontend README](./frontend/README.md)** - Frontend development guide

### Payment Integration
- **Setup Instructions**: See [Payment Integration (Razorpay)](#-razorpay-setup) above
- **API Endpoints**: See [backend/README.md](./backend/README.md#payment-api-endpoints)
- **Database Models**: See [backend/README.md](./backend/README.md#database-migrations-with-alembic)
- **Webhook Configuration**: See [backend/README.md](./backend/README.md#webhook-setup-for-local-development)

## 🏗️ Project Structure

```
.
├── backend/              # FastAPI backend
│   ├── app/
│   │   ├── api/         # API routes (including payments)
│   │   ├── models.py    # Database models (Order, Payment)
│   │   ├── crud.py      # Database operations
│   │   ├── services/    # Business logic (Razorpay service)
│   │   └── alembic/     # Database migrations
│   └── README.md        # Backend documentation
├── frontend/            # React frontend
│   ├── src/
│   │   ├── components/
│   │   │   └── Payments/  # Payment UI components
│   │   ├── routes/       # Application routes
│   │   └── client/       # Auto-generated API client
│   └── README.md        # Frontend documentation
├── img/                 # Screenshots and images
├── docker-compose.yml   # Docker services configuration
├── development.md       # Development guide
└── deployment.md        # Deployment guide
```

## 🎯 What's Included

### Backend Features

✅ **Payment API Endpoints**
- Create Razorpay orders
- Verify payment signatures
- Handle webhooks
- List user orders
- Get order details

✅ **Database Models**
- `Order` - Payment orders with Razorpay integration
- `Payment` - Payment records linked to orders
- Automatic migrations with Alembic

✅ **Services**
- Razorpay service for API interactions
- Secure signature verification
- Payment capture handling

### Frontend Features

✅ **Payment Components**
- Checkout page with integrated dashboard
- Payment success/failure pages
- Payment analytics dashboard
- Recent orders table

✅ **UI/UX**
- Modern blue theme
- Responsive design
- Sidebar navigation
- Real-time payment updates

## 🔄 Payment Flow

1. **User initiates payment** → Enters amount on `/checkout` page
2. **Backend creates order** → Saves to database, returns Razorpay order ID
3. **Razorpay modal opens** → User completes payment
4. **Payment verification** → Frontend sends payment details to backend
5. **Signature verification** → Backend verifies Razorpay signature
6. **Database update** → Order and payment records updated
7. **Success redirect** → User sees payment confirmation and analytics
8. **Webhook update** → Real-time status updates from Razorpay (optional)

## 🧪 Testing

### Run Backend Tests

```bash
docker compose exec backend bash scripts/test.sh
```

### Run Frontend E2E Tests

```bash
docker compose exec playwright npm run test
```

## 📝 Database Migrations

This project uses Alembic for database migrations. Migrations run automatically on startup.

**Quick Commands:**
```bash
# Check migration status
docker compose exec backend bash -c "cd /app && alembic current"

# Create new migration
docker compose exec backend bash -c "cd /app && alembic revision --autogenerate -m 'Description'"

# Apply migrations
docker compose exec backend bash -c "cd /app && alembic upgrade head"
```

**For detailed migration guide**, see [backend/README.md](./backend/README.md#database-migrations-with-alembic).

## 🛠️ Development

### Start Development Environment

```bash
docker compose watch
```

This enables:
- Hot-reload for backend and frontend
- Auto-regeneration of API client
- Live migration application

### Backend Development

See [backend/README.md](./backend/README.md) for:
- Local development setup
- Running tests
- Creating migrations
- Payment API details

### Frontend Development

See [frontend/README.md](./frontend/README.md) for:
- Local development
- Component structure
- API client generation

## 🌐 API Documentation

Once running, access interactive API docs:
- **Swagger UI**: http://localhost:8000/docs
- **ReDoc**: http://localhost:8000/redoc

All payment endpoints are documented and can be tested directly from the Swagger UI.

## 📦 What You Get

- ✅ Complete payment integration (Razorpay)
- ✅ User authentication & authorization
- ✅ Admin dashboard
- ✅ Payment analytics
- ✅ Webhook handling
- ✅ Database migrations
- ✅ API documentation
- ✅ E2E tests
- ✅ Production deployment config
- ✅ Docker Compose setup
- ✅ CI/CD ready

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License.

## 🙏 Acknowledgments

- Built on [Full Stack FastAPI Template](https://github.com/fastapi/full-stack-fastapi-template)
- Payment integration powered by [Razorpay](https://razorpay.com/)

---

**Ready to accept payments?** 🚀 Clone this repo, add your Razorpay keys, and start processing payments in minutes!
