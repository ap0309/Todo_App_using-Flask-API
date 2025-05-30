# Flask Todo App

A simple web-based todo list application built with Flask and SQLAlchemy, using MySQL as the backend database.

## Features

- **Add new tasks:** Enter a task and it gets added to your list.
- **View all tasks:** Tasks are displayed in order of creation.
- **Delete tasks:** Remove tasks you no longer need.
- **Update tasks:** Edit the content of existing tasks.

## Prerequisites

- **Python 3.x**
- **Flask**
- **Flask-SQLAlchemy**
- **MySQL database**
- **pymysql** (MySQL Python connector)

## Installation

1. **Clone the repository:**
git clone https://github.com/yourusername/flask-todo-app.git
cd flask-todo-app

text

2. **Install dependencies:**
pip install flask flask_sqlalchemy pymysql

text

3. **Setup your MySQL database:**
- Ensure MySQL is running.
- Create a database named `test` (or update the `SQLALCHEMY_DATABASE_URI` in the code).
- Update the user and password in the code if necessary.

4. **Initialize the database:**
- Open a Python shell in your project directory.
- Run:
  ```
  from app import app, db
  with app.app_context():
      db.create_all()
  ```
- (If you use a different script name, replace `app` accordingly.)

5. **Run the application:**
python app.py

text
(Replace `app.py` with your main script filename if different.)

## Usage

- **Homepage:** Visit `http://127.0.0.1:5000/` in your browser.
- **Add Task:** Use the form to add a new task.
- **Delete Task:** Click the delete button next to a task.
- **Update Task:** Click the update button, edit the task, and submit.

## Project Structure

project/
├── app.py
├── README.md
└── templates/
├── index.html
└── update.html

text

## Example Templates (Optional)

**index.html**
<h1>Todo List</h1> <form action="/" method="POST"> <input type="text" name="content" placeholder="Add a new task" required> <input type="submit" value="Add Task"> </form> <ul> {% for task in tasks %} <li> {{ task.content }} ({{ task.date_created.strftime('%Y-%m-%d %H:%M') }}) <a href="/update/{{ task.id }}">Update</a> <a href="/delete/{{ task.id }}">Delete</a> </li> {% endfor %} </ul> ```
update.html

text
<h1>Update Task</h1>
<form action="/update/{{ tasks.id }}" method="POST">
    <input type="text" name="content" value="{{ tasks.content }}" required>
    <input type="submit" value="Update Task">
</form>