# Jak upravovat obsah Agonia Wiki

Tento návod je určený pro členy týmu, kteří chtějí **upravovat obsah wiki** – tedy samotné texty, obrázky a strukturu článků.  
Nemusíš spouštět žádný vývojový server ani nic kompilovat – jen upravíš `.mdx` soubory a pošleš změny na GitHub.  
O zbytek (build, kontrolu, nasazení) se postará náš **privátní repozitář**, aby nebyl přístupný kód webu a nemohlo dojít k jeho úniku nebo poškození.

---

## 1. Co potřebuješ

1. **GitHub účet** – pro přístup k repozitářům.
2. **GitHub Desktop** – nejjednodušší nástroj pro klonování a posílání změn.  
   📥 [Stáhni z desktop.github.com](https://desktop.github.com/download/)
3. **Notepad++** nebo jiný textový editor – na úpravu `.mdx` souborů.  
   💻 [notepad-plus-plus.org/downloads](https://notepad-plus-plus.org/downloads/)
4. (Volitelné) **Git** – základní nástroj pro práci s repozitáři, ale GitHub Desktop ho nainstaluje automaticky.

> 💡 Pokud už něco z toho máš, tu část klidně přeskoč.

---

## 2. Kde upravovat soubory

Obsah wiki je uložený ve **veřejném repozitáři** na GitHubu, který slouží pouze pro texty a obrázky.  
Kód webu zůstává v **privátním repozitáři**, kde probíhá build a synchronizace.

### Postup

1. Otevři **GitHub Desktop**.  
2. Zvol **File → Clone repository... → URL**.  
3. Do pole vlož adresu veřejného repozitáře (např. `https://github.com/agonia/wiki-content`).  
4. Vyber, kam se má repozitář uložit (např. `C:\Users\ty\Documents\AgoniaWiki`).  
5. Potvrď **Clone**.  
6. Po dokončení klikni na **Open in Notepad++**, aby se otevřela složka s obsahem.

---

## 3. Struktura projektu

| Složka / soubor | Popis |
| ---------------- | ------ |
| `content/wiki` | Hlavní složka s články wiki. Každý `.mdx` soubor je jedna stránka. |
| `public` | Obrázky a ostatní statické soubory (např. `/images/mapa.png`). |
| `_meta.json` | Pomocné metadata pro menu a řazení článků. |

> 🛑 Nepotřebuješ nic z `src` nebo jiných technických částí projektu. Úprav se drž pouze ve `content/wiki` a `public`.

---

## 4. Jak upravit článek

1. Otevři v Průzkumníku složku `content/wiki`.
2. Najdi soubor, který chceš měnit (např. `getting-started.mdx`).
3. Dvojklikem ho otevři v **Notepad++**.
4. Nahoře uvidíš tzv. *frontmatter* – nastavení stránky:
   ```md
   ---
   title: První kroky
   description: Stručný úvod pro nové hráče serveru.
   ---
   ```
5. Pod ním je obsah v **Markdownu** nebo **MDX** formátu.
   - Nadpis: `## Kapitola`
   - Odrážky: `- položka`
   - Tučné: `**text**`
   - Komponenty: `<Callout>`, `<Steps>` apod.
6. Po úpravě dej **Ctrl+S** a soubor je uložený.

---

## 5. Přidání nové stránky

1. Najdi podobný článek (např. `getting-started.mdx`) a **zkopíruj ho**.  
2. Přejmenuj soubor – název určuje URL (např. `nove-tipy.mdx` → `/wiki/nove-tipy`).  
3. Otevři ho v Notepad++ a uprav `title`, `description` a obsah.  
4. Ulož změny.

> Menu se generuje automaticky podle názvů a složek, nemusíš nic přidávat ručně.

---

## 6. Wiki komponenty, které se dají použít

- **`<Callout>`** – zvýrazněné upozornění:
  ```mdx
  <Callout type="warning" title="Pozor">
    Nesahej na jiné složky než `content/wiki` a `public`.
  </Callout>
  ```
- **`<Steps>` + `<Step>`** – postup po krocích:
  ```mdx
  <Steps>
    <Step title="Otevři GitHub Desktop">
      Najdi repozitář wiki a otevři ho.
    </Step>
    <Step title="Uprav článek">
      V Notepad++ otevři `.mdx` soubor a proveď změny.
    </Step>
  </Steps>
  ```
- **`<Cards>` + `<Card>`** – dlaždice s odkazy:
  ```mdx
  <Cards>
    <Card title="Eventy" href="/wiki/eventy">
      Přehled všech akcí.
    </Card>
  </Cards>
  ```

---

## 7. Odeslání změn na GitHub

### GitHub Desktop

1. Po úpravách otevři **GitHub Desktop**.
2. Vlevo se zobrazí změněné soubory.
3. Napiš krátký popis (např. `Update wiki článku`) a klikni na **Commit to main**.
4. Poté stiskni **Push origin**, aby se změny odeslaly na GitHub.

### Terminál (alternativně)

```bash
git add content/wiki/tvuj-soubor.mdx
git commit -m "Update wiki článku"
git push
```

> 🔄 Privátní repozitář si pak změny automaticky stáhne a přebuilduje web.

---

## 8. Doporučení

- Před úpravami vždy dej **Fetch origin** (nebo `git pull`), aby ses vyhnul konfliktům.
- Upravuj pouze textový obsah, nikdy kód.
- Nové obrázky dávej do složky `public/images`.
- Udržuj konzistentní formátování (nadpisy, mezery, komponenty).

---

✅ Hotovo!  
Teď můžeš jednoduše upravovat obsah Agonia Wiki bez potřeby vývojového prostředí.  
Jakmile změny pushneš na GitHub, systém je automaticky přenese do privátního repozitáře, kde proběhne build a nasazení.



Oprav tohle 