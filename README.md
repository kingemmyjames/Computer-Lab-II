# Computer-Lab-II
<?php
// Database connection
$servername = "localhost"; 
$username = "root"; 
$password = ""; 
$dbname = "student_db";

// Create connection
$conn = new mysqli($servername, $username, $password, $dbname);

// Check connection
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

// Student details
$full_name = "NDUBUISI EMMANUEL CHINOYEREM";
$matric_number = "23/CSC/164";
$course_code = "CSC 282";
$email = "kingemmyjake@gmail.com";

// Input validation
if (empty($full_name) || empty($matric_number) || empty($course_code) || empty($email)) {
    die("Error: All fields are required.");
}

if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
    die("Error: Invalid email format.");
}

// Insert into database
$sql = "INSERT INTO student_records (full_name, matric_number, course_code, email) 
        VALUES (?, ?, ?, ?)";
$stmt = $conn->prepare($sql);
$stmt->bind_param("ssss", $full_name, $matric_number, $course_code, $email);

if ($stmt->execute()) {
    echo "Student record inserted successfully.<br>";
    echo "<a href='view.php'>View All Students</a>";
} else {
    echo "Error: " . $stmt->error;
}

$stmt->close();
$conn->close();
?>

 A work on Computer Lab II 
NAME: EMMANUEL CHINOYEREM NDUBUISI
MATRIC NUMBER:23/CSC/164
COURSE CODE; CSC 282
