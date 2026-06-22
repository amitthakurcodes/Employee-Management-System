

# Employee Management System — ASP.NET Core MVC

A complete, production-style **ASP.NET Core MVC** application built with **.NET 8**, showcasing **Master-Details CRUD operations** in an **Employee Management System** with a premium, fully responsive UI.

This project demonstrates real-world employee record management — including attendance tracking, salary aggregates, and grouped data analysis — built using ASP.NET MVC architecture (NOT Web API), Entity Framework Core, and SQL Server Stored Procedures.

---

## 📚 Features

- ASP.NET Core 8 MVC Framework
- Entity Framework Core 8 (Code-First with Migrations)
- SQL Server / LocalDB support
- Master-Details Form Handling (Employee + Attendance)
- Full CRUD Operations with Server-side & Client-side Validation
- Strongly Typed Views & ViewModels (separate Input/Edit models)
- **Stored Procedures** for Insert/Delete operations, executed via EF Core migrations
- Employee Profile Picture Upload
- Salary Aggregates Dashboard (Count, Max, Min, Average, Total)
- Grouped Data Analysis (by Gender / Joining Year-Month)
- Fully Responsive, Premium UI with custom design system (gradient hero, stat cards, badges)
- Collapsible attendance history per employee

---

## 📦 Technologies Used

| Category            | Technology                                                  |
|----------------------|--------------------------------------------------------------|
| Framework            | [.NET 8 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/8.0), ASP.NET Core MVC |
| ORM                  | Entity Framework Core 8.0.8                                  |
| Database             | SQL Server / LocalDB (SQL Server Express)                    |
| Database Logic       | Stored Procedures (`InsertAttendance`, `DeleteAttendanceOfEmployee`, `DeleteEmployee`) executed via `ExecuteSqlInterpolated` |
| Views                | Razor Views, Strongly Typed ViewModels                       |
| Frontend Styling     | Bootstrap 5, Bootstrap Icons, Custom CSS (premium design system) |
| Client-side Scripting| jQuery, jQuery Validation, jQuery Unobtrusive Validation      |
| File Handling        | Local file storage for employee profile pictures (`wwwroot/Pictures`) |
| Tooling              | Microsoft.VisualStudio.Web.CodeGeneration.Design (Scaffolding) |

---

## 🚀 Getting Started

### ✅ Prerequisites

- [.NET 8 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)
- Visual Studio 2022
- SQL Server / LocalDB / SQL Server Express
- SQL Server Management Studio (SSMS) — recommended for database inspection

### 🔧 Installation

1. **Clone this repository**
   ```bash
   git clone https://github.com/amitthakurcodes/Employee-Management-System.git
   cd Employee-Management-System
   ```

2. **Update your DB connection**
   - Open `EmployeeManagement/appsettings.json`
   - Edit the `ConnectionStrings` section with your own SQL Server / LocalDB instance:
     ```json
     "ConnectionStrings": {
       "db": "Server=.\\SQLEXPRESS;Database=EMP_1;Trusted_Connection=True;TrustServerCertificate=True;"
     }
     ```

3. **Apply EF Migrations & Create the Database**
   ```bash
   dotnet ef database update
   ```
   This will also create the required stored procedures (`InsertAttendance`, `DeleteAttendanceOfEmployee`, `DeleteEmployee`) as part of the migration.

4. **Run the application**
   ```bash
   dotnet run
   ```

5. Open your browser and navigate to the URL shown in the console (usually `https://localhost:xxxx`).

---

## 📂 Project Structure

```
📦 EmployeeManagement
 ┣ 📁 Controllers          → MVC Controllers (EmployeesController, HomeController)
 ┣ 📁 Models               → Entity models (Employee, Attendance, Gender enum)
 ┣ 📁 ViewModels           → Input/Edit DTOs (EmployeeInputModel, EmployeeEditModel, GroupData)
 ┣ 📁 Migrations           → EF Core migrations, including Stored Procedure creation scripts
 ┣ 📁 Views
 ┃ ┣ 📁 Employees          → Index, Create, Edit, Aggregates, Grouping, GroupingResult
 ┃ ┣ 📁 Home               → Dashboard / Landing page
 ┃ ┗ 📁 Shared             → _Layout.cshtml and shared partials
 ┣ 📁 wwwroot
 ┃ ┣ 📁 css                → site.css (custom premium UI styling)
 ┃ ┣ 📁 js                 → site.js
 ┃ ┣ 📁 lib                → Bootstrap, jQuery, jQuery Validation
 ┃ ┗ 📁 Pictures           → Uploaded employee profile pictures
 ┣ 📜 Program.cs           → Application entry point & service configuration
 ┣ 📜 appsettings.json     → Database connection configuration
 ┗ 📜 EmployeeManagement.csproj
```

