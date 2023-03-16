### »Die **Greta Garbo** der **Leichtathletik**« – <br />Eine systematische Analyse der Modifier vossianischer Antonomasien mithilfe von Word Embeddings

![intro pic](images/greta-garbo-middle-distance-runner_dall-e.jpg)<!-- .element height="200px;" -->

Michel Schwab ¹ <a href="https://orcid.org/0000-0001-5569-6568"><img height=20 src="https://upload.wikimedia.org/wikipedia/commons/0/06/ORCID_iD.svg"/></a> · Frank Fischer ² <a href="https://orcid.org/0000-0003-2419-6629"><img height=20 src="https://upload.wikimedia.org/wikipedia/commons/0/06/ORCID_iD.svg"/></a><!-- .element: style="font-size:0.8em;" -->

1 · Humboldt-Universität zu Berlin <br />
2 · Freie Universität Berlin<!-- .element: style="font-size:0.6em;" -->

<br />URL dieser Präsentation: **[bit.ly/PLACEHOLDER](https://bit.ly/PLACEHOLDER)** – Illustration: [DALL·E](https://labs.openai.com/s/mjHEyFFSZ6a82FurFVDajUcD)
<!-- .element: style="font-size:0.6em;" -->

[DHd2023](https://www.conftool.net/dhd2023/index.php?page=browseSessions&form_session=189&presentations=show) &nbsp;·&nbsp; Trier &nbsp;🇩🇪 &nbsp;·&nbsp; Fr, 17. März 2023, 15:00 Uhr
<!-- .element: style="font-size:0.8em;" -->

---
	  
## Inhalt

<br />

1. [Defintion und Beispiele](#/1)
2. [Forschungsstand](#/2)
3. [Task](#/3)
4. [Datensatz](#/4)
5. [Methoden](#/5)
6. [Ergebnisse](#/6)

---

# Defintion und Beispiele

--

## Vossianische Antonomasie (Vossanto)

<br/>
	  
- zuerst beschrieben um 1600 von Gerardus Vossius
- besteht aus Target, Source, Modifier (vgl. Bergien 2013)
- traditionelle Beispiele:
  - Vittorio Hösle, "der Boris Becker der Philosophie" (welt.de, 2013)
  - Alice Schwarzer, "der Erich Honecker des Feminismus" (cicero.de, 2014)
  - Markus Lanz, "der Christian Wulff des Showgeschäfts" (spiegel.de, 2014)
  - Jim Koch, "the Steve Jobs of Beer" (The Atlantic, 2014)
- titelgebendes Beispiel:
  - "[Wilson] Kipketer is as guarded [zurückhaltend] as he is fast; some reporters have labeled him the Greta Garbo of track and field.« (NYT, 8. August 1997)"
- Ziel des Projekts: Funktion, Wirkungsweise und Verbreitung der Vossanto in verschiedenen Sprachen auf Basis großer Korpora erforschen


--
	  
![VA Example](images/example.png)
<!-- .element width="450px" -->


<small>
image sources: <a href="https://commons.wikimedia.org/wiki">Wikimedia Commons</a></small>


---

# Forschungsstand

</br>

<div class="timeline">
  <div class="container left">
    <div class="date"></div>
    <i class="icon fa fa-home"></i>
    <div class="content">
      <h2>DHd 2017</h2>
      <p>
        Jaeschke et al.
      </p>
    </div>
  </div>
  <div class="container right">
    <div class="date"></div>
    <i class="icon fa fa-gift"></i>
    <div class="content">
      <h2>DSH 2019</h2>
      <p>
       Fischer and Jaeschke
      </p>
    </div>
  </div>
  <div class="container left">
    <div class="date"></div>
    <i class="icon fa fa-user"></i>
    <div class="content">
      <h2>EMNLP-IJCNLP 2019</h2>
      <p>
        Schwab et al.
      </p>
    </div>
  </div>
  <div class="container right">
    <div class="date"></div>
    <i class="icon fa fa-running"></i>
    <div class="content">
      <h2>Frontiers in Artificial Intelligence 2022</h2>
      <p>
      Schwab et al.
      </p>
    </div>
  </div>
  <div class="container left">
    <div class="date"></div>
    <i class="icon fa fa-cog"></i>
    <div class="content">
      <h2>ICNSLP 2022</h2>
      <p>
        Schwab et al.
      </p>
    </div>
  </div>
  <div class="container right">
    <div class="date"></div>
    <i class="icon fa fa-certificate"></i>
    <div class="content">
      <h2>DHd 2023</h2>
      <p>
      Schwab and Fischer
      </p>
    </div>
  </div>
</div>


---

# Task

</br>

- Bisher: Fokus auf Extraktion von Vossantos oder Analyse der Source
- In diesem Paper: Analyse der Modifier
- Fragestellungen:
- In welche Themengebiete werden Attribute verschoben?
  - Welche Modifier/Gebiete dominieren?
  - ...


- Webapp zur Exploration

---

# Datensatz


--


## Annotierter Datensatz

</br>

- Vossanto Datensatz (Schwab et. al (2019, 2022))
1. regulärer Ausdruck: a/an/the [up to 10 words] of/for/among

   ➜ Kandidatensätze 
2. Check mit Wikidata Liste bestehend aus Namen und Aliase aller Entitäten mit ‘instance-of’ Eigenschaft 'human'

   ➜ Fokus auf Menschen 
3. Abgleich mit manuell erstellter Streichliste

   ➜ <s>the House of Commons</s> (vgl. [Homer Doliver House](https://www.wikidata.org/wiki/Q3139666))


<p style="text-align:left;"> <b>Ergebnis</b>: 6095 Sätze, 3115 davon enthalten Vossanto </p>


--

## Häufigste Modifier

</br>

| Modifier       | Anzahl |
|----------------|--------|
| his day        | 56     |
| his time       | 35     |
| Japan          | 32     |
| the 90s        | 21     |
| China          | 17     |
| our time       | 17     |
| tennis         | 16     |
| his generation | 16     |
| baseball       | 16     |
| her time       | 14     |

---

# Methoden


--

## 1. Embeddings

</br>

Berechnen kontextabhängiger Word Embeddings, d.h. numerische Repräsentation von Wörtern in Abhängigkeit der Nachbarwörter
- **S-BERT** (Sentence-Transformer)
  - BERT mit siamesischer Netzwerk-Architektur 
  - Effizientes Berechnen von semantischen Ähnlichkeiten

--

## 2. Clustering

</br>

Gruppieren der Embeddings
- **k-means** Algorithmus
  - gruppiert Daten in `k` Cluster
  - Annahme: wenig Ausreißer 
  - feste Anzahl der Cluster bei Berechnung </br>
  ➜ Vorteil: Durchführung und Analyse mit verschiedenen `k`

--

## 3. Themenzuordnung

</br>

Zuweisung von Themengebieten je Cluster
- Modifier bestehen meist aus kurzen Nominalphrasen (1-4 Wörter)
- “klassisches” Topic-Modeling nicht möglich aufgrund der Kürze der Phrasen
- Ausnutzen von WordNet und **WordNet Domains**:
  - Jedes Wort/Synset aus WordNet ist einer oder mehreren Domains zugeordnet (hierarchisch gegliedert)
  - Themengebiet = Am häufigsten vorkommende Domain in Cluster


Beispiel: 
quarterbacks, bull riding, harness track, BMX racing, golf, the Dolphins, … ➜ Sport


--

## 4. Visualisierung

</br>

Dimensionsreduktionsverfahren zur Visualisierung
- Reduktion von 768d zu 2d
- verschiedene Verfahren:
  - PCA (linear)
  - t-SNE (non-linear)
  - UMAP (non-linear)
  - IVIS (non-linear, neural-network based)
  - Kombinationen

--

##

</br>

---

# Erkenntnisse und Ausblick

--

## Erkenntnisse

</br>

- eindeutige Cluster (Kultur, Sport, Geographie)
- Spezieller Cluster: Temporal: Nicht domain-spezifisch
- viele Grenzfälle, z.B. MTV (Musik vs. TV), Irish theaterland (Geo vs. Kultur)
- Cluster splitten sich teilweise logisch aus (Kultur → Musik, Kunst, Literatur, Film/TV)
- [Webapp](https://vossanto.weltliteratur.net/dhd2023/modifier.html)

--

## Ausblick

</br>

- Sind temporale Vossantos unterschiedlich aufgebaut bzw. sind die Source-Target Paare in derselben Domain?
- Können Modifier und deren Kategorisierung zur Entdeckung von Vossantos beitragen?
- Wie sehen die Verbindungen zwischen Source und Modifier aus?
- …

