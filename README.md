# AutoTracker

Web-based automobile tracking application for vehicle owners and
operators. Built with Django, AutoTracker provides comprehensive vehicle
and maintenance tracking with a modern, responsive interface.

## Features

- **Vehicle Management**: Track multiple vehicles with detailed
  specifications
- **Multi-User Support**: Role-based access (Owner, Primary Driver, Authorized User)
- **Theme System**: Built-in themes including automotive-inspired designs
- **Responsive Design**: Works on desktop, tablet, and mobile devices

## Quick Start

### Prerequisites

- Python 3.10+
- Python virtual environment usage is recommended

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd autotracker
```

2. Create and activate virtual environment:
```bash
python3 -m venv venv
```

3. Install dependencies:
```bash
./venv/bin/pip3 install -e .
./venv/bin/pip3 install -e .[dev]  # For development dependencies
```

4. Set up the database:
```bash
./venv/bin/python3 manage.py migrate
```

**Note**: The migration automatically creates a default admin user with
the following credentials:

- **Email**: `admin@autotracker.example.com`
- **Password**: `admin123`

This user is ready to use for testing and initial setup. You should change
the password after first login.

5. Start the development server:
```bash
./venv/bin/python3 manage.py runserver
```

6. Open your browser to `http://127.0.0.1:8000`

## User Management

### Admin Interface
Access the Django Admin at `http://127.0.0.1:8000/admin/` using the default admin credentials above. From here you can:
- Create new user accounts
- Manage user permissions and roles
- View and modify all application data

### Creating New Users
1. Log in to Django Admin (`/admin/`)
2. Go to "Users" under the "Accounts" section
3. Click "Add User" 
4. Fill in the user details (email is required, username is optional)
5. Set password and permissions as needed
6. Save the user

New users will be able to log in immediately without email verification.

## Development

### Code Quality
```bash
# Format code
black .

# Lint code
flake8 apps/ autotracker/ manage.py --exclude=*/migrations/*
```

### Project Structure
```
autotracker/
├── apps/
│   ├── accounts/      # User management and profiles
│   ├── vehicles/      # Vehicle tracking
│   ├── maintenance/   # Maintenance records
│   └── core/          # Shared utilities and mixins
├── templates/         # Django templates
├── static/            # CSS, JavaScript, images
├── autotracker/       # Django project settings
└── manage.py          # Django management script
```

## Usage

### Adding Your First Vehicle
1. Log in to the application
2. Click "Add Vehicle" from the dashboard
3. Fill in vehicle details (make, model, year, VIN, etc.)
4. Save the vehicle

## Contributing

1. Follow PEP 8 style guidelines
2. Run Black formatter before committing
3. Ensure all tests pass
4. Update documentation as needed

## License

ISC License - see LICENSE file for details.
