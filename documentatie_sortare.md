# Documentație - Analiza algoritmilor de sortare

## 1. Scopul proiectului

Proiectul are ca obiectiv compararea performanței mai multor algoritmi de sortare, folosind aceleași tipuri de date și aceleași dimensiuni de intrare. Pentru fiecare algoritm sunt măsurate:

- timpul mediu de execuție;
- memoria ocupată de vectorul de intrare;
- memoria suplimentară necesară în timpul sortării;
- memoria totală estimată.

Rezultatele sunt salvate în fișierul `results.csv`, pentru a putea fi analizate ulterior în Excel, Python sau alte instrumente de prelucrare.

## 2. Algoritmii implementați

În proiect sunt implementați următorii algoritmi:

| Algoritm | Idee principală | Complexitate timp (medie) | Memorie suplimentară |
| --- | --- | --- | --- |
| Bubble Sort | Compară elementele vecine și le interschimbă repetat | O(n^2) | O(1) |
| Insertion Sort | Inserează fiecare element în poziția corectă în partea deja sortată | O(n^2) | O(1) |
| Selection Sort | Alege minimul din partea nesortată și îl mută în față | O(n^2) | O(1) |
| Merge Sort | Împarte vectorul în subprobleme și interclasează rezultatele | O(n log n) | O(n) |
| Quick Sort | Alege un pivot și partitionează vectorul în jurul lui | O(n log n) | O(log n) |
| Heap Sort | Construiește un heap și extrage repetat maximul | O(n log n) | O(1) |
| Shell Sort | Generalizează Insertion Sort folosind intervale mai mari între comparații | aproximativ O(n^1.5) | O(1) |
| Radix Sort | Sortează pe cifre sau octeți, de la semnificația mică la cea mare | O(k * n) | O(n) |
| IntroSort | Folosește implementarea `std::sort`, optimizată pentru uz general | O(n log n) | O(log n) |

## 3. Metodele noi adăugate

Față de varianta inițială, au fost introduse trei metode noi de sortare:

### Shell Sort

Shell Sort este o extensie a lui Insertion Sort. În loc să compare doar elemente vecine, algoritmul începe cu distanțe mai mari între poziții și reduce treptat acest pas până la 1. În practică, această abordare reduce mult numărul de mutări comparativ cu metodele clasice pătratice.

### Radix Sort

Radix Sort este potrivit pentru valori întregi. Implementarea din proiect procesează valorile pe octeți și folosește o transformare internă pentru a ordona corect și numerele semnate. Avantajul principal este viteza foarte bună pentru volume mari de date, în schimb necesită memorie auxiliară liniară.

### IntroSort

IntroSort este reprezentat prin `std::sort`, algoritmul standard din biblioteca C++. În majoritatea implementărilor, acesta pornește ca Quick Sort, dar schimbă strategia atunci când detectează cazuri nefavorabile, pentru a evita degradarea puternică a performanței. Este util ca reper practic, deoarece reflectă soluția folosită frecvent în aplicații reale.

## 4. Tipurile de date testate

Benchmark-ul rulează fiecare algoritm pe mai multe distribuții de date:

- `Random` - valori aleatoare;
- `Sorted` - valori deja ordonate crescător;
- `Reverse` - valori ordonate descrescător;
- `NearlySorted` - vector aproape sortat, cu un număr mic de interschimbări;
- `FewUnique` - multe elemente repetate, cu puține valori distincte.

Aceste seturi permit observarea comportamentului algoritmilor atât în cazuri favorabile, cât și în cazuri dificile.

## 5. Dimensiunile testate

În proiectul din directorul `sort` sunt evaluate următoarele dimensiuni:

`10, 20, 50, 100, 500, 1000, 5000, 10000, 50000`

Pentru algoritmii foarte lenți, benchmark-ul poate sări automat peste dimensiuni prea mari. De exemplu, metodele de complexitate pătratică sunt limitate pentru a evita timpi de rulare nerezonabili.

## 6. Structura rezultatelor

Fișierul `results.csv` conține coloanele:

- `Algorithm` - numele algoritmului;
- `DataType` - tipul de date de intrare;
- `Size` - dimensiunea vectorului;
- `Iterations` - numărul de rulări folosite pentru medie;
- `AvgTime_ns` - timpul mediu, în nanosecunde;
- `ArrayMemory_bytes` - memoria vectorului de intrare;
- `ExtraMemory_bytes` - memoria auxiliară estimată;
- `TotalMemory_bytes` - suma memoriei de bază și a celei auxiliare.

## 7. Compilare și rulare

Exemplu de compilare cu `g++`:

```bash
g++ -std=c++17 -O2 main.cpp -o benchmark_sort
```

Rulare:

```bash
./benchmark_sort
```

După rulare, programul generează sau suprascrie fișierul `results.csv`.

## 8. Observații finale

Acest proiect este util pentru:

- compararea practică a algoritmilor de sortare;
- observarea diferențelor dintre complexitatea teoretică și comportamentul real;
- realizarea de grafice și concluzii pentru un raport academic;
- exersarea noțiunilor de analiză a timpului și memoriei.

Pentru extinderi viitoare, proiectul poate include grafice automate, export în formate suplimentare sau teste pe seturi de date mai variate.
