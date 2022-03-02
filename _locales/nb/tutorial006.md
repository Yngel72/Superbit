### @activities true

# Superbit del 6: Koble elektronikk til Micro:Biten, del 2 Neopixel
## Introduksjon
### Introduksjon @unplugged

NeoPixels er RGB-LED-pærer som kan programmeres til å lyse i alle regnbuens farger.
Om man kobler flere av dem sammen kan man lage et uendelig antall morsomme mønstre.
Hver NeoPixel består av en RGB LED og en liten chip som leser koden som sendes gjennom NeoPixelen.
NeoPixler er såkalt adresserbare LEDs.
Det betyr i prinsippet at koden du lager forteller første NeoPixel at den er nummer en, nummer to får vite at den er nummer to osv.
Dette gjør at du kan bestemme farge, lysstyrke og om den skal være av eller på eller blinke for hver enkelt NeoPixel.
NeoPixel har egne blokker som krever en egen utvidelse for MakeCode.
Det første du skal lære her er å legge til utvidelsen for NeoPixel

### Legge til utvidelse @unplugged

NeoPixel-menyen du skal bruke i denne gjennomgangen er ikke en del av grunnmenyen i MakeCode, men en utvidelse som må legges til manuelt.
Det går dessverre ikke an å legge til pakker i denne typen steg-for-steg gjennomgang, men her er en forklaring på hvordan det gjøres i alle fall:
Utvidelser legges til fra blokkmenyen i midten av skjermen.
Aller nederst i **"Avansert"**-menyen vil du kunne se en egen, lysegrå underkategori som heter **"Utvidelser"**.
Om du klikker på den, kommer du til siden der du finner utvidelsene som finnes til MakeCode.
Bla deg gjennom utvidelsene på siden eller søk etter NeoPixel i søkefeltet om du ikke ser utvidelsen på siden.
Når du har funnet utvidelsen klikker du på den, og så er den lagt til for programmet du er i ferd med å lage.
Om du oppretter en ny MakeCode-økt, må du legge til utvidelser på nytt.
De krever litt plass og minne, så derfor lastes de kun inn ved behov.
Verre er det egentlig ikke å laste inn en utvidelse.

### Steg 1 Bruke NeoPixel med krokodilleklemmer 1

Før du går igang trenger du NeoPixelstripen.
Det er den ca 35 cm lange stripen med svart, hvit og rød ledning med krokodilleklemmer på.
NeoPixler trenger å kobles til 3 steder på Miro:Biten:
Plusspolen (rød ledning) kobles til 3V, minuspolen (svart ledning) kobles til GND og den siste ledningen (den midterste, hvit) kobles til en av utdatakontaktene på Micro:Biten, altså 0, 1 eller 2 når du bruker krokodilleklemmer.
Vi kobler den hvite klemmen til utgang 2 i eksempelkoden, fordi det er den nærmest utgangen til 3V og GND.
Når du har koblet opp neopixelstripen som forklart, går du videre.

