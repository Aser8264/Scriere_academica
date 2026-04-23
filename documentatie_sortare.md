# Analiza Comparativă a Algoritmilor de Sortare

## Proiect: Scriere Academica
## Universitatea de Vest din Timișoara
## Facultatea de Informatică
## Realizat de: Bosioc Aser

---

## 1. Introducere

Această documentație prezintă un proiect realizat în limbajul C++, având ca scop studierea și compararea mai multor algoritmi de sortare din punct de vedere al timpului de execuție și al memoriei utilizate. Proiectul urmărește atât partea teoretică, prin descrierea principiului de funcționare al fiecărui algoritm, cât și partea practică, prin rularea unui benchmark pe seturi de date cu caracteristici diferite.

Sortarea reprezintă una dintre cele mai importante operații din informatică, deoarece apare frecvent în prelucrarea datelor, în optimizarea căutărilor și în organizarea informației. Din acest motiv, studiul comparativ al algoritmilor de sortare este relevant atât în context academic, cât și în aplicații reale.

În cadrul proiectului sunt analizate algoritmi clasici, dar și metode mai performante, folosite în practică. Programul generează seturi de date, rulează fiecare algoritm de mai multe ori, calculează un timp mediu de execuție și estimează memoria suplimentară necesară în timpul sortării.

## 2. Scopul proiectului

Scopul principal al proiectului este de a evidenția diferențele dintre algoritmii de sortare atunci când aceștia sunt aplicați pe date de dimensiuni și distribuții diferite.

Obiectivele urmărite sunt:

- implementarea mai multor algoritmi de sortare în același proiect;
- compararea performanței lor în condiții identice;
- observarea influenței tipului de date de intrare asupra performanței;
- estimarea memoriei suplimentare folosite de fiecare metodă;
- generarea unui fișier de rezultate care poate fi folosit în analize ulterioare sau în realizarea de grafice.

## 3. Descriere generală a aplicației

Aplicația este implementată în fișierul [sort/main.cpp](C:/Users/aserb/Desktop/faculta/Scriere_academica/sort/main.cpp:1). Ea conține:

- implementările algoritmilor de sortare;
- generatori de date pentru mai multe scenarii de test;
- o funcție de verificare a corectitudinii sortării;
- mecanismul de benchmark bazat pe `std::chrono`;
- exportul rezultatelor în fișierul [sort/results.csv](C:/Users/aserb/Desktop/faculta/Scriere_academica/sort/results.csv:1).

Programul parcurge toate combinațiile dintre algoritmi, tipuri de date și dimensiuni ale vectorilor. Pentru fiecare combinație, creează o copie a datelor inițiale, rulează algoritmul de un număr de ori adaptat dimensiunii problemei și calculează media timpilor obținuți.

## 4. Algoritmii implementați

În versiunea actuală a proiectului sunt implementați nouă algoritmi de sortare:

- Bubble Sort
- Insertion Sort
- Selection Sort
- Merge Sort
- Quick Sort
- Heap Sort
- Shell Sort
- Radix Sort
- IntroSort

### 4.1. Bubble Sort

Bubble Sort compară elementele vecine și le interschimbă atunci când acestea sunt în ordine greșită. Procesul se repetă până când vectorul devine complet sortat.

Caracteristici:

- este unul dintre cei mai simpli algoritmi de înțeles și implementat;
- are performanță slabă pentru seturi mari de date;
- funcționează acceptabil doar pentru exemple foarte mici sau pentru scopuri didactice.

Complexitate:

- caz favorabil: `O(n)` dacă vectorul este deja sortat și implementarea detectează lipsa schimbărilor;
- caz mediu: `O(n^2)`;
- caz nefavorabil: `O(n^2)`;
- memorie suplimentară: `O(1)`.

### 4.2. Insertion Sort

Insertion Sort construiește treptat o porțiune sortată a vectorului. Fiecare element nou este inserat la poziția corectă printre elementele deja ordonate.

