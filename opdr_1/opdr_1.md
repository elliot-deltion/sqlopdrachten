# Sql basis

### Database gegevens filteren
Maak gebruik van het sql-bestand school.sql en voer hierop onderstaande opdrachten uit.
Theorie kun je vinden op: https://www.edutorial.nl/dbq/introductie/

### Opdracht 1
* Geef de query voor een overzicht van de naam en roepnaam van alle cursisten die in Oosterhout wonen.
select naam,roepnaam from cursist where plaats = 'Oosterhout';


### Opdracht 2
* Geef de query voor een overzicht van het cursistnummer en de roepnaam van alle cursisten die niet in Oosterhout wonen.
select cursistnr,roepnaam from cursist where plaats != 'Oosterhout';


### Opdracht 3
* Geef de query voor een overzicht van alle cursisten die vrouw zijn.
select * from cursist where geslacht = 'V';


### Opdracht 4
* Geef de query voor een overzicht van alle cursisten die niet man zijn. (dit is een andere query dan de vorige vraag, maar met hetzelfde resultaat)
select * from cursist where geslacht != 'M';


### Opdracht 5
* Geef de query voor een overzicht van alle cursisten die in Breda wonen en vrouw zijn.
select * from cursist where plaats = 'Breda' and geslacht = 'V';


### Opdracht 6
* Geef de query voor een overzicht van alle cursisten die in Oosterhout of Made wonen.
select * from cursist where plaats = 'Made' or plaats = 'Oosterhout';


### Opdracht 7
* Geef de query voor een overzicht van alle plaatsen waar cursussen worden gegeven.
select curs_plts from cursus;
