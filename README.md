# Student-Management-System
1. index.html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Student Management System</title>

    <link rel="stylesheet" href="style.css">
</head>

<body>

<header class="topbar">
    <div>
        <h1>Student Management System</h1>
        <p>Manage student records efficiently</p>
    </div>
</header>

<main class="container">

    <!-- Dashboard -->
    <section class="dashboard">

        <div class="stat-card">
            <span>Total Students</span>
            <strong id="totalStudents">0</strong>
        </div>

        <div class="stat-card">
            <span>AI & Data Science</span>
            <strong id="aidsCount">0</strong>
        </div>

        <div class="stat-card">
            <span>Computer Science</span>
            <strong id="cseCount">0</strong>
        </div>

        <div class="stat-card">
            <span>Other Departments</span>
            <strong id="otherCount">0</strong>
        </div>

    </section>

    <!-- Student Form -->
    <section class="card">

        <div class="section-header">
            <div>
                <h2 id="formTitle">Add Student</h2>
                <p>Enter student information below</p>
            </div>
        </div>

        <form id="studentForm">

            <input type="hidden" id="editIndex">

            <div class="form-grid">

                <div class="form-group">
                    <label for="studentId">Student ID</label>
                    <input
                        type="text"
                        id="studentId"
                        placeholder="STU001"
                        required
                    >
                </div>

                <div class="form-group">
                    <label for="name">Full Name</label>
                    <input
                        type="text"
                        id="name"
                        placeholder="Enter full name"
                        required
                    >
                </div>

                <div class="form-group">
                    <label for="email">Email</label>
                    <input
                        type="email"
                        id="email"
                        placeholder="student@example.com"
                        required
                    >
                </div>

                <div class="form-group">
                    <label for="phone">Phone</label>
                    <input
                        type="tel"
                        id="phone"
                        placeholder="9876543210"
                        pattern="[0-9]{10}"
                        required
                    >
                </div>

                <div class="form-group">
                    <label for="department">Department</label>
                    <select id="department" required>
                        <option value="">Select department</option>
                        <option value="AI & Data Science">
                            AI & Data Science
                        </option>
                        <option value="Computer Science">
                            Computer Science
                        </option>
                        <option value="Information Technology">
                            Information Technology
                        </option>
                        <option value="Electronics">
                            Electronics
                        </option>
                        <option value="Mechanical">
                            Mechanical
                        </option>
                        <option value="Civil">
                            Civil
                        </option>
                    </select>
                </div>

                <div class="form-group">
                    <label for="year">Year</label>
                    <select id="year" required>
                        <option value="">Select year</option>
                        <option value="1">1st Year</option>
                        <option value="2">2nd Year</option>
                        <option value="3">3rd Year</option>
                        <option value="4">4th Year</option>
                    </select>
                </div>

                <div class="form-group">
                    <label for="gender">Gender</label>
                    <select id="gender" required>
                        <option value="">Select gender</option>
                        <option value="Male">Male</option>
                        <option value="Female">Female</option>
                        <option value="Other">Other</option>
                    </select>
                </div>

                <div class="form-group">
                    <label for="dob">Date of Birth</label>
                    <input
                        type="date"
                        id="dob"
                        required
                    >
                </div>

            </div>

            <div class="form-actions">
                <button type="submit" class="btn primary">
                    <span id="submitText">Add Student</span>
                </button>

                <button
                    type="button"
                    class="btn secondary"
                    id="cancelBtn"
                    onclick="resetForm()"
                >
                    Cancel
                </button>
            </div>

        </form>

    </section>

    <!-- Student Records -->
    <section class="card">

        <div class="section-header records-header">

            <div>
                <h2>Student Records</h2>
                <p>View and manage registered students</p>
            </div>

            <div class="filters">

                <input
                    type="text"
                    id="searchInput"
                    placeholder="Search students..."
                >

                <select id="filterDepartment">
                    <option value="">All Departments</option>
                    <option value="AI & Data Science">
                        AI & Data Science
                    </option>
                    <option value="Computer Science">
                        Computer Science
                    </option>
                    <option value="Information Technology">
                        Information Technology
                    </option>
                    <option value="Electronics">
                        Electronics
                    </option>
                    <option value="Mechanical">
                        Mechanical
                    </option>
                    <option value="Civil">
                        Civil
                    </option>
                </select>

            </div>

        </div>

        <div class="table-container">

            <table>

                <thead>
                    <tr>
                        <th>ID</th>
                        <th>Name</th>
                        <th>Email</th>
                        <th>Phone</th>
                        <th>Department</th>
                        <th>Year</th>
                        <th>Gender</th>
                        <th>DOB</th>
                        <th>Actions</th>
                    </tr>
                </thead>

                <tbody id="studentTableBody">
                </tbody>

            </table>

            <div id="emptyMessage" class="empty-message">
                No student records found.
            </div>

        </div>

    </section>

