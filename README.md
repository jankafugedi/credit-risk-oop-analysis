# 🏦 Banki Hitelkockázati és Portfólió Elemző Rendszer (Python OOP & NumPy)

## 📌 Projekt Áttekintés
Ez a projekt egy komplex banki hitelbírálati és kockázatkezelési logikát valósít meg objektumorientált (OOP) szoftvertervezési elvek és nagy teljesítményű numerikus számítások (NumPy) ötvözésével. A modell a Kaggle *Credit Risk Dataset* több mint 32 000 hiteligénylési rekordját dolgozza fel, elvégzi az egyedi hitelképességi bírálatokat (DTI és kockázati score), valamint portfólió szintű tőkekitettséget aggregál.

---

## 📐 Rendszertervezés és Szoftverarchitektúra (Visual Paradigm UML)

A rendszer üzleti logikája és adatmodellje előzetesen **Visual Paradigm** segítségével lett megtervezve UML osztálydiagram (Class Diagram) formájában.

![UML Osztálydiagram](credit_risk_class_diagram.png)

### Főbb Osztályok és Felelősségek:
1. **`Customer`**: Az ügyfél demográfiai és pénzügyi paramétereit (életkor, jövedelem, munkaviszony hossza, lakhatási jogcím) enkapszulálja.
2. **`Loan`**: A hiteligénylés adatait (tőkeösszeg, kamatláb, futamidő, hitelcél) és az annuitásos törlesztési logikát kezeli.
3. **`CreditEvaluation`**: Hitelelbíráló motor, amely a jövedelem és a törlesztőrészlet alapján kiszámítja az eladósodottsági mutatót (**DTI - Debt-to-Income**), és üzleti határértékek mentén besorolja a kockázatot (*Low*, *Medium*, *High Risk*).
4. **`PortfolioRiskManager`**: Menedzsment szintű aggregátor osztály, amely összefogja a beérkező hitelkérelmeket, összegzi a teljes tőkekitettséget, és kimutatja a kockázati kategóriák megoszlását.

---

## ⚡ Pénzügyi Számítások és Vektorizáció (NumPy)

A hagyományos ciklusok helyett a havi törlesztőrészletek kiszámítása a teljes portfólióra vektorizált NumPy műveletekkel történik az annuitás képlet alapján:

$$PMT = PV \times \frac{r(1 + r)^n}{(1 + r)^n - 1}$$

* **$PV$**: Hitel összege (`loan_amnt`)
* **$r$**: Havi kamatláb ($\frac{\text{loan\_int\_rate}}{100 \times 12}$)
* **$n$**: Futamidő hónapokban ($n = 36$)

---

## 🛠️ Alkalmazott Technológiák
- **Nyelv:** Python 3 (Google Colab környezetben tesztelve)
- **Tervezés:** UML Class Diagram (Visual Paradigm)
- **Könyvtárak:** `numpy` (vektorizált pénzügyi kalkulációk), `pandas` (adattisztítás és adatelemzés), `dataclasses` (tiszta adatstruktúrák)
- **Adathalmaz:** Kaggle – *Credit Risk Dataset* (32 581 sor)

---

## 📂 Repozitórium Tartalma
- `credit_risk_analysis.ipynb`: A teljes, részletesen dokumentált és feliratozott Jupyter notebook az elemzéssel és kimenetekkel.
- `credit_risk_analysis.py`: A tiszta objektumorientált forráskód.
- `credit_risk_class_diagram.png`: A Visual Paradigmban exportált UML osztálydiagram.
