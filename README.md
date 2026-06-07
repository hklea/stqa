# STQA - Library Management System

A desktop application for managing library operations, built with Java and JavaFX. Supports three user roles — **Librarian**, **Manager**, and **Administrator** — each with dedicated workflows for sales, inventory, and employee management.

## Features

- **Librarian**: Check out books, generate bill receipts, track personal sales performance
- **Manager**: Manage book inventory, monitor stock levels, view/add/edit librarians, see analytics (charts by day/month/year)
- **Administrator**: Full employee management (librarians, managers, admins), financial overview, salary tracking

## Tech Stack

| Layer | Technology |
|---|---|
| Language | Java 21 |
| GUI | JavaFX 21 |
| Styling | BootstrapFX 0.4.0 |
| Build | Apache Maven 3.11.0 |
| Testing | JUnit Jupiter 5.9.2 |
| Persistence | Java Object Serialization |

## Project Structure

```
stqa-main/
├── src/
│   ├── main/java/com/example/testingprj/
│   │   ├── MainFx.java          # Application entry point, all UI scenes
│   │   ├── Book.java            # Book entity with sales/purchase history
│   │   ├── Librarian.java       # Librarian role, checkout logic
│   │   ├── Manager.java         # Manager role, extends Librarian
│   │   ├── Administrator.java   # Admin role, extends Manager
│   │   └── BillNumber.java      # Abstract base class, bill counters, persistence
│   └── test/java/com/example/testingprj/
│       ├── BookTest.java
│       ├── LibrarianTest.java
│       ├── ManagerTest.java
│       ├── AdministratorTest.java
│       └── BillNumberTest.java
├── Books.bin                    # Serialized book inventory (auto-generated)
├── Bill*.txt                    # Generated transaction receipts
└── pom.xml
```

## Prerequisites

- Java 21+
- Maven 3.6+ (or use the included Maven wrapper)

## Running the Application

```bash
# Clone or extract the project, then:
mvn clean javafx:run
```

Or with the Maven wrapper:

```bash
# Linux/macOS
./mvnw clean javafx:run

# Windows
mvnw.cmd clean javafx:run
```

## Running Tests

```bash
mvn test
```

## Default Credentials

The application ships with hardcoded accounts for demo/testing:

| Role | Username | Password |
|---|---|---|
| Librarian | *(see `Manager.InstantiateLibrarians()`)* | *(see source)* |
| Manager | *(see `Administrator.InstantiateManagers()`)* | *(see source)* |
| Administrator | *(see `Administrator.InstantiateAdmins()`)* | *(see source)* |

> Credentials are set in `MainFx.java` at startup and are not stored in a config file.

## Data Persistence

- Book inventory is saved to `Books.bin` in the project root using Java serialization. This file is created automatically on first run.
- Each sales transaction generates a numbered bill file (e.g. `Bill1.txt`, `Bill2.txt`).

## Build

```bash
mvn clean package
```

Compiled output goes to the `target/` directory.
