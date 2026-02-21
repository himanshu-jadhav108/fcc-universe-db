# 🌌 Universe Database — PostgreSQL Project

A relational database that models a simplified universe consisting of galaxies, stars, planets, moons, and comets.

This project was built as part of the **freeCodeCamp Relational Database Certification** and demonstrates schema design, relationships, constraints, and data insertion using PostgreSQL.

---

## 🚀 Features

* Fully normalized relational schema
* Primary & foreign key relationships
* Auto-incrementing IDs using `SERIAL`
* Multiple data types used: `INT`, `NUMERIC`, `TEXT`, `BOOLEAN`, `VARCHAR`
* Unique and NOT NULL constraints
* Realistic sample space data

---

## 🗂️ Database Schema

### Tables

* **galaxy** → stores galaxy information
* **star** → belongs to a galaxy
* **planet** → belongs to a star
* **moon** → belongs to a planet
* **comet** → independent celestial objects

### Relationship Flow

```
Galaxy → Star → Planet → Moon
```

This enforces hierarchical space structure using foreign keys.

---

## 🧱 Example Columns

| Table  | Key Fields                                               |
| ------ | -------------------------------------------------------- |
| galaxy | name, description, galaxy_type, age_in_millions_of_years |
| star   | temperature, mass, galaxy_id                             |
| planet | planet_type, has_life, distance_from_star                |
| moon   | is_spherical, age_in_millions_of_years                   |
| comet  | speed, is_periodic                                       |

---

## 📊 Constraints Implemented

* Primary keys on all tables
* Foreign keys enforcing relationships
* Unique `name` column in every table
* Multiple NOT NULL columns per table
* Required data types per project rules

---

## 🧪 Sample Data

The database includes:

* 6 galaxies
* 6 stars
* 12 planets
* 20 moons
* 3 comets

This enables meaningful querying and analysis.

---

## ⚙️ Setup Instructions

### 1. Open PostgreSQL

```
psql --username=freecodecamp --dbname=postgres
```

### 2. Restore Database

```
psql -U postgres < universe.sql
```

This recreates the full database with schema and data.

---

## 🔎 Example Queries

```sql
-- Planets that may support life
SELECT name FROM planet WHERE has_life = true;

-- Moons of Jupiter
SELECT m.name
FROM moon m
JOIN planet p ON m.planet_id = p.planet_id
WHERE p.name = 'Jupiter';

-- Stars per galaxy
SELECT g.name, COUNT(s.star_id)
FROM galaxy g
LEFT JOIN star s ON g.galaxy_id = s.galaxy_id
GROUP BY g.name;
```

---

## 🎯 Learning Outcomes

* Designing relational schemas
* Implementing hierarchical foreign keys
* Writing SQL DDL & DML
* Data integrity using constraints
* Database export using `pg_dump`

---

## 📌 Future Improvements

* Add asteroid and satellite tables
* Build analytics queries
* Create API layer
* Visualize schema with ER diagram
* Build dashboard using Streamlit

---

## 👨‍💻 Author

Built by Himanshu as part of learning backend data engineering and database design.
