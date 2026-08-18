# 📚 Student Task & Study Planner

A lightweight Android application designed to help students **create, manage, track, and analyze academic tasks**. The application uses a local **SQLite database** to provide reliable offline data persistence without requiring an internet connection.

---

## 🎯 Project Objective

The primary objective of the **Student Task & Study Planner** is to provide Android users—specifically students—with a simple, intuitive, and efficient tool for managing:

* 📌 Academic tasks
* 📝 Assignments
* 📖 Study schedules
* ⏳ Task progress
* 📊 Study productivity statistics

The application focuses on **offline-first task management**, using SQLite to ensure that user data remains available even without an internet connection.

---

## ✨ Key Features

### 💾 Persistent Local Storage

* Uses an embedded **SQLite database**.
* Database management is handled using `SQLiteOpenHelper`.
* All tasks are stored locally on the device.
* No internet connection or external server is required.

### 🧭 Structured Navigation

The application provides a simple menu-driven interface that allows users to easily access:

* Add Task
* View Tasks
* Statistics
* About / Application Information

### 📊 Data-Driven Insights

The Statistics section provides a real-time breakdown of tasks based on their current status:

* ✅ Completed
* 🔄 In Progress
* ⏳ Not Started

This helps students understand their workload and monitor their progress.

---

# 🚀 Application Functionalities

## 1. 🏠 Navigation & Dashboard

### `MainActivity`

The main activity serves as the centralized navigation hub of the application.

Users can directly access:

* **Add Task**
* **View Tasks**
* **Statistics**

The activity also includes an **Options Menu** implemented using `main_menu.xml`.

### About / Information

The Options Menu includes an About/Information option that displays application metadata using an Android `Toast`.

---

## 2. ➕ Task Creation

### `AddTaskActivity`

Users can create new academic tasks through a dedicated form.

### Task Attributes

Each task can contain:

| Attribute       | Description                            |
| --------------- | -------------------------------------- |
| **Title**       | Name of the task                       |
| **Description** | Detailed information about the task    |
| **Subject**     | Related academic subject               |
| **Priority**    | Low, Medium, or High                   |
| **Status**      | Not Started, In Progress, or Completed |

### Form Validation

The application validates required fields before saving a task.

For example:

* The task title cannot be empty.
* Invalid or incomplete input is rejected before database insertion.

### Database Insertion

After successful validation, the task is inserted directly into the SQLite database using the `TABLE_TASKS` table.

---

## 3. 📋 Task Management

### `TaskListActivity`

All stored tasks are displayed dynamically using an Android `RecyclerView`.

Each task is displayed using the custom:

```text
task_row.xml
```

layout.

The task rows use styled borders and a grid-like structure to make the information easy to read.

### Task Interaction

The application supports multiple ways of interacting with tasks.

#### 🖱️ Normal Click

Clicking a task opens its complete details and allows the user to edit the task.

#### 🖱️ Long Click

Long-clicking a task opens an Android **Context Menu** containing options such as:

* Edit
* Delete

#### ⋮ Popup Menu

Each task row also contains a three-dot **Popup Menu**.

The Popup Menu allows the user to:

* ✏️ Edit the task
* 🗑️ Delete the task

After deletion, the RecyclerView is automatically refreshed to reflect the updated database contents.

---

## 4. ✏️ Task Updating & Deletion

### `TaskDetailsActivity`

This activity handles viewing and modifying existing tasks.

### Pre-Populated Fields

When a user selects a task, its `task_id` is passed through an Android `Intent`.

The application then retrieves the corresponding record from SQLite and dynamically fills the input fields.

This allows the user to view and modify the existing task information.

### Update

Users can modify:

* Title
* Description
* Subject
* Priority
* Status

The updated information is then saved back into the SQLite database.

### Delete

Users can permanently remove a task from the database.

The application provides feedback through Android `Toast` notifications after successful update or deletion operations.

---

## 5. 📊 Statistics & Progress Tracking

