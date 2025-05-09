# Digital Zoo Management System 🦁

This is a Django REST Framework backend project simulating a digital zoo. It includes features for managing animals, habitats, zookeepers, memberships, and ticketing, with token-based authentication and automatic zookeeper assignment.

---

## 📌 Features

- CRUD operations for animals, species, habitats, zookeepers
- Visitor registration, login, and token-based authentication
- Role-based user access (visitor, zookeeper)
- Auto-assign zookeepers based on workload using `.annotate(Count())`
- Membership system and event booking
- Clean API structure using Django REST Framework

---

## 🛠️ Technologies Used

- Python 3.11
- Django 4.x
- Django REST Framework
- SQLite3 (default Django DB)
- Token authentication (DRF auth)
- Postman or browser for testing API routes

---

## 📁 Project Structure

```text
digital_zoo/
├── zoo/                      # Django app
│   ├── models.py
│   ├── views.py
│   ├── urls.py
│   ├── serializers.py
│   └── admin.py
├── digital_zoo_project/      # Project config
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── manage.py
├── requirements.txt
└── README.md
```

---

## 🚀 Installation & Running

### 1. Clone the repository

```bash
git clone https://github.com/AbdellahSbh/Portfolio_Digital_Zoo_by_AbdellahSbh.git
cd Portfolio_Digital_Zoo_by_AbdellahSbh
```

### 2. Create a virtual environment

```bash
# Windows
python -m venv env
env\Scripts\activate

# macOS/Linux
python3 -m venv env
source env/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Run migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

### 5. Start the development server

```bash
python manage.py runserver
```

---

## 🔐 Authentication

- Token authentication is used (DRF).
- Login endpoint returns token + user role.
- Use the token for accessing protected routes.

```http
POST /login/
{
  "username": "your_user",
  "password": "your_pass"
}
```

---

## 🧠 Key Functionality

- `auto_assign_zookeeper`: Assigns the least busy zookeeper to a care task  
- `available_zookeepers`: Lists zookeepers with less than 5 assigned animals  
- Custom user model with roles (visitor, zookeeper)
- Uses `@api_view` and `.annotate()` to handle dynamic queries

---

## 📡 Example Endpoints

```text
POST    /login/                      → Log in and receive token
POST    /register/                   → Register a new user
GET     /animals/                    → List all animals
POST    /care/assign/                → Auto-assign zookeeper
GET     /zookeepers/available/       → List available zookeepers
GET/POST /memberships/              → Membership management
GET/POST /events/booking/           → Book events
```

> Use Postman or any API testing tool to interact with the system.

---

## 📄 License

This project is developed for academic purposes as part of the Programming Clinic module  
at Lancaster University Leipzig – Michaelmas Term 2025.
