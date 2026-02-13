# Learning Log

A Django web application for tracking learning topics and entries, from Part II of Python Crash Course (Chapters 18-20).

## Features

- User registration and authentication
- Create and manage learning topics
- Add detailed entries to each topic
- Private topics (users only see their own data)
- Responsive Bootstrap styling

## Project Structure

```
web_application/
├── learning_log/           # Main Django project
│   ├── settings.py         # Project settings
│   ├── urls.py             # Root URL configuration
│   └── wsgi.py             # WSGI entry point
├── learning_logs/          # Main app
│   ├── models.py           # Topic and Entry models
│   ├── views.py            # View functions
│   ├── urls.py             # App URL patterns
│   ├── forms.py            # TopicForm, EntryForm
│   └── templates/          # HTML templates
├── users/                  # User authentication app
│   ├── views.py            # Register view
│   ├── urls.py             # Auth URL patterns
│   └── templates/          # Login/register templates
├── manage.py               # Django CLI
├── requirements.txt        # Dependencies
├── Procfile                # Heroku deployment
└── runtime.txt             # Python version
```

## Models

**Topic**: A subject the user is learning about
- `text`: Topic name (max 200 chars)
- `date_added`: Creation timestamp
- `owner`: Foreign key to User

**Entry**: Specific notes about a topic
- `topic`: Foreign key to Topic
- `text`: Entry content
- `date_added`: Creation timestamp

## Requirements

```bash
pip install -r requirements.txt
```

## Setup

```bash
# Create database
python manage.py migrate

# Create admin user
python manage.py createsuperuser

# Run development server
python manage.py runserver
```

Visit `http://localhost:8000` to use the application.

## Deployment

The project includes configuration for Heroku deployment:
- `Procfile` - Gunicorn web server
- `runtime.txt` - Python version
- `requirements.txt` - Dependencies
