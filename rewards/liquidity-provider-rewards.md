---
description: Überblick über das Prämienprogramm für Liquiditätsanbieter.
---

#

Zunächst wurden **7,5 %** (`75.000.000 $ethDYDX`)  des Token-Angebots  für LP-Prämien bereitgestellt.

* In [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md) hat die dYdX-Community [dafür gestimmt](https://dydx.community/dashboard/proposal/14), die Prämien für Liquiditätsanbieter von `1.150.685 $ethDYDX` pro Epoche um 50 % auf `575.343 $ethDYDX` pro Epoche zu reduzieren. Infolgedessen sank die Zuteilung für LP-Prämien von `7,5 %` auf `5,2 %`.
*   In [DIP 29](https://dydx.community/dashboard/proposal/16)  hat die dYdX-Community [dafür gestimmt](https://dydx.community/dashboard/proposal/16), die Prämien für Liquiditätsanbieter von Epoch 30-32 auf dYdX v3 um ⅓ auf die folgenden Werte zu reduzieren:

    * Epoche 30: 383.562 $ethDYDX
    * Epoche 31: 191.781 $ethDYDX
    * Epoche 32: 0 $ethDYDX

    Nach Epoch 31 wird es keine Prämien für Liquiditätsanbieter auf dYdX v3 geben. In der Folge sank die Zuteilung für Prämien für Liquiditätsanbieter von `5,2 %` auf `3,2 %`.

Da es keine Verteilung von Prämien für Liquiditätsanbieter auf dYdX Chain gibt, hat die dYdX-Community in DIP 29 dafür gestimmt, die verbleibende Zuteilung von Prämien für Liquiditätsanbieter in die dYdX Chain Community Treasury zu migrieren.

**Ziele**

* Verbessern Sie die zweiseitige Liquidität und belohnen Sie Liquiditätsanbieter programmatisch.

## **Überblick**

Um Anreize für die Marktliquidität zu schaffen, werden $ethDYDX an Liquiditätsanbieter auf der Grundlage von Formeln verteilt, die die Teilnahme an Märkten, das Maker-Volumen, die zweiseitige Tiefe, den Spread (im Vergleich zum Mid-Market) und die Betriebszeit auf dYdX v3 belohnen.

In [DIP 15](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-15.md) hat die dYdX-Gemeinschaft dafür gestimmt, die Formel für die LP-Vergütung zu überarbeiten, indem die Funktionen für BTC/ETH-Märkte und Nicht-BTC/ETH-Märkte aufgeteilt werden. In [DIP 19](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-19.md)stimmte die dYdX-Gemeinschaft dafür, das Gewicht von 0,05 stkDYDX dem Maker-Volumen zuzuweisen.

Die Höhe des verdienten ethDYDX wird durch den relativen Anteil des $$Q_{FINAL}$$  ($$Q_{BTC}$$+$$Q_{ETH}$$+$$Q_{non BTC/ETH}$$) jedes Teilnehmers bestimmt.

<figure><img src="../.gitbook/assets/Updated LP Rewards Formulas.png" alt=""><figcaption></figcaption></figure>

Aufträge unter einer bestimmten **Mindesttiefe** (Größe) ($$MinDepth$$) pro Markt sind ausgeschlossen, und Aufträge über einem bestimmten **maximalen Spread **(Mid-Market-Spread) ($$MaxSpread$$) Markt sind ebenfalls ausgeschlossen.

Bei minütlichen Stichproben hat jede Epoche 28 Tage \* 24 Stunden \* 60 Minuten an Datenpunkten – insgesamt 40.320 Datenpunkte pro Epoche.

Liquiditätsanbieter verdienen monatliche Prämien basierend auf ihrem relativen Anteil von $$Q_{FINAL}$$ pro Epoche.

Die obige Formel wird unten in schrittweise Berechnungen für Details unterteilt:

| _Macher-Volumen_ | Gesamt-Macher-Volumen für die Epoche. |
| --------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <img src="../.gitbook/assets/1-qbid-formula.png" alt="" data-size="original"> | <p></p>Angenommen, ein Liquiditätsanbieter hat mehrere offene Gebotsaufträge (1 BTC zu 29.900 $, 5 BTC zu 29.850 $, 10 BTC zu 29.500 $) im BTC-USD-Auftragsbuch und BTC liegt derzeit bei 30.000 $ (basierend auf der Marktmitte). Angenommen, MinDepth beträgt 5.000 USD und MaxSpread gegenüber dem Mittelstand 200 USD oder 67 Basispunkte (200 USD/30.000 USD). Ein BP ist ein Hundertstel von einem Prozent.<br><p></p><span class="math">Q_{BID} = (1\ \times \left(\frac{$29.900}{$100/30000}\right)) + (5\ \times \left(\frac{$29.850}{$150/30000}\right))</span><p></p><br><span class="math">Q_{BID}</span> wird jede Minute per Zufallsstichprobe berechnet.<br> |
| <img src="../.gitbook/assets/1-qask-formula.png" alt="" data-size="original"> | <p></p>Angenommen, ein Liquiditätsanbieter hat mehrere offene Briefaufträge (0,1 BTC zu 30.100 $, 5 BTC zu 30.150 $, 10 BTC zu 30.175 $) im BTC-USD-Auftragsbuch und BTC wird derzeit bei 30.000 $ gehandelt (basierend auf der Marktmitte). Angenommen, MinDepth beträgt 5.000 USD und MaxSpread gegenüber dem Mittelstand 200 USD oder 67 Basispunkte (200 USD/30.000 USD). Ein BP ist ein Hundertstel von einem Prozent.<p></p><span class="math">Q_{ASK} = (5\ \times \left(\frac{$30,150}{$150/30000}\right)) + (10\ \times \left(\frac{$30,175}{$175/30000}\right))</span><p></p><br><span class="math">Q_{ASK}</span> wird jede Minute in einem zufälligen Intervall berechnet. |
| <img src="../.gitbook/assets/1-qmin-formula.png" alt="" data-size="original"> | <p></p>Belohnt 2-seitige Liquidität, indem das Minimum von <span class="math">Q_{BID}</span> und <span class="math">Q_{ASK}</span> genommen wird.<br><p></p>Berechnet jede Minute. |
| <img src="../.gitbook/assets/1-qpoech-formula.png" alt="" data-size="original"> | $$Q_{EPOCH}$$ ist die Summe aller $$Q_{MIN}$$ in einer gegebenen Epoche. |
| <img src="../.gitbook/assets/1-q-uptime-epoch-formula.png" alt="" data-size="original"> | $$Uptime_{EPOCH}$$ ist die Zeit in einer Epoche, in der ein bestimmter Marktmacher live war und sowohl auf der Geld- als auch auf der Briefseite mit Auftragsgrößen notierte, die größer als das angegebene Auftragsminimum (unten nach Markt angegeben) und Spreads kleiner als das angegebene Spread-Maximum waren (unten nach Markt notiert). |
| <img src="../.gitbook/assets/1-qfinal-epoch-formula.png" alt="" data-size="original"> | $$Q_{FINAL}$$normalisiert $$Q_{EPOCH}$$, um die Betriebszeit zu berücksichtigen |

Jeder Markt wird seinen eigenen Belohnungspool haben, der unterschiedlich gewichtet wird. In [DIP 15](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-15.md) hatte die dYdX-Community dafür gestimmt, die Zuteilung der Gesamtbelohnungen in BTC-USD und ETH-USDC auf jeweils 10 % zu verringern. Der anfängliche Satz von Gewichtungen, der auf jeden Markt angewendet wird, lautet wie folgt:

| Markt | % Zuteilung des Gesamtprämienpools |
| ----------------------- | ---------------------------------------------------------------- |
| BTC-USD | 10 % |
| ETH-USD | 10 % |
| Andere ewige Märkte | ![](../.gitbook/assets/1-other-perpetual-markets-lp-weights.png) |

## FAQ

<details>

<summary>Wer hat Anspruch auf Prämien von Liquiditätsanbietern?</summary>

Alle Liquiditätsanbieter, die in der vorherigen Epoche mindestens 0,25 % des Herstellervolumens auf dYdX v3 erreicht haben, sind berechtigt, ethDYDX als Belohnung in einer bestimmten Epoche zu erhalten.

dYdX v3 ist nicht für Liquiditätsanbieter in den Vereinigten Staaten oder in den eingeschränkten Gebieten verfügbar, wie in den [Nutzungsbedingungen](https://dydx.exchange/terms) von dYdX Trading Inc. definiert.

</details>

<details>

<summary>Wie viel $ethDYDX habe ich im Rahmen des Bonusprogramms für Liquiditätsanbieter verdient?</summary>

In einer bestimmten Epoche erzielen Liquiditätsanbieter Renditen basierend auf ihren relativen $$Q_{SCORE}$$ auf dem Markt eines bestimmten Paares. Jedes Paar hat seinen eigenen relativen Belohnungsbetrag, der von der Governance festgelegt wird. Der erwartete Betrag an verdienten ethDYDX wird im [LP-Rewards Dashboard](https://p.datadoghq.com/sb/dc160ddf0-b32271920202875868dc46be6b66cf87?tpl\_var\_Market=btc\&from\_ts=1661805073576\&to\_ts=1661891473576\&live=true) angezeigt und kann auf Grundlage der Anzahl der beteiligten Liquiditätsanbieter, des relativen $$$Q_{SCORE}$$ und der Höhe der für ein bestimmtes Paar verfügbaren Rewards ermittelt werden.

</details>

<details>

<summary>Wie beanspruche ich meine Liquidity-Provider-Prämien?</summary>

Belohnungen für Liquiditätsanbieter werden in der [dYdX API](https://docs.dydx.exchange/) aufgestellt. Obwohl sie nicht auf der Governance-Benutzeroberfläche aufgetaucht sind, können sie [hier](https://dydx.community/dashboard) immer noch über die Governance am Ende jeder Epoche beansprucht werden.

</details>

<details>

<summary>Wann kann ich meine beanspruchten $ethDYDX Liquidity-Provider-Prämien abheben und übertragen?</summary>

Die über das Liquidity-Provider-Prämienprogramm gewährten $ethDYDX-Token werden nach Ablauf der anfänglichen Übertragungssperre anspruchsberechtigt und übertragbar.

Ab Epoche 1 können $ethDYDX-Token, die über das Liquidity-Provider-Prämienprogramm gewährt werden, `7 Tage` (**Wartezeit**) nach dem Ende jeder Epoche eingefordert werden.

</details>

<details>

<summary>Wie werden zweiseitige Tiefe, Geld-Brief-Spanne und Betriebszeit definiert und gemessen?</summary>

* **Zweiseitige Tiefe**



* **Mittlerer Markt-Spread**



* **Betriebszeit**

Die Verfügbarkeit von Liquiditätsanbietern ist für die Märkte von entscheidender Bedeutung, insbesondere in Zeiten hoher Volatilität. Durch die Anwendung eines Exponenten von 5 auf $$Uptime_{epoch}$$ als Eingabe für $$Q_{FINAL}$$ werden die Belohnungen in Richtung Liquiditätsanbieter verschoben, die ständig zweiseitige Liquidität aufrechterhalten. Mit anderen Worten, ein Liquiditätsanbieter, der 99 % der Zeit Betriebszeit bietet, ist exponentiell wertvoller als ein Liquiditätsanbieter, der 90 % Betriebszeit bietet.



</details>

<details>

<summary>Wie werden die maximalen Spreads pro Markt definiert?</summary>

Es werden keine $$Q_{BID}$$ oder $$Q_{ASK}$$ generiert, wenn der Spread über dem $$MaxSpread$$ eines bestimmten Marktes liegt.

Die anfänglichen maximalen Spreads sind wie folgt:

*
*
*

</details>

<details>

<summary>Wie wird die minimale Tiefe (Größe) pro Markt definiert?</summary>

Es werden keine $$Q_{BID}$$ oder $$Q_{ASK}$$ generiert, wenn die Größe unter der $$MinDepth$$ eines bestimmten Marktes liegt.

Die anfänglichen Mindesttiefen sind wie folgt:

*
*
*

</details>

