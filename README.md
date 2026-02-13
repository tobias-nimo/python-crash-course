# Python Crash Course - Notes

Personal notes and exercises from the book [**Python Crash Course**](https://ehmatthes.github.io/pcc_3e/) by Eric Matthes.

## Structure

### Part I: Basics

Located in `basics/`, this section covers Python fundamentals:

- **Part I - Basics.ipynb** - Main notebook covering chapters 1-11
- **try_it_yourself/** - Exercise solutions:
  - [8] Functions
  - [9] Classes
  - [10] Files and Exceptions
- **python_work/** - Code examples and practice files

Topics covered:
- Variables and data types
- Lists and dictionaries
- If statements and loops
- Functions
- Classes and OOP
- Files and exceptions
- Testing code

### Part II: Projects

Located in `proyects/`, three hands-on projects:

#### 1. Alien Invasion (`alien_invasion/`)
A 2D arcade game built with Pygame. Shoot down waves of aliens before they reach the bottom of the screen.

#### 2. Data Visualization (`data_visualization/`)
Data analysis and visualization using Matplotlib and Plotly:
- Generating data (random walks, dice simulations)
- Downloading and analyzing CSV/JSON data
- Visualizing earthquakes, weather data, and GitHub API data

#### 3. Web Application (`web_application/`)
A Django web application called "Learning Log" that allows users to track topics they're learning about.

### Appendix

Located in `appendix/`:
- **version_control/** - Git basics with an example repository

## Requirements

- Python 3.x
- Pygame (for Alien Invasion)
- Matplotlib, Plotly (for Data Visualization)
- Django (for Web Application)

## Running the Projects

```bash
# Alien Invasion
cd proyects/alien_invasion
python alien_invasion.py

# Web Application
cd proyects/web_application
python manage.py runserver
```
