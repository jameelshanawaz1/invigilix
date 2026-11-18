# Smart Examination Management System

### Software-Based Examination Hall and Invigilator Allocation Assistant

## 📌 Project Overview

The Smart Examination Management System is a web-based application developed to simplify and automate the process of examination hall management and invigilator allocation in educational institutions.

The system provides a centralized platform for administrators and faculty members to manage examination schedules, faculty details, timetables, hall information, and invigilation duties efficiently.

It helps reduce manual work, avoid scheduling conflicts, and improve coordination between examination coordinators and faculty members.

## 🎯 Objectives

- To automate the invigilator allocation process.
- To manage faculty details and academic timetables.
- To identify faculty availability based on class schedules and existing examination duties.
- To detect scheduling conflicts and prevent duplicate duty allocation.
- To provide examination duty notifications to faculty members.
- To maintain organized digital examination records.

## ✨ Key Features

### 👨‍💼 Admin Dashboard
- Manage faculty details.
- Add, update, and delete faculty records.
- Manage examination schedules.
- Manage examination halls and time slots.
- Allocate invigilation duties.
- Check faculty availability.
- Detect scheduling conflicts.
- View and manage examination duty records.

### 👩‍🏫 Faculty Dashboard
- Faculty login and authentication.
- View personal timetable.
- View assigned examination duties.
- Check available periods.
- Receive examination duty notifications.
- Access examination-related information.

### ⚙️ System Features
- Automated faculty availability checking.
- Timetable and examination duty conflict detection.
- Centralized database management.
- Email notification support.
- Organized examination duty records.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| HTML | Webpage structure |
| CSS | User interface design |
| JavaScript | Frontend interactions |
| Python | Backend development |
| Flask | Web application framework |
| SQLite | Database management |
| VS Code | Development environment


## Conflict Management module (added)

The admin sidebar now includes **Conflict Management** at `/conflict-management`.
The module extends the existing duty-allocation checks and records blocked attempts.

### Checks performed before saving a duty
- Faculty member already assigned to another duty during an overlapping time.
- Faculty member has a timetable class during the examination.
- Faculty member has approved leave recorded for that examination date.
- Examination hall already has an overlapping allocation.
- Duplicate faculty/exam/hall assignment.
- Existing validation still checks examination date/time and hall seating capacity.

### Recording approved leave
1. Sign in using the administrator account.
2. Open **Conflict Management** from the sidebar.
3. Select the faculty member, choose the leave date, and optionally enter a note.
4. Select **Save Approved Leave**. The record is treated as approved and allocations for that faculty member on that date are blocked.

### Conflict history
When an attempted allocation is blocked, every detected reason is stored in `conflict_logs` and shown on the Conflict Management page (latest 200 entries). The existing SQLite database is migrated automatically when the app starts; two new tables are created if they do not already exist: `faculty_leave_requests` and `conflict_logs`. Existing faculty, examination, hall, timetable, duty and notification tables are retained.

### Important
The leave form is an administrator-entered **approved leave register**, not a faculty leave-application/approval workflow. The project should be tested with a copy of its database before deployment. Change the default administrator credentials and Flask secret key before using real institutional data.
