# TireSouq - Comprehensive Tire Marketplace Platform

A modern full-stack tire marketplace application built with Flutter frontend and FastAPI backend. This graduation project demonstrates a complete e-commerce solution with advanced features including multi-user roles, payment integration, appointment booking, and comprehensive product management.

## 🚀 Features

### Authentication & User Management

- JWT-based authentication with secure token storage
- Multi-role user system (Customer, Vendor, Shop Owner, Admin)
- User registration and login with email verification
- Profile management with image upload
- Password reset functionality
- OAuth integration ready

### Product & Inventory Management

- Comprehensive tire catalog with detailed specifications
- Product search and filtering by brand, category, size, and vehicle compatibility
- Dynamic pricing with discount management
- Product image gallery with multiple images per product
- Stock management and availability tracking
- Vendor inventory management dashboard

### E-commerce Functionality

- Shopping cart with quantity management
- Order placement and tracking system
- Payment processing with Stripe integration
- Order history and status updates
- Coupon and discount code system
- Multi-vendor order processing

### Service & Appointment System

- Tire installation appointment booking
- Shop location and service management
- Appointment scheduling and confirmation
- Service provider dashboard
- Customer appointment history

### Vehicle Integration

- Vehicle information management
- Tire compatibility checking
- Vehicle-specific product recommendations
- Multiple vehicle support per user

### Admin & Management

- Comprehensive admin dashboard
- User, vendor, and shop approval system
- Category and brand management
- System analytics and reporting
- Platform monitoring and settings
- Content moderation tools

### Mobile & Web Support

- Responsive design for mobile and web platforms
- Cross-platform Flutter implementation
- Progressive Web App (PWA) ready
- Offline capability with local storage

## 🛠️ Technology Stack

### Frontend (Flutter)

- **Framework**: Flutter 3.7.2+ with Dart
- **State Management**: Flutter BLoC pattern
- **Navigation**: GoRouter for declarative routing
- **HTTP Client**: Dio for API communication
- **UI Components**: Material Design with custom widgets
- **Storage**: Flutter Secure Storage & SharedPreferences
- **Internationalization**: Flutter Intl for multi-language support
- **Payment**: Flutter Stripe integration
- **Image Handling**: Image Picker for photo uploads

### Backend (FastAPI)

- **Framework**: FastAPI with Python 3.10+
- **Database**: MySQL with SQLAlchemy ORM
- **Authentication**: JWT tokens with PassLib for hashing
- **Migration**: Alembic for database schema management
- **Image Storage**: ImageKit for cloud image management
- **API Documentation**: Auto-generated OpenAPI/Swagger docs
- **CORS**: Enabled for cross-origin requests

### Database & Infrastructure

- **Database**: MySQL with relational design
- **ORM**: SQLAlchemy for Python
- **Migrations**: Alembic migration system
- **Image CDN**: ImageKit for optimized image delivery
- **Environment**: Docker-ready configuration

## 🚀 Getting Started

### Prerequisites

