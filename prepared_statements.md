# Mysqli-sheetsheet

## Mysqli And Prepared Statements

Je moet __altijd__ gebruik maken van `prepared statements` als je en SQL query gebruikt met een _variabele_. Dit voorkomt namelijk SQL-injecties en dus voorkomt het kwetsbaarheden in je applicatie.

### SELECT Data with Prepared Statements

```php
$sql = "SELECT * FROM drivers WHERE id = ?"; // SQL with parameters
$stmt = mysqli_prepare($conn, $sql);
mysqli_stmt_bind_param($stmt, "i", $id); // een i staat voor integer / een s staat voor string
mysqli_stmt_execute($stmt);
$result = mysqli_stmt_get_result($stmt); // get the mysqli result
$user = mysqli_fetch_assoc($result); // fetch data
```

### INSERT INTO with Prepared Statements

```php

$sql = "INSERT INTO drivers (forename, surname, nationality) VALUES (?, ?, ?)";
$stmt = mysqli_prepare($conn, $sql);
mysqli_stmt_bind_param($stmt, "sss", $firstname, $lastname, $country); // drie strings worden gebonden aan de query

// set parameters and execute
$firstname = "John";
$lastname = "Doe";
$country = "USA";
mysqli_stmt_execute($stmt);

$firstname = "Mary";
$lastname = "Moe";
$email = "British";
mysqli_stmt_execute($stmt);

echo "New records created successfully";
```
