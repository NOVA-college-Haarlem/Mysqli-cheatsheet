## Mysqli And Prepared Statements

You must **always** use `prepared statements` for any SQL query that would contain a PHP variable. This will prevent SQL injections.

#### SELECT Data with Prepared Statements

```php
$sql = "SELECT * FROM drivers WHERE id=?"; // SQL with parameters
$stmt = $mysqli->prepare($sql);
$stmt->bind_param("i", $id);
$stmt->execute();
$result = $stmt->get_result(); // get the mysqli result
$user = $result->fetch_assoc(); // fetch data
```

### INSERT INTO with Prepared Statements

```php

// prepare and bind
$stmt = $mysqli->prepare("INSERT INTO drivers (forename, surname, nationality) VALUES (?, ?, ?)");
$stmt->bind_param("sss", $firstname, $lastname, $country);

// set parameters and execute
$firstname = "John";
$lastname = "Doe";
$country = "USA";
$stmt->execute();

$firstname = "Mary";
$lastname = "Moe";
$email = "British";
$stmt->execute();

echo "New records created successfully";
```