Caracteristici:

- este eficient pentru vectori mici;
- se comportă bine pe date aproape sortate;
- este frecvent folosit ca subrutină în algoritmi mai sofisticați.

Complexitate:

- caz favorabil: `O(n)`;
- caz mediu: `O(n^2)`;
- caz nefavorabil: `O(n^2)`;
- memorie suplimentară: `O(1)`.

### 4.3. Selection Sort

Selection Sort caută minimul din partea nesortată a vectorului și îl mută pe poziția următoare din partea sortată. Procesul continuă până la ordonarea completă.

Caracteristici:

- este simplu de implementat;
- execută puține interschimbări;
- rămâne lent pentru volume mari de date, deoarece numărul de comparații este ridicat.

Complexitate:

- caz favorabil: `O(n^2)`;
- caz mediu: `O(n^2)`;
- caz nefavorabil: `O(n^2)`;
- memorie suplimentară: `O(1)`.

### 4.4. Merge Sort

Merge Sort aplică paradigma divide et impera. Vectorul este împărțit recursiv în jumătăți, apoi subvectorii rezultați sunt interclasați în ordine.

Caracteristici:

- oferă performanță stabilă și predictibilă;
- este foarte bun pentru seturi mari de date;
- necesită memorie auxiliară liniară pentru interclasare.

Complexitate:

- caz favorabil: `O(n log n)`;
- caz mediu: `O(n log n)`;
- caz nefavorabil: `O(n log n)`;
- memorie suplimentară: `O(n)`.

### 4.5. Quick Sort

Quick Sort alege un pivot și rearanjează elementele astfel încât valorile mai mici să ajungă înaintea pivotului, iar cele mai mari după acesta. Algoritmul se aplică apoi recursiv pe subsecțiunile rezultate.

Caracteristici:

- în practică este foarte rapid pentru multe tipuri de date;
- poate avea performanță foarte bună la cost mic de memorie;
- poate suferi degradări în anumite cazuri nefavorabile, în funcție de alegerea pivotului.

Complexitate:

- caz favorabil: `O(n log n)`;
- caz mediu: `O(n log n)`;
- caz nefavorabil: `O(n^2)`;
- memorie suplimentară: `O(log n)`.

### 4.6. Heap Sort

Heap Sort transformă vectorul într-un heap, apoi extrage repetat elementul maxim și îl plasează la finalul vectorului.

Caracteristici:

- are complexitate garantată `O(n log n)`;
- nu necesită memorie auxiliară liniară;
- în practică poate fi mai lent decât Quick Sort sau IntroSort.

Complexitate:

- caz favorabil: `O(n log n)`;
- caz mediu: `O(n log n)`;
- caz nefavorabil: `O(n log n)`;
- memorie suplimentară: `O(1)`.

### 4.7. Shell Sort

Shell Sort este una dintre cele trei metode noi adăugate în proiect. Algoritmul pornește de la ideea lui Insertion Sort, dar compară elemente aflate la o anumită distanță, numită gap. Acest gap este redus treptat până când ajunge la 1.

Caracteristici:

- este mai rapid decât algoritmii clasici pătratici în multe situații;
- se potrivește bine pentru dimensiuni medii;
- performanța sa depinde de șirul de gap-uri ales.

Complexitate:

- depinde de implementare și de secvența de pași;
- în practică este considerat semnificativ mai bun decât `O(n^2)`;
- memorie suplimentară: `O(1)`.

### 4.8. Radix Sort

Radix Sort este a doua metodă nouă introdusă în proiect. În această implementare, sortarea este realizată pe octeți, de la partea cea mai puțin semnificativă la partea cea mai semnificativă. Pentru a trata corect numerele întregi semnate, se aplică o transformare internă asupra bitului de semn.

Caracteristici:

