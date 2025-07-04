# TireSouq Backend - FastAPI REST API Server

A high-per### Database seeding utilities

## 🛠️ Technology Stack

### Backend Framework & Core
- **Framework**: FastAPI 0.104+ with Python 3.11+
- **ASGI Server**: Uvicorn with auto-reload for development
- **Database**: MySQL 8.0+ with connection pooling
- **ORM**: SQLAlchemy 2.0+ with async support
- **Migrations**: Alembic for database schema versioning
- **Authentication**: JWT tokens with python-jose
- **Password Hashing**: PassLib with bcrypt

### API & Documentation
- **API Documentation**: Auto-generated OpenAPI/Swagger docs
- **Request Validation**: Pydantic schemas for type safety
- **CORS**: Enabled for cross-origin requests
- **Error Handling**: Custom exception handlers
- **Logging**: Structured logging with Python logging

### Data & Storage
- **Database**: MySQL with relational design
- **Image Storage**: ImageKit for cloud image management and CDN
- **Environment Config**: python-dotenv for environment variables
- **Data Seeding**: Faker for generating test data

### Development & Testing
- **Testing**: pytest with test fixtures
- **Code Quality**: Type hints and validation
- **Database Tools**: eralchemy for ERD generation
- **Development Tools**: Hot reload and debugging support

---mance REST API backend built with FastAPI and SQLAlchemy for the TireSouq tire marketplace platform. This graduation project backend provides comprehensive APIs for user management, product catalog, e-commerce functionality, appointment booking, and administrative controls with advanced features including JWT authentication, payment processing, and multi-role user system.

## 🚀 Features

### Authentication & Security
- JWT-based authentication with secure token management
- Password hashing with bcrypt and salt
- Multi-role user system (Customer, Vendor, Shop Owner, Admin)
- Protected routes with role-based access control
- Token refresh and expiration handling
- OAuth2 integration ready

### User & Vendor Management
- User registration, login, and profile management
- Vendor application and approval workflow
- Shop owner registration and verification
- Admin user management dashboard
- User profile image upload via ImageKit
- Email verification and password reset

### Product & Inventory APIs
- Comprehensive tire catalog with detailed specifications
- Product CRUD operations with filtering and search
- Category and brand management
- Tire size and vehicle compatibility matching
- Product image management with multiple images
- Stock tracking and inventory updates
- Dynamic pricing and discount management

### E-commerce Backend
- Shopping cart management with session persistence
- Order processing and status tracking
- Payment integration preparation (Stripe-ready)
- Coupon and discount code validation
- Multi-vendor order handling
- Order history and reporting

### Service & Appointment System
- Appointment booking and scheduling APIs
- Shop location and service management
- Appointment confirmation and tracking
- Service provider dashboard APIs
- Calendar integration support

### Vehicle Integration
- Vehicle information management
- Tire compatibility checking APIs
- Vehicle-specific product recommendations
- Multiple vehicle support per user

### Admin & Analytics
- Comprehensive admin APIs
- User, vendor, and shop approval endpoints
- System analytics and reporting
- Platform monitoring endpoints
- Content moderation APIs
- Database seeding utilities

---

## 🚀 Getting Started

### Prerequisites

