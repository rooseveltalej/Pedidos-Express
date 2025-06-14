## ✨ Key Features

* **Restaurant Management:**
    * Add new restaurants with details like name, type, and an image.
    * Dynamically add multiple meals to a new restaurant, each with a name, price, and optional image.
    * View a list of all restaurants.
* **Discover & Search:**
    * A main dashboard displaying all restaurants, recently favorited restaurants, and top-ordered restaurants.
    * Search for restaurants by name or type.
* **Ordering System:**
    * View a detailed page for each restaurant, listing all its available meals.
    * An interactive shopping cart where users can add meals, adjust quantities, or remove items.
    * Place an order with a calculated subtotal, tax, shipping, and service fees.
    * View the complete order history for a specific restaurant.
* **Favorites:**
    * Mark and unmark restaurants as favorites.
    * View a dedicated section for recently favorited restaurants on the homepage.
* **RESTful API:**
    * A well-structured backend API that handles all business logic.
    * Automatic creation of the SQLite database and tables on startup.

## 🚀 Technologies Used

This project is divided into a frontend and a backend.

**Backend:**
* **Framework:** FastAPI
* **Database:** SQLite
* **ORM:** SQLAlchemy
* **Server:** Uvicorn
* **Data Validation:** Pydantic
* **Dependencies:** `fastapi`, `uvicorn`, `sqlalchemy`, `pydantic`.

**Frontend:**
* **Core:** HTML, CSS, JavaScript (ESM)
* **Styling:** Tailwind CSS
* **UI:** Vanilla JavaScript for DOM manipulation and interactivity.

## 📂 Project Structure

The repository is organized into a `backend` and a `frontend` directory, keeping a clear separation of concerns.

```
├── backend/
│   ├── db/
│   │   ├── init.py
│   │   ├── db.py           # SQLAlchemy setup and session management
│   │   ├── init__db.py     # Script to initialize tables
│   │   └── script.sql      # Raw SQL schema definition
│   ├── models/             # SQLAlchemy ORM models
│   ├── routes/             # API endpoint definitions (routers)
│   ├── schemas/            # Pydantic models for data validation
│   ├── scripts/            # Scripts to populate the database
│   ├── utils/              # Utility functions (e.g., image handling)
│   ├── app.py              # Main FastAPI application
│   ├── requirements.txt    # Python dependencies
│   └── run_server.py       # Script to run the backend server
└── frontend/
├── components/         # Reusable HTML components (navbar)
├── images/             # Placeholder images
├── pages/              # HTML files for different views
├── scripts/            # JavaScript files for each page
└── index.html          # Main entry point
```

## 🗄️ Database Schema

The application uses a relational database to store information about restaurants, meals, orders, and favorites. The relationships are managed by SQLAlchemy.

* **`Restaurants`**: Stores restaurant information.
* **`RestaurantMeals`**: Stores the meals available at each restaurant.
* **`Orders`**: Stores order details, linked to a restaurant.
* **`OrderMeals`**: A junction table linking orders to the specific meals included.
* **`Favorite`**: Stores which restaurants have been marked as favorites.

These relationships are defined in the SQL file and implemented in the SQLAlchemy models.

## 🌐 API Endpoints

The FastAPI backend exposes several RESTful endpoints to be consumed by the frontend.

| Method | Endpoint                                   | Description                                                 |
| :----- | :----------------------------------------- | :---------------------------------------------------------- |
| `POST` | `/restaurants/add-restaurant`              | Creates a new restaurant with its meals.         |
| `GET`  | `/restaurants/restaurants`                 | Retrieves all restaurants.                       |
| `GET`  | `/restaurants/restaurants/search`          | Searches for restaurants by a query string (`q`).  |
| `GET`  | `/restaurants/restaurants/favorites-recent`| Gets the most recently favorited restaurants.      |
| `GET`  | `/restaurants/restaurants/top-ordered`     | Gets the top-ordered restaurants.                |
| `GET`  | `/restaurants/restaurants/{id}`            | Retrieves details for a specific restaurant.       |
| `PUT`  | `/restaurants/restaurants/{id}/favorite`   | Marks a restaurant as a favorite.                |
| `DELETE`| `/restaurants/restaurants/{id}/favorite` | Removes a restaurant from favorites.               |
| `POST` | `/restaurants/restaurants/{id}/orders`     | Creates a new order for a specific restaurant.     |
| `GET`  | `/orders/restaurants/{id}/orders`          | Retrieves the order history for a restaurant.      |


## ⚙️ Getting Started

To get a local copy up and running, follow these simple steps.

### Prerequisites

* Python 3.8+
* A web browser

### Backend Setup

1.  **Navigate to the backend directory:**
    ```sh
    cd backend
    ```

2.  **Create a virtual environment and activate it:**
    ```sh
    python -m venv venv
    # On Windows
    venv\Scripts\activate
    # On macOS/Linux
    source venv/bin/activate
    ```

3.  **Install the required Python packages:**
    ```sh
    pip install -r requirements.txt
    ```

4.  **Populate the database with sample data (optional but recommended):**
    Run the following scripts in order to seed the database.
    ```sh
    python scripts/populate_restaurants.py
    python scripts/populate_meals.py
    python scripts/populate_orders.py
    ```

5.  **Run the FastAPI server:**
    ```sh
    python run_server.py
    ```
    The API will be available at `http://localhost:8000`.

### Frontend Setup

The frontend is composed of static files and requires no build process. You can open the HTML files directly in your browser, but for full functionality (especially API requests), it's best to serve them. A simple way is to use a live server extension in your code editor (like VS Code's Live Server).

1.  **Open the project root in your code editor.**
2.  **Right-click on `frontend/index.html` and choose "Open with Live Server"** (or your preferred method of serving static files).

Your application should now be running and fully interactive!
