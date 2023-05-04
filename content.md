layout: true
  
<div class="my-header"></div>

<div class="my-footer">
  <table>
    <tr>
      <td style="text-align:right">Sächsische Landesbibliothek – Staats- und Universitätsbibliothek</td>
      <td>Date</td>
      <td style="text-align:right"><a href="https://www.slub-dresden.de/">www.slub-dresden.de</a></td>
    </tr>
    <tr>
      <td style="text-align:right">Referat 4.3</td>
      <td />
    </tr>
  </table>
</div>

<div class="my-title-footer">
  <table>
    <tr>
      <td style="text-align:left"><b>Kay-Michael Würzner</b></td>
    </tr>
    <tr>
      <td style="text-align:left">Referat 4.3</td>
    </tr>
    <tr>
      <td style="font-size:8pt"><b>05. Mai 2023</b></td>
    </tr>
    <tr>
      <td style="font-size:8pt">Seminar *Datenkompetenz für Digital Humanities*</td>
    </tr>
  </table>
</div>

---

class: title-slide
count: false

# The Unix shell
## Taking your daily computer routine to the next level

---

# Overview

- Zwei Startpunkte
  + Unix
  + Sprachmodellierung
- Hands-on: Unix for Poets

---

class: part-slide
count: false

# Unix

---

# Was ist Unix?

.cols[
.sixty[
- Unix ist ein Betriebssystem (OS).
    + grundlegende Bedienfunktionalität für Computer
    + modularer Aufbau
    + schrittweise Entwicklung zum verbreitetsten OS
- Unix ist eine Philosophie.
    + Mischung aus Bedienung und Programmierung
    + Basis des POSIX-Standards als Referenz für alle OS
- Unix ist cool.
    + Gegenpol zu Windows
    + Linux als freie Implementierung
]
.fourty[
<p>
<img src="https://upload.wikimedia.org/wikipedia/commons/2/2e/UNIX®.png" height="200px" /><br />
<a style="font-size:8pt" href="https://commons.wikimedia.org/wiki/File:UNIX%C2%AE.png">Bild: Open Company Ltd. (Registered TM)</a>
</p>
]
]

---

# Kurze Geschichte von Unix

- **1969**: erstes Unix von Ken Thompson für DEC PDP-7
- **1973**: Portierung nach C
- **1974**: erstmals Verwendung des Names Unix, Weiterentwicklung unter dem Dach von Bell Labs
- **1984**: Start des GNU-Projektes von Richard Stallmann, Ziel: freies und quelloffenes OS
- **1991**: Entwicklung von Linux, eines freien und quelloffenen Nachbaus von Linux durch Linus Torvalds
- **Heute**: Mehrheit der Computer dieser Welt laufen mit Unix-basierten Systemen 

---

# Shell als basales Steuerungsinstrument

.cols[
.sixty[
- hierarchiches Ordnersystem
    + **Baumstruktur** mit Wurzelelement `/`
    + versteckte Dateien
    + Links als Querverbindungen
- Shell selbst ein Befehl (`sh`, `bash`, `zsh` ...)
    + Fokus: **B**ourne-**a**gain **sh**ell
- wichtige Befehle
    + `ls` ... *list*
    + `mkdir` ... *make directory*
    + `cd` ... *change directory*
    + `touch` ... *create an empty file*
    + `echo` ... *repeat a given string*
    + `>,<` ... *redirect input*
    + `|` ... *concatenate commands*
]
.fourty[
<p>
<img src="https://upload.wikimedia.org/wikipedia/commons/e/e7/Bash_screenshot.png" /><br />
<a style="font-size:8pt" href="https://commons.wikimedia.org/wiki/File:Bash_screenshot.png">Bild: Emx (Wikimedia Foundation), GPL</a>
</p>
]
]

---

class: part-slide
count: false

# Sprachmodellierung

---

# Sprachmodellierung

- Bestimmung der Wahrscheinlichkeit einer Ereignisfolge `\(P(E)\)`
- wichtiges Element in vielen Ansätzen des maschinellen Lernens
- Teilterm im **Satz von Bayes**: `\(P(C|E) = \frac{P(E|C)\cdot P(C)}{P(E)}\)`
- Heute: neuronale Netze → Schätzung bzw. *Training* von Wahrscheinlichkeitsverteilungen
- Früher: *n*-Gramme → Berechnung von Wahrscheinlichkeitsverteilungen