</main>

<div id="toast" class="toast"></div>

<script src="script.js"></script>

</body>
</html>


2. style.css

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, Helvetica, sans-serif;
    background: #f4f7fb;
    color: #1f2937;
}

/* Topbar */

.topbar {
    background: #111827;
    color: white;
    padding: 25px 7%;
}

.topbar h1 {
    font-size: 28px;
    margin-bottom: 5px;
}

.topbar p {
    color: #cbd5e1;
}

/* Main container */

.container {
    width: 86%;
    max-width: 1500px;
    margin: 30px auto;
}

/* Dashboard */

.dashboard {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 20px;
    margin-bottom: 25px;
}

.stat-card {
    background: white;
    border-radius: 14px;
    padding: 25px;
    box-shadow: 0 5px 20px rgba(0, 0, 0, 0.06);
}

.stat-card span {
    display: block;
    color: #64748b;
    font-size: 14px;
    margin-bottom: 12px;
}

.stat-card strong {
    font-size: 30px;
}

/* Cards */

.card {
    background: white;
    border-radius: 14px;
    padding: 28px;
    margin-bottom: 25px;
    box-shadow: 0 5px 20px rgba(0, 0, 0, 0.06);
}

.section-header {
    margin-bottom: 25px;
}

.section-header h2 {
    margin-bottom: 5px;
}

.section-header p {
    color: #64748b;
}

/* Form */

.form-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
}

.form-group {
    display: flex;
    flex-direction: column;
    gap: 8px;
}

.form-group label {
    font-size: 14px;
    font-weight: 600;
}

.form-group input,
.form-group select,
.filters input,
.filters select {
    width: 100%;
    padding: 12px 14px;
    border: 1px solid #d1d5db;
    border-radius: 8px;
    font-size: 14px;
    outline: none;
    background: white;
}

.form-group input:focus,
.form-group select:focus,
.filters input:focus,
.filters select:focus {
    border-color: #2563eb;
}

/* Buttons */

.form-actions {
    margin-top: 25px;
    display: flex;
    gap: 10px;
}

.btn {
    border: none;
    padding: 12px 20px;
    border-radius: 8px;
    cursor: pointer;
    font-weight: 600;
}

.primary {
    background: #2563eb;
    color: white;
}

.secondary {
    background: #e5e7eb;
    color: #111827;
}

.btn:hover {
    opacity: 0.9;
}

/* Records header */

.records-header {
    display: flex;
    justify-content: space-between;
    gap: 20px;
    align-items: center;
}

.filters {
    display: flex;
    gap: 10px;
}

.filters input {
    min-width: 230px;
}

/* Table */

.table-container {
    overflow-x: auto;
}

table {
    width: 100%;
    border-collapse: collapse;
}

thead {
    background: #f8fafc;
}

th,
td {
    text-align: left;
    padding: 14px;
    border-bottom: 1px solid #e5e7eb;
    font-size: 13px;
    white-space: nowrap;
}

th {
    font-weight: 700;
}

.action-buttons {
    display: flex;
    gap: 6px;
}

.edit-btn,
.delete-btn {
    border: none;
    padding: 7px 10px;
    border-radius: 6px;
    cursor: pointer;
}