- este foarte eficient pentru date numerice întregi;
- poate depăși clar metodele bazate pe comparații pentru volume mari;
- are nevoie de memorie auxiliară suplimentară pentru buffer și vectorul de frecvențe.

Complexitate:

- timp: `O(k * n)`, unde `k` este numărul de pași necesari pentru reprezentarea valorilor;
- memorie suplimentară: `O(n)`.

### 4.9. IntroSort

IntroSort este a treia metodă nouă adăugată și este reprezentată prin `std::sort`. Acest algoritm combină avantajele mai multor strategii și comută automat între ele pentru a evita cazurile foarte nefavorabile.

Caracteristici:

- este una dintre cele mai bune alegeri practice pentru uz general;
- beneficiază de optimizările bibliotecii standard C++;
- oferă un reper realist pentru performanța sortării din aplicații reale.

Complexitate:

- caz favorabil: `O(n log n)`;
- caz mediu: `O(n log n)`;
- caz nefavorabil: `O(n log n)`;
- memorie suplimentară: aproximativ `O(log n)`.

## 5. Tabel comparativ al algoritmilor

| Algoritm | Tip de metodă | Timp mediu | Memorie suplimentară | Observație principală |
| --- | --- | --- | --- | --- |
| Bubble Sort | comparații | `O(n^2)` | `O(1)` | foarte lent pentru date mari |
| Insertion Sort | comparații | `O(n^2)` | `O(1)` | bun pe date aproape sortate |
| Selection Sort | comparații | `O(n^2)` | `O(1)` | simplu, dar ineficient |
| Merge Sort | divide et impera | `O(n log n)` | `O(n)` | stabil și predictibil |
| Quick Sort | divide et impera | `O(n log n)` | `O(log n)` | foarte rapid în practică |
| Heap Sort | structură heap | `O(n log n)` | `O(1)` | robust, dar uneori mai lent |
| Shell Sort | inserare cu gap | aproximativ sub-pătratic | `O(1)` | bun pentru dimensiuni medii |
| Radix Sort | necomparativ | `O(k * n)` | `O(n)` | excelent pentru întregi |
| IntroSort | hibrid | `O(n log n)` | `O(log n)` | optimizat pentru uz general |

## 6. Datele de test folosite

Pentru a obține o comparație relevantă, programul nu testează algoritmii pe un singur tip de intrare, ci pe mai multe distribuții de date:

- `Random` pentru valori aleatoare;
- `Sorted` pentru date deja ordonate crescător;
- `Reverse` pentru date ordonate descrescător;
- `NearlySorted` pentru date aproape sortate;
- `FewUnique` pentru date cu multe repetiții și puține valori distincte.

Aceste scenarii sunt importante deoarece un algoritm poate avea rezultate foarte bune pe un anumit tip de date și mult mai slabe pe altul. De exemplu, Insertion Sort este avantajat de datele aproape sortate, în timp ce algoritmii pătratici devin rapid ineficienți pe intrări aleatoare mari.

## 7. Dimensiunile de intrare

Benchmark-ul din proiect testează mai multe dimensiuni ale vectorilor, pentru a surprinde atât comportamentul pe cazuri mici, cât și pe cazuri mai mari.

În implementarea din directorul `sort`, dimensiunile urmărite sunt:

`10, 20, 50, 100, 500, 1000, 5000, 10000`

Pentru dimensiuni mici se execută multe iterații, astfel încât media timpilor să fie mai relevantă. Pentru dimensiuni mai mari, numărul de iterații scade, pentru a menține timpul total de benchmark într-o zonă rezonabilă.

## 8. Metodologia de măsurare

Timpul de execuție este măsurat cu ajutorul bibliotecii `chrono`, folosind `high_resolution_clock`. Pentru fiecare test:

- se generează vectorul sursă;
- se copiază datele într-un vector de lucru;
- se rulează algoritmul de sortare;
- se repetă procesul de mai multe ori;
- se calculează media în nanosecunde.

