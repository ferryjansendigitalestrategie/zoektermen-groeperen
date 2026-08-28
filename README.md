# Zoektermen groeperen op wat Google werkelijk toont

Een Google Colab-notebook dat voor elke zoekterm de zoekresultaten ophaalt en daarmee
drie vragen beantwoordt.

1. **Welke zoektermen horen bij elkaar?** Zoektermen die dezelfde resultaten opleveren,
   beantwoordt Google met hetzelfde soort pagina. Die horen op één pagina.
2. **Welke onderdelen toont Google?** Een AI-overzicht, andere vragen, een videoblok,
   een kaart. Dat bepaalt hoeveel ruimte er voor een gewoon resultaat overblijft.
3. **Wie staat er het vaakst?** Welke domeinen nemen in jouw verzameling zoektermen de
   meeste ruimte in, gewogen naar positie.

Je krijgt drie dingen terug:

- **een Excel-werkblad** met je zoektermen gelabeld, en dat is het bestand waar je mee
  verder werkt
- **een PDF-rapport** om te lezen en door te sturen
- **drie CSV-bestanden** voor wie liever zelf rekent

De uitleg met de stappen staat op **[ferryjansen.nl/tools/zoektermen-groeperen/](https://ferryjansen.nl/tools/zoektermen-groeperen/)**.

## Beginnen

1. **[Open het notebook direct in Google Colab](https://colab.research.google.com/github/ferryjansendigitalestrategie/zoektermen-groeperen/blob/main/zoektermen-groeperen.ipynb)**.
   Je hoeft niets te downloaden. Wil je je eigen versie bewaren, kies dan in Colab
   *Kopie opslaan in Drive*.
2. Draai blok 1 om de benodigdheden te installeren.
3. Vul in blok 2 je inloggegevens van DataForSEO in. Dat doe je één keer.
4. Zet in blok 3 je zoektermen erin. Dat kan op twee manieren: plak ze in het blok,
   één per regel, of zet `UPLOADEN` op `True` en kies een CSV- of Excel-bestand,
   bijvoorbeeld een export uit Search Console.
5. Draai de rest van boven naar beneden.

Je hebt verder niets nodig. Geen installatie op je eigen computer, geen Google Cloud,
geen Search Console-koppeling.

## Wat het kost

Het ophalen van zoekresultaten loopt via [DataForSEO](https://dataforseo.com/) en dat
kost geld per zoekterm. Twintig zoektermen kwamen in een meting van augustus 2026 uit op
ongeveer zeven dollarcent. Je werkt daar met tegoed dat je vooraf opwaardeert, dus er
kan nooit een rekening ontstaan die je niet hebt zien aankomen.

Het notebook rekent vóór het ophalen uit wat een run ongeveer kost en stopt als dat boven
je eigen grens uitkomt. Die grens staat in blok 2 als `MAX_KOSTEN`.

## De instellingen die ertoe doen

| Instelling | Wat het doet |
|---|---|
| `TOP_N` | Hoeveel resultaten meetellen bij het vergelijken. Tien is de gangbare keuze |
| `SAMEN_VANAF` | Vanaf hoeveel gedeelde resultaten twee zoektermen hetzelfde onderwerp zijn. Drie van de tien is een goed startpunt |
| `VERWANT_VANAF` | De lagere drempel. Zoektermen die deze halen horen bij elkaar maar verdienen een eigen pagina |
| `LOCATIE_CODE` | 2528 is Nederland, 2056 is België, 2840 zijn de Verenigde Staten |
| `MAX_KOSTEN` | Je plafond in dollar. Hierboven stopt het notebook voordat het iets uitgeeft |

## Hoe het groepeert

Twee zoektermen horen bij elkaar als ze genoeg van dezelfde webadressen in hun
zoekresultaat hebben staan. Niet als hun woorden op elkaar lijken, want dat zegt weinig:
"marketing dashboard" en "marketing dashboard maken" schelen één woord en leverden in de
meting van augustus 2026 verschillende resultaten op.

Er zijn twee drempels. Boven de hoge drempel is het één onderwerp en dus één pagina.
Daartussenin is het dezelfde familie: verwante onderwerpen die elk een eigen pagina
verdienen en naar elkaar horen te linken.

De groepering is een keten, geen kliek. Hangt A aan B en B aan C, dan zitten ze in
dezelfde groep, ook als A en C elkaar niet raken. Dat is bewust, want zo werkt een
onderwerp.

## Wat het niet doet

- Het zegt niet welke zoekterm de belangrijkste is. Daar is zoekvolume of je eigen
  data voor nodig, en dat zit hier niet in
- Het schrijft geen content en geeft geen titeladvies
- Het kijkt niet naar je eigen site, alleen naar wat er in de zoekresultaten staat
- Voor één zoekterm heeft het geen zin. Dan kun je net zo goed zelf zoeken. De waarde
  ontstaat over tientallen zoektermen tegelijk

## Het werkblad

Zes tabbladen, waarvan het eerste een **Lees mij** is: wat het bestand is, wat het verschil
tussen een onderwerp en een familie is, hoe je de kolommen leest, met welke instellingen er
gemeten is, en wat het niet doet. Zo blijft het bestand te lezen als je het over twee maanden
weer opent of naar een collega stuurt. Daarna volgt de kern: elke zoekterm met zijn onderwerp, zijn familie en
in gewone taal wat dat betekent. De oranje regels zijn de onderwerpen waar meer dan één
zoekterm in zit, want daar valt de winst te halen.

De overige bladen zijn de onderwerpen op een rij, wat Google toont, welke domeinen er het
vaakst staan, en hoeveel resultaten elk paar zoektermen deelt zodat je de groepering zelf
kunt nakijken.

De kopbanden zijn donker met oranje accenten en de rest is licht. Een volledig donker
werkblad staat leuk maar is niet te gebruiken en drukt slecht af.

## Het rapport

De opmaak van het PDF-rapport zit in het notebook zelf. Er wordt geen sjabloon van een
website opgehaald, zodat het notebook blijft werken als die site verandert en je kunt
zien wat er gebeurt. Alleen de twee lettertypes komen van Google Fonts; lukt dat niet,
dan gebruikt het rapport een standaardletter en gaat de rest gewoon door.

## Meegeven

Doorsturen mag. Haal wel eerst je eigen inloggegevens uit blok 2 voordat je het notebook
deelt of opslaat in een openbare map.
