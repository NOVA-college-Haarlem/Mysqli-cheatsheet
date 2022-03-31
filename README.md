# Mysqli-sheetsheet

Using Mysqli Object Oriented Style

## Database connectie

```php
$dbhost = 'localhost';
$dbuser = 'root';
$dbpass = '';
$dbname = 'WHAT IS THE NAME OF YOUR DATABASE?';
$mysqli = new mysqli($dbhost, $dbuser, $dbpass, $dbname);
```

## Test Database connection

```php

if($mysqli->connect_errno ) {
    printf("Connect failed: %s<br />", $mysqli→connect_error);
    exit();
}

printf('Connected successfully.<br />');
```

## DATA OPSLAAN

Add data to the database

```php

$sql = "INSERT INTO drivers (forename, surname, nationality)
VALUES ('John', 'McTire','British')";

if ($mysqli->query($sql) === TRUE) {
    echo "New record created successfully";
} else {
    echo "Error: " . $sql . "<br>" . $conn->error;
}$mysqli->close();

```

## DATA OPHALEN

Selecteer 1 RIJ uit de database.

```php

$result = $mysqli->query("SELECT forename, surname FROM users ORDER BY ID LIMIT 1");

$user = $result->fetch_assoc(); //met fetch_assoc

echo $user["forename"] . " ".  $user["surname"];
```

Selecteer MEERDERE RIJEN uit de database.

```php

$result = $mysqli->query("SELECT forename, surname FROM drivers ORDER BY ID LIMIT 3");

$rows = $result->fetch_all(MYSQLI_ASSOC); //met fetch_all()

foreach ($rows as $row) {
    echo $row["forename"] . " ".  $row["surname"];
}

```

## DATA VERWIJDEREN

```php

$id = $_GET['id'];

$sql = "DELETE FROM student WHERE id = $id";


if ($mysqli->query($sql)) {
    header("location: student_index.php");
}

```

## DATA UPDATEN

```php

$id = $_GET['id'];

$sql = "UPDATE student SET firstname, lastname, email WHERE id = $id";


if ($mysqli->query($sql)) {
    header("location: student_index.php");
}

```
