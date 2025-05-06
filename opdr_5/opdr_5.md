# Sql basis

### Database
Maak gebruik van het sql-bestand flits.sql en voer hierop onderstaande opdrachten uit.
Theorie kun je vinden op: https://www.edutorial.nl/dbq/introductie/

### Queries flitspaal
* Welke cameras zijn er en waar staan ze (id, address, city, max_speed).
# ANTWOORD
select id, address, city, max_speed from cameras;

* Overzicht van boetes op 50km wegen.
# ANTWOORD
select * from fines 
where speed_limit = 50;

* Overzicht van overtredingen van 1 kenteken.
# ANTWOORD
select * from licenses
join fines on licenses.id = fines.id
where licenses.id = 4;

* N.a.w.-gegevens van de hardrijders die het meest in de fout zijn gegaan. (top 10)
# ANTWOORD
select licenses.first_name, licenses.address, licenses.city from licenses
join fines on licenses.id = fines.id
group by fines.id
ORDER by fines.id
limit 10;

* Welke camera’s (id, address, city) meten de meeste snelheidsovertredingen (top 10).
# ANTWOORD
select cameras.id, cameras.address, cameras.city from cameras
join flashes on cameras.id = flashes.id
group by flashes.id
order by flashes.id
limit 10;

* Welke auto’s (kenteken, merk, type) zijn het meeste geflitst.
# ANTWOORD
select licenses.license from licenses
join flashes on licenses.id = flashes.id
group by flashes.id
order by flashes.id
limit 10;

* Welke flitspaal (=camera met id, address, city) flitst het meest (top 10).
# ANTWOORD
select cameras.id, cameras.address, cameras.city from cameras
join flashes on cameras.id = flashes.id
group by flashes.id
order by flashes.id
limit 10;


* Kentekens van auto’s die het hoogste bedrag aan boetes hebben gekregen (top 10).
# ANTWOORD
select licenses.license from licenses
join fines on licenses.id = fines.id
group by fines.fine
order by fines.fine
limit 10;

* Overzicht van auto’s (kenteken, merk, type) waarvan het kenteken overeenkomt met sitecode 10 (zoals X-999-XX) https://nl.wikipedia.org/wiki/Nederlands_kenteken.
# ANTWOORD
select license from licenses
where license LIKE '%-999-%';