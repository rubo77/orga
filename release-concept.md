# Konzept zur Erstellung neuer Firmware-Releases

## Motivation
Nach den vergangen Eskapaden, die die eigentliche Entwicklung des Freifunk Netzes etwas bremsten 
und einige Prozesse in die Länge zogen, hier eine Konzeptidee, wie man Firmware anders releasen 
kann und so, sowohl Updates als auch Features, sicher in den Stable-Betrieb bringen kann.

Hierzu greife ich auf meine Erfahrungen und Konzepte aus mehreren Rollout-Projekten für Firmen 
zurück, die durchaus zeitnah und im Produktivbetrieb stattfanden. Ebenso wie auf die bereits 
bestehenden Strukturen.

## Release Phasen
Es wird ein 3 phasiges System verwendet, welches folgene Release-Phases beinhaltet:

1. Development
2. Testing
3. Stable


### Development
Im Development-Release werden grundsätzlich alle Ideen und Bugfixes verbaut. Dieser Release kann durchaus gebrochen werden, sollte allerdings ebenfalls eine saubere Commit-Historie besitzen. 
Hierzu werden neue Features und Updates bis zu einer Grundfassung, deren Bulding möglich ist, 
in einer seperaten Branch entwickelt und mit einem einzelnen Pull Request, im folgenden mit PR 
abgekürzt, der ebenfalls zu einem zu einem einzelnen Commit zusammengefasst worden ist, in die 
Development Branch eingefügt. Beim Einfügen des PR wird die Development-Grundbranch für neue 
Features eingefroren . Deswegen sollte insbesondere vor einfügen von neuen Features und Updates 
bereits im PR geklärt werden, ob man diese überhaupt einbauen möchte.

Sobald dies geklärt ist und der PR in den Development-Branch gemerged ist, wird dieser gebaut und 
getestet. Funktioniert dieser grundlegend und auch ein Upgrade vom Testing Release auf den 
Development-Release mit Facorty- und Sysupgrade-Image ohne sichtbare Verluste wird der 
Development-Branch in den Testing-Branch gemerged. Von nun an bleibt der Development-Branch 
eingefroren bis die Neuerung in den Stable-Branch gemerged ist und wird nur für das nachträgliche einfügen von Bugfixes für die aktuelle Testing Variante genutzt.

Sollte ein Fehler im Testing-Branch auftreten, wird dieser im Development Branch gefixt und geprüft. 
Tritt er nicht erneut auf oder ist nicht reproduzierbar, wird der Bugfix in den Testing-Branch 
gemerged. Die Testphase wird daraufhin auf mindestens 3 Tage nach dem zur Verfügung stellen des Builds verlängert. Hierdurch wird sichergestellt, dass der Bugfix keine größeren Fehler erzeugt und 
falls doch, können diese noch in einer kleinen Testgruppe behoben werden.

### Testing
Im Testing-Release werden die neuen Features aus dem Development-Release für eine kleine ausgewählte 
Gruppe von produktiv verwendeten Knoten ausgerollt und getestet. Alle Fehler die hier auftreten 
werden in einem Issue oder PR gegen den Development-Branch erfasst und unter einem Meilenstein mit 
dem Ende des Testbetriebs des aktuell neuen Featues eingegliedert. Der Testzeitraum eines neuen 
Featues beträgt 2 Wochen nach Bereitstellung des Testing-Releases dieses Features. Nach Ablauf 
dieses Meilensteins wird die Testing-Branch in die Stable-Branch gemergt, vorausgesetzt alle PRs und 
Issues unter dem Meilenstein sind seit mindestens 3 Tagen gelöst und im Testing-Release vorhanden. 
Sollte ein Problem erst 1 oder 2 Tage vor Ablauf des Meilensteins auftreten, wird dieser auf 3 Tage 
nach Lösen des Problems verlängert.

### Stable
Im Stable-Relase wird die Firmware für sämtliche Knoten verteilt, die keine eigene Firmware 
verwenden oder sich in der Testing-Gruppe befinden und produktiv genutzt werden. Hier sollten alle 
Features in vollem Funktionsumfang getestet und als funktionierend eingestuft sein. 
Hierdurch wird die Funktionstüchtigkeit dieses Releases sichergestellt.


## Ausnahmeregelungen
### Sicherheitspatches
Um die Sicherheit innerhalb des Netzes zu erhöhen dürfen für sicherheitskritische Updates jederzeit 
in den Developmentbranch eingespielt werden. Je nach Risikostatus kann hier auch die Testphase auf 
biszu 3 Tage für die Testingbranch heruntergebrochen werden. Um dennoch sicher zu gehen, dass ein 
solches Update nicht im schlimmsten Fall doch zu größeren Problmen im Netz führt und somit das 
gesamte Netz aus den Fugen bringt.

## Hinweise und Begriffsklärungen
### Branch
Hierbei handelt es sich um einen Entwicklungsabschnitt innerhalb des Versionsverwaltungstool git.

### Release
Hierbei handelt es sich um ein, aus dem entsprechenden Branch, kompiliertes Image für Freifunk-Router.

### ausgewählt
Im Fall des Testing-Releases wird von einer ausgewählten Gruppe gesprochen. Hierbei handelt es sich nicht um eine administrativ ausgewählte Gruppe sondern lediglich um eine Gruppe von Knoten die durch den Besitzer des selbigen zum testen ausgewählt wurde. Niemand kann verbieten oder erzwingen, dass sich ein Knoten dieser Gruppe anschließt oder nicht. Es obliegt dem Inhaber/Besitzer des Knotens dies zu entscheiden.