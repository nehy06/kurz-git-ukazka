# Git a GitHub: pořadí příkazů

Dvě cesty, jak dostat projekt do počítače a na GitHub, a každodenní cyklus práce. Příkazy fungují v PowerShellu, Git Bash i v Terminálu na Macu.

Všechny jednotlivé příkazy z kurzu najdete v [tahak.md](tahak.md).

---

## Kterou cestu zvolit

| Situace | Cesta |
|---|---|
| Projekt mám **ve svém počítači** a chci ho dostat na GitHub | **A: git init → GitHub** |
| Projekt už **je na GitHubu** (můj, kolegy, nebo jsem ho tam právě založil(a)) a chci ho do počítače | **B: git clone** |
| Projekt už mám v počítači i na GitHubu a jen na něm pracuji | **C: každodenní cyklus** |

> [!TIP]
> **Jednou na počítači (před první cestou)**
>
> ```
> git config --global user.name "Jméno Příjmení"
> git config --global user.email "jmeno@pef.czu.cz"
> git config --global init.defaultBranch main
> ```
> E-mail stejný jako na GitHubu. Kontrola: `git config --global --list`.

---

## A: Začínám u sebe (git init) a napojím na GitHub

**V počítači**

1. Přejděte tam, kde mají být projekty, a založte složku projektu:
   ```
   cd ~/projekty
   mkdir muj-projekt
   cd muj-projekt
   ```
2. Zkontrolujte, kde jste: `pwd`. V cestě **nesmí** být OneDrive, iCloud ani Mobile Documents.
3. Z obyčejné složky udělejte repozitář: `git init`
4. Vytvořte nebo zkopírujte soubory (třeba README.md) a uložte první verzi:
   ```
   git status
   git add README.md
   git commit -m "Založen projekt"
   ```

**Na GitHubu**

5. Vpravo nahoře **+ → New repository** → název (ideálně stejný jako složka) → Private nebo Public.
6. **Nic nezaškrtávejte** (žádné README, .gitignore ani licenci). Repozitář musí být prázdný → Create repository.

**Zpět v terminálu**

7. Řekněte Gitu, kde je projekt na GitHubu (adresu zkopírujte ze stránky repozitáře):
   ```
   git remote add origin https://github.com/JMENO/muj-projekt.git
   ```
8. Kontrola adresy: `git remote -v`
9. Pojistka, aby se hlavní větev jmenovala main: `git branch -M main`
10. První nahrání: `git push -u origin main`
    `-u` si zapamatuje, kam nahráváte. Příště stačí jen `git push`.

**Pořadí v kostce:** `git init` → `git add` → `git commit` → (GitHub: prázdný repozitář) → `git remote add origin ADRESA` → `git push -u origin main`

---

## B: Projekt je na GitHubu a stáhnu si ho (git clone)

1. Přejděte do složky, **ve které** má projekt vzniknout (clone si vlastní složku vytvoří sám):
   ```
   cd ~/projekty
   pwd
   ```
   Nesmíte být uvnitř jiného repozitáře (jinak vznikne repozitář v repozitáři) ani v OneDrivu.
2. Stáhněte projekt i s celou historií (adresu najdete na GitHubu pod zeleným tlačítkem **Code**):
   ```
   git clone https://github.com/JMENO/muj-projekt.git
   ```
3. Vejděte do nové složky: `cd muj-projekt`
4. Podívejte se do historie: `git log --oneline`
5. Pracujte podle cesty C. Napojení na GitHub už je hotové: **žádné** `git init` ani `git remote add`.

**Pořadí v kostce:** `git clone ADRESA` → `cd složka` → pracuji → `git add` → `git commit` → `git push`

> [!NOTE]
> **Klonuji prázdný repozitář, který jsem právě založil(a)**
>
> Git ohlásí *You appear to have cloned an empty repository*. To je v pořádku. Vložte soubory, udělejte první commit a první nahrání proveďte s `-u`:
> ```
> git add README.md
> git commit -m "Založen projekt"
> git push -u origin main
> ```
> Tahle cesta je jednodušší než A: nemusíte psát `git init` ani `git remote add`.

> [!WARNING]
> **Do cizího repozitáře nahrát nemůžete**
>
> Clone funguje i u veřejných projektů jiných lidí, ale `git push` do nich bez práv neprojde. Svoje úpravy si ukládejte do vlastního repozitáře.

---

## C: Každodenní cyklus

| Krok | Příkaz | Proč |
|---|---|---|
| 1 | `git pull` | **Na začátku práce:** stáhnout změny z GitHubu (z jiného počítače, od kolegy, z webu) |
| 2 | (upravit soubory, uložit) | |
| 3 | `git status` | co se změnilo |
| 4 | `git diff` | co přesně se změnilo |
| 5 | `git add soubor` | dát změny do přípravny |
| 6 | `git commit -m "popisek"` | uložit verzi |
| 7 | `git push` | **Na konci práce:** nahrát verze na GitHub |

---

## Když něco nejde

| Hláška | Co se stalo | Řešení |
|---|---|---|
| `! [rejected] … (fetch first)` | Na GitHubu je něco, co u sebe nemáte (např. úprava na webu nebo z jiného počítače) | `git pull`, pak znovu `git push` |
| totéž hned při prvním `git push` (cesta A) | Při zakládání repozitáře na GitHubu bylo zaškrtnuté README | Nejjednodušší: repozitář na GitHubu smazat (Settings → Delete) a založit znovu prázdný |
| `refusing to merge unrelated histories` | Viz řádek výše: projekt v počítači a na GitHubu vznikly zvlášť | Stejně jako výše, nebo si domluvit [konzultaci](https://bookings.cloud.microsoft/book/book-PEFAI@czu.cz/?ismsaljsauthenabled) |
| `remote origin already exists` | Adresa už je nastavená | Opravit: `git remote set-url origin ADRESA` |
| `src refspec main does not match any` | Lokální větev se jmenuje master, nebo ještě není žádný commit | `git branch -M main`, případně nejdřív `git commit` |
| `Repository not found` | Překlep v adrese, nebo k repozitáři nemáte přístup | `git remote -v` a porovnat s adresou na GitHubu |
| `destination path … already exists` | Složka s tímto jménem už existuje | Klonovat jinam, nebo použít existující složku |
| `fatal: not a git repository` | Jste ve špatné složce | `pwd`, pak `cd` do složky projektu |

---

## HTTPS, nebo SSH adresa?

GitHub nabízí pod tlačítkem **Code** dvě adresy téhož repozitáře:

- **HTTPS** `https://github.com/JMENO/projekt.git`: přihlášení přes prohlížeč (Windows) nebo token či VS Code (Mac). Tuto používáme na kurzu.
- **SSH** `git@github.com:JMENO/projekt.git`: přihlášení SSH klíčem, pokud ho máte nastavený (bonus z kurzu).

Obě vedou do stejného repozitáře. Adresu lze kdykoli změnit příkazem `git remote set-url origin NOVÁ-ADRESA`.
