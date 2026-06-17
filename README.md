# Academia Portal – Client Server Based Course Registration System

A multi-threaded client-server based academic course registration portal developed in C using TCP sockets, pthreads, mutex synchronization, and file-based persistence.

The system supports three user roles:

- Admin
- Faculty
- Student

Users connect through a client application while the server handles authentication, course management, enrollment operations, and concurrent access control.

---

## Features

### Admin

- Add new students
- Add new faculty members
- Activate/Deactivate student accounts
- Update student details
- Update faculty details

### Faculty

- Add new courses
- Remove offered courses
- View course enrollments
- Change password

### Student

- Enroll in courses
- Unenroll from courses
- View enrolled courses
- Change password

---

## System Architecture

```
+------------+
|   Client   |
+------------+
       |
       | TCP Socket
       |
+------------+
|   Server   |
+------------+
       |
       +------------------+
       |                  |
+-------------+   +-------------+
| students.dat|   | faculty.dat |
+-------------+   +-------------+
       |
+-------------+
|  admin.dat  |
+-------------+
```

---

## Technologies Used

- C Programming
- POSIX Sockets
- Pthreads
- Mutex Locks
- File Handling System Calls
- Linux System Programming

---

## Concurrency Handling

The server supports multiple simultaneous clients using threads.

Each connected client is assigned a dedicated thread.

### Mutexes Used

| Mutex | Purpose |
|---------|----------|
| student_mutex | Protects student records |
| faculty_mutex | Protects faculty records |
| course_mutex | Protects course enrollment operations |

This prevents race conditions during concurrent access.

---

## Data Storage

The system uses binary files for persistence.

### admin.dat

Stores administrator credentials.

### students.dat

Stores:

- Student ID
- Username
- Password
- Active Status
- Enrolled Courses

### faculty.dat

Stores:

- Faculty ID
- Username
- Password
- Offered Courses
- Available Seats

---

## Project Structure

```
Academia-Portal/
│
├── server.c
├── client.c
├── admin.dat
├── students.dat
├── faculty.dat
├── README.md
└── screenshots/
```

---

## Compilation

### Server

```bash
gcc server.c -o server -lpthread
```

### Client

```bash
gcc client.c -o client
```

---

## Running the Application

### Start Server

```bash
./server
```

Server runs on:

```text
Port: 8080
```

### Start Client

```bash
./client
```

---

## Default Admin Credentials

```text
Username: admin
Password: admin123
```

---

## Functional Workflow

### Admin

1. Login
2. Add Students
3. Add Faculty
4. Activate/Deactivate Students
5. Update Records

### Faculty

1. Login
2. Add Courses
3. Remove Courses
4. View Enrollments

### Student

1. Login
2. View Available Courses
3. Enroll/Unenroll
4. View Registered Courses

---

## Sample Output

### Admin Operations

- Student Creation
- Faculty Creation
- Student Activation/Deactivation

### Faculty Operations

- Add Courses
- View Student Enrollments

### Student Operations

- Enroll in Available Courses
- View Registered Courses

---

## Key Concepts Demonstrated

- Socket Programming
- Client-Server Architecture
- Multithreading
- Synchronization using Mutexes
- File-Based Database Management
- Concurrent User Handling
- Role-Based Access Control

