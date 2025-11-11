# Kundens app

Här är en konkret tolkning av kraven för kundens app, och hur dess behov kan tillgodoses

## Vad den ska kunna göra givet att användaren är inloggad

1. VISA på karta (före/efter hyrning)
    a) Stadszon (tänker mig att man inte kan köra utanför stadens gränser)
    * Parkeringszoner
    * Laddstationer
    * Cyklar som är tillgängliga att hyra
    * Användarens position
* VISA när man klickar på en cykel på kartan
    * Cykelinfo
        * id
        * batteri %
    * Knapp för att hyra cykel
* HYRA cykel
* VISA karta (under hyrning)
    * Stadszon, Parkeringszoner, Laddstationer, användarens position (ej lediga cyklar)
    * Knapp för att parkera cykel
* VISA historik över resor? (I kravspecen står det olika under "Bakgrund" och "Kundens app")
    * VISA bara senaste resan?


## Förslag på hur APIet kan stödja appen

* GET `/api/v1/city-zones<?city=xxx>`
    * 200 OK { data: [ GeoJSON*, ... ] }
* GET `/api/v1/parking-zones<?city=xxx>`
    * 200 OK { data: [ GeoJSON*, ... ] }
* GET `/api/v1/charging-stations<?city=xxx>`
    * 200 OK { data: [ GeoJSON*, ... ] }
* GET `/api/v1/bikes<?city=xxx>`
    * A regular user only get available bikes
    * 200 OK { data: [ id: "xxx", position: GeoJSON*, battery: 100, ... ] }
* GET `/api/v1/rentals/<rent-id>`
    * 200 OK { id: "xxx", bike_id: "yyy", start: "date", end: "date", positions: [GeoJSON*, ...], status: "parked", cost: "zzz" }
* POST `/api/v1/rentals`
    * Request body: { bike_id: "xxx" }
    * Response: 201 Created `Location: api/v1/rentals/<rent-id>`
* PUT `/api/v1/rentals/<rent-id>`
    * Request body: { status: "parked" }
    * Response: 200 OK { id: "xxx", bike_id: "yyy", start: "date", end: "date", positions: [GeoJSON*, ...], status: "parked", cost: "zzz" }


[* Info om GeoJSON](https://geojson*.org/)
