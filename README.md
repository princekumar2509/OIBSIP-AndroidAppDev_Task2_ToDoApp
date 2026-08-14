# 📝 ToDo App

A simple and user-friendly **Android ToDo application** developed using **Java and Android Studio**. The application allows users to register and log in, create tasks, edit existing tasks, delete tasks, and mark tasks as completed.

The app uses **SQLite Database** for local data storage and provides a clean Material Design interface.

---

## 📱 Project Overview

**ToDo App** is designed to help users manage their daily tasks efficiently.

Each registered user has their own tasks, which are stored locally in an SQLite database. Users can add task names and notes, update existing tasks, mark tasks as completed, and delete tasks when they are no longer needed.

---

## ✨ Features

- 🔐 User Registration
- 🔑 User Login
- 🚪 Logout
- 📝 Add New Tasks
- ✏️ Edit/Update Tasks
- 🗑️ Delete Tasks
- ✅ Mark Tasks as Completed
- ❌ Unmark Completed Tasks
- 📋 Task Notes
- 👤 User-specific Tasks
- 💾 Local SQLite Database
- 🔄 Automatic Task Refresh
- 📭 Empty Task State
- 🎨 Material Design UI
- 🌙 Dark Mode Support
- 📱 Android APK Generation

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Java | Application programming |
| Android Studio | Development environment |
| XML | UI design |
| SQLite | Local database |
| RecyclerView | Displaying tasks |
| Material Components | UI components |
| SharedPreferences | Session management |
| Gradle | Build system |

---

## 🏗️ Project Structure

```text
ToDoApp
│
├── app
│   │
│   ├── src
│   │   └── main
│   │       │
│   │       ├── java
│   │       │   └── com.example.todoapp
│   │       │       │
│   │       │       ├── adapter
│   │       │       │   └── TaskAdapter.java
│   │       │       │
│   │       │       ├── database
│   │       │       │   └── DBHelper.java
│   │       │       │
│   │       │       ├── model
│   │       │       │   └── Task.java
│   │       │       │
│   │       │       ├── utils
│   │       │       │   └── SessionManager.java
│   │       │       │
│   │       │       ├── AddTasksActivity.java
│   │       │       ├── LoginActivity.java
│   │       │       ├── MainActivity.java
│   │       │       └── RegisterActivity.java
│   │       │
│   │       └── res
│   │           │
│   │           ├── drawable
│   │           ├── layout
│   │           ├── mipmap
│   │           └── values
│   │
│   └── AndroidManifest.xml
│
└── README.md
```

---

## 🔐 Authentication

The application provides a basic authentication system.

### Registration

A new user can provide:

- Name
- Email
- Password

The information is stored in the SQLite `users` table.

### Login

Users log in using their registered:

- Email
- Password

After successful login, the user is redirected to the main task screen.

### Logout

The logout button clears the current session and allows the user to log in again.

---

## 🗄️ Database

The application uses an SQLite database named:

```text
TodoApp.db
```

### Users Table

```text
users
```

Columns:

```text
id
name
email
password
```

### Tasks Table

```text
tasks
```

Columns:

```text
id
user_id
task_name
notes
completed
```

The `user_id` connects each task with its corresponding user.

---

## 📝 Task Management

### Add Task

Users can enter:

```text
Task Name
Task Notes
```

and press the **Save Task** button.

The task is stored in the SQLite database.

---

### Edit Task

Users can tap an existing task to open it in edit mode.

The application loads the existing:

- Task name
- Task notes

The button changes to:

```text
Update Task
```

After editing, the updated information is stored in SQLite.

---

### Complete Task

Each task contains a checkbox.

When the checkbox is selected:

```text
Task → Completed
```

The task is visually displayed with a strike-through effect.

The completion status is also stored in the database.

---

### Delete Task

The delete button removes the selected task from:

1. SQLite database
2. RecyclerView

---

## 🔄 RecyclerView

`TaskAdapter.java` is responsible for displaying tasks.

It handles:

- Task name
- Task notes
- Completion checkbox
- Delete button
- Edit click
- Strike-through completed tasks

Example:

```java
holder.txtTask.setText(task.getName());
holder.txtNotes.setText(task.getNotes());
holder.checkTask.setChecked(task.isCompleted());
```

---

## 🎨 User Interface

The application uses Android Material Components for a modern interface.

The UI contains:

- Purple application header
- Task cards
- Floating Action Button
- Checkboxes
- Delete icons
- Add/Edit task screen
- Login screen
- Registration screen

