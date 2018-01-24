[Home](README.md) | [Biografie](bio.md) | [Uitvinding](uitvinding.md) | [Bronnen](bronnen.md) | [Opgave](opgave.md) |  [Presentatie](https://gitpitch.com/bloemenmeisje/jaarwerk-klas8/master?grs=github&t=moon)

# De basis van Git

## Een Git repository verkrijgen

Je kunt op twee manieren een Git project verkrijgen. De eerste maakt gebruik van een bestaand project of directory en importeert dit in Git. De tweede maakt een kloon (clone) van een bestaande Git repository op een andere server.
```
$ git init
```
Als je een kopie wilt van een bestaande Git repository, bijvoorbeeld een project waaraan je wilt bijdragen, dan is git clone het commando dat je nodig hebt. (zie verder)

## De status van je bestanden controleren
Het commando dat je voornamelijk zult gebruiken om te bepalen welk bestand zich in welke status bevindt is git status. Als je dit commando direct na het clonen uitvoert, dan zal je zoiets als het volgende zien:

$ git status
On branch master
nothing to commit, working tree clean

## Nieuwe bestanden volgen (tracking)

Om een nieuw bestand te beginnen te volgen (tracken), gebruik je het commando git add. Om een bestand te tracken, voer je dit uit:

$ git add nieuwbestand

Als je het status commando nogmaals uitvoert, zie je dat je nieuwbestand nu getrackt en ge-staged is:

$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   nieuwbestand

Om te zien wat je gewijzigd maar nog niet gestaged hebt, typ je:

$ git diff --cached
diff --git a/werken met git b/werken met git
index 10dac7d..1b40157 100644
--- a/werken met git
+++ b/werken met git
@@ -30,7 +30,7 @@ Changes to be committed:

         new file:   nieuwbestand

-# bekijk de aanpassingen
+Om te zien wat je gewijzigd maar nog niet gestaged hebt, typ je:


## Je wijzigingen committen
Nu je staging area gevuld is zoals jij het wilt, kun je de wijzigingen committen. Onthoud dat alles wat niet gestaged is, dus ieder bestand dat je gemaakt of gewijzigd hebt en waarop je nog geen git add uitgevoerd hebt, niet in deze commit mee zal gaan.

De makkelijkste manier om te committen typ je:

$ git commit -m "vertel hier wat je gedaan hebt"

## Bestanden verwijderen

Om een bestand van Git te verwijderen, moet je het van de getrackte bestanden verwijderen en dan een commit doen. Het git rm commando doet dat, en verwijdert het bestand ook van je werkdirectory.

$ git rm bestand03
rm 'bestand03'

Als je de volgende keer een commit doet, zal het bestand verdwenen zijn en niet meer getrackt worden.


# Bestand verplaatsen of hernoemen

Als je een bestand wilt hernoemen in Git, kun je zoiets als dit doen

$ git mv bestand04 bestand07


en dat werkt prima. Sterker nog, als je zoiets als dit uitvoert en naar de status kijkt, zul je zien dat Git het als een hernoemd bestand beschouwt:

$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)


        renamed:    bestand04 -> bestand07




## De commit geschiedenis bekijken

Nadat je een aantal commits gemaakt hebt, of als je een repository met een bestaande commit-geschiedenis gecloned hebt, zul je waarschijnlijk terug willen zien wat er gebeurd is, dat kan met:

$ git log

en en geef alle wijzigingen tot nu toe

$ git log -p

of beperk het bijvoorbeeld tot de 2 laatste aanpassingen

$ git log -p -2


## Dingen ongedaan maken

Op enig moment wil je misschien iets ongedaan maken. Hier zullen we een aantal basis-tools laten zien om veranderingen die je gemaakt hebt weer ongedaan te maken. Maar pas op, je kunt niet altijd het ongedaan maken weer ongedaan maken. Dit is één van de weinige gedeeltes in Git waarbij je werk kwijt kunt raken als je het verkeerd doet.

