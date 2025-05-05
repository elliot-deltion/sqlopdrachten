# Sql basis

### Database 
Maak gebruik van het sql-bestand reisbureau.sql en voer hierop onderstaande opdrachten uit.
Theorie kun je vinden op: https://www.edutorial.nl/dbq/introductie/

### Queries reisbureau
* Geef de namen van de klanten die in Rotterdam wonen.
# ANTWOORD
select naam from klanten where plaats = 'Rotterdam'


* Geef de namen van de klanten die geen reis geboekt hebben.
# ANTWOORD
select Naam from klanten where klantnummer not in (select klantnummer from boekingen);


* Hoeveel klanten komen er niet uit Rotterdam.
# ANTWOORD
select count(*) from klanten where plaats != 'Rotterdam';


* Hoeveel reizen hebben als bestemming Afrika?
# ANTWOORD
select count(*) from boekingen
join reizen on boekingen.Reisnummer = reizen.Reisnummer
join bestemmingen on reizen.Bestemmingcode = bestemmingen.Bestemmingcode
 where bestemmingen.Werelddeel = 'Afrika';


* Hoeveel moeten de klanten, die naar Azië gaan, in totaal betalen?
# ANTWOORD
select sum(boekingen.`Betaald bedrag`) from boekingen
join reizen on boekingen.Reisnummer = reizen.Reisnummer
join bestemmingen on reizen.Bestemmingcode = bestemmingen.Bestemmingcode
where bestemmingen.werelddeel = 'Azie';


* Geef de namen van de klanten die met kinderen op reis gaan.
# ANTWOORD
select Naam from klanten
join boekingen on klanten.Klantnummer = boekingen.Klantnummer
where boekingen.`aantal kinderen` >= 1;

* Hoeveel verschillende reizen kun je boeken bij dit reisbureau?
# ANTWOORD
select SUM(aantal) from (select count(bestemmingcode) as aantal from reizen); 
WERKT NOG NIET!!

* Geef de naam en postcode van de klanten die in een postcode gebied wonen dat begint met een 9.
# ANTWOORD
select Naam, Postcode from klanten
where postcode like '9%';

* Groepeer de klanten op woonplaats. Geef de woonplaats en het aantal klanten per woonplaats.
# ANTWOORD
select Plaats, count(Plaats) as klanten_per_plaats from klanten
group by Plaats;

* Geef naam en datum van de klanten die voor de maand April een reis hebbben geboekt.
# ANTWOORD
select klanten.naam, boekingen.boekdatum from klanten
join boekingen on klanten.Klantnummer = boekingen.Klantnummer
where boekingen.Boekdatum LIKE '%-04-%';

* Geef de namen van klanten, het werelddeel van de bestemming en het aantal dagen van de reis voor boekingen van minimaal 15 dagen.
# ANTWOORD
select klanten.naam, bestemmingen.Werelddeel, reizen.`aantal dagen` from klanten
join (boekingen 
      	join (reizen
      		join bestemmingen on reizen.Bestemmingcode = bestemmingen.Bestemmingcode)
      	on boekingen.Reisnummer = reizen.Reisnummer)
      on klanten.Klantnummer = boekingen.Klantnummer
where reizen.`aantal dagen` > 14;