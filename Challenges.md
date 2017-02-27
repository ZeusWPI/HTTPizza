# Opdrachten

Hieronder zijn een reeks opdrachten gegeven die jullie kunnen completen voor de rewards die erbij gespecifieerd zijn, het is aan te raden om de opdrachten in volgorde op te lossen. [TBD] De rewards zullen namelijk ook incrementeel toegekend worden, dus je bent niets met de code van opdracht 5, als je 4 nog niet hebt opgelost.
Als een opdracht correct uitgevoerd wordt zal een code meegeleverd worden in de response, die jullie kunnen gebruiken om aan de toog van jullie rewards gebruik te maken.

De code is uniek per team en opdracht, dus het heeft geen zin om de codes van andere teams te gebruiken.

Er wordt verwacht dat jullie de team naam en opprachtnummer meegeven als message-headers zoals (bvb.) in onderstaand voorbeeld.

Voorbeeld
```
Customer => Team3
Challenge => 4
```
Thematisch zullen jullie stap voor stap een systeem opstellen om automatisch pizza naar wens te bestellen bij onze fictieve pizzeria `Hot n' Tasty Tomato Palace`. Harold, de uitbater heeft zijn online bestel platform jammer genoeg outsourced naar India, en snapt helemaal niet hoe de code werkt, dus je kan hem niets vragen. De opracht is dus stapsgewijs zijn systeem te verkennen, om uiteindelijk bij een full-featured pizza order bot tercht te komen.

## Challenge 1
To get things started, we need to start things. De beste plaats daarvoor is natuurlijk de welkom-pagina!

### Opdracht
Stuur een simpele PIZZA request naar `pizza!?!be:ugent:zeus:pi/welcome`. Vergeet je team naam en het challenge nummer niet bij te sluiten, voor de rest mag de request leeg zijn. De server stuurt een response terug met daarin je code (lees die voorlopig manueel).

### Rewards: Part of the crew
Je kan met je net gekregen code aan de toog een Zeus sticker en Google goodies gaan afhalen voor elk team lid.

## Challenge 2
Je pizza-bots zal snel moeten kunnen omgaan met server-responses, onder andere om time-outs te vermijden.

### Opdracht
Stuur opnieuw een simpele PIZZA request, maar nu naar `pizza!?!be:ugent:zeus:pi/login`, je zal een response terug krijgen met daarin de `Token => [field-value]` message-header, waarbij de field-value een token is die je kan gebruiken om in te loggen. Deze token expired echter na 1 seconde, stuur dus rap een ORDER, met `application/x-www-form-urlencoded` as `Pizza-Type`, en in de body `Code=[token]`. De server response dan zal opnieuw een code bevatten.

### Rewards: 
Je kan per teamlid, een bonnetje gaan halen aan de toog, waarmee je (eenmalig) drank kan gaan halen aan 50 cent korting.

## Challenge 3
Pizzas zijn ook configureerbaar. Pizza-opties kan je doorgeven als bijkomende velden in de header van een request. Voor deze opgave moet je aangepaste pizzas kunnen bestellen bij `Hot n' Tasty Tomato Palace`.

### Opdracht
Stuur eerst een PIZZA request naar `/pizzas` om pizzadetails op te vragen. Je vindt deze opties terug in de body van het antwoord van de server, hetzij in JSON, hetzij url-encoded. De encodering wordt aangegeven door het `Pizza-Type` veld in de header: `application/json` voor JSON en `application/x-www-form-urlencoded` voor url-encoding. Vervolgens dien je deze pizza te bestellen met een ORDER request naar `/pizzas`, **met elke entry uit de respons in de header geplaatst**. Als je bestelling juist is doorgegeven, zal je als antwoord een nieuwe opgave krijgen op dezelfde manier. Dit blijf je doen tot je een rewardcode (of foutmelding) krijgt. Deze kan je herkennen aan de `text/plain` handling.

### Reward
Alle pizza's zijn nu 50 cent goedkoper voor jullie team! (voor de rest van de avond)

## Challenge 4
Om sneller pizza informatie te kunnen geven, zal Harold sommige requests zippen met gzip, zorg er dus voor dat je bot daar mee kan omgaan.

### Opdracht
Stuur een simpele PIZZA request naar `pizza!?!be:ugent:zeus:pi/fastlane`, je zal dan een response terug krijgen waarbij de header `Transfer-Encoding` soms op `gzip` staat, maar zeker niet altijd, pas als `Transfer-Encoding` effectief op `gzip` staat, zal er een code inzitten (1 kans op 50).
Opletten, in het `HTTPizza-protocol` wordt `Handling` in de plaats gebruikt.

### Rewards:
Je krijgt een kwart pizza per persoon naar keuze gratis! (eenmalig)
