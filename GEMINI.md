# GEMINI.md: Project Overview

## Project Overview

This is a Hotel Revenue Management web application. It consists of a Python/FastAPI backend that serves a REST API, and two distinct single-page front-ends for user and administrative functions.

The application allows hotel managers to upload pricing and availability data from Excel/CSV files, configure partner details (like commissions) via JSON files, and then use this data to simulate room prices and check availability.

**Key Technologies:**

*   **Backend:** Python, FastAPI, SQLModel, Pandas, PostgreSQL (inferred)
*   **Frontend:** HTML, JavaScript, Tailwind CSS
*   **Containerization:** Docker

## Building and Running

### Backend

1.  **Install Dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

2.  **Run the Server:**
    The application is a standard FastAPI project. It can be run using uvicorn.
    ```bash
    uvicorn main:app --reload --port 8000
    ```

### Frontend

The front-end files (`frontend/index.html` and `admin/index.html`) are static and can be served by any web server. For local development, you can open them directly in your browser.

**Note:** The front-end is configured to communicate with a production API at `https://api-folkestone.e-hotelmanager.com`. For local development, you will need to change the `API_BASE` and `API_URL` constants in the HTML files to point to your local server (e.g., `http://localhost:8000`).

### Docker

A `Dockerfile` is present, indicating the application is designed to be run in a container.

```bash
# TODO: Add Docker build and run commands.
# Example:
# docker build -t hotel-rm-app .
# docker run -p 8000:8000 -v $(pwd)/data:/app/data hotel-rm-app
```

## Development Conventions

*   **Backend:** The backend code in `main.py` is well-structured, using Pydantic for data validation and SQLModel for database interaction. It follows standard FastAPI practices.
*   **API:** The API is RESTful and includes endpoints for managing hotels, uploading files, and performing simulations.
*   **Data:** The application uses a PostgreSQL database for structured data (hotel info, configs) and a file-based storage (`/app/data`) for uploaded Excel/JSON data.