### `StatisticsActivity`

The Statistics activity provides a real-time overview of the user's tasks.

The application queries the SQLite database and calculates:

* **Total Tasks**
* **Completed Tasks**
* **In Progress Tasks**
* **Not Started Tasks**

Example:

```text
Total Tasks: 20

Completed:    8
In Progress:  7
Not Started:  5
```

These statistics allow students to quickly evaluate their current workload and progress.

---

# 🗄️ Database

The application uses **SQLite** for local data storage.

Database operations are handled using:

```text
SQLiteOpenHelper
```

The main task table is:

```text
TABLE_TASKS
```

The database is responsible for supporting the application's complete CRUD functionality:

| Operation  | Function                   |
| ---------- | -------------------------- |
| **Create** | Add new tasks              |
| **Read**   | Display and retrieve tasks |
| **Update** | Modify existing tasks      |
| **Delete** | Remove tasks               |

---

# 🔄 CRUD Workflow

The overall task-management workflow can be summarized as:

```text
              ┌───────────────┐
              │   MainActivity│
              └───────┬───────┘
                      │
        ┌─────────────┼─────────────┐
        ▼             ▼             ▼
   Add Task       View Tasks     Statistics
        │             │
        ▼             ▼
 AddTaskActivity  TaskListActivity
        │             │
        ▼             ├──────────────┐
     INSERT           │              │
                      ▼              ▼
                TaskDetailsActivity
                      │
                ┌─────┴─────┐
                ▼           ▼
              UPDATE      DELETE
                │           │
                └─────┬─────┘
                      ▼
                 SQLite DB
```

---

# 🧩 Main Application Components

| Component             | Responsibility                             |
| --------------------- | ------------------------------------------ |
| `MainActivity`        | Main dashboard and navigation              |
| `AddTaskActivity`     | Creating new tasks                         |
| `TaskListActivity`    | Displaying all tasks                       |
| `TaskDetailsActivity` | Viewing, updating, and deleting tasks      |
| `StatisticsActivity`  | Calculating and displaying task statistics |
| `TaskAdapter`         | Connecting task data to the RecyclerView   |
| `SQLiteOpenHelper`    | Managing the local SQLite database         |
|                       |                                            |

---

# 🛠️ Technologies Used

* **Android**
* **Java**
* **SQLite**
* **SQLiteOpenHelper**
* **RecyclerView**
* **Android Intents**
* **Options Menu**
* **Context Menu**
* **Popup Menu**
* **Toast Notifications**
* **XML Layouts**

---

# 📱 Application Design

The application follows a simple and lightweight design philosophy:

* 🎯 Easy navigation
* 📋 Clear task organization
* 💾 Offline data persistence
* ⚡ Fast local database operations
* 📊 Simple progress analysis
* 📱 Android-native UI components

---

# 🔐 Offline-First Approach

One of the main characteristics of the application is that it does **not depend on an external backend or internet connection**.

All task operations are performed locally:

```text
User
  │
  ▼
Android UI
  │
  ▼
Application Logic
  │
  ▼
SQLite Database
  │
  ▼
Local Device Storage
```

This makes the application suitable for students who need access to their tasks regardless of network availability.

---

# 📌 Future Improvements

Potential future improvements could include:

* 🔔 Task reminders and notifications
* 📅 Calendar-based task scheduling
* 🔍 Search and filtering
* 🏷️ Task categories
* 📈 More detailed statistics
* 🌙 Dark mode
* ☁️ Cloud synchronization
* 🔐 User authentication
* 📤 Data export and backup

---

# 👨‍💻 Project Summary

The **Student Task & Study Planner** demonstrates the implementation of a complete Android task-management application with:

* **CRUD database operations**
* **SQLite local persistence**
* **RecyclerView-based dynamic lists**
* **Multiple Android menu types**
* **Form validation**
* **Intent-based navigation**
* **Real-time task statistics**

The project combines Android UI components with local database management to provide students with a practical and efficient academic planning tool.