---

## 🧩 Core Modules

### 👥 Employees
Create, view, update, and delete employee records — each with profile picture, gender, joining date, salary, and active status. Supports nested attendance entries per employee.

### 📊 Aggregates
A statistics dashboard showing total employee count, maximum/minimum/average/total salary — computed using LINQ aggregate functions over the employee dataset.

### 🧩 Grouping
Groups employee data either by **Gender** or by **Joining Year/Month**, helping visualize workforce composition and hiring trends.

### 🕒 Attendance
Each employee can have multiple attendance records (date, in-time, out-time), managed through dynamic Master-Details form rows and backed by stored procedures.

---

## 🧪 Validation

- **Server-side validation** via Data Annotations (`[Required]`, etc.) on ViewModels
- **Client-side validation** via jQuery Validation + jQuery Unobtrusive Validation, integrated with Bootstrap form feedback

---

## 📸 Screenshots

### 🏠 Homepage
<img width="1900" height="910" alt="Screenshot 2026-06-22 130034" src="https://github.com/user-attachments/assets/fc0b9ef4-9a54-4489-9e33-46cc434641e0" />

A premium, gradient-themed landing page that gives users quick access to all core modules — Employees, Aggregates, Grouping, and Attendance — through clean, icon-based navigation cards.

---

### 👥 Employee List
<img width="1891" height="911" alt="Screenshot 2026-06-22 130250" src="https://github.com/user-attachments/assets/0c24c093-96f6-447d-9d6f-200cec07fd04" />

Displays all employee records in a modern card layout. Each card shows the employee's profile picture, name, gender badge, joining date, salary, and active status, along with an expandable section to view their attendance history. Includes quick Edit and Delete actions.

---

### ➕ Create Employee
<img width="1042" height="833" alt="Screenshot 2026-06-22 130358" src="https://github.com/user-attachments/assets/fe9c3620-db35-4f18-a32c-dd5a24d25585" />

A clean form for adding new employees, including fields for name, gender, joining date, salary, and profile picture upload. Supports dynamically adding or removing multiple attendance entries directly within the form.

---

### 📊 Aggregates
<img width="1901" height="653" alt="Screenshot 2026-06-22 130427" src="https://github.com/user-attachments/assets/7d23698f-d2a1-4521-9602-b3ffd89a3b50" />

A statistics dashboard presenting key salary insights at a glance — total employee count, maximum salary, minimum salary, average salary, and total salary — displayed as colorful, easy-to-read summary cards.

---

### 🧩 Grouping
<img width="1900" height="628" alt="Screenshot 2026-06-22 130459" src="https://github.com/user-attachments/assets/db93d62c-7ddd-432c-92c6-b4caac71e485" />

Allows users to choose how employee data should be grouped — either by **Gender** or by **Joining Year/Month** — through simple, icon-based selection cards.

---

### 🧍 Grouping Result — By Gender
<img width="1892" height="782" alt="Screenshot 2026-06-22 130528" src="https://github.com/user-attachments/assets/ceba19b6-44a7-4963-9891-b9b0b333b682" />

Shows employees organized into groups based on gender, with each group displaying the employee's name, gender, and salary in a structured, easy-to-scan table.

---

### 📅 Grouping Result — By Joining Date
<img width="1901" height="778" alt="Screenshot 2026-06-22 130558" src="https://github.com/user-attachments/assets/add8f184-2bda-426f-bafd-8b80ba43aeef" />

Groups employees by their joining year and month, making it easy to visualize hiring trends and onboarding patterns over time.

---

## 📄 License

This project is licensed under the MIT License.

---

## 👨‍💻 Author

Built by **Amit Thakur**
[GitHub](https://github.com/amitthakurcodes)
