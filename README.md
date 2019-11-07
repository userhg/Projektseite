# Projektseite

Von Gesche Meyer und Hannah Fußner

Stormarnschule

Klasse 12ab

Schuljahr 2019/2020

## Inhaltsverzeichnis
[Vorwort](#1)

[Das Programm](#2)

[Die Spielidee](#3)

[Der Spielanfang](#4)

### Vorwort<a name="1"></a>
Vor unserer ersten Informatikstunde hatten wir beide keinerlei Vorstellungen oder Vorkenntnisse von Informatik. Aufwendige Kurse im Internet konnten wir aus zeitlichen Gründen leider nicht durchführen und wagten so den Sprung ins kalte Wasser. Was ohne jegliche Vorkenntnisse oder Hilfsmittel aus dem Internet, sondern nur durch eigenes logisches Denken und vielen Anlaufversuchen entstanden ist, wird im Folgenden präsentiert.

### Das Programm<a name="2"></a>
Das Programm, welches wir für das Erstellen unseres Projekts verwendet haben, ist die Plattform Snap! (https://snap.berkeley.edu/)
Diese wirbt mit anfängerfreundlichen Designs und hilfreichen Tipps, die uns jeoch nicht viel geholfen haben. Das Konzept von Snap! basiert aucf einer visuellen Programmiersprache, sodass Scipts durch vorgefertigte Blocks nachvollziehbar sind. 

### Die Spielidee<a name="3"></a>
Das Spiel, welches wir programmiert haben, ist eine Computerversion des bekannten Spiels "Schere, Stein, Papier". Dieses Spiel benötigt in der Praxis normalerweise zwei Spieler, die gegeneinander spielen. Durch unsere Computerversion ermöglichen wir auch Einzelpersonen, die keinen Spielpartner gefunden haben, den Spaß zu erleben. 

Für die, die dieses Spiel und seine Regeln nicht kennen, hier eine kleine Zusammenfassung: 
Es gibt die Auswahlmöglichkeiten Schere, Stein und Papier, die jeder Spieler für sich im Geheimen auswählt. 

Schere schneidet Papier

Papier umwickelt Stein

Stein zerstört Schere

### Der Spielanfang<a name="4"></a>
Der Startbildschirm unseres Spiels zeigt zwei Fäuste, dargestellt aus zwei Sprites. Die rechte Hand ist die Computer Faust (Sprite: Fist C) und hat in dem Spiel keine besondere Funktion. Sie zeigt sich zu Anfang und verschwindet durch den "Broadcast: Hide" bei der Spielauswertung. Die linke Hand stellt die Faust des Spielers dar (Sprite: Fist P) und koordiniert den Spielanfang.
Im Hintergrund ist die "Play Stage" angezeigt.

![image1](https://github.com/userhg/Stundenblog/blob/master/images/Play%20stage.png)

Zu Anfang wird der Spieler durch Anweisungen in Sprechblase dazu aufgefordert sein Wahl des Werkzeuges zu betätigen.
Dazu haben wir zwei Variablen eingeführt: *userchoice* und *Spacekeypressed*
Beide Variablen werden zu Anfang auf 0 gesetzt.
In der ersten Sprechblase wird dazu aufgefordert zuerst die Leertaste zu drücken, um das Spiel zu starten.
Sobald dies erfolgt, wird die Variable *Spacekeypressed* auf 1 gesetzt und die Sprechblase verschwindet.
Gleichzeitig wird eine Nachricht (broadcast) *spacepressed* gesendet, worauf die drei verschiedene Sprites mit den Symbolen Schere, Stein und Papier erscheinen. Nun wird der Spieler dazu aufgefordert, sich durch einen Klick für eines der drei Auswahlmöglichkeiten zu entscheiden. Wenn eines dieser drei Sprites angeklickt wird, wird die Variable *userchoice* auf 1 (Rock), 2 (Scissors) oder 3 (Paper) gesetzt. 


![image 2](https://github.com/userhg/Stundenblog/blob/master/images/Spielanfang%20endv..png)