![NeoPixelkobling](https://raw.githubusercontent.com/Yngel72/Superbit/master/static/NeoPixelkobling.jpg)

### Steg 2 Bruke neopixel med krokodilleklemmer 2

Til dette programmet trenger du aller først en ``||basic.ved start||``-blokk.
Fra ``||neopixel.NeoPixel||``-menyen trenger du en ``||variables.sett strip til||`` ``||neopixel.NeoPixel at p0 with 24 leds as RGB (GRB format)||``.
Dra den inn i ``||basic.ved start||``-blokken og endre ``||neopixel.24||`` til ``||neopixel.20||``, eller det antall NeoPixler du har på din stripe.
Det er 20 NeoPixels på stripen som følger med Superbit.

```blocks
// @highlight
let strip = neopixel.create(DigitalPin.P2, 20, NeoPixelMode.RGB)
```

### Forskjellige typer NeoPixels @unplugged

``||variables.sett strip til...||`` definerer NeoPixelstripen som en variabel med navn "strip".
Siden hver NeoPixelstripe er definert som en variabel kan man bruke mange NeoPixelstriper i samme program og få dem til å gjøre forskjellige ting.
Neopixler kan settes sammen i andre fasonger også. Ringer eller rektangler er populære former.
For at koden skal virke, må programmet vite hvor mange NeoPixler det er snakk om og hvilken type NeoPixler som sitter på NeoPixelstripen eller ringen eller uansett fasong.
På stripen som følger med Superbit er NeoPixlene av et format som kalles GRB, men det finnes andre formater.
Om du bruker en annen NeoPixelstripe og merker at fargene ikke stemmer, prøv å endre på NeoPixelformat-delen i denne blokken.

### Steg 3 Bruke neopixel med krokodilleklemmer 3

Nå skal du få NeoPixlene til å lyse i en bestemt farge. Der er 9 farger å velge mellom, pluss svart (av).
Til dette trenger du blokken ``||neopixel.strip show color red||`` fra ``||neopixel.NeoPixel||``-menyen.
Sett den inn i koden under ``||variables.sett strip til||``-blokken.
Nå kan du laste programmet opp til Micro:Biten og se hva som skjer.
Prøv å endre farge i ``||neopixel.strip show color red||``-blokken og se om fargen som lyser stemmer med den du har lagt inn når du laster opp programmet til Micro:Biten.

```blocks
let strip = neopixel.create(DigitalPin.P2, 20, NeoPixelMode.RGB)
// @highlight
strip.showColor(neopixel.colors(NeoPixelColors.Red))
```

### Nullstille NeoPixler @unplugged

Hver NeoPixel har en liten chip som tar imot instruksjoner fra koden.
Siden hver NeoPixel har sin egen adresse, leser den kun koden som gjelder sin adresse og ignorer resten.
Akkurat nå er hver NeoPixel instruert til å lyse med den siste fargen du gav dem i forrige steg.
I neste steg skal du få én NeoPixel på stripa til å lyse med én bestemt farge.
For å få til dette må du først slukke alle NeoPixlene, slik at den du vil skal lyse er den eneste som lyser.
En enkel måte å slukke en NeoPixel på er å be den vise fargen svart.
En svart NeoPixel er en slukket NeoPixel.

### Steg 4 Bruke neopixel med krokodilleklemmer 4

Nå skal du slå på en bestemt NeoPixel med en bestemt farge.
Du må aller først få NeoPixlene som ikke skal lyse til å slukke, ellers kommer de til å lyse med den fargen du sist programmerte dem med.
Sett fargen til ``||neopixel.black||`` i ``||neopixel.strip show color||``-blokken som allerede ligger i ``||basic.ved start||``-blokken.
Nå har du slått av alle NeoPixlene i stripa.

```blocks
let strip = neopixel.create(DigitalPin.P2, 20, NeoPixelMode.RGB)
// @highlight
strip.showColor(neopixel.colors(NeoPixelColors.Black))
```

### Steg 5 Bruke neopixel med krokodilleklemmer 5

Nå må du klikke på``||neopixel. ...Mer||`` under ``||neopixel.NeoPixel||``-menyen og hente blokken ``||neopixel.set pixel color at 0 to red||``.
Sett denne blokken inn nederst i ``||basic.ved start||``-blokken og velg deg en farge.
Rød er standardfargren når du henter blokka.
Skriv inn et tall i det hvite feltet på blokka.
Tallet kan være fra og med 0 til og med 19, til sammen 20 mulige valg.
NeoPixelen nærmest Micro:Biten har adressen 0, den siste i stripa har adressen 19.
NeoPixel 4, som vist i eksempelkoden, er den femte NeoPixelen fra Micro:Biten.

```blocks
let strip = neopixel.create(DigitalPin.P2, 20, NeoPixelMode.RGB)
strip.showColor(neopixel.colors(NeoPixelColors.Black))
// @highlight
strip.setPixelColor(4, neopixel.colors(NeoPixelColors.Red))
```

### Set color og show @unplugged

Om du laster opp koden slik den er nå, vil ingen av NeoPixlene lyse.
Det er slik at det er forskjell på å sette fargen til en NeoPixel og å få den til å lyse i den angitte fargen.
``||neopixel.Set color||`` bestemmer fargen uten å slå på NeoPixler.
``||neopixel.Show||`` slår pixler på, og får dem til å lyse i den fargen de har fått angitt.
Dersom en blokk inneholder ordet **"show"** er det ganske sikkert at blokken både setter farger og slår på NeoPixlene.

### Steg 6 Bruke neopixel med krokodilleklemmer 6

For å slå på NeoPixelen din, trenger du blokken ``||neopixel.strip show||``, som ikke må forveksles med ``||neopixel.strip show color||``.
Dra blokken ``||neopixel.strip show||`` fra ``||neopixel.NeoPixel||``-menyen inn nederst i ``||basic.ved start||``-blokken.
Nå kan du laste opp programmet til Micro:Biten og se hvilken NeoPixel som lyser.

```blocks
let strip = neopixel.create(DigitalPin.P2, 20, NeoPixelMode.RGB)
strip.showColor(neopixel.colors(NeoPixelColors.Black))
strip.setPixelColor(4, neopixel.colors(NeoPixelColors.Red))
// @highlight
strip.show()
```

### Steg 7 Bruke neopixel med krokodilleklemmer 7

Du kan nå kopiere blokken ``||neopixel.set pixel color at 0 to red||`` noen ganger og velge andre NeoPixler og farger.
Endre adressene til NeoPixlene du vil slå på ved å sette inn tall mellom 0 og 19, i de hvite feltene og farger ved å velge fra rullegardinmenyen.

```blocks
let strip = neopixel.create(DigitalPin.P2, 20, NeoPixelMode.RGB)
strip.showColor(neopixel.colors(NeoPixelColors.Black))
// @highlight
strip.setPixelColor(4, neopixel.colors(NeoPixelColors.Red))
strip.setPixelColor(9, neopixel.colors(NeoPixelColors.Yellow))
strip.setPixelColor(14, neopixel.colors(NeoPixelColors.Violet))
strip.setPixelColor(19, neopixel.colors(NeoPixelColors.Green))
strip.show()
```

### Steg 8 Bruke neopixel med krokodilleklemmer 8

Nå skal du animere NeoPixelstripen din.
Animasjonen må kjøre i en ``||basic.gjenta for alltid||``-blokk.
Nå trenger du blokken ``||neopixel.strip rotate pixels by 1||`` fra ``||neopixel.NeoPixel||``-menyen.
Denne blokken forteller pixlene at de skal flytte fargen sin en adresse opp i stripa helt til de kommer til enden, og så skal de starte på 0 igjen.
Endringene vises ikke før du kaller på ``||neopixel.strip show||`` igjen, så hent ``||neopixel.strip show||``-blokken fra ``||neopixel.NeoPixel||``-menyen.
For at ikke animasjonen skal gå for fort må du legge inn en liten pause mellom hver rotasjon, så hent en ``||basic.pause 100 ms||`` fra ``||basic.Basis||``-menyen og sett den inn nederst i ``||basic.gjenta for alltid||``-blokken.

```blocks
let strip = neopixel.create(DigitalPin.P2, 20, NeoPixelMode.RGB)
strip.showColor(neopixel.colors(NeoPixelColors.Black))
strip.setPixelColor(4, neopixel.colors(NeoPixelColors.Red))
strip.setPixelColor(9, neopixel.colors(NeoPixelColors.Yellow))
strip.setPixelColor(14, neopixel.colors(NeoPixelColors.Violet))
strip.setPixelColor(19, neopixel.colors(NeoPixelColors.Green))
strip.show()
// @highlight
basic.forever(function () {
    strip.rotate(1)
    strip.show()
    basic.pause(100)
})
```

### Forskjellen på shift pixels og rotate pixels @unplugged

Du la kanskje merke til at det lå en animasjonsblokk til rett over ``||neopixel.strip rotate pixels by 1||``?
``||neopixel.strip shift pixels by 1||`` gjør nesten det samme som ``||neopixel.strip rotate pixels by 1||``, men starter ikke på 0 igjen når bevegelsen når enden.
Dermed slutter animasjonen når siste animerte pixel når enden av stripa.
Denne animasjonen kan være kul i mange tilfeller, men passer ikke for animasjoner som skal gå for alltid.
Om du setter inn et negativt tall i det hvite feltet, endrer animasjonen retning.

### Steg 9 Bruke neopixel med krokodilleklemmer 9

Du kan også lage dine helt egen fargekombinasjoner for hver enkelt NeoPixel.
Hent den ovale blokken ``||neopixel.red 255 green 255 blue 255||`` fra nederst på ``||neopixel.NeoPixel/...mer||``-menyen.
Erstatt fargene i ``||neopixel.set pixel color at 0 to [farge]||``-blokkene dine med ``||neopixel.red 255 green 255 blue 255||``-ovaler.
Tallene 0-255 bestemmer hvor kraftig hver enkelt av de tre fargene LEDene i hver NeoPixel skal lyse.
Kombinasjonen 255-0-0 vil gi rødt, 0-255-0 gir grønt, 0-0-255 gir blått. Kombinasjonen 100-248-39 gir... Øh... En eller annen farge.
Det blir noe sånt som 16,8 millioner mulige farger man kan lage selv ved å blande fargene på denne måten.
Når det står 255 i alle de tre feltene, vil pixelen lyse hvitt.
Prøv litt forskjellige tallkombinasjoner i de forskjellige blokkene og test resultatet ved å laste opp koden til Micro:Biten.

```blocks
let strip = neopixel.create(DigitalPin.P2, 20, NeoPixelMode.RGB)
strip.showColor(neopixel.colors(NeoPixelColors.Black))
// @highlight
strip.setPixelColor(4, neopixel.rgb(0, 255, 255))
strip.setPixelColor(9, neopixel.rgb(255, 0, 255))
strip.setPixelColor(14, neopixel.rgb(255, 255, 0))
strip.setPixelColor(19, neopixel.rgb(0, 255, 0))
strip.show()
basic.forever(function () {
    strip.rotate(1)
    strip.show()
    basic.pause(100)
})
```

### Steg 10 Bruke neopixel med krokodilleklemmer 10

Nå skal du bruke en av de ferdige fargefunksjonene som finnes for NeoPixel.
I dette steget skal du animere en regnbue.
Fjern alle ``||neopixel.set pixel color at 0 to [farge]||`` fra ``||basic.ved start||``-blokken din.
Fjern også ``||neopixel.set strip show color black||``-blokken.
Hent blokken ``||neopixel.strip show rainbow from 0 to 360||`` fra ``||neopixel.NeoPixel||``-menyen og sett den inn mellom ``||variables.sett strip til||``-blokken og ``||neopixel.strip show||``-blokken.
La ``||basic.gjenta for alltid||``-blokken være som den er.
Last ned programmet til Micro:Biten og se på lysshowet.

```blocks
let strip = neopixel.create(DigitalPin.P2, 20, NeoPixelMode.RGB)
// @highlight
strip.showRainbow(1, 360)
strip.show()
basic.forever(function () {
    strip.rotate(1)
    strip.show()
    basic.pause(100)
})
```

### Mer om regnbuefunksjonen @unplugged

NeoPixelregnbuen går fra 0 til 360, med jevn fargeendring mellom pixlene i 360 trinn.
Blokken ``||neopixel.strip show rainbow from 0 to 360||`` viser alle fargene i regnbuen.
Om du velger andre tall, for eksempel ``||neopixel.strip show rainbow from 90 to 270||``, vil Micro:Biten bare vise en del av fargene i regnbuen.
Eksemplet 90 til 270 viser fargene mellom grønt og fiolett.

### Steg 11 Bruke neopixel med krokodilleklemmer 11

Nå skal du få regnbuen til å gå fram og tilbake på NeoPixelstripa.
Til det trenger du en ``||loops.gjenta 4 ganger||``-blokk fra ``||loops.Løkker||``-menyen.
Dra ``||loops.gjenta 4 ganger||``-blokken inn i ``||basic.gjenta for alltid||``-blokken.
Endre ``||loops.gjenta 4 ganger||`` til ``||loops.gjenta 20 ganger||``

```blocks
let strip = neopixel.create(DigitalPin.P2, 20, NeoPixelMode.RGB)
strip.showRainbow(0, 360)
strip.show()
basic.forever(function () {
    // @highlight
    for (let index = 0; index < 20; index++) {
    	
    }
    strip.rotate(1)
    strip.show()
    basic.pause(100)
})

```

### Steg 12 Bruke neopixel med krokodilleklemmer 12

Flytt de andre kodeblokkene i ``||basic.gjenta for alltid||``-blokken inn i ``||loops.gjenta 20 ganger||``-blokken.

```blocks
let strip = neopixel.create(DigitalPin.P2, 20, NeoPixelMode.RGB)
strip.showRainbow(0, 360)
strip.show()
basic.forever(function () {
    // @highlight
    for (let index = 0; index < 20; index++) {
        strip.rotate(1)
        strip.show()
        basic.pause(100)
    }
})
```

### Steg 13 Bruke neopixel med krokodilleklemmer 13

Kopier hele ``||loops.gjenta 20 ganger||``-blokken.
Endre ``||neopixel.strip rotate pixels by 1||`` til ``||neopixel.strip rotate pixels by -1||`` i den ene blokken.
Nå har du en regnbuescanner som kjører regnbuen fram og tilbake. Last ned til Micro:Biten og test!

```blocks
let strip = neopixel.create(DigitalPin.P2, 20, NeoPixelMode.RGB)
strip.showRainbow(0, 360)
strip.show()
basic.forever(function () {
    for (let index = 0; index < 20; index++) {
        strip.rotate(1)
        strip.show()
        basic.pause(100)
    }
    // @highlight
    for (let index = 0; index < 20; index++) {
        strip.rotate(-1)
        strip.show()
        basic.pause(100)
    }
})
```

### Steg 14 Bruke neopixel med krokodilleklemmer 14

Nå skal du bruke akselerometeret som inndata for NeoPixelstripa.
Da må du først fjerne kode til du bare har ``||basic.ved start||``, ``||variables.sett strip til||`` ``||neopixel.NeoPixel at p0 with 24 leds as RGB (GRB format)||`` og ``||basic.gjenta for alltid||`` igjen.

```blocks
// @highlight
let strip = neopixel.create(DigitalPin.P2, 20, NeoPixelMode.RGB)
basic.forever(function () {
	
})
```

### Steg 15 Bruke neopixel med krokodilleklemmer 15

Hent en ``||neopixel.strip show bargraph of 0 up to 255||`` fra ``||neopixel.NeoPixel||``-menyen.
Plasser den nye blokken i ``||basic.gjenta for alltid||``.

```blocks
let strip = neopixel.create(DigitalPin.P2, 20, NeoPixelMode.RGB)
basic.forever(function () {
    // @highlight
    strip.showBarGraph(0, 255)
})
```

### Steg 16 Bruke neopixel med krokodilleklemmer 16

Hent en oval ``||input.akselerasjon (mG) X||``-blokk fra ``||input.Inndata||``-menyen og plasser den i det hvite feltet der det står 0 i ``||input.akselerasjon (mG) X||``-blokken.

```blocks
let strip = neopixel.create(DigitalPin.P2, input.acceleration(Dimension.X), NeoPixelMode.RGB)
basic.forever(function () {
    // @highlight
    strip.showBarGraph(input.acceleration(Dimension.X), 255)
})
```

### Steg 17 Bruke neopixel med krokodilleklemmer 17

Endre tallet 255 i ``||neopixel.strip show bargraph of 0 up to 255||``-blokken til 1000.
Dette tallet viser hvor mye tyngdekraften påvirker akselerometeret i X-retningen (Sidelengs).
Når Micro:Biten står på høykant vil påvirkningen være 1000 mG, altså 1 G, derfor passer det å sette inn 1000 her.
Så lenge Micro:Biten ikke står på høykant vil gravitasjonspåvirkningen være mindre enn 1 G i X-retningen av planet Micro:Biten utgjør.

```blocks
let strip = neopixel.create(DigitalPin.P2, input.acceleration(Dimension.X), NeoPixelMode.RGB)
basic.forever(function () {
    // @highlight
    strip.showBarGraph(input.acceleration(Dimension.X), 1000)
})
```



### Avrunding @unplugged

Det var en kjapp gjennomgang av noen triks du kan gjøre med NeoPixels.
Som du sikkert skjønner finnes mye mer du kan gjøre med dem som du kan utforske på egen hånd.



```package
neopixel=github:microsoft/pxt-neopixel
```

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>