 # My First Blog

A Django-based personal blogging application with post management, commenting system, and user authentication.

## Project Overview

This is a complete blogging platform built with Django that allows users to:
- Write and publish blog posts
- Add comments to posts
- Manage drafts and published posts
- User authentication and author management

## Technology Stack

- **Backend**: Django 4.2.7
- **Database**: SQLite
- **Frontend**: HTML, CSS with Bootstrap
- **Authentication**: Django built-in auth system
- **Deployment**: PythonAnywhere compatible

## Project Structure

```
my-first-blog/
├── blog/
│   ├── migrations/           # Database migrations
│   ├── static/
│   │   └── css/
│   │       └── blog.css     # Custom styles
│   ├── templates/
│   │   └── blog/
│   │       ├── base.html    # Base template
│   │       ├── post_list.html
│   │       ├── post_detail.html
│   │       ├── post_edit.html
│   │       └── post_draft_list.html
│   ├── admin.py
│   ├── forms.py             # Post and Comment forms
│   ├── models.py            # Post and Comment models
│   ├── urls.py              # Blog URL routes
│   └── views.py             # View functions
├── mysite/
│   ├── settings.py          # Django settings
│   ├── urls.py              # Project URL configuration
│   └── wsgi.py
├── manage.py
└── requirements.txt
```

## Installation & Setup

### Prerequisites
- Python 3.x
- pip (Python package manager)

### Installation Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/eyob42/my-first-blog.git
   cd my-first-blog
   ```

2. **Create and activate virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run database migrations**
   ```bash
   python manage.py migrate
   ```

5. **Create superuser account**
   ```bash
   python manage.py createsuperuser
   ```

6. **Start development server**
   ```bash
   python manage.py runserver
   ```

7. **Access the application**
   - Blog: http://localhost:8000
   - Admin: http://localhost:8000/admin

## Database Models

### Post Model
- `author`: ForeignKey to User
- `title`: CharField (max_length=200)
- `text`: TextField (blog post content)
- `created_date`: DateTimeField (auto_now_add=True)
- `published_date`: DateTimeField (nullable, blank=True)
- Methods:
  - `publish()`: Sets published_date to current time
  - `approve_comments()`: Filters approved comments
  - `__str__()`: Returns post title

### Comment Model
- `post`: ForeignKey to Post (related_name='comments')
- `author`: CharField (max_length=200)
- `text`: TextField (comment content)
- `created_date`: DateTimeField (auto_now_add=True)
- `approved_comment`: BooleanField (default=False)
- Methods:
  - `approve()`: Sets approved_comment to True
  - `__str__()`: Returns comment text

## URL Routes

### Blog URLs
- `/`: Post list view (homepage)
- `post/<int:pk>/`: Post detail view
- `post/new/`: Create new post
- `post/<int:pk>/edit/`: Edit existing post
- `post/<int:pk>/publish/`: Publish draft post
- `post/<int:pk>/remove/`: Delete post
- `post/<int:pk>/comment/`: Add comment to post
- `comment/<int:pk>/approve/`: Approve comment
- `comment/<int:pk>/remove/`: Delete comment
- `drafts/`: List of unpublished posts

## Features

### Blog Post Management
- **Create Posts**: Authenticated users can create new blog posts
- **Edit Posts**: Authors can edit their existing posts
- **Draft System**: Save posts as drafts and publish later
- **Post Deletion**: Remove unwanted posts

### Comment System
- **Public Comments**: Anyone can comment on posts
- **Comment Moderation**: Approve or delete comments
- **Author Identification**: Track comment authors

### User Interface
- **Responsive Design**: Bootstrap-based styling
- **Post List**: Chronological listing of published posts
- **Post Detail**: Full post view with comments
- **Draft Management**: Separate view for unpublished posts

## Templates

### Base Template (`base.html`)
- Common layout for all pages
- Navigation header
- Bootstrap CSS integration
- Content blocks for inheritance

### Page Templates
- `post_list.html`: Homepage with post listings
- `post_detail.html`: Individual post with comments
- `post_edit.html`: Create/edit post form
- `post_draft_list.html`: Draft post management

## Forms

### PostForm
- Fields: title, text
- Used for creating and editing posts

### CommentForm
- Fields: author, text
- Used for adding comments to posts

## Views

### Post-related Views
- `post_list`: Display published posts
- `post_detail`: Show individual post with comments
- `post_new`: Create new post
- `post_edit`: Edit existing post
- `post_draft_list`: List unpublished posts
- `post_publish`: Publish a draft post
- `post_remove`: Delete a post

### Comment-related Views
- `add_comment_to_post`: Add comment to post
- `comment_approve`: Approve a comment
- `comment_remove`: Delete a comment

## Admin Features

The Django admin interface provides:
- Full CRUD operations for posts and comments
- User management
- Database administration

## Custom Styling

The project includes custom CSS (`blog.css`) with:
- Typography improvements
- Layout enhancements
- Form styling
- Responsive design elements

## Deployment

This project is configured for deployment on PythonAnywhere and includes:
- WSGI configuration
- Production-ready settings
- Static files configuration

## Testing

Run the Django test suite:
```bash
python manage.py test blog
```

## Dependencies

- Django==4.2.7
- asgiref==3.7.2
- sqlparse==0.4.4
- tzdata==2023.3

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License

This project is open source and available under the MIT License