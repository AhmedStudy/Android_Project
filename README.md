1. Project Objective
The primary objective of the Student Task & Study Planner is to provide Android users—specifically students—with a lightweight, intuitive, and efficient local management tool to track academic tasks, assignments, and study schedules.
Key objectives include:
•	Persistent Local Storage: Leveraging an embedded SQLite database (SQLiteOpenHelper) to ensure data remains persistent, reliable, and accessible offline without requiring network dependency.
•	Structured UI & UX: Offering clean menu-driven and list-based interfaces to navigate seamlessly between creating, reviewing, updating, and analyzing study tasks.
•	Data-Driven Insights: Providing users with statistical breakdowns of task progress (Completed, In Progress, Not Started) to foster better time management habits.

2. Project Functionalities
The application provides end-to-end CRUD (Create, Read, Update, Delete) capabilities alongside analytical summary views:
A. Navigation & Dashboard (MainActivity)
•	Centralized Navigation Hub: Provides direct access to Add Task, View Tasks, and Statistics interfaces via styled buttons and an Options Menu (main_menu.xml).
•	About / Information: Includes an Options Menu item displaying application metadata via Android Toast.
B. Task Creation (AddTaskActivity)
•	Form Validation: Validates required input fields (e.g., ensuring title fields are non-empty before saving).
•	Attribute Management: Allows input of title, detailed description, subject title, priority selection via Spinner (Low, Medium, High), and completion status via RadioGroup (Not Started, In Progress, Completed).
•	Database Insertion: Inserts newly formed Task entities directly into the SQLite database table (TABLE_TASKS).
C. Task Management & RecyclerView (TaskListActivity & TaskAdapter)
•	Dynamic Task Listing: Displays stored tasks inside a dynamic RecyclerView using custom layouts (task_row.xml) with styled grid-like borders.
•	Interactive Menus:
o	Normal Click: Opens full task details for editing.
o	Long Click (Context Menu): Triggers an Android Context Menu allowing fast Edit and Delete actions.
o	Row Menu (Popup Menu): Triggers an overflow menu (three-dot menu) per list item to perform Edit or direct SQLite Deletion with auto-refreshing UI.
D. Task Updating & Deletion (TaskDetailsActivity)
•	Pre-populated Fields: Fetches existing task records using task_id extras passed through Android Intent and fills input controls dynamically.
•	Database Update & Delete Operations: Allows users to modify details or remove records from SQLite with feedback provided via Toast notifications.
E. Real-time Progress Tracking (StatisticsActivity)
•	Task Analytics: Dynamically queries the SQLite database to compute and display total task counts and categorizes them by status (Completed, In Progress, and Not Started).
