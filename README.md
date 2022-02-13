# Mysqli-sheetsheet

Using Mysqli Object Oriented Style

## Database connectie

```php
$dbhost = 'localhost';
$dbuser = 'root';
$dbpass = '';
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

## SQL

### INSERT Data Using Mysqli

Add data to the database

```php

$sql = "INSERT INTO students (student_name, student_email, student_city)
VALUES ('John', 'john@example.com','los angeles')";

if ($mysqli->query($sql) === TRUE) {
    echo "New record created successfully";
} else {
    echo "Error: " . $sql . "<br>" . $conn->error;
}$mysqli->close();

```

### SELECT Data Using Mysqli

Select Data from the database.

```php

$result = $mysqli->query("SELECT Name, CountryCode FROM City ORDER BY ID LIMIT 3");

$rows = $result->fetch_all(MYSQLI_ASSOC);
foreach ($rows as $row) {
    echo $row["Name"] . " ".  $row["CountryCode"]);
}

```

## Mysqli And Prepared Statements

You must __always__ use `prepared statements` for any SQL query that would contain a PHP variable. This will prevent SQL injections.

#### SELECT Data with Prepared Statements

```php
$sql = "SELECT * FROM users WHERE id=?"; // SQL with parameters
$stmt = $mysqli->prepare($sql);
$stmt->bind_param("i", $id);
$stmt->execute();
$result = $stmt->get_result(); // get the mysqli result
$user = $result->fetch_assoc(); // fetch data
```


### INSERT INTO with Prepared Statements



```php

// prepare and bind
$stmt = $mysqli->prepare("INSERT INTO MyGuests (firstname, lastname, email) VALUES (?, ?, ?)");
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

echo "New records created successfully";
```
