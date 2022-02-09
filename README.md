# Mysqli-sheetsheet

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

if($mysqli→connect_errno ) {
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

