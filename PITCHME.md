# Linus Torvalds 

### Een verhaal over Linus, Linux en Git

---

## Tips!

<br>

@fa[arrows gp-tip](Druk op F voor een volledig scherm)

@fa[microphone gp-tip](Druk op S voor notities)

---

## Linus Torvalds

![](figuren/Linus_workdesk.jpg)

---

## Biografie

- geboren in Helsinki in Finland op 28 december 1969 |
- Op 5 oktober 1991 maakte Torvalds de eerste release bekend |
- 1997 naar Silicon Valley |
- 2003 een fulltime baan bij Transmeta |
- 2012 één van de twee winnaars van de Millennium Technology Prize |

---

## Techniek - Git

![](figuren/github-social-coding.resized.jpg)

---

## De basis van GIT

Een Git repository verkrijgen

```
$ git init
```

+++

## De basis van GIT

De status van je bestanden controleren

```
$ git status
On branch master
nothing to commit, working tree clean
```

+++

## De basis van GIT

Nieuwe bestanden volgen (tracking)

```
$ git add nieuwbestand

$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   nieuwbestand
```

+++

## De basis van GIT

wijzigingen committen

```
$ git commit -m "vertel hier wat je gedaan hebt"
```

+++

## De basis van GIT

Bestanden verwijderen

```
$ git rm bestand03
rm 'bestand03'
```

+++

## De basis van GIT

Bestand verplaatsen of hernoemen

```
$ git mv bestand04 bestand07

$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)


        renamed:    bestand04 -> bestand07
```

+++

## De basis van GIT

De commit geschiedenis bekijken

```
$ git log
```

---

## Gebruik van versies in GIT

de verschillende versies oplijsten

```
$ git branch
```

+++

## Gebruik van versies in GIT

een nieuwe versie maken

```
$ git checkout -b nieuwe_versie
```

+++

## Gebruik van versies in GIT

overschakelen tussen versies

```
$ git checkout andere_versie
```
+++

## Gebruik van versies in GIT

terug naar de hoofdversie
```
$ git checkout master
```

---

# Vragen?

---

# waar vind je dit 


https://github.com/bloemenmeisje/jaarwerk-klas8

https://bloemenmeisje.github.io/jaarwerk-klas8/

https://gitpitch.com/bloemenmeisje/jaarwerk-klas8/master?grs=github&t=sky

