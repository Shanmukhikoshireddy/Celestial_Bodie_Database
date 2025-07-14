# Celestial_Bodie_Database
This is a PostgreSQL-based relational database project designed to model a miniature universe. It includes data for galaxies, stars, planets, moons, and space missions. This project is built to fulfill the requirements of the [freeCodeCamp Relational Database Certification](https://www.freecodecamp.org/learn/relational-database/).

## 📁 Project Structure

universe/

├── universe.sql # SQL file with full schema and data (optional dump)

├── README.md # This file


---

## 📌 Features

- A normalized relational schema with 5+ interrelated tables
- Proper use of data types: `INT`, `NUMERIC`, `TEXT`, `BOOLEAN`, and `VARCHAR`
- Foreign key constraints with naming conventions
- At least:
  - 6 galaxies
  - 6 stars
  - 12 planets
  - 20 moons
- Logical relationships:
  - A **galaxy** has many **stars**
  - A **star** has many **planets**
  - A **planet** has many **moons**

---

## 🗃️ Database Schema

### `galaxy` Table
| Column         | Type     | Constraints          |
|----------------|----------|----------------------|
| galaxy_id      | SERIAL   | PRIMARY KEY          |
| name           | VARCHAR  | UNIQUE, NOT NULL     |
| type           | TEXT     | NOT NULL             |
| age_in_millions_of_years | NUMERIC |              |
| has_black_hole | BOOLEAN  | NOT NULL             |
| is_spiral      | BOOLEAN  | NOT NULL             |

---

### `star` Table
| Column         | Type     | Constraints              |
|----------------|----------|--------------------------|
| star_id        | SERIAL   | PRIMARY KEY              |
| name           | VARCHAR  | UNIQUE, NOT NULL         |
| galaxy_id      | INT      | FK → galaxy(galaxy_id)   |
| temperature    | INT      | NOT NULL                 |
| mass           | NUMERIC  |                          |
| is_main_sequence | BOOLEAN | NOT NULL                |
| has_solar_flare | BOOLEAN  | NOT NULL                |

---

### `planet` Table
| Column         | Type     | Constraints              |
|----------------|----------|--------------------------|
| planet_id      | SERIAL   | PRIMARY KEY              |
| name           | VARCHAR  | UNIQUE, NOT NULL         |
| star_id        | INT      | FK → star(star_id)       |
| distance_from_star | INT  |                          |
| has_life       | BOOLEAN  | NOT NULL                 |
| is_gas_giant   | BOOLEAN  | NOT NULL                 |
| planet_type    | TEXT     |                          |

---

### `moon` Table
| Column         | Type     | Constraints              |
|----------------|----------|--------------------------|
| moon_id        | SERIAL   | PRIMARY KEY              |
| name           | VARCHAR  | UNIQUE, NOT NULL         |
| planet_id      | INT      | FK → planet(planet_id)   |
| diameter_km    | INT      |                          |
| is_spherical   | BOOLEAN  | NOT NULL                 |
| has_atmosphere | BOOLEAN  | NOT NULL                 |
| description    | TEXT     |                          |

---

### `space_mission` Table (Bonus)
| Column            | Type     | Constraints                   |
|-------------------|----------|-------------------------------|
| space_mission_id  | SERIAL   | PRIMARY KEY                   |
| name              | VARCHAR  | UNIQUE, NOT NULL              |
| target_planet_id  | INT      | FK → planet(planet_id)        |
| mission_success   | BOOLEAN  | NOT NULL                      |
| duration_days     | INT      |                               |
| agency            | TEXT     |                               |

---

## 🧪 Sample Query


-- List all planets with life in the Milky Way galaxy

SELECT planet.name

FROM planet

JOIN star USING(star_id)

JOIN galaxy USING(galaxy_id)

WHERE has_life = true AND galaxy.name = 'Milky Way';

## 🔧 How to Run
1. Connect to PostgreSQL

``` psql --username=freecodecamp --dbname=postgres ```

2. Create and Use the Database

``` CREATE DATABASE universe; \c universe ```

3. Create Tables and Insert Data

You can run the full SQL schema (manually or from a .sql file):

```psql --username=freecodecamp --dbname=universe < universe.sql```
## ✅ Requirements Checklist
Requirement	Status

5+ tables	✅

Each table has a PK with SERIAL	✅

Foreign key relationships (galaxy → star → planet → moon)	✅

At least 6 galaxies & stars	✅

At least 12 planets, 20 moons	✅

Correct data types used: INT, NUMERIC, TEXT, BOOLEAN	✅

Each name column is VARCHAR and UNIQUE	✅

At least 2 NOT NULL columns per table	✅

Foreign key names match referenced column names	✅

## 🧠 Learning Goals
Mastery of PostgreSQL relational design

Use of constraints and normalization

Handling hierarchical relationships with foreign keys

Understanding data types and when to use them

## 📜 License
This project was created as part of the freeCodeCamp Relational Database curriculum.

## 🙋 Author
Built with ❤ by Shanmukhi

