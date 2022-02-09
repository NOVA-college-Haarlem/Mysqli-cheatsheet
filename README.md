# Mysqli-sheetsheet

Using Mysqli Object Oriented Style

## Database connectie

```php
$dbhost = 'localhost';
$dbuser = 'root';
$dbpass = 'root@123';
$dbname = 'TUTORIALS';
$mysqli = new mysqli($dbhost, $dbuser, $dbpass, $dbname);
```

### Test Database connection

```php

if($mysqli->connect_errno ) {
    printf("Connect failed: %s<br />", $mysqli→connect_error);
    exit();
}

printf('Connected successfully.<br />');
```

## INSERT Data Using Mysqli

```php

$sql = "INSERT INTO students (student_name, student_email, student_city)
VALUES ('John', 'john@example.com','los angeles')";

if ($conn->query($sql) === TRUE) {
    echo "New record created successfully";
} else {
    echo "Error: " . $sql . "<br>" . $conn->error;
}$conn->close();


```

## SELECT Data Using Mysqli

```php

$result = $mysqli->query("SELECT Name, CountryCode FROM City ORDER BY ID LIMIT 3");

$rows = $result->fetch_all(MYSQLI_ASSOC);
foreach ($rows as $row) {
    echo $row["Name"] . " ".  $row["CountryCode"]);
}

```

### SELECT with Prepared Statements

```php
/* Non-prepared statement (NOT GOOD) */
$mysqli->query("DROP TABLE IF EXISTS test");
$mysqli->query("CREATE TABLE test(id INT, label TEXT)");

// prepare and bind
$stmt = $conn->prepare("INSERT INTO MyGuests (firstname, lastname, email) VALUES (?, ?, ?)");
$stmt->bind_param("sss", $firstname, $lastname, $email);

// set parameters and execute
$firstname = "John";
$lastname = "Doe";
$email = "john@example.com";
$stmt->execute();

$firstname = "Mary";
$lastname = "Moe";
$email = "mary@example.com";
$stmt->execute();


```

