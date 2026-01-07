# Connectly Backend

A Django REST API backend with JWT authentication and CORS support.

## Features

- **Django 4.x** - Modern Python web framework
- **Django REST Framework** - Powerful API toolkit
- **JWT Authentication** - Token-based auth via SimpleJWT
- **CORS Support** - Cross-origin resource sharing enabled
- **Environment Variables** - Secure config with python-dotenv

---

## Prerequisites

- **Python 3.10+** (3.11+ recommended)
- **Git**
- **VS Code** (optional but recommended)

> **macOS Users:** Use `python3` instead of `python` when outside virtual environments.

---

## Installation

### 1. Clone the Repository
```bash
git clone <YOUR_REPO_URL>
cd connectly
```

### 2. Create Virtual Environment

**macOS/Linux:**
```bash
python3 -m venv env
source env/bin/activate
```

**Windows (PowerShell):**
```powershell
python -m venv env
.\env\Scripts\Activate.ps1
```

> **Windows Security Error?** Run this first:
> ```powershell
> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
> ```

### 3. Install Dependencies
```bash
# Upgrade pip first
python -m pip install --upgrade pip

# Install requirements
pip install -r requirements.txt
```

---

## Configuration

### 1. Create Environment File

**macOS/Linux:**
```bash
cp .env.example .env
```

**Windows:**
```powershell
copy .env.example .env
```

### 2. Generate Secret Key
```bash
python -c "from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())"
```

Copy the output and paste it into your `.env` file:
```env
DJANGO_SECRET_KEY=your-generated-secret-key-here
DEBUG=True
```

> **Important:** Never commit `.env` to Git! It's already in `.gitignore`.

---

## Database Setup

### 1. Run Migrations
```bash
python manage.py migrate
```

### 2. Create Admin User
```bash
python manage.py createsuperuser
```

Follow the prompts to set username, email, and password.

---

## Running the Server

Start the development server:
```bash
python manage.py runserver
```

The server will be available at:
- **API:** http://127.0.0.1:8000/
- **Admin Panel:** http://127.0.0.1:8000/admin/

**Stop the server:** Press `CTRL + C`

---

## VS Code Setup

### 1. Open Project in VS Code
```bash
code .
```

### 2. Select Python Interpreter

1. Press `Cmd/Ctrl + Shift + P`
2. Type: `Python: Select Interpreter`
3. Choose your virtual environment:
   - **macOS/Linux:** `./env/bin/python`
   - **Windows:** `.\env\Scripts\python.exe`

### 3. Reload if Needed

If import errors persist:
1. Press `Cmd/Ctrl + Shift + P`
2. Type: `Developer: Reload Window`

---

## Common Issues & Solutions

### `command not found: python` (macOS)
Use `python3` outside virtual environments:
```bash
python3 --version
```

### Import Errors in VS Code
**Solution:** Select the correct Python interpreter (see VS Code Setup above)

### "You have unapplied migrations"
**Solution:** Run migrations:
```bash
python manage.py migrate
```

### Blank Page at http://127.0.0.1:8000/
**Solution:** This is normal until you configure URLs. Admin panel still works at `/admin/`

---

## 📁 Project Structure
```
connectly/
├── config/              # Django settings, URLs, WSGI/ASGI
├── manage.py            # Django management script
├── requirements.txt     # Python dependencies
├── .env.example         # Environment template
├── .gitignore          # Git ignore rules
└── README.md           # This file

# Not committed to Git:
├── env/                # Virtual environment (local only)
└── .env                # Your secrets (local only)
```

---

## Security Notes

This is a **development setup** with:
- SQLite database
- `DEBUG=True`
- Permissive CORS settings

**Before deploying to production:**
- [ ] Set `DEBUG=False`
- [ ] Configure `ALLOWED_HOSTS`
- [ ] Restrict `CORS_ALLOWED_ORIGINS`
- [ ] Use PostgreSQL or MySQL
- [ ] Use environment-specific `.env` files
- [ ] Set up proper secret management

---

## Updating Dependencies

After installing new packages:
```bash
pip freeze > requirements.txt
```

---

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## Support

For issues and questions:
- Open an issue on GitHub
- Contact: your-email@example.com

---

**Happy Coding! 🎉**
