# Azure-miljö från grunden – Novatrix AB

Kursrepo för Microsoft Azure där jag bygger upp en miljö åt det fiktiva företaget Novatrix AB vecka för vecka: från en Ubuntu-VM med Nginx till identiteter, nätverk, lagring, infrastruktur som kod, automatisering och serverless. Alla veckor bygger vidare på samma miljö, och varje vecka har en egen mapp med genomförande, dokumentation och skärmdumpar.

> Projekt inom utbildningen Moln- och virtualiseringsspecialist, Campus Mölndal.

**Teknik:** Azure · Ubuntu · Nginx · Entra ID · RBAC · VNet · NSG · Storage · Managed identity · ARM-templates · Bicep · Azure CLI · Power Automate · Microsoft 365 · Azure Functions · Containers

---

## Översikt

| Vecka | Tema | Nyckelteknik |
|:-----:|------|--------------|
| [**v34**](v34/README.md) | Virtuell maskin och webbserver | Ubuntu VM · Nginx |
| [**v35**](v35/README.md) | Entra ID och behörigheter | Entra ID · RBAC · Bicep |
| [**v36**](v36/README.md) | Nätverk och säkerhet | VNet · Subnät · NSG · Bicep |
| [**v37**](v37/README.md) | Lagring | Storage Account · Blob · Managed Identity |
| [**v38**](v38/README.md) | Infrastruktur som kod | ARM-mallar |
| [**v39**](v39/README.md) | Automation och integration | Power Automate · Microsoft 365 |
| [**v40**](v40/README.md) | VM, containers och serverless | Azure Functions · Container |

---

## Så hänger miljön ihop

[![Arkitekturkarta över hela Azure-miljön – från lokal dator och GitHub till VNet, identiteter, lagring och Power Automate](docs/arkitektur.png)](docs/arkitektur.png)

Kartan visar hela kedjan: från lokal dator och GitHub, via Entra ID, RBAC och det virtuella nätverket, in i lagringen och vidare ut till Power Automate och Microsoft 365. Klicka på bilden för att öppna den i full storlek.

---

## Veckor

<details open>
<summary><b>v34 — Virtuell maskin och webbserver</b></summary>

<br>

- [x] Kursrepo uppsatt med README
- [x] Ubuntu-VM utrullad i Azure
- [x] Nginx installerat och igång
- [x] Kundtjänstsida med ärendeformulär publicerad
- [x] Testat och dokumenterat

**[Läs dokumentationen för v34](v34)**

</details>

<details>
<summary><b>v35 — Entra ID och behörigheter</b></summary>

<br>

- [x] Veckoavsnitt tillagt i repot
- [x] Användare och grupper uppsatta i Entra ID
- [x] RBAC-roller tilldelade på resursgruppen enligt least privilege
- [x] Managed identity förberedd inför v37
- [x] Behörigheterna verifierade och dokumenterade

**[Läs dokumentationen för v35](v35/README.md)**

</details>

<details>
<summary><b>v36 — Nätverk och säkerhet</b></summary>

<br>

- [x] Veckoavsnitt tillagt i repot
- [x] VNet med publikt och privat subnät
- [x] Trafiken styrd med NSG-regler
- [x] Lösningen flyttad in i nätverket
- [x] Testat och dokumenterat

**[Läs dokumentationen för v36](v36/README.md)**

</details>

<details>
<summary><b>v37 — Lagring</b></summary>

<br>

- [x] Veckoavsnitt tillagt i repot
- [x] Storage account och blob-container skapade
- [x] Ärendeformuläret skriver till lagringen
- [x] Managed identity kopplad med minsta möjliga behörighet
- [x] Testat och dokumenterat

**[Läs dokumentationen för v37](v37/README.md)**

</details>

<details>
<summary><b>v38 — Infrastruktur som kod</b></summary>

<br>

- [x] Veckoavsnitt tillagt i repot
- [x] ARM-mallar för nätverk och lagring
- [x] Miljön utrullad från mallarna
- [x] Ändring gjord och synlig i historiken
- [x] Dokumenterat hur miljön byggs upp från noll

**[Läs dokumentationen för v38](v38/README.md)**

</details>

<details>
<summary><b>v39 — Automation och integration</b></summary>

<br>

- [x] Veckoavsnitt tillagt i repot
- [x] Power Automate-flöde som triggas av nytt ärende
- [x] Koppling mot Microsoft 365
- [x] Flödet ihopkopplat med Azure-lösningen
- [x] Hela kedjan testad och dokumenterad

**[Läs dokumentationen för v39](v39/README.md)**

</details>

<details>
<summary><b>v40 — VM, containers och serverless</b></summary>

<br>

- [x] Veckoavsnitt tillagt i repot
- [x] Paketera och kör en del av kundtjänsten som en container på Azure
- [x] Implementera mottagningen av ett ärende serverless med en Azure Function
- [x] Beskriv och jämför VM, containers och serverless
- [x] Hela kedjan testad och dokumenterad
- [x] För- och nackdelar för just en funktion som ärendemottagningen

**[Läs dokumentationen för v40](v40/README.md)**

</details>

---

## Struktur

```text
Azure-novatrix-mov25/
├── README.md
├── docs/              Arkitekturkarta
├── v34/               Virtuell maskin och webbserver
├── v35/               Entra ID och behörigheter
├── v36/               Nätverk och säkerhet
├── v37/               Lagring
├── v38/               Infrastruktur som kod
├── v39/               Automation och integration
└── v40/               VM, containers och serverless
```

Vill du följa arbetet kronologiskt? Börja i **v34** och läs vidare. Varje vecka förutsätter miljön som byggdes veckan innan.

---

## Vad jag lärde mig

**Hur en molnmiljö växer i lager.** Varje vecka byggde på den förra: först en server, sedan vem som får göra vad, sedan nätverket runt den, lagringen bakom och till sist automatisering. Ordningen gjorde det tydligt hur beroende delarna är av varandra.

**Att en regel inte gör något förrän den sitter på rätt ställe.** En NSG är bara en lista tills den kopplas till ett subnät, och en webbserver som svarar lokalt är inte nåbar förrän nätverket släpper igenom trafiken. Jag har lärt mig att alltid testa utifrån, inte bara på servern.

**Att identitet är säkrare än nycklar.** Med managed identity och RBAC kunde webbappen skriva till lagringen utan att något lösenord eller någon nyckel fanns i koden, och varje roll fick bara den behörighet den behövde.

**Att infrastruktur som kod gör miljön förutsägbar.** När nätverk och lagring beskrevs i ARM-mallar och Bicep gick det att bygga om miljön från noll och se varje ändring i historiken, i stället för att minnas vad jag klickat i portalen.

**Att välja tjänst efter behovet.** Jämförelsen mellan VM, containers och serverless visade att ärendemottagningen passar som en Azure Function: den används ojämnt, ska skala själv och kostar inget när ingen skickar in något.
