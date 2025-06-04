# Backend Service

This module provides the API for the AI News Dashboard.
It will be responsible for:
- Serving news data to the frontend.
- Managing the database of news articles.
- Handling any other backend logic.

## Technology Stack

- Python
- Flask (for the web framework)
- PostgreSQL (as the database)
- SQLAlchemy (for ORM)
- Marshmallow (for schema validation and serialization)

## Module Construction

- **Core Components:**
    - `app.py`: Initializes the Flask application, extensions (SQLAlchemy, Marshmallow, etc.), and ties everything together.
    - `config.py`: Manages application configuration (database URI, secret keys, etc.).
    - `models.py`: Defines SQLAlchemy database models (e.g., `Article`, `Source`).
    - `routes.py`: Contains Flask Blueprints defining API endpoints.
    - `schemas.py` (new file): Defines Marshmallow schemas for validating and serializing data.
- **Database Schema:**
    - `articles` table:
        - `id` (PK)
        - `title`
        - `content` (full text or summary)
        - `url` (unique)
        - `source_id` (FK to `sources` table)
        - `published_at`
        - `fetched_at`
    - `sources` table:
        - `id` (PK)
        - `name` (e.g., "TechCrunch API", "Ars Technica RSS")
        - `url` (base URL or feed URL)
        - `type` (e.g., "api", "rss", "scrape")
- **RESTful API Endpoints:**
    - `/api/articles`:
        - `GET`: List articles (with pagination, filtering by source, date range, search query).
        - `POST`: (Potentially, for manual article submission or if data collection posts here)
    - `/api/articles/<id>`:
        - `GET`: Retrieve a single article.
    - `/api/sources`:
        - `GET`: List available news sources.
        - `POST`: Add a new news source (admin functionality).
- **Data Flow:**
    - Data collection module populates the PostgreSQL database.
    - Frontend fetches data from the Flask API endpoints.
    - API uses SQLAlchemy to query the database and Marshmallow to serialize/deserialize data.

## Testing Strategy

- **Unit Tests (`pytest`):**
    - Test business logic in services/utility functions (e.g., data transformation, specific queries).
    - Test Marshmallow schema validation and serialization.
    - Test individual model methods if any complex logic is embedded.
- **API Integration Tests (`pytest` + Flask Test Client):**
    - Test each API endpoint for correct responses, status codes, and error handling.
    - Use a separate test database or in-memory SQLite for testing database interactions.
    - Mock external dependencies if any (though less common for backend API tests).
