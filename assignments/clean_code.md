# Snygg kod


## Vilken är din egen tolkning och definition av begreppet "snygg kod"?

När jag tänker på begreppet "snygg kod", är läsbarhet den enskilt viktigaste faktorn. God läsbarhet gör koden begriplig för dem som kommer i kontakt med den, och dess syfte blir därmed tydligt.

Faktorer som ofta bidrar till läsbarhet är låg komplexitet och modulär struktur, med hög sammanhållning (cohesion) och lös koppling (coupling).

En annan betydelsefull faktor är val av koncept och beroenden, där ett minimalistiskt tänk kan göra koden enklare att jobba med. 

* Läsbar
* Begripligt
* Låg komplexitet
* Modulär - high cohesion, loose coupling (LoD)
* DRY
* Lätt att underhålla
* Lätta att testa
* Begränsa koncept, beroenden
* POGE
* Premature optimization
* YAGNI 

## Hur kan ni i ert projekt lyfta fram att ni har "snygg kod" och visa upp det för er omgivning som en kvalitetsstämpel?

I grunden handlar det om att hitta överenskommelser kring vad som är viktigt för att hålla kodbasen ren. Det kan vara saker som att försöka undvika att slänga iväg kod som man inte ens själv är någerlunda nöjd med, eller att försöka hålla saker så enkla som möjligt.

Det finns en mängd verktyg som kan hjälpa till med en mer objektiv utvärdering, och som ger konkreta förslag på förbättringar. Vi använder os till exempel av ESlint och SonarCloud i vårt CI flöde, och där finns det även en konkret möjlighet att visa upp värden för kodkvalitet för omgivningen med hjälp av badges.

* Enkelhet och tydlighet
* Släng inte iväg kod
* Kommunicera kring principer
* 

## När det gäller "software filosofier", hittade du några som du känner passar in i ert projekt i kursen och hittar du några som du själv ofta använder dig av?

I ett komplext projekt blir det viktigt att fokusera på den mest vässentliga funktionaliteten först. Koncept som "80-20" och "Satisficing" är viktiga för oss i projektet, för att samla energin mot de centrala delarna först.

En annan aspekt är att vara förlåtande med att fyra individer i ett skolprojekt har lite olika sätt att ta sig an en uppgift. Det kan resultera i att koden blir strukturerad på lite olika sätt i olika moduler, vilket relaterar till oknceptet "Tim Toady".

Det är lättare sagt än gjort att applicera i ett programvaruprojekt, men jag har ganska stor respekt för "broken window"-teorin. Om man börjar med att slänga in slarvig kod, finns en risk att det föder ny slarvir kod, och att tid aldrig ges att refaktorera.

* Satisficing
* Tim Toady - koppla ihop olika fristående delar
* Broken windows