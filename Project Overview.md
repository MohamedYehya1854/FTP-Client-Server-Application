# FTP-Client-Server-Application
This project is a basic FTP (File Transfer Protocol) client-server application implemented in C#. It consists of two main components: an FTP server (Program.cs) and a GUI-based FTP client (Form1.cs and Form1.Designer.cs). Below is a detailed breakdown:

1. FTP Server (Program.cs)
Features
Control/Data Channels: Uses port 21 for control commands and port 20 for data transfers.

Concurrency: Handles multiple clients simultaneously using ThreadPool.

Authentication: Requires hardcoded credentials (USER "std" and PASS "123").

Supported Commands:

USER/PASS: Authentication.

LIST: Returns directory contents (files/folders).

CWD: Changes the working directory.

RETR: Downloads a file.

STOR: Uploads a file.

EXIT: Terminates the session.

Directory Management:

Root directory: G:\Root (configurable via RootDirectory variable).

Tracks each client’s current directory using ConcurrentDictionary.

File Transfers:

Files are sent/received over port 20 using TcpListener and NetworkStream.

Timeout handling for data connections during uploads.

Limitations
Hardcoded credentials (no user database).

No encryption (passwords/data sent in plaintext).

Fixed data port (20) may cause conflicts with simultaneous transfers.

Basic error handling (e.g., directory not found).

2. FTP Client (Form1.cs)
GUI Components
Input Fields: Server IP, username, password.

Buttons:

Connect: Establishes a control connection to the server.

List: Fetches directory contents.

Download/Upload: File transfer actions.

Open Folder: Navigates into a selected directory.

Back: Returns to the parent directory.

Exit: Closes the application.

List Boxes:

lbFiles: Displays files.

lbFolders: Displays directories (marked with <DIR>).

Status Label: Shows connection status and command responses.

Functionality
Authentication: Sends USER and PASS commands to the server.

Directory Navigation: Uses CWD and CWD .. to navigate folders.

File Transfers:

RETR: Downloads a file via port 20 and saves it locally using SaveFileDialog.

STOR: Uploads a file selected via OpenFileDialog.

UI Updates: Reflects server responses in real-time (e.g., success/failure messages).

Limitations
Assumes the server uses port 21 and 20 (no configurability).

No support for passive (PASV) mode, which may cause issues with firewalls/NAT.

Minimal error recovery (e.g., no retry logic for failed transfers).

3. Design (Form1.Designer.cs)
Layout: Organized into sections for server connection, file/folder listings, and action buttons.

Controls:

Text boxes for server IP, username, and password.

Separate list boxes for files and folders.

Status bar at the bottom for feedback.

Event Handlers: Linked to button clicks and list selections.

4. Workflow
Server Startup:

Listens on port 21 for incoming connections.

Spawns a thread for each client via ThreadPool.

Client Connection:

User enters server IP and credentials.

Establishes a control channel and authenticates.

Directory Interaction:

LIST command populates files/folders in the UI.

CWD and Back buttons enable folder navigation.

File Transfers:

RETR/STOR trigger data channel connections on port 20.

Files are streamed between client and server.

5. Potential Improvements
Security: Add SSL/TLS encryption for credentials and data.

Configuration: Allow customizable ports and root directory via config files.

Error Handling: Implement retries and detailed error logging.

Passive Mode: Support PASV command for firewall-friendly transfers.

User Management: Replace hardcoded credentials with a user database.

6. Usage
Server:

Run Program.cs (ensure G:\Root exists or modify RootDirectory).

Client:

Enter server IP (default 127.0.0.1), username (std), password (123).

Use buttons to navigate directories and transfer files.

This project demonstrates core FTP functionalities but is not production-ready due to security and scalability limitations. It serves as a foundational example for understanding FTP protocol basics and C# network programming.
