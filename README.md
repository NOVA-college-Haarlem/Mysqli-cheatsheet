# Mysqli-sheetsheet

Using Mysqli **Procedural** Style

## Database connectie

```php
// Database configuratie
$host  = "localhost";
$dbuser = "root";
$dbpass = "";
$dbname = "GFG";

// Maak een  database connectie
$conn = mysqli_connect($host, $dbuser, $dbpass, $dbname);
```

## Test Database connection

```php
// Controleer de verbinding
if(mysqli_connect_error())
{
 echo "Connection establishing failed!";
}
else
{
 echo "Connection established successfully.";
}
```

## DATA OPSLAAN

Add data into the database

```php

require 'database.php';

$sql = "INSERT INTO drivers (forename, surname, nationality)
VALUES ('John', 'McTire','British')";

// Voer de INSERT INTO STATEMENT uit
mysqli_query($conn, $sql);

echo "Inserted successfully";
mysqli_close($conn); // Sluit de database verbinding

```

## DATA OPHALEN

### Selecteer ALLE RIJEN uit de database.

```php
require 'database.php';

//de sql query
$sql = "SELECT forename, surname FROM users";

//hier wordt de query uitgevoerd met de database
$result = mysqli_query($conn,$sql);

/**
 * Hier wordt het resultaat ($result) omgezet
 * in een *multidimensionale associatieve array
 * in dit voorbeeld staat $all_users maar dit mag
 * voor bijvoorbeeld producten $all_products heten.
 * Maar dit kies je zelf
 */
$all_users = mysqli_fetch_all($result, MYSQLI_ASSOC);



/**
 * Hier loop (iterate) je over alle waardes die gevonden zijn.
 * Je kunt zoals je zien paragraaf-tags gebruiken
 * maar je kunt ook andere HTML-**tags** gebruiken
 */
?>
<?php foreach($users as $user): ?>
  <p><?php echo $user["voornaam"] ?></p>
<?php endforeach; ?>
```

### Selecteer 1 RIJ uit de database

```php
require 'database.php';

$sql = "SELECT forename, surname FROM users ORDER BY ID LIMIT 1";

$result = mysqli_query($conn,$sql);
  //zolang een rij gevuld kan worden wordt de loop uitgevoerd
$user = mysqli_fetch_assoc($result);

echo $user['forename'];
echo $user['surname'];

// Haal het resultaat uit het geheugen
mysqli_free_result($result);

mysqli_close($conn);
```

## DATA VERWIJDEREN

```php
require 'database.php';

$id = $_GET['id'];

$sql = "DELETE FROM student WHERE id = $id";

if (mysqli_query($conn,$sql)) {
    header("location: student_index.php");
}

```

## DATA UPDATEN

```php
require 'database.php';

$id = $_GET['id'];

$sql = "UPDATE student SET firstname = $firstname, lastname = $lastname, email = $email WHERE id = $id";

if (mysqli_query($conn,$sql)) {
    header("location: student_index.php");
}

```