- [Flutter SDK 3.7.2+](https://docs.flutter.dev/get-started/install)
- [Dart SDK](https://dart.dev/get-dart)
- [Python 3.10+](https://www.python.org/downloads/)
- [MySQL 8.0+](https://www.mysql.com/)
- [Git](https://git-scm.com/)

### Installation & Setup

#### 1. Clone the Repository

```bash
git clone https://github.com/Mohmmadshabrani/Graduation-Project.git
cd "Graduation Project"
```

#### 2. Setup (Flutter)

```bash
# Install dependencies
flutter pub get

# Generate code (if needed)
flutter packages pub run build_runner build

# Run on mobile/desktop
flutter run

# Run on web
flutter run -d chrome
```

#### 4. Database Configuration

```sql
-- Create database
CREATE DATABASE tiresouq;

-- Update Backend/config.py with your database credentials
DATABASE_URL = "mysql://username:password@localhost/tiresouq"
```

## 📁 Project Structure

````
Frontend/
├── lib/
│   ├── core/               # Core utilities and constants
│   ├── data/               # Data models and repositories
│   ├── features/           # Feature-based modules
│   │   ├── auth/           # Authentication features
│   │   ├── storefront/     # E-commerce features
│   │   │   ├── home/       # Homepage and navigation
│   │   │   ├── product/    # Product browsing and details
│   │   │   ├── checkout/   # Cart and checkout process
│   │   │   ├── orders/     # Order management
│   │   │   └── settings/   # User settings
│   │   └── admin/          # Admin panel features
│   ├── services/           # API services and external integrations
│   ├── shared/             # Shared widgets and utilities
│   └── l10n/               # Internationalization files
├── assets/
│   └── images/             # Static images and icons
└── web/                    # Web-specific configurations


## 📦 Key Dependencies

### Frontend Dependencies

```yaml
# Core Flutter packages
flutter_bloc: ^9.0.0 # State management
go_router: ^15.1.2 # Navigation
dio: ^5.8.0+1 # HTTP client

# UI & UX
carousel_slider: ^5.0.0 # Image carousels
intl_phone_field: ^3.1.0 # Phone input
flutter_svg: ^2.0.7 # SVG support

# Storage & Security
flutter_secure_storage: ^9.0.0 # Secure token storage
shared_preferences: ^2.5.3 # Local preferences

# Payments & Images
flutter_stripe: ^11.1.0 # Payment processing
image_picker: ^1.0.4 # Image selection

# Utilities
equatable: ^2.0.7 # Value equality
get_it: ^8.0.0 # Dependency injection
flutter_dotenv: ^5.2.1 # Environment variables
````

## 🔧 Development Commands

### Frontend Commands

```bash
# Development
flutter run                    # Run on connected device
flutter run -d chrome          # Run on web browser
flutter run --release          # Run optimized build

# Building
flutter build apk              # Build Android APK
flutter build web              # Build for web deployment
flutter build ios              # Build for iOS (macOS only)

# Testing & Analysis
flutter test                   # Run unit tests
flutter analyze                # Static code analysis
flutter pub get                # Install dependencies

# Code Generation
flutter packages pub run build_runner build --delete-conflicting-outputs
```

### Frontend (.env)

```env
# API Configuration
API_BASE_URL=http://localhost:8000
API_TIMEOUT=30000

# Stripe
STRIPE_PUBLISHABLE_KEY=pk_test_your-stripe-publishable-key
```

## 🚀 Deployment

### Frontend Deployment

```bash
# Web deployment
flutter build web --release
# Deploy the build/web folder to your hosting provider

# Android deployment
flutter build apk --release
# Distribute the build/app/outputs/flutter-apk/app-release.apk

# iOS deployment (macOS only)
flutter build ios --release
# Follow iOS App Store deployment guidelines
```

### Backend Deployment

```bash
# Using Docker
docker build -t tiresouq-backend .
docker run -p 8000:8000 tiresouq-backend

# Using pip
pip install -r requirements.txt
gunicorn -w 4 -k uvicorn.workers.UvicornWorker main:app
```

## 🧪 Testing

### Frontend Testing

```bash
flutter test                 # Unit tests
flutter integration_test     # Integration tests
flutter test --coverage     # Generate coverage report
```

### Backend Testing

```bash
pytest                       # Run all tests
pytest tests/test_auth.py    # Run specific test file
pytest --cov=routers         # Coverage for specific module
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Code Style Guidelines

- **Flutter**: Follow [Dart style guide](https://dart.dev/guides/language/effective-dart/style)
- **Python**: Follow [PEP 8](https://www.python.org/dev/peps/pep-0008/) style guide
- Use meaningful commit messages
- Add tests for new features
- Update documentation as needed

## 📄 License

This project is developed for educational purposes as part of a graduation requirement.

## 📞 Support & Contact

For questions, issues, or contributions, please:

- Open an issue on GitHub
- Check the [API Documentation](http://localhost:8000/docs) when backend is running
- Review the [Flutter Documentation](https://docs.flutter.dev/)
- Consult [FastAPI Documentation](https://fastapi.tiangolo.com/)

**Built with Flutter & FastAPI**