- [Python 3.11+](https://www.python.org/downloads/)
- [MySQL 8.0+](https://www.mysql.com/downloads/)
- [Git](https://git-scm.com/)
- [pip](https://pip.pypa.io/en/stable/installation/) (Python package manager)

### Installation & Setup

#### 1. Clone the Repository

```bash
git clone https://github.com/Mohmmadshabrani/Graduation-Project.git
cd "Graduation Project/Backend"
```

#### 2. Create Virtual Environment

```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate
```

#### 3. Install Dependencies

```bash
# Install production dependencies
pip install -r requirements.txt

# For development (includes testing tools)
pip install -r dev-requirements.txt
```

#### 4. Environment Configuration

Create a `.env` file in the Backend directory:

```env
# Database Configuration
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_HOST=localhost
DB_PORT=3306
DB_NAME=tiresouq

# JWT Configuration
SECRET_KEY=your-super-secret-key-here
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30

# ImageKit Configuration (for image uploads)
IMAGEKIT_PUBLIC_KEY=your_imagekit_public_key
IMAGEKIT_PRIVATE_KEY=your_imagekit_private_key
IMAGEKIT_URL_ENDPOINT=your_imagekit_url_endpoint
```

#### 5. Database Setup

```bash
# Create database
mysql -u root -p -e "CREATE DATABASE tiresouq;"

# Run migrations
bash scripts/migrate_fresh.sh tiresouq

# Seed initial data
bash scripts/run_seeder.sh
```

#### 6. Run the Development Server

```bash
# Start the FastAPI server with auto-reload
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

Access the API documentation at:
- **Swagger UI**: http://localhost:8000/docs
- **ReDoc**: http://localhost:8000/redoc

## 📁 Project Structure

```
Backend/
├── alembic/                    # Database migration environment
│   ├── versions/              # Migration version files
│   ├── env.py                 # Alembic environment configuration
│   └── script.py.mako         # Migration script template
├── core/                      # Core application utilities
│   ├── error_handlers.py      # Custom exception handlers
│   ├── logging_config.py      # Logging configuration
│   └── settings.py            # Application settings
├── dependencies/              # Dependency injection modules
│   ├── admin.py               # Admin authentication dependencies
│   ├── auth.py                # Authentication dependencies
│   └── db.py                  # Database session dependencies
├── models/                    # SQLAlchemy ORM models
│   ├── user.py                # User model and relationships
│   ├── vendor.py              # Vendor model
│   ├── shop.py                # Shop model
│   ├── product.py             # Product and tire models
│   ├── category.py            # Category model
│   ├── brand.py               # Brand model
│   ├── cart.py                # Shopping cart model
│   ├── order.py               # Order and order items models
│   ├── appointment.py         # Appointment booking model
│   ├── payment.py             # Payment processing model
│   ├── coupon.py              # Coupon and discount model
│   ├── vehicle.py             # Vehicle information model
│   └── product_images.py      # Product image model
├── routers/                   # FastAPI route handlers
│   ├── auth.py                # Authentication endpoints
│   ├── user.py                # User management endpoints
│   ├── vendor.py              # Vendor management endpoints
│   ├── shop.py                # Shop management endpoints
│   ├── product.py             # Product CRUD endpoints
│   ├── category.py            # Category management endpoints
│   ├── brand.py               # Brand and tire size endpoints
│   ├── cart.py                # Shopping cart endpoints
│   ├── order.py               # Order processing endpoints
│   ├── vehicle.py             # Vehicle management endpoints
│   ├── product_image.py       # Image upload endpoints
│   ├── crud.py                # Generic CRUD operations
│   ├── messages.py            # Messaging endpoints
│   └── size.py                # Tire size endpoints
├── schemas/                   # Pydantic validation schemas
│   ├── user.py                # User-related schemas
│   ├── vendor.py              # Vendor schemas
│   ├── shop.py                # Shop schemas
│   ├── product.py             # Product schemas
│   ├── category.py            # Category schemas
│   ├── brand.py               # Brand schemas
│   ├── cart.py                # Cart schemas
│   ├── order.py               # Order schemas
│   ├── appointment.py         # Appointment schemas
│   └── vehicle.py             # Vehicle schemas
├── scripts/                   # Database and deployment scripts
│   ├── migrate_fresh.sh       # Fresh migration script
│   └── run_seeder.sh          # Database seeding script
├── seeder/                    # Database seeding utilities
│   └── seed.py                # Data seeding logic
├── tests/                     # Test suite
│   ├── test_auth.py           # Authentication tests
│   ├── test_users.py          # User management tests
│   └── test_products.py       # Product management tests
├── utils/                     # Utility functions
├── docs/                      # Documentation files
│   ├── API_DOCS.md            # API endpoints documentation
│   ├── AUTHENTICATION_GUIDE.md # Authentication guide
│   └── erd.md                 # Entity relationship diagram
├── images/                    # Static image storage
│   └── products_images/       # Product image uploads
├── config.py                  # Application configuration
├── database.py                # Database connection setup
├── main.py                    # FastAPI application entry point
├── requirements.txt           # Production dependencies
├── dev-requirements.txt       # Development dependencies
├── pyproject.toml             # Project metadata
├── alembic.ini                # Alembic configuration
└── README.md                  # This documentation file
```

└── README.md                  # This documentation file
```

## 📦 Key Dependencies

### Core Backend Dependencies

```python
# Core Framework
fastapi                     # Modern, fast web framework for building APIs
uvicorn                     # ASGI server implementation

# Database & ORM
sqlalchemy                  # SQL toolkit and ORM
mysql-connector-python      # MySQL database connector
alembic                     # Database migration tool

# Authentication & Security
python-jose                 # JWT token creation and verification
passlib[bcrypt]            # Password hashing with bcrypt

# External Services & Utilities
imagekitio                 # Image storage and optimization service
python-dotenv              # Environment variable loading
httpx                      # HTTP client library

# Development Dependencies (dev-requirements.txt)
pytest                     # Testing framework
Faker                      # Test data generation
eralchemy                  # Entity relationship diagram generation
graphviz                   # Graph visualization for ERD
pymysql                    # MySQL client for testing
```

---

## 🔧 Development Commands

### Database Management

```bash
# Create fresh database with migrations
bash scripts/migrate_fresh.sh tiresouq

# Run specific migration
alembic upgrade head

# Create new migration
alembic revision --autogenerate -m "Description of changes"

# Seed database with test data
bash scripts/run_seeder.sh

# Generate Entity Relationship Diagram
python -c "from eralchemy import render_er; render_er('mysql://user:pass@localhost/tiresouq', 'erd.png')"
```

### Development Server

```bash
# Start development server with auto-reload
uvicorn main:app --reload --host 0.0.0.0 --port 8000

# Start with custom port
uvicorn main:app --reload --port 8001

# Start with debug logging
uvicorn main:app --reload --log-level debug

# Production-like server
uvicorn main:app --host 0.0.0.0 --port 8000 --workers 4
```

### Testing & Quality

```bash
# Run all tests
pytest

# Run tests with coverage
pytest --cov=routers --cov=models --cov=schemas

# Run specific test file
pytest tests/test_auth.py

# Run tests with verbose output
pytest -v

# Run tests in parallel
pytest -n auto
```

### API Documentation

```bash
# Access interactive API docs (Swagger UI)
# http://localhost:8000/docs

# Access alternative API docs (ReDoc)
# http://localhost:8000/redoc

# Generate OpenAPI JSON schema
curl http://localhost:8000/openapi.json > api_schema.json
```

---

## 🚀 Deployment

### Environment Configuration

Create production environment file:

```env
# Production Database
DB_USER=prod_user
DB_PASSWORD=secure_password
DB_HOST=prod-mysql-server
DB_PORT=3306
DB_NAME=tiresouq_prod

# Secure JWT Configuration
SECRET_KEY=your-super-secure-production-secret-key
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=60

# ImageKit Production Keys
IMAGEKIT_PUBLIC_KEY=prod_public_key
IMAGEKIT_PRIVATE_KEY=prod_private_key
IMAGEKIT_URL_ENDPOINT=https://ik.imagekit.io/your_id
```

### Docker Deployment

```bash
# Build Docker image
docker build -t tiresouq-backend .

# Run container
docker run -d \
  --name tiresouq-api \
  -p 8000:8000 \
  --env-file .env.prod \
  tiresouq-backend

# Docker Compose deployment
docker-compose up -d
```

### Traditional Deployment

```bash
# Install production dependencies
pip install -r requirements.txt

# Run with Gunicorn
gunicorn -w 4 -k uvicorn.workers.UvicornWorker main:app --bind 0.0.0.0:8000

# Run with systemd service
sudo systemctl start tiresouq-backend
sudo systemctl enable tiresouq-backend
```

---

## 📊 API Endpoints Overview

### Authentication
- `POST /auth/register` - User registration
- `POST /auth/login` - User login
- `POST /auth/refresh` - Token refresh
- `GET /auth/me` - Current user info

### User Management
- `GET /users/` - List users (Admin)
- `GET /users/{id}` - Get user details
- `PUT /users/{id}` - Update user profile
- `DELETE /users/{id}` - Delete user (Admin)

### Product Management
- `GET /products/` - List products with filtering
- `POST /products/` - Create product (Vendor)
- `GET /products/{id}` - Get product details
- `PUT /products/{id}` - Update product
- `DELETE /products/{id}` - Delete product

### E-commerce
- `GET /cart/` - Get user cart
- `POST /cart/add` - Add item to cart
- `POST /orders/` - Create order
- `GET /orders/` - List user orders
- `GET /orders/{id}` - Get order details

### Vendor & Shop Management
- `POST /vendors/apply` - Vendor application
- `GET /vendors/` - List vendors
- `POST /shops/` - Create shop
- `GET /shops/` - List shops

For complete API documentation, visit `/docs` when the server is running.

---

## 🧪 Testing
## 🧪 Testing

The backend includes comprehensive test suites covering authentication, user management, product operations, and API endpoints.

### Running Tests

```bash
# Run all tests
pytest

# Run with coverage report
pytest --cov=routers --cov=models --cov=schemas --cov-report=html

# Run specific test categories
pytest tests/test_auth.py          # Authentication tests
pytest tests/test_users.py         # User management tests
pytest tests/test_products.py      # Product management tests

# Run tests with verbose output
pytest -v

# Run tests in parallel for faster execution
pytest -n auto
```

### Test Structure

```
tests/
├── conftest.py              # Test configuration and fixtures
├── test_auth.py             # Authentication endpoint tests
├── test_users.py            # User CRUD operation tests
├── test_vendors.py          # Vendor management tests
├── test_products.py         # Product management tests
├── test_orders.py           # Order processing tests
└── fixtures/                # Test data fixtures
```

### Test Data

Tests use Faker library to generate realistic test data including:
- User profiles with valid email addresses
- Product catalogs with specifications
- Order scenarios with multiple items
- Vendor and shop information

---

## 📈 Performance & Monitoring

### Database Optimization
- Connection pooling with SQLAlchemy
- Database indexes on frequently queried fields
- Efficient relationship loading strategies
- Query optimization for large datasets

### API Performance
- Async/await support for non-blocking operations
- Request/response validation with Pydantic
- Efficient JSON serialization
- CORS optimization for frontend requests

### Monitoring Endpoints
- Health check endpoint: `GET /health`
- Database connection status: `GET /health/db`
- System metrics endpoint: `GET /metrics`

---

## 🔒 Security Features

### Authentication Security
- JWT tokens with configurable expiration
- Secure password hashing with bcrypt
- Role-based access control (RBAC)
- Protected routes with dependency injection

### Data Security
- Input validation with Pydantic schemas
- SQL injection prevention with parameterized queries
- XSS protection through proper data encoding
- CORS configuration for trusted origins

### Environment Security
- Secure secret management with environment variables
- Database credential protection
- API key management for external services

---

## 🚀 Production Considerations

### Environment Variables

```bash
# Required for production
export SECRET_KEY="your-production-secret-key"
export DB_PASSWORD="secure-database-password"
export IMAGEKIT_PRIVATE_KEY="your-imagekit-private-key"

# Optional optimizations
export WORKERS=4
export MAX_CONNECTIONS=100
export TIMEOUT=60
```

### Database Configuration

```sql
-- Production database optimizations
SET innodb_buffer_pool_size = 1G;
SET max_connections = 200;
SET query_cache_size = 256M;

-- Create database with proper charset
CREATE DATABASE tiresouq 
CHARACTER SET utf8mb4 
COLLATE utf8mb4_unicode_ci;
```

### Deployment Checklist

- [ ] Environment variables configured
- [ ] Database migrations applied
- [ ] SSL certificates installed
- [ ] Backup strategy implemented
- [ ] Monitoring and logging configured
- [ ] API rate limiting enabled
- [ ] Security headers configured

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes following the coding standards
4. Add tests for new functionality
5. Commit your changes (`git commit -m 'Add amazing feature'`)
6. Push to the branch (`git push origin feature/amazing-feature`)
7. Open a Pull Request

### Coding Standards

- **Python**: Follow [PEP 8](https://www.python.org/dev/peps/pep-0008/) style guide
- **Type Hints**: Use type hints for all function parameters and return values
- **Documentation**: Add docstrings for all public functions and classes
- **Testing**: Write tests for new features and bug fixes
- **Validation**: Use Pydantic schemas for all API inputs/outputs

### Development Setup

```bash
# Install development dependencies
pip install -r dev-requirements.txt

# Install pre-commit hooks
pre-commit install

# Run code formatting
black .
isort .

# Run linting
flake8 .
mypy .
```

---

## 📚 Additional Resources

### Documentation
- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [SQLAlchemy Documentation](https://docs.sqlalchemy.org/)
- [Alembic Tutorial](https://alembic.sqlalchemy.org/en/latest/tutorial.html)
- [Pydantic Documentation](https://docs.pydantic.dev/)

### API Documentation
- **Interactive Docs**: http://localhost:8000/docs (when server is running)
- **Alternative Docs**: http://localhost:8000/redoc
- **OpenAPI Schema**: http://localhost:8000/openapi.json

### Database Schema
- See `docs/erd.md` for Entity Relationship Diagram
- Check `models/` directory for detailed model definitions

---

## 📞 Support & Contact

For questions, issues, or contributions:

- **API Issues**: Check the interactive docs at `/docs`
- **Database Issues**: Review migration files in `alembic/versions/`
- **Performance Issues**: Check the monitoring endpoints
- **Security Concerns**: Review the security documentation

## 📄 License

This project is developed for educational purposes as part of a graduation requirement.

**Built with FastAPI & SQLAlchemy**
