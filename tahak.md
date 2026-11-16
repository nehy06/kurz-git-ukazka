# Tahák: terminál a Git

Příkazy z kurzu B1 Příprava prostředí pro práci s AI agenty. Fungují v PowerShellu, Git Bash i v Terminálu na Macu, výjimky jsou označené.

přidaný řádek - podívejte se po pull co se změnilo

## Terminál

| Příkaz | Co dělá |
|---|---|
| `pwd` | kde jsem (vypíše cestu k aktuální složce) |
| `ls` | co je ve složce |
| `ls -Force  /  ls -a` | včetně skrytých souborů (PowerShell / Git Bash a Mac) |
| `cd název` | vejít do složky |
| `cd ..` | o úroveň výš |
| `cd ~` | do domovské složky |
| `cd + přetáhnout složku` | cestu nepsat, přetáhnout složku z Průzkumníku či Finderu do terminálu |
| `mkdir název` | vytvořit složku |
| `mv starý nový` | přejmenovat (nebo přesunout) |
| `start .  /  open .` | otevřít aktuální složku v Průzkumníku / Finderu |
| `code .` | otevřít aktuální složku ve VS Code |
| `clear` | vyčistit obrazovku terminálu |
| `Tab · šipka nahoru · Ctrl + C` | doplnit název · předchozí příkaz · zastavit |

## Git — jednou na počítači

| Příkaz | Co dělá |
|---|---|
| `git --version` | je Git nainstalovaný? |
| `git config --global user.name "Jméno"` | kdo jsem |
| `git config --global user.email "e-mail"` | můj e-mail (stejný jako na GitHubu) |
| `git config --global init.defaultBranch main` | hlavní větev se jmenuje main |

## Git — jednou na projekt

| Příkaz | Co dělá |
|---|---|
| `git init` | z obyčejné složky udělat repozitář |
| `git remote add origin ADRESA` | propojit s repozitářem na GitHubu |
| `git push -u origin main` | první nahrání |
| `git clone ADRESA` | stáhnout celý projekt z GitHubu i s historií (jednou; pak už git pull) |

## Git — pořád dokola

| Příkaz | Co dělá |
|---|---|
| `git pull` | stáhnout změny z GitHubu (na začátku práce) |
| `git status` | co je nového od poslední verze |
| `git diff` | co přesně se změnilo |
| `git add soubor` | dát soubor do přípravny |
| `git add .` | dát do přípravny všechny změny ve složce |
| `git commit -m "popisek"` | uložit verzi do historie |
| `git push` | nahrát verze na GitHub (na konci práce) |
| `git log --oneline` | historie verzí (q = konec výpisu) |
| `git restore soubor` | zahodit neuložené změny v souboru |

## Git — větve

| Příkaz | Co dělá |
|---|---|
| `git branch` | jaké mám větve (* = ta, ve které jsem) |
| `git switch -c název` | vytvořit novou větev a přepnout do ní |
| `git switch main` | vrátit se na hlavní větev |
| `git merge název` | převzít změny z větve do té, ve které jsem |
| `git log --oneline --graph --all` | historie včetně větví |
