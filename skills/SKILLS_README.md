# XLAB Claude Skills — Prirucka

Aktualni verze XLAB skills pro Claude AI. Kazdy skill je Markdown soubor, ktery nahrajete do Claude.ai Projectu nebo pouzijete v Claude Code.

**Posledni aktualizace:** 2026-05-06
**Source of truth:** [GitHub — XLAB_OFFICE_AUTOMATION](https://github.com/jtrjtrjtr/XLAB_OFFICE_AUTOMATION/tree/main/skills)

---

## Prehled skills

| Skill | Ucel | Kdy pouzit |
|-------|------|------------|
| **xlab-brand** | Vizualni identita XLAB | Cokoliv s XLAB brandem — barvy, fonty, logo, layouty |
| **xlab-content** | Hlas znacky + portfolio | Psani textu pro XLAB — web, nabidky, emaily, PR |
| **xlab-events** | Eventova produkce | Poptavky, RFP, briefingy, koncepty eventu |
| **xlab-pricing** | Kalkulace a cenotvorba | Cenove nabidky, kalkulace, rozpocty |
| **xlab-proposal** | Klientske nabidky (PPTX) | Nabidky, pitch decky, klientske prezentace |
| **xlab-social** | Socialni site | Posty na Instagram a LinkedIn |
| **xlab-pptx-template** | PowerPoint sablona | Interni prezentace v XLAB stylu |

---

## Detailni popis

### xlab-brand
**Co dela:** Aplikuje oficialni XLAB brand identitu na vsechny vystupy — prezentace, dokumenty, HTML stranky, socialni site.

**Obsahuje:**
- Barevna paleta (Black #000000, White #F8F7F2, Neon Yellow #E3E829)
- Typografie (GT America / Arial)
- Pravidla pro X symbol (pomer 1.6:1, umisteni vpravo dole)
- Dark theme a White theme varianty
- Layout pravidla pro PPTX, DOCX, HTML
- Zakazane postupy (zadne gradienty, zadne efekty na logu)

**Jak pouzit:** Aktivuje se automaticky pri tvorbe XLAB materialu. Staci rici "Udelej prezentaci pro XLAB" nebo "Vytvor webovou stranku v XLAB stylu".

---

### xlab-content
**Co dela:** Kompletni znalostni baze pro XLAB komunikaci — hlas znacky, pravidla tonu, zakazane fraze, a detailni popisy vsech produktovych oblasti.

**Obsahuje:**
- Komunikacni rezim (profesionalni) vs kreativni rezim (konceptualni)
- Pravidla hlasu: klidny, vecny, zadne superlativy, zadne vykricniky
- Zakazane fraze a marketingove klise
- Portfolio v cestine i anglictine (6 produktovych oblasti)
- Pravidla pro preklad CZ <-> EN

**Jak pouzit:** "Napis text na web o nasich sluzbach", "Priprav popis projektu pro klienta", "Zkontroluj, jestli text odpovida XLAB hlasu". Vzdy kombinujte s xlab-brand.

---

### xlab-events
**Co dela:** Orchestrator pro kompletni zivotni cyklus eventove nabidky — od prijeti brifu pres kreativni koncept az po finalni deliverables.

**Obsahuje:**
- Intake checklist pro analyzu brifu
- Typy eventu (konference, brand activation, imerzivni instalace...)
- Dramaturgicky framework
- Engagement architektura
- Referencni projekty XLAB
- Sablona pro tvorbu nabidek

**Jak pouzit:** "Prisla poptavka na event, tady je brief", "Vytvor koncept pro firemni konferenci", "Analyzuj tenhle brief a priprav brief card". Automaticky koordinuje xlab-pricing, xlab-proposal, xlab-content a xlab-brand.

**Zavislosti:** Pouziva xlab-pricing (kalkulace), xlab-proposal (PPTX), xlab-content (texty), xlab-brand (vizual).

---

### xlab-pricing
**Co dela:** Generuje profesionalni cenove kalkulace jako brandovane Excel soubory.

**Obsahuje:**
- Dva rezimy: Standard (z centralniho ceniku) a Freeform (vlastni ceny)
- Eventove kalkulace (s dennimi sazbami)
- Stale instalace (s backup komponentami)
- Kreativni projekty (set-based pricing)
- Branded Excel vystup (listy Kalkulace + Summary)

**Jak pouzit:** "Naceni event pro 500 lidi", "Kolik by stala projekcni instalace?", "Priprav kalkulaci pro konferenci". Rekni "kalkulace", "cenova nabidka", "pricing", "budget".

---

### xlab-proposal
**Co dela:** Generuje klientske nabidky jako brandovane PPTX prezentace.

**Obsahuje:**
- Kombinace cover/closing slidu ze sablony + generovane obsahove slidy
- Profesionalni layout s XLAB brandem
- Podpora pro scope, timeline, pricing, team slides

**Jak pouzit:** "Vytvor nabidku pro klienta X", "Priprav pitch deck pro projekt Y", "Udelej offer prezentaci". Potrebuje informace o projektu — scope, rozpocet, timeline.

**Zavislosti:** Vyzaduje xlab-brand a xlab-pptx-template.

---

### xlab-social
**Co dela:** Generuje pripraveny-k-publikaci obsah pro Instagram a LinkedIn XLAB.

**Obsahuje:**
- Dvojjazycne vystupy (CZ + EN vzdy spolecne)
- Captiony, navrhy textu na cover, vizualni smer
- Hashtagy
- Pravidla pro Instagram vs LinkedIn formaty
- Referencni guides pro obe platformy

**Jak pouzit:** "Priprav post o projektu X na Instagram a LinkedIn", "Napis caption k fotce z eventu", "Vytvor obsah na socialni site o nasem novem projektu".

**Zavislosti:** Pouziva xlab-content (hlas) a xlab-brand (vizual).

---

### xlab-pptx-template
**Co dela:** Poskytuje XLAB PowerPoint sablonu (XLAB_PPT_ALL.pptx) s brandovanymi layouty.

**Obsahuje:**
- Cover slide, content slides, section dividers, closing slide
- Vsechny layouty v XLAB stylu
- Sablonovy soubor pro dalsi skills

**Jak pouzit:** "Vytvor interni prezentaci v XLAB stylu", "Priprav slidy pro poradu". NEPOUZIVAT pro klientske nabidky (na to je xlab-proposal).

---

## Jak skills pouzivat

### V Claude.ai (web/app)
1. Vytvorte si Project "XLAB"
2. Stahnete prislusny .md soubor z teto slozky (nebo z SharePointu)
3. Vlozte obsah do Project Instructions
4. Pracujte uvnitr projektu — skills se aktivuji automaticky

### V Claude Code (CLI/desktop)
1. Naklonujte repo: `git clone --recurse-submodules https://github.com/jtrjtrjtr/claude-team-config.git`
2. Spustte Claude Code v tom adresari
3. Skills se nactou automaticky z `.claude/skills/`

### Tipy
- Pro kompletni nabidku pouzijte **xlab-events** — ten orchestruje ostatni skills
- Pro rychly brand check pouzijte **xlab-brand** + **xlab-content** spolecne
- **xlab-pricing** funguje samostatne — nepotrebuje ostatni skills
- Vzdy specifikujte jazyk (CZ/EN), pokud chcete konkretni

---

## Mapa zavislosti

```
xlab-events (orchestrator)
  ├── xlab-pricing      (kalkulace)
  ├── xlab-proposal     (PPTX vystup)
  │     ├── xlab-brand        (vizual)
  │     └── xlab-pptx-template (sablona)
  ├── xlab-content      (texty, hlas)
  └── xlab-brand        (vizual)

xlab-social
  ├── xlab-content      (hlas)
  └── xlab-brand        (vizual)

xlab-pricing            (samostatny, bez zavislosti)
```

## Aktualizace

Skills se aktualizuji z [GitHub repa](https://github.com/jtrjtrjtr/XLAB_OFFICE_AUTOMATION). Pri zmene se novy soubor objevi na SharePointu v `1.6 X KNOWLEDGE BASE / 11_XLAB_CLAUDE / skills/`.
