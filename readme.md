<div align="center">

# 🆘 Disaster Relief Supply Distribution System

### A structured desktop solution for coordinating disaster relief operations — manage affected families, track inventory, and generate operational reports with ease.

<br/>

![Java](https://img.shields.io/badge/Java-8%2B-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Swing](https://img.shields.io/badge/GUI-Java%20Swing-4A90D9?style=for-the-badge&logo=java&logoColor=white)
![MySQL](https://img.shields.io/badge/Database-MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![JDBC](https://img.shields.io/badge/Connectivity-JDBC-00758F?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Stable-brightgreen?style=for-the-badge)
![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey?style=for-the-badge)

<br/>

[Features](#-key-features) • [Architecture](#-system-architecture) • [Tech Stack](#-technology-stack) • [Installation](#-installation) • [Usage](#-running-the-application) • [Modules](#-application-modules) • [Contributing](#-contributing) • [License](#-license)

</div>

---

## 📌 Overview

When disasters strike, coordinated response saves lives. The **Disaster Relief Supply Distribution System** is a lightweight, desktop-based Java application built to help relief organizations take control of their operations quickly and efficiently.

This system provides a centralized platform to:
- Register and manage **disaster-affected families**
- Track and restock **relief inventory** in real time
- Generate **operational reports** for better decision-making
- Restrict access to **authorized personnel** only

Built with **Java Swing** for a responsive desktop UI and **MySQL** for reliable persistent data storage, this tool is designed for fast deployment in resource-constrained environments where simplicity and reliability matter most.

---

## ✨ Key Features

| Feature | Description |
|---|---|
| 🔐 **User Authentication** | Secure login interface to restrict system access to authorized users |
| 👨‍👩‍👧 **Family Registration** | Register, view, and manage disaster-affected households |
| 📦 **Inventory Management** | Track all available relief supplies with real-time quantity monitoring |
| 🔄 **Restocking Module** | Add new stock or replenish existing supplies with ease |
| 📊 **Inventory Dashboard** | Monitor stock levels and identify shortages at a glance |
| 📋 **Report Generation** | Generate data-driven reports for families and inventory records |
| 🗄️ **MySQL Integration** | Reliable relational database backend for persistent data storage |
| 🖥️ **Desktop Deployment** | Minimal setup — runs on any machine with Java installed |

---

## 🏗️ System Architecture

The application follows a clean, **4-layer architecture** that ensures modularity, maintainability, and ease of future extension:

```
┌─────────────────────────────────────────────┐
│          PRESENTATION LAYER                  │
│       Java Swing UI Components               │
│  LoginUI · MainUI · InventoryUI · ReportUI  │
└──────────────────┬──────────────────────────┘
                   │
┌──────────────────▼──────────────────────────┐
│         BUSINESS LOGIC LAYER                 │
│    Inventory & Operational Management        │
│       InventoryManager · Validators          │
└──────────────────┬──────────────────────────┘
                   │
┌──────────────────▼──────────────────────────┐
│          DATA ACCESS LAYER                   │
│       JDBC-Based DB Connectivity             │
│              DBConnection.java               │
└──────────────────┬──────────────────────────┘
                   │
┌──────────────────▼──────────────────────────┐
│           DATABASE LAYER                     │
│        MySQL Relational Database             │
│            disaster_relief DB                │
└─────────────────────────────────────────────┘
```

This separation of concerns ensures that UI changes don't affect business logic, and database migrations remain isolated from application code.

---

## 🛠️ Technology Stack

| Component | Technology | Purpose |
|---|---|---|
| **Programming Language** | Java 8+ | Core application logic |
| **GUI Framework** | Java Swing | Desktop user interface |
| **Database** | MySQL | Persistent data storage |
| **DB Connectivity** | JDBC | Java-to-database bridge |
| **MySQL Driver** | mysql-connector-j 9.2.0 | MySQL JDBC driver |
| **Table Rendering** | rs2xml | Populating Swing JTables from ResultSets |

---

## 📁 Project Structure

```
DISASTER-MANAGEMENT-SYS/
│
├── 📂 database/
│   └── sqlcode.sql                  # Full DB schema & seed data
│
├── 📂 disasterrelief/
│   ├── 📂 database/
│   │   ├── DBConnection.java        # Manages JDBC connection
│   │   └── InventoryManager.java    # Core inventory business logic
│   │
│   ├── 📂 models/
│   │   ├── Family.java              # Family data model
│   │   └── InventoryItem.java       # Relief item data model
│   │
│   └── 📂 views/
│       ├── LoginUI.java             # Authentication screen
│       ├── MainUI.java              # Main dashboard/navigation
│       ├── InventoryUI.java         # Inventory overview
│       ├── ManageFamiliesUI.java    # Family management panel
│       ├── RegisterFamilyUI.java    # New family registration form
│       ├── RestockUI.java           # Supply restocking panel
│       ├── ViewInventoryUI.java     # Inventory detail view
│       └── ReportUI.java            # Report generation panel
│
├── 📂 icon/
│   └── login.png                    # Application icon assets
│
├── 📂 lib/
│   ├── mysql-connector-j-9.2.0.jar  # MySQL JDBC driver
│   └── rs2xml.jar                   # ResultSet-to-XML table utility
│
├── .gitignore
├── LICENSE
└── README.md
```

---

## ⚙️ Installation

### Prerequisites

Make sure the following are installed on your system:

- ✅ **Java JDK 8 or later** — [Download here](https://www.oracle.com/java/technologies/downloads/)
- ✅ **MySQL Server 5.7+** — [Download here](https://dev.mysql.com/downloads/mysql/)
- ✅ **Git** — [Download here](https://git-scm.com/)

### Step 1 — Clone the Repository

```bash
git clone https://github.com/smaharx/disaster-management-system.git
cd disaster-management-system
```

### Step 2 — Database Setup

Start your MySQL server, then create the database:

```sql
CREATE DATABASE disaster_relief;
```

Import the schema and seed data:

```bash
mysql -u root -p disaster_relief < database/sqlcode.sql
```

### Step 3 — Configure the Database Connection

Open the file `disasterrelief/database/DBConnection.java` and update the following constants with your MySQL credentials:

```java
private static final String URL      = "jdbc:mysql://localhost:3306/disaster_relief";
private static final String USERNAME = "your_mysql_username";
private static final String PASSWORD = "your_mysql_password";
```

> ⚠️ **Security Note:** Never commit real credentials to version control. Use environment variables or a `.env` config file for production deployments.

---

## ▶️ Running the Application

### Compile the Source

```bash
javac -cp "lib/*" -d out $(find . -name "*.java")
```

> **Windows users** — replace `$(find . -name "*.java")` with a manual file list or use an IDE like IntelliJ IDEA or Eclipse.

### Launch the Application

```bash
# Linux / macOS
java -cp "out:lib/*" disasterrelief.views.MainUI

# Windows
java -cp "out;lib/*" disasterrelief.views.MainUI
```

> 💡 **Tip:** For the smoothest experience, consider importing the project into **IntelliJ IDEA** or **Eclipse** and running it directly from the IDE with the `/lib` JARs added to the build path.

---

## 🖥️ Application Modules

### 🔐 Login Module
Handles secure authentication of system users. Only authorized personnel can access the system, ensuring that sensitive relief data is protected.

### 👨‍👩‍👧 Family Management
Register and manage disaster-affected households. Captures key details like family ID, head of household, address, contact information, and household size.

### 📦 Inventory Management
Real-time tracking of all available relief resources. View quantities, filter by item type, and quickly identify what's running low.

### 🔄 Restocking Module
Allows administrators to add new inventory items or top up quantities of existing supplies to meet ongoing demand.

### 📊 Inventory Dashboard
A monitoring panel that provides an at-a-glance view of current stock levels across all relief categories.

### 📋 Report Generation
Generates structured reports for both family records and inventory data — essential for coordination between field teams and headquarters.

---

## 🗃️ Data Models

### `Family`
Represents a disaster-affected household registered in the system.

| Field | Type | Description |
|---|---|---|
| `familyId` | INT | Unique household identifier |
| `headOfFamily` | VARCHAR | Name of the registered head |
| `address` | VARCHAR | Current location/address |
| `contactInfo` | VARCHAR | Phone or contact details |
| `householdSize` | INT | Total number of members |

### `InventoryItem`
Represents a relief supply item tracked in the system.

| Field | Type | Description |
|---|---|---|
| `itemId` | INT | Unique item identifier |
| `itemName` | VARCHAR | Name of the relief item |
| `description` | VARCHAR | Details about the item |
| `quantity` | INT | Current stock count |

---

## 📦 Dependencies

All required libraries are bundled in the `/lib` directory — no additional package manager is needed.

| Library | Version | Purpose |
|---|---|---|
| `mysql-connector-j` | 9.2.0 | MySQL JDBC connectivity driver |
| `rs2xml` | Latest | Converts JDBC ResultSets into Swing JTable models |

---

## 🔒 Security Considerations

- **Never hardcode credentials** — use environment variables or a config file excluded from version control for any production deployment.
- **Use parameterized queries** — all database interactions should use `PreparedStatement` to prevent SQL injection attacks.
- **Restrict DB user permissions** — create a dedicated MySQL user with only the permissions needed by this application (`SELECT`, `INSERT`, `UPDATE`, `DELETE` on `disaster_relief` only).

---

## 🐛 Troubleshooting

| Problem | Likely Cause | Fix |
|---|---|---|
| `Connection refused` | MySQL not running | Start MySQL service |
| `Access denied for user` | Wrong credentials | Update `DBConnection.java` |
| `ClassNotFoundException: com.mysql.cj.jdbc.Driver` | JAR missing from classpath | Ensure `lib/` is in `-cp` |
| `Table doesn't exist` | Schema not imported | Re-run `sqlcode.sql` import |
| Blank JTable on load | `rs2xml.jar` missing | Add `rs2xml.jar` to classpath |

---

## 🚀 Future Improvements

The following features are planned or proposed for future development:

- [ ] 🌐 Web-based interface (Spring Boot + React)
- [ ] ☁️ Cloud database integration (AWS RDS / Firebase)
- [ ] 🔑 Role-based access control (Admin, Operator, Viewer)
- [ ] 📝 Audit logging for all system actions
- [ ] 📈 Advanced analytics and reporting dashboard
- [ ] 📱 Mobile companion app for field workers
- [ ] 🌍 Multi-language / localization support
- [ ] 🔔 Low-stock alerts and notifications

---

## 🤝 Contributing

Contributions are welcome and appreciated! Here's how to get involved:

1. **Fork** the repository
2. **Create** a feature branch
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Commit** your changes with a clear message
   ```bash
   git commit -m "feat: add your feature description"
   ```
4. **Push** to your fork
   ```bash
   git push origin feature/your-feature-name
   ```
5. **Open a Pull Request** — describe what you changed and why

Please ensure your code follows consistent formatting and includes comments where necessary.

---

## 👥 Authors & Contributors

This project was built as a collaborative effort:

| Name | GitHub |
|---|---|
| **Shahzaib Mahar** | [@smaharx](https://github.com/smaharx) |
| **Najaf** | — |
| **Deepak** | — |

View the full contributors list on [GitHub](https://github.com/smaharx/disaster-management-system/graphs/contributors).

---

## 📄 License

This project is licensed under the **MIT License** — you are free to use, modify, and distribute it with attribution.

See the [LICENSE](./LICENSE) file for full details.

---

<div align="center">

Made with ❤️ to support disaster relief operations

⭐ If this project helped you, please consider giving it a star on GitHub!

</div>
