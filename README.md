# AI News Dashboard

This project aims to create a dashboard for collecting and displaying AI news from across the internet.

## Modules:
- **data_collection:** Fetches news from various sources.
- **backend:** Provides an API to serve the news data and manages the database.
- **frontend:** Displays the news dashboard to the user.

## Technology Stack

- **Backend:** Python (Flask), PostgreSQL (with SQLAlchemy)
- **Frontend:** React, Tailwind CSS
- **Data Collection:** Python (`requests`, `BeautifulSoup`/`Scrapy`, `feedparser`)
- **Scheduling (Data Collection):** `APScheduler`
- **Containerization:** Docker
