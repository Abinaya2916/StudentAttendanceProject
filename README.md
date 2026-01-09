# StudentAttendanceProject
Student Attendance Management System
<!DOCTYPE html>
<html>
<head>
    <title>Student Attendance System</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

<div class="container">
    <h2>Student Attendance Management</h2>

    <input type="text" id="studentName" placeholder="Enter Student Name">

    <div class="radio">
        <input type="radio" name="status" id="present" value="Present">
        <label for="present">Present</label>

        <input type="radio" name="status" id="absent" value="Absent">
        <label for="absent">Absent</label>
    </div>

    <button onclick="markAttendance()">Submit</button>

    <h3>Attendance List</h3>
    <ul id="attendanceList"></ul>

    <p id="count"></p>
</div>

<script src="script.js"></script>
</body>
</html>

body {
    font-family: Arial, sans-serif;
    background-color: #f2f2f2;
}

.container {
    width: 350px;
    margin: 80px auto;
    background: white;
    padding: 20px;
    border-radius: 10px;
}

h2, h3 {
    text-align: center;
}

input[type="text"] {
    width: 95%;
    padding: 8px;
    margin-bottom: 10px;
}

.radio {
    text-align: center;
    margin-bottom: 10px;
}

button {
    width: 100%;
    padding: 8px;
    background-color: #4CAF50;
    color: white;
    border: none;
    cursor: pointer;
}

ul {
    list-style: none;
    padding: 0;
}

li {
    padding: 6px;
    margin: 4px 0;
    background-color: #eee;
}

let presentCount = 0;
let absentCount = 0;

function markAttendance() {
    let name = document.getElementById("studentName").value;
    let status = document.querySelector('input[name="status"]:checked');

    if (name === "" || status === null) {
        alert("Please enter name and select attendance");
        return;
    }

    let li = document.createElement("li");
    li.innerHTML = name + " - " + status.value;

    document.getElementById("attendanceList").appendChild(li);

    if (status.value === "Present") {
        presentCount++;
    } else {
        absentCount++;
    }

    document.getElementById("count").innerHTML =
        "Present: " + presentCount + " | Absent: " + absentCount;

    document.getElementById("studentName").value = "";
    status.checked = false;
}
