# Sicherheit in Freifunknetzen
## Sind unverschlüsselte WLANs wirklich unsicherer?
In den Medien wird es immer wieder propagiert und auch sonst überall hört man immer "Vorsicht vor offenen WLANs" oder "Achtung, verschlüsseln Sie ihr WLAN, damit Hacker keinen Zugriff darauf haben".

Falsch sind diese Aussagen nicht, soviel vorweg, aber das liegt eher daran, was sich in deinem Heimnetzwerk befindet.
Heutzutage kann so ziemlich alles WLAN haben.
Vom PC bis zum Toaster in der Küche.
Damit die auch das tun, was sie tun, ist ihr Primärziel erstmal untereinander zu kommunizieren und ggf. noch Updates von der Hersteller-Webseite beziehen.
Besonders die Kommunikation untereinander erfolgt innerhalb des eigenen Netzwerks häufig unverschlüsselt.
Man verlässt sich hier darauf, dass z.B. eben gerade das WLAN bereits verschlüsselt ist und nur vertrauenswürdige Geräte Zugriff haben.
Also zuhause das private WLAN verschlüsseln, ist in jedem Fall keine schlechte Idee. 

Freifunk dient aber hauptsächlich zur Kommunikation nach außen, also ins Internet und da auch eher mit Geräten wie einem Smartphone, Tablet oder Laptop.
Hiermit werden dann außerdem meist Webseiten aufgerufen, vielleicht ein wenig über Skype oder Mumble kommuniziert und über diverse Chat-Applikationen miteinander Nachrichten ausgetauscht.
Bei den gängigen Applikationen ist das offene WLAN also kein Problem.
Denn die meisten Verbindungen funktionieren über HTTPS.
Das S am Ende steht für Secure und stellt für jeden Angreifer erstmal eine ziemlich große Hürde da.
HTTPS-Webseiten erkennst du in allen gängigen Browser am Schlosssymbol in der Adresszeile.
Achte auf das Schlosssymbol, wenn du Passwörter eingibst.
Nicht nur im Freifunknetwerk, sondern überall. 

Du fragst dich jetzt vielleicht, warum man Freifunk nicht einfach verschlüsselt und das Passwort z.B. auf die Flyer schreibt.
Das Problem ist: Selbst ein als sicher geltendes WPA2-PSK, welches du zuhause nutzt, ist eben nur so lange sicher, wie nur die Leute das Passwort kennen, die auch keine schlechten Absichten haben.
In Firmen sieht die Umgebung teilweise anders aus.
Wenn du aber z.B. in einem Café ein verschlüsseltes WLAN betrittst, bei dem alle das gleiche Passwort nutzen, bist du auch nicht sicherer als in einem unverschlüsselten Netzwerk, wie dem Freifunk Netz.

Viele Firewall-Programme und auch die Windows-Firewall bietet für genau solche WLANs die Option des öffentlichen Netzwerks.
Diese Einstellung ist empfohlen, da sie versucht alle unnötigen Zugriffe von außen zu blockieren.

Also alles in allem ist das Freifunk-Netzwerk eine sichere Sache, wenn man darauf achtet, dass die Firewall das Netzwerk als öffentlich Netzwerk ansieht und man auf HTTPS und andere TLS Verbindungen achtet.

## Dinge auf die man achten sollte, wenn man in offenen/fremden Netzwerken unterwegs ist

* Netzwerk als öffentliches Netzwerk in den Firewalleinstellungen markieren
* Freigaben von Daten ins Netzwerk abschalten
* HTTPS für alle Seiten, wo man sich anmeldet
* Bei Sicherheitswarnungen im Browser vorsichtig sein
* (optional) Verwenden von VPN

## Dinge die man in offenen/fremden Netzwerken vermeiden sollte

* Filesharing
* Öffnen von Ports 
* Firmen-/Heimnetzwerkeinstellungen nutzen
