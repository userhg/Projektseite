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

[Wahl des Spielers](#5)

[Wahl des Computers](#6)

[Auswertung des Spiels](#7)

[Spielreflexion](#8)



### Vorwort<a name="1"></a>
Vor unserer ersten Informatikstunde hatten wir beide keinerlei Vorstellungen oder Vorkenntnisse von Informatik. Aufwendige Kurse im Internet konnten wir aus zeitlichen Gründen leider nicht durchführen und wagten so den Sprung ins kalte Wasser. Was ohne jegliche Vorkenntnisse oder Hilfsmittel aus dem Internet, sondern nur durch eigenes logisches Denken und vielen Anlaufversuchen entstanden ist, wird im Folgenden präsentiert.

### Das Programm<a name="2"></a>
Das Programm, welches wir für das Erstellen unseres Projekts verwendet haben, ist die Plattform Snap! (https://snap.berkeley.edu/)
Diese wirbt mit anfängerfreundlichen Designs und hilfreichen Tipps, die uns jedoch nicht viel geholfen haben. Das Konzept von Snap! basiert auf einer visuellen Programmiersprache, sodass Scipts durch vorgefertigte Blocks nachvollziehbar sind. 

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
Gleichzeitig wird eine Nachricht (broadcast) *spacepressed* gesendet, worauf die drei verschiedene Sprites mit den Symbolen Schere, Stein und Papier erscheinen. Nun wird der Spieler dazu aufgefordert, sich durch einen Klick für eines der drei Auswahlmöglichkeiten zu entscheiden. Wenn eines dieser drei Sprites angeklickt wird, wird die Variable *userchoice* auf 1 (Rock), 2 (Scissors) oder 3 (Paper) gesetzt. Da unser Block leider aus unerklärlichen Gründen nicht funktioniert hat, haben wir durch das Einsetzen des leeren say-Befehls einen Hack erzeugt.

![image 2](https://github.com/userhg/Stundenblog/blob/master/images/Spielanfang%20endv..png)

### Wahl des Spielers<a name="5"></a>

Zu Anfang des Spiels sind die drei Sprites mit den drei verschiedenen Symbolen im versteckten Zustand. 

![image 4](https://github.com/userhg/Stundenblog/blob/master/images/Sprites%20RPS.png)

Durch die Nachricht *spacepressed* treten sie zum ersten Mal in Erscheinung. Nun kann ein Symbol durch Anklicken von dem Spieler ausgewählt werden. Damit der Gegenstand nur einmalig angeklickt werden kann haben wir einen Statusindikator (Flag) gesetzt. Dazu haben wir die lokale Variable *WarSchonGeklickt* für alle drei Sprites eingeführt. Zu Anfang wird diese Variable auf *false* gesetzt. 
Nun wird mit dem If-Befehl nur bei dem Fall das die Variable *false* ist die Variable auf *true* gesetzt, sodass der Befehl nicht ein zweites Mal ablaufen kann. Außerdem wird eine Nachricht geschickt mit *paper clicked*, *scissors clicked* oder *rock clicked*, worauf die jeweiligen nicht ausgewählten Sprites wieder in den versteckten Zustand wechseln. Das angeglickte Sprite gleitet auf das Faustsymbol des Spielers und macht sich für das Spiel bereit. Gleichzeitig wird das eigentliche Spiel mit der Nachricht *start pick random* gestartet.  

![image 3](https://github.com/userhg/Stundenblog/blob/master/images/Script%20Paper.png) 


### Wahl des Computers<a name="6"></a>

Die Wahl des Computers spielt sich in einem Sprite (Choice C) ab, in das wir die drei Symbole Schere, Stein und Papier als Kostüme eingeführt haben. Der im Bild unten gezeigte Block startet, wenn die Nachricht *start random pick* von vorher angeklickten Sprite des Spielers gesendet wurde (siehe [Wahl des Spielers](#5)).
Nun wird die neue Variable *fistchoice* in das Script integriert. Der Computer wählt nun zufällig zwischen 1 und 3 eine Zahl aus. Mit dem if-Befehl erscheint er bei 1 im Vordergrund im Kostüm des Steins, bei 2 im Kostüm der Schere und bei 3 im Kostüm des Papiers. Wenn dies erfolgt ist, wird die Nachricht "Chosen" verschickt. 

![image 5](https://github.com/userhg/Stundenblog/blob/master/images/Script%20computer.png)

### Auswertung des Spiels<a name="7"></a>

Für die Auswertung des Spiels haben wir einen neuen Sprite "Win or Lose" eingeführt, der jedoch während des gesamten Spiels nicht zu sehen ist. Dieser empfängt, wenn die Wahl des Coputers abgeschlossen ist, die Nachricht "Chosen" (siehe [Wahl des Computers](#6))
Nun haben wir den if-Befehl eingesetzt. Wenn die Variablen 

*fistchoice* = 1 und *userchoice* = 3 (Spieler gewinnt mit Papier gegen Computer mit Stein) oder 

*fistchoice* = 2 und *userchoice* = 1 (Spieler gewinnt mit Stein gegen Computer mit Schere) oder

*fistchoice* = 3 und *userchoice* = 2 (Spieler gewinnt mit Schere gegen Computer mit Papier)

lauten, wird die Nachricht "Win" gesendet. Diese erhält unsere "Play Stage", der Hintergrund, der während des Spiels zu sehen ist (siehe [Der Spielanfang](#4)). 
Nach zwei Sekunden, die wir zur Vermeidung eines zu schnellen Wechsels eingebaut haben, wird die Nachricht "Hide" an alle Sprites geschickt, die daraufhin verschwinden. Gleichzeitig ändert sich der Hintergrund zur "Win Stage" PIC 

Drei Sekunden kann der Spieler sein Ergebnis betrachten, dann wechselt es wieder zur "Play Stage" und die Nachricht "NewBeginning" wird versendet. Diese empfängt der Sprite Fist P, erscheint und fordert den Spieler mit "Press the green flag!" dazu auf, das Spiel erneut zu starten. 

Wenn jedoch der Fall  *fistchoice* = *userchoice* (Computer und Spieler haben beide entweder Stein, Schere oder Papier gewählt) eintritt, wird die Nachricht "TryAgain" versendet. Daraufhin verändert sich der Hintergrund zur "Try again stage". Der Rest vom Ende des Spiels verläuft von dort genau so wie im Fall "Win". 

Wenn die Variabeln 

*fistchoice* = 1 und *userchoice* = 2 (Spieler vierliert mit Schere gegen Computer mit Stein) oder 

*fistchoice* = 2 und *userchoice* = 3 (Spieler verliert mit Papier gegen Computer mit Schere) oder

*fistchoice* = 3 und *userchoice* = 1 (Spieler veliert mit Stein gegen Computer mit Papier)

lauten,  wird die Nachricht "Lose" verschickt, der Hintergrund verändert sich zur "Lose stage" und wie bei den anderen Spielausgängen,verschwinden alle Sprites und es erscheint nach drei Sekunden Fist P im "Play Stage" Hintergund und fordert den Spieler zum Neustart auf und das Spiel beginnt wieder von vorne. 


### Spielreflexion<a name="8"></a>

Nach zweieinhalb Monaten, in denen wir sowohl Erfolgserlebnisse, als auch so manchen Tiefpunkt erlitten haben, sind wir mit dem Ergebnis unseres ersten Projekts zufrieden.
Unser Spiel wäre alledings auch noch ausbaufähig gewesen. Man hättte das Ganze auf mehrere Runden erweitern können, bis der Spieler oder der Computer beispielsweise mit drei Punkten gewinnt. Jedoch fehlte uns dazu die Zeit, da wir viel Zeit benötigten, unere eigenen Ideen und Ansaätze erfolgreich umzusetzen. Daher haben wir entschieden, dass das Spiel nach einer Runde zu Ende ist. So konnten wir uns auf die wesentlichen Vorgänge des Spiels besser konzentrieren.
Wir sind sehr stolz darauf "Rock, Paper Scissors" ohne jegliche Hilfsmittel aus dem Internet oder Vorwissen programmiert zu haben. Uns gefällt auch d
