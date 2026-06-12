# PPS2 vežbe — HTML prezentacije

Slajd-prezentacije za vežbe iz predmeta **Planiranje prostora i saobraćaja 2** (PPS2).
Biće ukupno ~10 vežbi; svaka se drži u terminu 2×45 min (prvi čas predavanje sa
primerom, drugi čas samostalni rad studenata na Postavci u Excel-u). Studenti
koriste sajt kao referencu kod kuće.

- **Live sajt:** https://nprikolic.github.io/PPS2-vezbe-html/ (GitHub Pages, auto-deploy sa `main`)
- **Repo:** https://github.com/nprikolic/PPS2-vezbe-html
- **Izvorni materijali** (PDF primeri, Excel postavke): `D:\My Drive\Nastava\PPS2\Vežba X\`

## Struktura

```
index.html        — početna strana sa spiskom vežbi (00, 01, …)
vezba-00.html     — uvodni čas: organizacija nastave (sadrži [dopuniti] placeholdere!)
vezba-01.html     — Vežba 1: vremenska i prostorna akumulacija
_template.html    — šablon za nove vežbe; sadrži sve komponente i drawChart()
program-vezbi.txt — zvaničan program: nazivi svih 10 vežbi, nedelje, časovi, bodovi
CLAUDE.md         — ovaj fajl
```

Nazivi, termini (nedelje) i bodovi svih vežbi su u `program-vezbi.txt` — index
već ima sve kartice (02–10 kao „uskoro"), a vežba 00 slajd „Program vežbi".
Elaborat ukupno nosi 40 poena.

Svaki deck je **samostalan HTML fajl** — bez eksternih zavisnosti (CSS/JS/QR inline),
radi offline. Ne uvoditi CDN biblioteke (MathJax, Chart.js…).

## Dodavanje nove vežbe

1. Kopirati `_template.html` → `vezba-XX.html`
2. Izmeniti `<title>`, naslovni slajd, sadržaj (šablon ima primere svih komponenti)
3. Na `index.html` zameniti jedan „uskoro" red pravom karticom (uzor: red 01)
4. Commit + push na `main` — Pages se sam ažurira

Tipičan redosled slajdova (videti `vezba-01.html` kao uzor): naslov → plan časa →
pojam → tamni divider po delovima → formule (kartice) → proračunska tabela →
dijagrami (SVG) → pokazatelji (metrics grid) → interpretacija → tamni slajd
„Samostalni rad" sa zadacima iz Postavke → koraci u Excel-u → rezime sa QR-om.

**Opisi na index strani (`.vdesc`) moraju biti kratki** — jedna rečenica koja
imenuje temu/primer (npr. „Garaža i linija javnog prevoza sa 12 stanica."),
bez nabrajanja formula i pokazatelja. Nedelja i bodovi idu u `.vmeta` red.

## Konvencije — JEZIK (obavezno)

- Srpski, **latinica**; specijalna slova kao HTML entiteti (`&scaron;`, `&ccaron;`, `&zcaron;`, `&cacute;`, `&dstrok;`)
- **Bez direktnog obraćanja studentima** — nikad „vam/vaš/dobijate/otvorite".
  Koristiti bezlične oblike („se dobija", „potrebno je", „treba da") ili treće lice
  („svaki student dobija"). Mi-forme („računamo", „brojimo") su dozvoljene.
- Bez školske godine/semestra na naslovnim slajdovima
- Decimalni zarez u rezultatima (5,10 h; 1,79), oznake kao u nastavnim materijalima
  (Qmax, Qsr, N, tsr, dsr, γrt, γrx)

## Konvencije — DIZAJN

Stil po uzoru na thariqs.github.io/html-effectiveness (09-slide-deck):
ivory/clay/slate paleta, scroll-snap slajdovi preko celog ekrana, serif naslovi,
mono eyebrow/anotacije. Tokeni su u `:root` svakog fajla.

- Boje dijagrama (poklapaju se sa Excel dijagramima studenata):
  **ulaz #3E6B9E** (plava), **izlaz #D9962E** (žuta), Q krive `--clay`,
  anotacije (Qmax, tsr, dsr strelice) `#C04B4B`, Qsr isprekidane linije `--olive`
- Dijagrami: SVG generisan iz nizova podataka pozivom `drawChart(id, opts)` —
  ne hardkodovati koordinate. Podržava linijske i stepenaste serije, anotacije
  (`h`/`v`/`arrow`/`txt`) i legendu.
- Formule: HTML/CSS (`.eq`, `.frac`, `.sum`) — bez MathJax-a
- Tabele: `.tbl` u `.tblwrap`; ključni rezultat (npr. Qmax red) označiti klasom `hl`
- Široki sadržaj (tabele/dijagrami): klasa `wide` na `<section class="slide">`
- QR kod (vodi na index, isti za sve vežbe): definisan jednom kao `<path id="qrcode">`
  u skrivenom `<defs>`, koristi se preko `<use href="#qrcode">` — mali u uglu
  naslovnog slajda + veći na završnom slajdu
- Navigacija: strelice/Space/PageUp/PageDown/Home/End (kliker radi), brojač slajdova

## Otvorena pitanja / TODO

- `vezba-00.html` ima **22 placeholder-a** `[dopuniti: …]` (klasa `.todo`, crveni
  chipovi): bodovi, prisustvo, termini kolokvijuma, kontakt. Kad se upišu stvarne
  vrednosti, ukloniti `<span class="todo">` omotače.

## Razno

- Lokalni pregled: launch config `pps2-vezbe` (python http.server, port 8741) u
  `C:\Users\A5U5\Documents\.claude\launch.json`
- Repo je na Google Drive-u — ako git prijavi lock greške, pauzirati Drive sync
- Štampa: Ctrl+P daje jedan slajd po strani (`@media print` postoji u svakom decku)
