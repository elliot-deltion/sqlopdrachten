# Sql basis

### Database gegevens aanpassen
Maak gebruik van het sql-bestand reisbureau.sql en voer hierop onderstaande opdrachten uit.
Theorie kun je vinden op: https://www.edutorial.nl/dbq/introductie/

### Opdracht 1
* Geef de query om alle tabellen in de database 'reisbureau' weer te gegeven
show TABLES;


### Opdracht 2
* Voeg 2 nieuwe klanten toe aan de tabel 'customers' (je mag de waarden zelf bedenken)
INSERT INTO `customers` (`id`, `first_name`, `last_name`, `email`, `address`, `postal_code`, `city`, `country_code`, `phone`, `created_at`, `updated_at`) VALUES (NULL, 'Peepee', 'Poopoo', 'peepeepoopoo@gmail.com', 'toiletstraat 30', '8043', 'Zwolle', 'da_DK', '06345839453', '2025-04-10 15:27:08', NULL)INSERT INTO `customers` (`id`, `first_name`, `last_name`, `email`, `address`, `postal_code`, `city`, `country_code`, `phone`, `created_at`, `updated_at`) VALUES (NULL, 'Henk', 'Kat', 'henkkat@gmail.com', 'zoostraat 24', '8043', 'Zwolle', 'da_DK', '0633945453', '2025-04-10 15:27:08', NULL)


### Opdracht 3
* Geef de query om de eerste 10 boekingen te verwijderen (reservations)
    DELETE FROM `reservations` WHERE `reservations`.`id` = 1;
    DELETE FROM `reservations` WHERE `reservations`.`id` = 2;
    DELETE FROM `reservations` WHERE `reservations`.`id` = 3;
    DELETE FROM `reservations` WHERE `reservations`.`id` = 4;
    DELETE FROM `reservations` WHERE `reservations`.`id` = 5;
    DELETE FROM `reservations` WHERE `reservations`.`id` = 6;
    DELETE FROM `reservations` WHERE `reservations`.`id` = 7;
    DELETE FROM `reservations` WHERE `reservations`.`id` = 8;
    DELETE FROM `reservations` WHERE `reservations`.`id` = 9;
    DELETE FROM `reservations` WHERE `reservations`.`id` = 10;


### Opdracht 4
* De klant met id 13 is verhuist naar 'De van der veldensteeg 81' in 'Apeldoorn'.
* Pas het record aan en geef de query
* Toon het record en controleer of de gegevens correct zijn.
UPDATE `customers` SET `address` = 'De van der veldensteeg 81', `city` = 'Apeldoorn', `updated_at` = NULL WHERE `customers`.`id` = 13; 