.edit-btn {
    background: #dbeafe;
    color: #1d4ed8;
}

.delete-btn {
    background: #fee2e2;
    color: #b91c1c;
}

.empty-message {
    text-align: center;
    padding: 30px;
    color: #64748b;
}

/* Toast */

.toast {
    position: fixed;
    right: 25px;
    bottom: 25px;
    background: #111827;
    color: white;
    padding: 14px 20px;
    border-radius: 8px;
    opacity: 0;
    pointer-events: none;
    transition: 0.3s;
}

.toast.show {
    opacity: 1;
}

/* Responsive */

@media (max-width: 1000px) {

    .dashboard {
        grid-template-columns: repeat(2, 1fr);
    }

    .records-header {
        flex-direction: column;
        align-items: flex-start;
    }

    .filters {
        width: 100%;
    }

    .filters input,
    .filters select {
        flex: 1;
        min-width: 0;
    }
}

@media (max-width: 700px) {

    .container {
        width: 94%;
    }

    .dashboard {
        grid-template-columns: 1fr;
    }

    .form-grid {
        grid-template-columns: 1fr;
    }

    .filters {
        flex-direction: column;
    }

    .topbar {
        padding: 20px;
    }

    .card {
        padding: 20px;
    }
}


3. script.js

let students = JSON.parse(localStorage.getItem("students")) || [];

const studentForm = document.getElementById("studentForm");
const studentTableBody = document.getElementById("studentTableBody");
const emptyMessage = document.getElementById("emptyMessage");

const searchInput = document.getElementById("searchInput");
const filterDepartment = document.getElementById("filterDepartment");

const totalStudents = document.getElementById("totalStudents");
const aidsCount = document.getElementById("aidsCount");
const cseCount = document.getElementById("cseCount");
const otherCount = document.getElementById("otherCount");

const formTitle = document.getElementById("formTitle");
const submitText = document.getElementById("submitText");
const editIndex = document.getElementById("editIndex");

const studentIdInput = document.getElementById("studentId");
const nameInput = document.getElementById("name");
const emailInput = document.getElementById("email");
const phoneInput = document.getElementById("phone");
const departmentInput = document.getElementById("department");
const yearInput = document.getElementById("year");
const genderInput = document.getElementById("gender");
const dobInput = document.getElementById("dob");


/* ================================
   FORM SUBMISSION
================================ */

studentForm.addEventListener("submit", function (event) {

    event.preventDefault();

    const student = {
        studentId: studentIdInput.value.trim(),
        name: nameInput.value.trim(),
        email: emailInput.value.trim(),
        phone: phoneInput.value.trim(),
        department: departmentInput.value,
        year: yearInput.value,
        gender: genderInput.value,
        dob: dobInput.value
    };

    // Validation

    if (
        !student.studentId ||
        !student.name ||
        !student.email ||
        !student.phone ||
        !student.department ||
        !student.year ||
        !student.gender ||
        !student.dob
    ) {
        showToast("Please fill all fields.");
        return;
    }

    if (!/^[0-9]{10}$/.test(student.phone)) {
        showToast("Phone number must contain 10 digits.");
        return;
    }

    if (editIndex.value === "") {

        // Duplicate Student ID

        const duplicate = students.some(
            item => item.studentId.toLowerCase() === student.studentId.toLowerCase()
        );

        if (duplicate) {
            showToast("Student ID already exists.");
            return;
        }

        students.push(student);

        showToast("Student added successfully.");

    } else {

        const index = Number(editIndex.value);

        students[index] = student;

        showToast("Student updated successfully.");
    }

    saveStudents();

    renderStudents();

    resetForm();
});


/* ================================
   SAVE DATA
================================ */

function saveStudents() {

    localStorage.setItem(
        "students",
        JSON.stringify(students)
    );
}


/* ================================
   DISPLAY STUDENTS
================================ */

