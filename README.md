# EMU SCT — Android Application (Legacy)

An Android application developed in **2014 as my Information Technology master's graduation project at Eastern Mediterranean University (EMU)**.

The application brings together information about EMU's School of Computing and Technology (SCT), academic programs, announcements and contact services. It combines a Java Android client with a PHP backend and MySQL database.

**Project type:** Academic graduation project  
**Original development:** 2014  
**Platform:** Android  
**Status:** Legacy project preserved for portfolio and reference purposes

## Purpose

The project was designed to give students and prospective students a single mobile entry point for school information and communication.

Public screens provide access to academic programs, staff information, admission requirements, announcements and useful university links. Administration screens support announcement management and reviewing submitted contact messages.

## Features

### Public Features

- Browse academic programs through an expandable, categorized list:
  - Graduate programs
  - Four-year undergraduate programs
  - Three-year diploma programs
  - Two-year diploma programs
- Open university information pages inside the application using WebView.
- Access school information, staff pages and admission requirements.
- View announcements retrieved from the backend.
- Read announcement titles, descriptions, dates, times and locations.
- Submit a contact form containing a name, email address and message.
- Access useful university links.

### Administration Features

- Administrator login screen.
- Create, list, update and delete announcements.
- View submitted contact messages.
- Delete contact messages.

These features reflect the original source implementation. Their current operation depends on restoring the backend and legacy development environment.

## Technology Stack

| Area | Technologies |
|---|---|
| Android application | Java, Android SDK |
| User interface | XML layouts, Activities, ListView, ExpandableListView |
| University web content | Android WebView |
| Networking | Apache HttpClient, HTTP POST |
| Background requests | AsyncTask |
| Data exchange | JSON |
| Backend | PHP |
| Database | MySQL |
| Original project format | Eclipse ADT |

The Android manifest declares a minimum SDK of **8** and a target SDK of **18**. The project build target is also API **18**.

## How It Works

The application uses two content paths:

1. **University information:** Program, staff, admission and school information screens load external university pages through WebView.
2. **Application data:** Announcements, contact submissions and administration operations communicate with the PHP backend over HTTP.

PHP scripts query or modify MySQL records and return JSON responses to the Android client.

The Android implementation is organized primarily by screen. Activities contain navigation, interface handling and, where needed, background network requests.

## Repository Guide

| Path | Contents |
|---|---|
| `src/com/example/schoolofcomputingandtecnology/` | Java application source |
| `res/` | XML layouts, menus, strings, styles and drawable resources |
| `PHP/` | PHP backend scripts and database connection configuration |
| `libs/` | Bundled Android support library |
| `AndroidManifest.xml` | Application configuration, permissions and registered Activities |
| `project.properties` | Legacy Android build target |
| `bin/` | Historical build outputs, including an APK |
| `gen/` | Generated Android source files |

### Key Source Files

| File | Responsibility |
|---|---|
| `MainActivity.java` | Main menu and navigation |
| `Dept.java` | Academic program categories and navigation |
| `ExpandableListAdapter.java` | Expandable program list |
| `Announcement.java` | Fetching and displaying announcements |
| `Contact.java` | Contact form validation and submission |
| `Login.java` | Original administrator login flow |
| `AdminAnnouncement.java` | Announcement creation |
| `UpAnn.java` | Announcement updates |
| `DelAnn.java` | Announcement deletion |
| `AdminContact.java` | Contact message listing and deletion |

## Backend Scripts

| Script | Responsibility |
|---|---|
| `connect.php` | MySQL connection configuration |
| `selectannoun.php` | Retrieve announcements |
| `insertannoun.php` | Create an announcement |
| `updateann.php` | Update an announcement |
| `deleteann.php` | Delete an announcement |
| `insertcontact.php` | Store a contact message |
| `selectcontact.php` | Retrieve contact messages |
| `deletecontact.php` | Delete a contact message |
| `loginselect.php` | Retrieve administrator records for the original login flow |

## Technical Experience Demonstrated

This project documents my early experience connecting a mobile interface to a database-backed server:

- Building Android screens and navigation in Java.
- Creating XML layouts and custom list adapters.
- Combining native screens with embedded web content.
- Sending form data through HTTP requests.
- Parsing JSON responses and displaying database records.
- Implementing announcement CRUD operations across client and server.
- Handling basic input validation, connectivity checks and loading feedback.

It provides historical context for my development work and the technologies I used during my master's studies.

## Inspecting and Restoring the Project

Clone the repository:

```bash
git clone https://github.com/hakanberat/EMU-SCT-Android-Application-Legacy.git
cd EMU-SCT-Android-Application-Legacy
```

The source can be inspected directly. Running the complete application requires additional restoration work:

1. Restore a compatible Eclipse ADT environment or migrate the Android project to a supported build system.
2. Configure a local PHP and MySQL environment.
3. Reconstruct the database schema expected by the PHP scripts. A SQL schema or database dump is not included.
4. Update `PHP/connect.php` for the local database.
5. Update the hardcoded backend URLs in the Java source.
6. Review external university URLs used by WebView screens.

The original connection configuration uses a database named `sct`. The PHP scripts reference the `admin`, `announcement` and `contact` tables.

Backend URLs use `10.0.2.2` and contain both `/SCT/` and `/sct/` path variants. These paths need to match the configured server directory, particularly on case-sensitive systems.

**The repository does not include a Gradle wrapper or a verified setup for current Android tooling.** A historical APK is available in `bin/`, but compatibility with current devices has not been verified.

## Legacy Limitations

The code preserves the original academic implementation and requires modernization before deployment.

- Network requests use plain HTTP and hardcoded addresses.
- PHP scripts use legacy `mysql_*` functions and concatenate request values into SQL.
- The login implementation retrieves administrator records and compares credentials on the client.
- Administrative backend scripts do not implement server-side session or token authorization.
- External university pages may have changed since development.
- No automated test suite is included.

These limitations are documented to distinguish the original implementation from current production requirements.

## Author

**Hakan Berat Demircan**

Originally developed as an Information Technology master's graduation project at Eastern Mediterranean University in 2014.

[GitHub Profile](https://github.com/hakanberat)
