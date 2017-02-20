# Opdrachten

Hieronder zijn een reeks opdrachten gegeven die jullie kunnen completen voor de rewards die erbij gespecifieerd zijn, het is aan te raden om de opdrachten in volgorde op te lossen. [TBD] De rewards zullen namelijk ook incrementeel toegekend worden, dus je bent niets met de code van opdracht 5, als je 4 nog niet hebt opgelost.
Als een opdracht correct uitgevoerd wordt zal een code meegeleverd worden in de response, die jullie kunnen gebruiken om aan de toog van jullie rewards gebruik te maken.

De code is uniek per team en opdracht, dus het heeft geen zin om de codes van andere teams te gebruiken.

Er wordt verwacht dat jullie de team naam en opprachtnummer meegeven als message-headers zoals (bvb.) in onderstaand voorbeeld.

Voorbeeld
```
Customer => Team3
Opdracht => 4
```
Thematisch zullen jullie stap voor stap een systeem opstellen om automatisch pizza naar wens te bestellen bij onze fictieve pizzeria `Hot n' Tasty Tomato Palace`. Harold, de uitbater heeft zijn online bestel platform jammer genoeg outsourced naar India, en snapt helemaal niet hoe de code werkt, dus je kan hem niets vragen. De opracht is dus stapsgewijs zijn systeem te verkennen, om uiteindelijk bij een full-featured pizza order bot tercht te komen.

## Challenge 1
To get things started, we need to start things. De beste plaats daarvoor is natuurlijk de welkom-pagina!

### Opdracht
Stuur een simpele PIZZA request naar `/welkom`. Vergeet je team naam en het challenge nummer niet bij te sluiten, voor de rest mag de request leeg zijn. De server stuurt een response terug met daarin je code (lees die voorlopig manueel).

### Rewards: Part of the crew
Je kan met je net gekregen code aan de toog een Zeus sticker gaan afhalen voor elk team lid.

## Challenge 2
Je pizza-bots zal snel moeten kunnen omgaan met server-responses, onder andere om time-outs te vermijden.

### Opdracht
Stuur opnieuw een simpele PIZZA request, maar nu naar /login, je zal een response terug krijgen met daarin de `Token => [field-value]` message-header, waarbij de field-value een token is die je kan gebruiken om in te loggen. Deze token expired echter na 1 seconde, stuur dus rap een ORDER, met `application/x-www-form-urlencoded` as `Pizza-Type`, en in de body `Code=[token]`. De server response dan zal opnieuw een code bevatten.

### Rewards: 
Je kan per teamlid, een bonnetje gaan halen aan de toog, waarmee je (eenmalig) drank kan gaan halen aan 50 cent korting.

## Challenge 4
Om sneller pizza informatie te kunnen geven, zal Harold sommige requests zippen met gzip, zorg er dus voor dat je bot daar mee kan omgaan.

### Opdracht
Stuur een simpele PIZZA request naar /fastlane, je zal dan een response terug krijgen waarbij de header `Content-Encoding` soms op 
`gzip` staat, maar zeker niet altijd, pas als `Content-Encoding` effectief op `gzip` staat, zal er een code inzitten (1 kans op 50).

### Rewards:
Je krijgt een kwart pizza naar keuze gratis! (eenmalig)