<p style="margin-top:-20px">
<center>
<img src="https://upload.wikimedia.org/wikipedia/commons/6/68/Six_n-grams_frequently_found_in_titles_of_publications_about_Coronavirus_disease_2019%2C_as_of_7_May_2020.svg" height="200px" /><br />
<a style="font-size:8pt" href="https://commons.wikimedia.org/wiki/File:Six_n-grams_frequently_found_in_titles_of_publications_about_Coronavirus_disease_2019,_as_of_7_May_2020.svg">Bild: Daneil Mietchen (Own work), CC0</a>
</center>
</p>

---

# Sprachmodelle

- (gemeinsame) Wahrscheinlichkeit einer Folge von Ereignissen als Produkt der bedingten Wahrscheinlichkeiten der Einzelereignisse
`\(P(e_1^m)=P(e_1)\prod_{i=2}^{m}P(e_i|e_1^{i-1})\)`
- Berechnung der bedingten Einzelwahrscheinlichkeiten durch Zählen
`\(P(e_i|e_1^{i-1})=\frac{C(w_1^{i-1}\cdot w_i)}{\sum_{a\in\Sigma}C(w_1^{i-1}\cdot a)}\)`
- Summe der Wahrscheinlichkeiten für alle Einzelereignisse: 1
- Problem?

---

count: false

# Sprachmodelle

- (gemeinsame) Wahrscheinlichkeit einer Folge von Ereignissen als Produkt der bedingten Wahrscheinlichkeiten der Einzelereignisse
`\(P(e_1^m)=P(e_1)\prod_{i=2}^{m}P(e_i|e_1^{i-1})\)`
- Berechnung der bedingten Einzelwahrscheinlichkeiten durch Zählen
`\(P(e_i|e_1^{i-1})=\frac{C(w_1^{i-1}\cdot w_i)}{\sum_{a\in\Sigma}C(w_1^{i-1}\cdot a)}\)`
- Summe der Wahrscheinlichkeiten für alle Einzelereignisse: 1
- Problem?
    + Sprachmodell = Korpus
    + kein Korpus groß genug (unendlich viele Kontexte)
    + **keine Verallgemeinerung**

---

# *n*-Gramme

- Folge von *n* Sachen
    + Zeichen, Wörter, Silben etc.
- Markov-Annahme `\(P(e_i|e_1^{i-1})\approx P(e_i|e_{i-(\pmb{n}-1)}^{i-1})\)`
    + Verdichtung des Ereignisraumes (Anzahl Kontexte entspricht `\(\Sigma^{\pmb{N}-1}\)`)
- Anwendung über Sprachmodellierung hinaus: typische Verbindungen (Kollokationen)
    + häufige, nicht-triviale *n*-Gramme (i.e. gemeinsame Vorkommen von Wörtern)
- Immer noch Probleme?
---

count: false

# *n*-Gramme

- Folge von *n* Sachen
    + Zeichen, Wörter, Silben etc.
- Markov-Annahme `\(P(e_i|e_1^{i-1})\approx P(e_i|e_{i-(\pmb{n}-1)}^{i-1})\)`
    + Verdichtung des Ereignisraumes (Anzahl Kontexte entspricht `\(\Sigma^{\pmb{N}-1}\)`)
- Anwendung über Sprachmodellierung hinaus: typische Verbindungen (Kollokationen)
    + häufige, nicht-triviale *n*-Gramme (i.e. gemeinsame Vorkommen von Wörtern)
- Immer noch Probleme?
    + selten alle *n*-Gramme in einem Korpus beobachtbar
    + unendlich große Alphabete (z.B. Wörter im Deutschen)

---

class: part-slide
count: false

# Unix for Poets

---

# Unix for Poets

- Erstellung *n*-Gramm-basierter Sprachmodelle mit der Unix Shell
- Kenneth W. Church 
    + Amerikanischer Computerlinguist
    + Head of data mining, Bell Labs
    + [Publikationsliste](https://dblp.org/pid/c/KennethWardChurch.html)
        * U.a. *Mutual Information* [(Church and Hanks 1989)](https://aclanthology.org/P89-1010.pdf)

<p>
<img src="https://avatars.githubusercontent.com/u/18170281?v=4" height="200px" /><br />
<a style="font-size:8pt" href="https://github.com/kwchurch">Bild: Kenneth Church (Own work), All rights res.</a>
</p>

---

class: part-slide

# Many thanks for your attention!

<center>
<a href="https://wrznr.github.io/dhm_dk_shell/">wrznr.github.io/dhm_dk_shell/</a>
</center>