Pe lângă timp, programul verifică dacă vectorul rezultat este într-adevăr sortat. Această etapă este importantă, deoarece un benchmark este relevant doar dacă algoritmii produc rezultate corecte.

Programul estimează și memoria totală utilizată:

- memoria vectorului inițial;
- memoria auxiliară specifică algoritmului;
- memoria totală rezultată din suma celor două valori.

## 9. Structura fișierului de rezultate

Fișierul CSV generat conține următoarele coloane:

- `Algorithm` pentru numele algoritmului;
- `DataType` pentru tipul datelor de intrare;
- `Size` pentru dimensiunea vectorului;
- `Iterations` pentru numărul de rulări folosite la calculul mediei;
- `AvgTime_ns` pentru timpul mediu în nanosecunde;
- `ArrayMemory_bytes` pentru memoria ocupată de vector;
- `ExtraMemory_bytes` pentru memoria auxiliară estimată;
- `TotalMemory_bytes` pentru memoria totală estimată.

Acest format permite filtrarea și compararea ușoară a rezultatelor în aplicații precum Excel, LibreOffice Calc sau în scripturi Python.

## 10. Interpretarea rezultatelor

Pe baza rulărilor efectuate, se observă câteva concluzii importante:

- algoritmii pătratici, precum Bubble Sort, Insertion Sort și Selection Sort, devin rapid neperformanți pe măsură ce dimensiunea datelor crește;
- Insertion Sort rămâne totuși competitiv pe date aproape sortate, unde numărul de mutări necesare este redus;
- Merge Sort, Quick Sort, Heap Sort și IntroSort oferă rezultate mult mai bune pe seturi mari;
- Shell Sort se poziționează între metodele simple și algoritmii moderni, fiind o alegere rezonabilă pentru dimensiuni medii;
- Radix Sort are rezultate foarte bune pe valori întregi și poate depăși clar metodele bazate strict pe comparații;
- IntroSort reprezintă o referință practică solidă, deoarece reflectă soluția optimizată din biblioteca standard.

Într-o analiză academică, aceste rezultate arată clar că alegerea algoritmului nu trebuie făcută doar după ușurința implementării, ci și după natura datelor și resursele disponibile.

## 11. Avantajele proiectului

Proiectul are mai multe avantaje din punct de vedere didactic și practic:

- reunește într-un singur program mai multe paradigme de sortare;
- permite comparații directe între algoritmi;
- oferă un fișier de ieșire ușor de analizat;
- poate fi extins simplu cu noi metode sau noi tipuri de date;
- poate servi drept bază pentru un raport academic sau pentru prezentări.

## 12. Posibile îmbunătățiri

Proiectul poate fi dezvoltat în continuare prin:

- adăugarea unor grafice generate automat;
- testarea pe dimensiuni și mai mari;
- introducerea unor algoritmi suplimentari, precum Counting Sort sau TimSort;
- exportul rezultatelor și în formate suplimentare;
- realizarea unei interfețe grafice pentru selectarea testelor.

## 13. Compilare și rulare

Un exemplu de compilare este:

```bash
g++ -std=c++17 -O2 main.cpp -o benchmark_sort
```

Rularea programului se face astfel:

```bash
./benchmark_sort
```

După execuție, fișierul `results.csv` este generat sau actualizat automat.

## 14. Concluzie

Proiectul demonstrează în mod clar diferențele dintre algoritmii de sortare clasici și cei mai performanți. Algoritmii simpli sunt utili pentru învățare și pentru intrări mici, însă pentru volume mai mari devine necesară utilizarea unor metode mai eficiente, precum Merge Sort, Quick Sort, Radix Sort sau IntroSort.

Din perspectivă academică, proiectul este relevant deoarece combină teoria algoritmilor cu măsurători practice și oferă o bază solidă pentru formularea unor concluzii argumentate privind performanța și consumul de memorie.
