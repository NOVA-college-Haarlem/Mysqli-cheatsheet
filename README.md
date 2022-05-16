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

$sql = "SELECT forename, surname FROM users";

$result = mysqli_query($conn,$sql);

$all_users = mysqli_fetch_all($result, MYSQL_ASSOC);
?>

<?php foreach($users as $user): ?>
  <p><?php echo $user["voornaam"] ?></p>
<?php endforeach; ?>
```

### Selecteer 1 RIJ uit de database

```php
require 'database.php';

$sql = "SELECT forename, surname FROM users ORDER BY ID LIMIT 1";
 
if ( $result = mysqli_query($conn,$sql) )
{
  // haal een enkele db-rij op.
  while ($row=mysqli_fetch_assoc($result))
    {
        echo " Naam Item :".$row["name"]." , ";
        echo " Beschrijving : ".$row["description"];
        echo  nl2br (" \n ");
    }
    // Haal het resultaat uit het geheugen
  mysqli_free_result($result);
}
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

$sql = "UPDATE student SET firstname, lastname, email WHERE id = $id";

if (mysqli_query($conn,$sql)) {
    header("location: student_index.php");
}

```
