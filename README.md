<img width="1265" alt="image" src="https://github.com/user-attachments/assets/83916345-8670-40a8-9d62-c6618627be21">

# Travel Tracker

Travel Tracker is a web application that allows users to track the countries they have visited. The app features user management and a visual representation of visited countries on an SVG world map.

## Features

- **Track Visited Countries**: Add and view countries you have visited on a world map.
- **User Management**: Create and manage user profiles with customizable colors.
- **Data Storage**: Store user and country data in a PostgreSQL database.
- **Interactive Map**: Visualize visited countries with a color-coded SVG map.

## Technologies Used

- **Express.js**: Web framework for Node.js.
- **PostgreSQL**: Relational database for storing user and country data.
- **EJS**: Embedded JavaScript templating for rendering views.
- **Body-Parser**: Middleware for parsing incoming request bodies.

## Setup and Installation

### Prerequisites

- Node.js 
- PostgreSQL

### Getting Started

1. **Clone the Repository**

   ```bash
   git clone https://github.com/amlansahoo07/travel-tracker.git
   cd travel-tracker
   ```

2. **Install Dependencies**

   ```bash
   npm install
   ```

3. **Set Up PostgreSQL**

   - Create a PostgreSQL database named `world`.
   - Set up the required tables (`users`, `visited_countries`, `countries`) with the appropriate [schema](Schema-Template).

4. **Configure Environment**

   - Update the PostgreSQL connection details in `index.js` if needed.

5. **Start the Application**

   ```bash
   node index.js
   ```

   The application will be available at `http://localhost:3000`.

## Usage

- **Homepage** (`/`): 
  - Select an existing user or add a new one.
  - Add a new country to your visited list.
  - View the SVG map with color-coded visited countries.

- **Add Country** (`/add`): 
  - Submit a country name to add it to your visited list.

- **User Management** (`/user`): 
  - Select an existing user or navigate to the form for creating a new user.

- **Create New User** (`/new`): 
  - Fill out the form with a name and select a color to create a new user profile.

## Routes

- **GET /**: Renders the homepage with the list of visited countries and user information.
- **POST /add**: Adds a new country to the visited list.
- **POST /user**: Selects an existing user or navigates to the form for creating a new user.
- **POST /new**: Creates a new user and sets it as the current user.

## Files

- **`index.ejs`**: The homepage view with a form for user selection/addition, a form to add new countries, and an SVG map.
- **`new.ejs`**: The form for creating a new user with a selection of colors.

## Schema Template

### Users Table

```sql
CREATE TABLE users(
	id SERIAL PRIMARY KEY,
	name VARCHAR(15) UNIQUE NOT NULL,
	color VARCHAR(15)
);
```

### Countries Table

```sql
CREATE TABLE countries (
	id serial primary key,
	country_code char(2),
	country_name varchar(100)
)
```

### Visited Countries Table

```sql
CREATE TABLE visited_countries(
	id SERIAL PRIMARY KEY,
	country_code CHAR(2) NOT NULL,
	user_id INTEGER REFERENCES users(id)
);
```

## Acknowledgements

This project is inspired and developed as part of [Angela Yu's Complete Web Development Bootcamp](https://www.udemy.com/course/the-complete-web-development-bootcamp/)'s on Udemy.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
