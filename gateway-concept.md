# Konzept der Gatewayorganisation

## Motivation
Um einen erleichterten Einstieg für neue Freifunker zu ermöglichen, stellen wir nun ein Kozept zur 
Verfügung, welches erläutern soll wie unsere Gateways strukturiert und verwaltet werden.

## Aufgaben
Gateways stellen die Verbindung zwischen allen Freifunkknoten und dem Internet dar. Sie fungieren 
also als Switch und Router für den freifunkinternen Datenverkehr, ebenso wie dem Datenverkehr ins 
Inter-City-VPN und dem Internet. Außerdem stellen sie grundlegende Netzwerkdienste wie DHCP und DNS zur Verfügung, die die Navigation innerhalb des Freifunknetzes ermöglichen.

## Gatewaygruppen
1. Stable
2. Experimental/Testing

### Stable
Bei dieser Gatewaygruppe handelt es sich um die primären Gateways aller Freifunkknoten, die den 
Stable-Release der Freifunk Firmware nutzen. Diese Gateways werden ausschließlich durch Saltstack 
konfiguriert um Fehler und Asynchronität zu vermeiden. Änderungen müssen zunächst auf 
Experimental/Testing-Gateways getestet und vorbereitet worden sein.

### Experimental/Testing
Bei dieser Gatewaygruppe handelt es sich um Gateways, die zur Weiterentwicklung des Netzes verwendet 
werden. Hier werden neue Konfigurationen, im Zweifel in Abstimmung mit der Testing-Firmware, 
entwickelt und getestet. Diese werden dann, sobald sie einen funktionstüchtigen Zustand erreicht 
haben, in Saltstack verpackt und nach einer Testphase von 2 Wochen auf die Stable-Gateways übertragen.

## Ausnahmeregelungen
### Logindaten
Da gewisse Logindaten auf allen Gateways eingesetzt werden und müssen bei vertraglichen oder 
sicherheitsrelevanten Fällen jederzeit überall austauschbar sein.

## Fazit und Ziel
Das Konzept zielt darauf ab eine die Abstimmung von Firmware und Gateways zu erleichtern und die 
Entwicklung des Freifunknetzes voran zu treiben.