The application also supports **Light and Dark themes** using Android's `DayNight` theme system.

---

## 🌙 Dark Mode

The application uses:

```xml
Theme.Material3.DayNight.NoActionBar
```

This allows the application to respond to the device's system light/dark theme.

Dark mode uses:

```text
Dark background
Dark task cards
White primary text
Light secondary text
Purple accent
```

---

## ⚙️ Important Classes

### `MainActivity.java`

Responsible for:

- Displaying tasks
- Loading tasks from database
- RecyclerView initialization
- Add task button
- Logout
- Empty task message

---

### `AddTasksActivity.java`

Responsible for:

- Adding tasks
- Editing tasks
- Validating task names
- Saving task information
- Updating existing tasks

The activity determines whether it is in:

```java
isEditMode
```

When editing, the existing task ID is used to update the database.

---

### `DBHelper.java`

Responsible for all SQLite database operations.

Main methods include:

```java
registerUser()
loginUser()
getUserId()
addTask()
getTasks()
updateTaskStatus()
updateTask()
deleteTask()
```

---

### `TaskAdapter.java`

Responsible for displaying and interacting with individual task cards.

It handles:

```text
Checkbox
Task title
Task notes
Delete
Edit
Completed state
```

---

### `SessionManager.java`

Responsible for maintaining the logged-in user's session using local preferences.

---

## 🐛 Error Handling

During development, an SQLite database error occurred because the update method used:

```text
task_notes
```

while the actual database column was:

```text
notes
```

The update method was corrected to use the same column name defined in the database schema.

The final implementation uses:

```java
values.put(TASK_NAME, taskName);
values.put(TASK_NOTES, taskNotes);
```

This keeps the database column names consistent.

---

## 🚀 How to Run the Project

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/ToDoApp.git
```

### 2. Open in Android Studio

Open Android Studio and select:

```text
Open
```

Then select the project folder.

### 3. Sync Gradle

Allow Android Studio to download and synchronize the required dependencies.

### 4. Connect Android Device

Enable:

```text
Developer Options
USB Debugging
```

on your Android phone.

Or use an Android Emulator.

### 5. Run

Click the green:

```text
▶ Run
```

button in Android Studio.

---

## 📦 Generate APK

To generate a debug APK:

```text
Build
→ Build Bundle(s) / APK(s)
→ Build APK(s)
```

The APK can usually be found at:

```text
app/build/outputs/apk/debug/app-debug.apk
```

For a release APK:

```text
Build
→ Generate Signed Bundle / APK
→ APK
```

Then select the `release` build variant and create/use a signing key.

---

## 🔒 Security Note

This project is intended primarily for learning and demonstration purposes.

For a production application, passwords should **not** be stored as plain text. Password hashing and stronger authentication mechanisms should be implemented.

---

## 🔮 Future Improvements

Possible future features include:

- 🔔 Task reminders and notifications
- 📅 Due dates
- 🏷️ Task categories
- ⭐ Task priorities
- 🔎 Search tasks
- ↕️ Task sorting
- ↩️ Undo delete
- 📊 Task statistics
- ☁️ Cloud synchronization
- 👤 Profile management
- 🔒 Secure password hashing
- 🔐 Biometric authentication
- 📤 Export and import tasks

---

## 🎯 Learning Outcomes

Through this project, the following Android development concepts were practiced:

- Android Activity lifecycle
- XML UI design
- Java programming
- SQLite database management
- CRUD operations
- RecyclerView
- Adapter implementation
- Intent and Activity navigation
- SharedPreferences
- Session management
- Material Design
- Dark/Light themes
- Debugging Android applications
- APK generation

---

## 📸 Application Screens

Add screenshots of your application here:

```text
screenshots/
├── login.png
├── register.png
├── home.png
├── add_task.png
├── edit_task.png
└── dark_mode.png
```

Example Markdown:

```markdown
![Login Screen](screenshots/login.png)

![Home Screen](screenshots/home.png)

![Dark Mode](screenshots/dark_mode.png)
```

---

## 👨‍💻 Developer

**Prince Kumar**

Computer Science Student

---

## 📄 License

This project is created for educational and academic purposes.

You are free to modify and improve the project for learning purposes.

---

## ⭐ Acknowledgement

This project was developed as an Android application to practice mobile application development, database management, UI design, and CRUD functionality.

If you find this project useful, consider giving the repository a ⭐ on GitHub.