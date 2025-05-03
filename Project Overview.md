# FTP-Client-Server-Application
# FTP Client-Server Application

A basic FTP (File Transfer Protocol) client-server implementation in C#, demonstrating core FTP functionalities with a GUI client and a console-based server.

---

## Table of Contents
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Limitations](#limitations)
- [Improvements](#potential-improvements)
- [Contributing](#contributing)

---

## Features

### **FTP Server** (`Program.cs`)
- 🖥️ **Control/Data Channels**: Uses port `21` (control) and `20` (data).
- 🔒 **Authentication**: Hardcoded credentials (`USER "std"`, `PASS "123"`).
- 📁 **Commands Supported**:
  - `LIST`: Lists files/folders in the current directory.
  - `CWD`: Changes the working directory.
  - `RETR`: Downloads a file.
  - `STOR`: Uploads a file.
  - `EXIT`: Ends the session.
- 🧩 **Concurrency**: Handles multiple clients via `ThreadPool`.
- 📂 **Directory Management**: Root directory set to `G:\Root` (configurable).

### **FTP Client** (`Form1.cs`)
- 🖼️ **GUI Interface**: Input fields for server IP, username, and password.
- 📋 **Actions**:
  - Connect to server.
  - List, download, and upload files.
  - Navigate folders (`CWD` and `Back` buttons).
- 📊 **UI Components**:
  - Separate list boxes for files and folders.
  - Status bar for real-time feedback.

---

## Installation

1. **Prerequisites**:
   - .NET Framework (compatible with .NET Core 3.1+).
   - Ensure the server root directory exists (`G:\Root` by default; modify in `Program.cs` if needed).

2. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/ftp-client-server.git
