# PixelCat Games · Projecte Fase 2 (RA2)

Web estàtica del catàleg de la botiga de videojocs **PixelCat Games**, feta amb HTML5 semàntic i CSS3.

- **Autora:** Laia Carrillo
- **Mòdul:** 0373 · Llenguatges de marques
- **Resultat d'aprenentatge:** RA2, publicació web del catàleg

Totes les dades de la botiga i dels jocs surten del fitxer `cataleg.xml` de la Fase 1, copiades tal com hi estan escrites. Aquesta web serà la base per afegir-hi interactivitat amb JavaScript a RA3.

## Com veure-la

1. Descomprimeix el `.zip`.
2. Obre `index.html` amb el navegador.

No cal servidor ni connexió a internet: totes les rutes són relatives i les tipografies són locals.

## Estructura

```
RA2_Projecte_Fase_2_botiga_Laia_Carrillo/
├── index.html      Catàleg amb una targeta per a cada joc (8)
├── fitxa.html      Fitxa de Kingdoms of Eldoria
├── contacte.html   Formulari de contacte
├── css/
│   ├── estils.css  Full d'estils únic
│   └── fonts/      Tipografies Jersey 10 i Atkinson Hyperlegible
├── img/            Portades dels jocs, logotip i pòster del tràiler
└── media/          Tràiler en vídeo (WebM i MP4)
```

## Pàgines

| Pàgina | Contingut |
| --- | --- |
| `index.html` | Portada amb les dades de la botiga, 8 targetes (`article`) i un `aside` amb destacats calculats del XML |
| `fitxa.html` | Totes les dades del joc, tràiler en vídeo, llista de definicions i taula d'estoc |
| `contacte.html` | Formulari amb camps de diversos tipus i les dades de la botiga del XML |

## Dades del XML que es mostren

- **Botiga:** nom, moneda i data de l'última actualització.
- **Cada joc:** codi, títol, gèneres, plataformes, preu, valoració, estoc per plataforma, data de sortida i descripció.

## Part HTML

- **Capçalera de cada document:** `<!DOCTYPE html>`, `lang="ca"`, `charset`, `viewport`, `<title>` i `meta description`.
- **Elements semàntics:** `header`, `nav`, `main`, `section`, `article`, `aside` i `footer`, amb un sol `h1` per pàgina i una jerarquia de títols coherent.
- **Llistes:** menú (`ul`), rànquing (`ol`), ruta de navegació i llistes de definicions (`dl`).
- **Format de text amb sentit:** `strong`, `em`, `abbr`, `code`, `time`, `data` i `small`.
- **Enllaços:** interns entre pàgines i a ancoratges (`#joc-003`) i externs (PEGI i tipografies).
- **Taula:** a la fitxa, amb `caption`, `thead`, `tbody`, `tfoot` i `scope` a les capçaleres.
- **Multimèdia:** `video` amb dues fonts (WebM i MP4), pòster i text alternatiu.
- **Formulari:**
  - camps de tipus text, email, tel, number, date, select, radio, checkbox i textarea;
  - una `label` per a cada camp;
  - camps obligatoris (`required`);
  - botons d'enviar i esborrar.

## Part CSS

- **Un únic full extern:** `css/estils.css`, enllaçat des de les tres pàgines, sense cap estil en línia.
- **Selectors:** d'element, de classe, d'id, descendent, fill (`>`), germà adjacent (`+`), d'atribut, pseudoclasses (`:hover`, `:focus-visible`, `:nth-child`, `:not()`, `:user-invalid`) i pseudoelements (`::before`, `::after`, `::marker`).
- **Model de caixa:** `box-sizing: border-box`, marges, farcits i vores controlats.
- **Unitats relatives:** `rem`, `em`, `%`, `fr`, `vw` i `ch`. No hi ha cap `px` fora dels comentaris.
- **Flexbox:** al menú, a la capçalera i a l'interior de les targetes.
- **Grid:** a la quadrícula de targetes, a la fitxa i al formulari.
- **Disseny adaptable:** pensat primer per a mòbil, amb media queries a 40rem, 48rem i 64rem.
- **Identitat visual:** paleta i tipografies definides com a variables a `:root` i aplicades a totes les pàgines.

### Cas d'especificitat

El peu de cada targeta ha d'ocupar tota l'amplada, però la regla `.targeta-joc > :not(img)` li posa marges laterals.

| Selector | Especificitat |
| --- | --- |
| `.targeta-joc > :not(img)` | (0,1,1) |
| `.targeta-joc__peu` | (0,1,0) |
| `.targeta-joc > .targeta-joc__peu` | (0,2,0) |

`.targeta-joc__peu` té menys especificitat, i per això no pot treure els marges encara que estigui escrita després. Cal fer servir `.targeta-joc > .targeta-joc__peu`, que sí que guanya.

Al menú hi ha un cas de cascada per ordre. `.menu a:hover` i `.menu a.actiu` tenen la mateixa especificitat, així que guanya la que està escrita més avall.

Tots dos casos estan comentats dins de `estils.css`.

## Preparat per a RA3

Cada targeta té un `id` únic (`joc-001` … `joc-008`) i atributs de dades:

```html
<article class="targeta-joc" id="joc-003" data-codi="JOC-003" data-preu="49.99"
         data-valoracio="9.4" data-sortida="2025-06-10" data-estoc="15">
```

Els elements importants també tenen `id` i classes coherents perquè es puguin seleccionar amb JavaScript, com `#llista-jocs`, `#formulari-contacte` o `#taula-estoc`.

## Restriccions

- Sense JavaScript.
- Sense frameworks CSS.
- Sense caràtules oficials.

## Crèdits

- **Imatges, logotip, tràiler i música:** creació original per a aquest projecte.
- **Tipografies:** [Jersey 10](https://fonts.google.com/specimen/Jersey+10) i [Atkinson Hyperlegible](https://fonts.google.com/specimen/Atkinson+Hyperlegible), amb llicència SIL Open Font License.