### Je laatste commit veranderen
Een van de veel voorkomende acties die ongedaan gemaakt moeten worden vinden plaats als je te vroeg commit en misschien vergeet een aantal bestanden toe te voegen, of je verknalt je commit boodschap. Als je opnieuw wilt proberen te committen, dan kun je commit met de --amend optie uitvoeren:

$ git commit --amend

bestand terugzetten maar voor je commit

$ git reset HEAD bestand

een bestand terugzetten naar vorige versie, dit is gevaarlijk!

$ git checkout -- bestand

# Werken met remotes
Om samen te kunnen werken op eender welke Git project, moet je weten hoe je de remote repositories moet beheren. Remote repositories zijn versies van je project, die worden beheerd op het Internet of ergens op een netwerk.
Samenwerken met anderen houdt in dat je deze remote repositories kunt beheren en data kunt pushen en pullen op het moment dat je werk moet delen.

## Een bestaand repository clonen

Om te zien welke remote servers je geconfigureerd hebt, kun je het git remote commando uitvoeren. Het laat de verkorte namen van iedere remote alias zien die je gespecificeerd hebt. Als je de repository gecloned hebt, dan zul je op z'n minst de origin zien; dat is de standaard naam die Git aan de server geeft waarvan je gecloned hebt:

$ git clone git://github.com/bloemenmeisje/jaarwerk-klas8
Cloning into 'jaarwerk-klas8'...
remote: Counting objects: 459, done.
remote: Compressing objects: 100% (23/23), done.

remote: Total 459 (delta 12), reused 5 (delta 1), pack-reused 435
Receiving objects: 100% (459/459), 1.09 MiB | 615.00 KiB/s, done.
Resolving deltas: 100% (269/269), done.

$ cd jaarwerk-klas8/
$ git remote
origin

# Remotes fetchen en pullen

Je kan om data van je remote projecten te halen dit uitvoeren:

$ git fetch origin

Het is belangrijk om te weten dat het fetch commando de data naar je locale repository haalt; het merget niet automatisch met je werk of verandert waar je momenteel aan zit te werken. Je moet het handmatig in je werk mergen wanneer je er klaar voor bent.

$ git pull

Git pull doet hetzelfde als fetch maar voegt het ineens samen.(fetch + merge). Mogelijk zal je dit meer gebruiken dan fetch.

# Naar je remotes pushen

Wanneer je jouw project op een punt hebt dat je het wilt delen, dan moet je het
stroomopwaarts pushen. Het commando hiervoor is simpel:

$ git push origin master

Dit commando werkt alleen als je gecloned hebt van een server waarop je schrijfrechten hebt, en als niemand in de tussentijd gepusht heeft. Als jij en iemand anders op hetzelfde tijdstip gecloned hebben en zij pushen eerder stroomopwaarts dan jij, dan zal je push terecht geweigerd worden. Je zult eerst hun werk moeten pullen en in jouw werk verwerken voordat je toegestaan wordt te pushen.

# Een remote inspecteren

Als je meer informatie over een bepaalde remote wilt zien, kun je het git remote show [remote-name] commando gebruiken. Als je dit commando met een bepaalde alias uitvoert, zoals origin, dan krijg je zoiets als dit:

$ git remote show origin
* remote origin
  Fetch URL: git://github.com/bloemenmeisje/jaarwerk-klas8
  Push  URL: git://github.com/bloemenmeisje/jaarwerk-klas8
  HEAD branch: master
  Remote branch:
    master tracked
  Local branch configured for 'git pull':

    master merges with remote master
  Local ref configured for 'git push':
    master pushes to master (up to date)

Op dit punt kun je alle basis locale Git operaties doen: een repository creëren of clonen, wijzigingen maken, de wijzigingen stagen en committen en de historie bekijken van alle veranderingen die de repository ondergaan heeft. Als volgende gaan we de beste eigenschap van Git bekijken: het branching model.
