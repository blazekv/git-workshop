# Git Tahák — Workshop

## Základní cyklus

```
Uprav soubor → git add → git commit → git push
```

---

## Nejpoužívanější příkazy

### Informace
```bash
git status                        # co se děje?
git diff                          # co přesně se změnilo?
git log --oneline                 # historie commitů
git log --graph --oneline --all   # všechny větve vizuálně
git branch -a                     # všechny větve (lokální + remote)
```

### Základní workflow
```bash
git add [soubor]                  # přidej soubor do stage
git add .                         # přidej vše (opatrně!)
git commit -m "zpráva"            # vytvoř commit
git push                          # pošli na server
git pull                          # stáhni ze serveru
```

### Větve
```bash
git checkout -b [název]           # nová větev
git switch [název]                # přepni větev
git switch main                   # zpět na main
git branch -d [název]             # smaž větev (po merge)
git push -u origin [název]        # push nové větve poprvé
```

### Stash
```bash
git stash                         # odlož změny
git stash list                    # co mám odložené?
git stash pop                     # vrať změny (a odstraň ze stash)
git stash apply                   # vrať změny (zachová ve stash)
```

### Synchronizace
```bash
git fetch                         # stáhni info, ale nespojuj
git pull                          # fetch + merge
git pull --rebase                 # fetch + rebase
```

### Rebase
```bash
git rebase main                   # přehraj větev nad main
git rebase -i HEAD~3              # interaktivní rebase posl. 3 commitů
git rebase --continue             # pokračuj po vyřešení konfliktu
git rebase --abort                # zruš rebase, vrať se zpět
```

### Merge
```bash
git merge [větev]                 # merge (fast-forward pokud možno)
git merge --no-ff [větev]         # vždy vytvoř merge commit
git merge --squash [větev]        # jeden commit ze všeho
```

### Opravy
```bash
git commit --amend                # uprav poslední commit (jen lokálně!)
git reset HEAD~1                  # zruš poslední commit (zachová změny)
git revert [hash]                 # bezpečné "zrušení" commitu (přidá nový)
git restore [soubor]              # zahoď změny v souboru
```

---

## Jak napsat dobrý commit message

```
Sloveso + co + kde (volitelně)

✅ Přidat sekci o van life do kapitoly 3
✅ Opravit překlep v OBSAH.md
✅ Aktualizovat barevnou paletu - tmavší terakota
✅ Vyřešit konflikt v kapitole 5

❌ update
❌ změny
❌ wip
❌ aaa
```

---

## Konfliktní markery

Když nastane conflict, soubor bude vypadat takto:
```
<<<<<<< HEAD
text z tvé větve
=======
text z jejich větve
>>>>>>> origin/main
```

1. Odstraň všechny markery (`<<<<`, `====`, `>>>>`)
2. Nech v souboru jen správný výsledek
3. `git add [soubor]`
4. `git commit`

---

## GitFlow ve zkratce

```
main        ← produkce (nikdy přímo nepushuj)
develop     ← integrace (základ pro feature větve)
  feature/  ← tvoje práce
  hotfix/   ← urgentní opravy
```

---

## Záchranné příkazy

```bash
# Jsem lost — kde jsem?
git status
git log --oneline -5

# Chci vrátit soubor do stavu z posledního commitu
git restore [soubor]

# Chci úplně zrušit co dělám a začít znova
git rebase --abort
git merge --abort

# Jsem v detached HEAD
git switch main
```

---

*Více na: https://ohshitgit.com*