function renderStudents() {

    const searchValue =
        searchInput.value.toLowerCase().trim();

    const departmentValue =
        filterDepartment.value;

    const filteredStudents = students.filter(student => {

        const matchesSearch =
            student.studentId.toLowerCase().includes(searchValue) ||
            student.name.toLowerCase().includes(searchValue) ||
            student.email.toLowerCase().includes(searchValue);

        const matchesDepartment =
            departmentValue === "" ||
            student.department === departmentValue;

        return matchesSearch && matchesDepartment;
    });

    studentTableBody.innerHTML = "";

    if (filteredStudents.length === 0) {

        emptyMessage.style.display = "block";

    } else {

        emptyMessage.style.display = "none";

        filteredStudents.forEach(student => {

            const originalIndex =
                students.indexOf(student);

            const row = document.createElement("tr");

            row.innerHTML = `
                <td>${escapeHTML(student.studentId)}</td>
                <td>${escapeHTML(student.name)}</td>
                <td>${escapeHTML(student.email)}</td>
                <td>${escapeHTML(student.phone)}</td>
                <td>${escapeHTML(student.department)}</td>
                <td>${escapeHTML(student.year)}</td>
                <td>${escapeHTML(student.gender)}</td>
                <td>${escapeHTML(student.dob)}</td>

                <td>
                    <div class="action-buttons">

                        <button
                            class="edit-btn"
                            onclick="editStudent(${originalIndex})"
                        >
                            Edit
                        </button>

                        <button
                            class="delete-btn"
                            onclick="deleteStudent(${originalIndex})"
                        >
                            Delete
                        </button>

                    </div>
                </td>
            `;

            studentTableBody.appendChild(row);
        });
    }

    updateDashboard();
}


/* ================================
   EDIT STUDENT
================================ */

function editStudent(index) {

    const student = students[index];

    studentIdInput.value = student.studentId;
    nameInput.value = student.name;
    emailInput.value = student.email;
    phoneInput.value = student.phone;
    departmentInput.value = student.department;
    yearInput.value = student.year;
    genderInput.value = student.gender;
    dobInput.value = student.dob;

    editIndex.value = index;

    formTitle.textContent = "Edit Student";
    submitText.textContent = "Update Student";

    window.scrollTo({
        top: 0,
        behavior: "smooth"
    });
}


/* ================================
   DELETE STUDENT
================================ */

function deleteStudent(index) {

    const student = students[index];

    const confirmation = confirm(
        `Are you sure you want to delete ${student.name}?`
    );

    if (!confirmation) {
        return;
    }

    students.splice(index, 1);

    saveStudents();

    renderStudents();

    showToast("Student deleted successfully.");
}


/* ================================
   RESET FORM
================================ */

function resetForm() {

    studentForm.reset();

    editIndex.value = "";

    formTitle.textContent = "Add Student";

    submitText.textContent = "Add Student";
}


/* ================================
   SEARCH
================================ */

searchInput.addEventListener(
    "input",
    renderStudents
);


/* ================================
   FILTER
================================ */

filterDepartment.addEventListener(
    "change",
    renderStudents
);


/* ================================
   DASHBOARD
================================ */

function updateDashboard() {

    totalStudents.textContent = students.length;

    const aids = students.filter(
        student =>
            student.department === "AI & Data Science"
    ).length;

    const cse = students.filter(
        student =>
            student.department === "Computer Science"
    ).length;

    const other =
        students.length - aids - cse;

    aidsCount.textContent = aids;
    cseCount.textContent = cse;
    otherCount.textContent = other;
}


/* ================================
   TOAST MESSAGE
================================ */

function showToast(message) {

    const toast = document.getElementById("toast");

    toast.textContent = message;

    toast.classList.add("show");

    setTimeout(() => {

        toast.classList.remove("show");

    }, 2500);
}


/* ================================
   BASIC HTML ESCAPING
================================ */

function escapeHTML(value) {

    return String(value)
        .replace(/&/g, "&amp;")
        .replace(/</g, "&lt;")
        .replace(/>/g, "&gt;")
        .replace(/"/g, "&quot;")
        .replace(/'/g, "&#039;");
}


/* ================================
   INITIAL LOAD
================================ */

renderStudents();

