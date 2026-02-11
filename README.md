# ITCS 6190 - Assignment 1

This project builds and runs a two-container stack using Docker and Docker Compose: one container using a PostgreSQL database, and the other hosting a Python application. The Pyton app connects to the database, queries a few rows, computes basic statistics, then prints and saves the results in a `summary.json` file in the `out` folder.

To run the project, you can either do:
`docker compose up --build`
or
`make` (to run the Makefile)

## Example Input/Output

### Input

`CREATE TABLE trips (
id SERIAL PRIMARY KEY,
city TEXT NOT NULL,
minutes INT NOT NULL,
fare NUMERIC(6,2) NOT NULL
);
INSERT INTO trips (city, minutes, fare) VALUES
('Charlotte', 12, 12.50),
('Charlotte', 21, 20.00),
('New York', 9, 10.90),
('New York', 26, 27.10),
('San Francisco', 11, 11.20),
('San Francisco', 28, 29.30);`

### Output (in `out/summary.json`)

`{
  "total_trips": 6,
  "avg_fare_by_city": [
    {
      "city": "Charlotte",
      "avg_fare": 16.25
    },
    {
      "city": "New York",
      "avg_fare": 19.0
    },
    {
      "city": "San Francisco",
      "avg_fare": 20.25
    }
  ],
  "top_by_minutes": [
    {
      "city": "San Francisco",
      "minutes": 28,
      "fare": 29.3
    },
    {
      "city": "New York",
      "minutes": 26,
      "fare": 27.1
    },
    {
      "city": "Charlotte",
      "minutes": 21,
      "fare": 20.0
    },
    {
      "city": "Charlotte",
      "minutes": 12,
      "fare": 12.5
    },
    {
      "city": "San Francisco",
      "minutes": 11,
      "fare": 11.2
    },
    {
      "city": "New York",
      "minutes": 9,
      "fare": 10.9
    }
  ]
}`

## Troubleshooting

### `Dockerfile` not found

Ensure filenames:
`db/Dockerfile`
`app/Dockerfile`

### `make` not found on Windows

Use Git Bash, WSL, or run the Docker Compose commands manually.
