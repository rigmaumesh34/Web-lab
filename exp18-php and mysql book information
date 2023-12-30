<html>
<head>
        <title>Book Details</title>
</head>
<body>

<h2>Add Book</h2>
<form method="post" action="<?php echo $_SERVER["PHP_SELF"]; ?>">
    <label for="book_no">Book No:</label>
    <input type="text" name="book_no" required><br>

    <label for="title">Title:</label>
    <input type="text" name="title" required><br>

    <label for="edition">Edition:</label>
    <input type="text" name="edition" required><br>

    <label for="publisher">Publisher:</label>
    <input type="text" name="publisher" required><br>

    <input type="submit" value="Add Book">
</form>

<?php
$servername = "localhost";
$username = "root";
$password = "";
$dbname = "library";

$conn = new mysqli($servername, $username, $password, $dbname);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $book_no = $_POST["book_no"];
    $title = $_POST["title"];
    $edition = $_POST["edition"];
    $publisher = $_POST["publisher"];

     $sql = "INSERT INTO book_details (book_no, title, edition, publisher) VALUES ('$book_no', '$title', '$edition', '$publisher')";
    
    if ($conn->query($sql) === TRUE) {
        echo "<p>Book information added successfully!</p>";
    } else {
        echo "Error: " . $sql . "<br>" . $conn->error;
    }
}

$sql = "SELECT * FROM book_details";
$result = $conn->query($sql);

if ($result->num_rows > 0) {
    echo "<h2>Book Details</h2>";
    echo "<table border='1'><tr><th>Book No</th><th>Title</th><th>Edition</th><th>Publisher</th></tr>";
    while($row = $result->fetch_assoc()) {
        echo "<tr><td>".$row["book_no"]."</td><td>".$row["title"]."</td><td>".$row["edition"]."</td><td>".$row["publisher"]."</td></tr>";
    }
    echo "</table>";
} else {
    echo "<p>No books found.</p>";
}

$conn->close();
?>

</body>
</html>
