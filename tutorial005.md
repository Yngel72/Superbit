### @activities true

# Superbit del 5: Koble elektronikk til Micro:Biten, del 1
## Introduksjon
### Introduksjon @unplugged

Micro:Bit har mange inn- og utganger som gjør at vi kan koble den til forskjellige elektroniske komponenter.
Den kan brukes som en elektronisk hjerne som styrer motorer, lys eller lyd. Man kan faktisk bruke Micro:Bit som hjernen i en robot.
Men før vi gjør noe mer avansert, skal vi begynne helt enkelt.
Vi skal få Micro:Biten til å slå en LED-pære av og på.
Om du ser på Micro:Biten, ser du at den har metallstriper langs kanten under displayet.
5 av disse stripene er brede, med et hull i.
Mellom disse liggger det mange smalere striper.
De brede stripene med hull kan brukes med krokodilleklemmer.
Stripene som er merket 0, 1 og 2 er inn- og utganger for elektronikk.
3V er plusspolen for en 3V likespenningskilde (f.eks. 2 AA-batterier) og GND er minuspolen.
Du skal nå bruke disse brede metallstripene og krokodilleklemmer for å koble til en LED-pære.
Totalt vil du trenge 6 ledninger med krokodilleklemmer og 3 LED-pærer i tillegg til Micro:Bit og evt. batteripakke om du bruker iPad eller Android, eller USB-kabelen om du bruker PC.

### Få en LED til å blinke 1 @unplugged

Du trenger 2 ledninger med krokodilleklemmer i hver ende, en LED-pære og en Micro:Bit m. USB-ledning (Evt. batteripakke om du bruker iPad eller Android-brett) til gjennomgangen.
Før du starter kodingen:
Koble en ledning med krokodilleklemme til stripen der det står "0" på Micro:Biten.
Koble det lange benet til LED-pæren til andre enden av ledningen.
Koble det korte benet på LED-pæren til den andre ledningen med krokodilleklemme.
LED-pærene som følger med i Superbitsettet har innebygget motstand som beskytter dem mot for høy spenning fra Micro:Biten, derfor kan de kobles på direkte..
Pass på at krorkodilleklemmene på bena til LED-pæra ikke er i kontakt med hverandre.
Du kan bøye bena til LED-pæra forsiktig ut for å få større avstand.
Koble den andre enden av den siste ledningen til stripen der det står GND på Micro:Biten.
Koble Micro:Biten til PCen ved hjelp av USB-ledningen. (Koble til en batteripakke om du bruker iPad eller Android-brett)
Nå er koblingene klare.

### Steg 1 Få en LED til å blinke 1

Om du ikke har en ``||basic.gjenta for alltid||``-blokk i arbeidsområdet, hent en fra ``||basic.Basis||``-menyen.
``||pins.Tilkoblinger||`` finner du under **"Avansert"** i menyen. Hent en ``||pins.skriv digital til p0 verdi 0||``-blokk fra ``||pins.Tilkoblinger||``-menyen og dra den inn i ``||basic.gjenta for alltid||``-blokken.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 0)
})
```

### Steg 2 Få en LED til å blinke 2

Hent en ``||basic.pause||``-blokk fra ``||basic.Basis||``-menyen og legg den inn i ``||basic.gjenta for alltid||``-blokken under ``||pins.skriv digital til p0 verdi 0||``-blokken.
Endre tiden i ``||basic.pause||``-blokken til 500 ms.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 0)
    basic.pause(500)
})
```

### Steg 3 Få en LED til å blinke 3

Kopier ``||pins.skriv digital til p0 verdi||``-blokken og legg kopien inn under ``||basic.pause||``-blokken.
Endre verdien i det hvite feltet i ``||pins.skriv digital til p0 verdi 0||``-blokken fra 0 til 1.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 0)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P0, 1)
})
```

### Om digitale inn- og utdata @unplugged

Ordet "digital" betyr i denne sammenhengen at signalet til eller fra en tilkobling enten kan være av eller på.
Digitale signaler kan altså ikke ha varierende styrke, de er bare enten på eller av.
Når vi bruker blokken ``||pins.skriv digital til p0 verdi 0||``, kan verdien i det hvite feltet bare være 0 eller 1.
I denne blokken betegner "p0" en "pin" på Micro:Biten, mens verdien i det hvite feltet bestemmer om p0 skal sende signal eller ikke.
Om verdien er 0 går det ikke noe signal fra p0, og LED-pæra vil være slukket.
Er verdien 1 vil det gå et signal fra p0, og LED-pære vil være på helt til verdien settes til 0 igjen.
Med krokodilleklemmer er bare p0, p1 og p3 tilgjengelige på Micro:Biten.
For å få tilgang på alle inn- og utganger (pins) trenger man et såkalt "breakout board".
Til sammen har Micro:Bit 19 inn- og utganger du kan bruke dersom du har et breakout board.

### Steg 4 Få en LED til å blinke 4

Kopier ``||basic.pause||``-blokken og legg kopien inn under den siste ``||pins.skriv digital til p0 verdi 1||``-blokken.
Nå kan du laste opp programmet til Micro:Biten og se hva som skjer.
Hva skjer om du endrer verdiene på tiden?
Klarer du å lage et program som sender morsekoden for SOS? (Tre korte, tre lang, tre korte blink)

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 0)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.pause(500)
})
```

### Få 3 LED-pærer til å blinke @unplugged

Før du går videre trenger du 4 ledninger med krokodilleklemmer i hver ende og 2 LED-pærer.
Før du starter kodingen:
Koble en ledning med krokodilleklemme til stripen der det står "1" på Micro:Biten.
Koble det lange benet til en LED-pære til andre enden av ledningen.
Koble det korte benet på LED-pæren til den andre ledningen med krokodilleklemme.
Koble den andre enden av den siste ledningen til stripen der det står GND på Micro:Biten, eller til krokodilleklemmen som allerede er koblet til der etter forrige steg.
Koble en ledning med krokodilleklemme til stripen der det står "2" på Micro:Biten.
Koble det lange benet til en LED-pære til andre enden av ledningen.
Koble det korte benet på LED-pæren til den andre ledningen med krokodilleklemme.
Koble den andre enden av den siste ledningen til stripen der det står GND på Micro:Biten, eller til en av krokodilleklemmene som allerede er koblet på.
Koble Micro:Biten til PCen ved hjelp av USB-ledningen. (Koble til en batteripakke om du bruker iPad eller Android-brett)

### Steg 5 Få 3 LED-pærer til å blinke 1

