# Formalna Konstrukcja Arytmetyki

Niniejszy dokument stanowi dedukcyjny system arytmetyki. Wyprowadzamy liczby całkowite i wymierne, opierając się wyłącznie na aksjomatach liczb naturalnych i logice pierwszego rzędu. Każde twierdzenie wynika z aksjomatów lub twierdzeń udowodnionych wcześniej.

---

## I. Liczby Naturalne ($\mathbb{N}$)

Definiujemy zbiór $\mathbb{N}$ za pomocą aksjomatyki Peano.

### 1.1 Aksjomaty Peano
Przyjmujemy istnienie zbioru $\mathbb{N}$, wyróżnionego elementu $0$ oraz funkcji następnika $S: \mathbb{N} \to \mathbb{N}$.

1.  **Aksjomat 1:** $0 \in \mathbb{N}$.
2.  **Aksjomat 2:** Dla każdego $n \in \mathbb{N}$, $S(n) \in \mathbb{N}$.
3.  **Aksjomat 3:** Dla każdego $n \in \mathbb{N}$, $S(n) \neq 0$ (Zero nie jest następnikiem).
4.  **Aksjomat 4:** Funkcja $S$ jest różnowartościowa: $S(n) = S(m) \implies n = m$.
5.  **Aksjomat 5 (Indukcja):** Niech $K \subseteq \mathbb{N}$. Jeżeli $0 \in K$ oraz $\forall n (n \in K \implies S(n) \in K)$, to $K = \mathbb{N}$.

### 1.2 Definicja Dodawania (+)
Dodawanie definiujemy rekurencyjnie na podstawie aksjomatu indukcji.
Dla dowolnych $m, n \in \mathbb{N}$:

$$m + 0 := m$$

$$m + S(n) := S(m + n)$$

### 1.3 Definicja Jedynki
Definiujemy symbol $1$ jako następnik zera:

$$1 := S(0)$$

### 1.4 Definicja Mnożenia ($\cdot$)
Mnożenie definiujemy rekurencyjnie:

$$m \cdot 0 := 0$$

$$m \cdot S(n) := (m \cdot n) + m$$

### 1.5 Kluczowe Twierdzenia $\mathbb{N}$ (Baza dla dalszych działów)
Poniższe własności można udowodnić indukcją (pomijamy dowody indukcyjne dla zwięzłości, ale uznajemy je za udowodnione w tym punkcie, by móc z nich korzystać).

* **T1 (Łączność dodawania):** $(a + b) + c = a + (b + c)$
* **T2 (Przemienność dodawania):** $a + b = b + a$
* **T3 (Łączność mnożenia):** $(a \cdot b) \cdot c = a \cdot (b \cdot c)$
* **T4 (Przemienność mnożenia):** $a \cdot b = b \cdot a$
* **T5 (Element neutralny mnożenia):** $a \cdot 1 = a$
* **T6 (Rozdzielność mnożenia względem dodawania):** $a \cdot (b + c) = a \cdot b + a \cdot c$

---

## II. Liczby Całkowite ($\mathbb{Z}$)

Konstruujemy $\mathbb{Z}$ jako rozszerzenie $\mathbb{N}$, aby umożliwić odejmowanie.

### 2.1 Aksjomat Rozszerzenia i Elementu Przeciwnego
Rozszerzamy zbiór $\mathbb{N}$ do $\mathbb{Z}$, zachowując własności T1-T6, i wprowadzamy aksjomat:
Dla każdego $a \in \mathbb{Z}$ istnieje element przeciwny oznaczany $-a$, taki że:

$$a + (-a) = 0$$

### 2.2 Twierdzenie: Jednoznaczność zera w mnożeniu
Zanim przejdziemy do znaków, musimy sformalizować mnożenie przez zero w $\mathbb{Z}$.

**Twierdzenie:** $\forall a \in \mathbb{Z}, a \cdot 0 = 0$.
**Dowód:**
1. $0 + 0 = 0$ (z def. elementu neutralnego dodawania).
2. $a \cdot (0 + 0) = a \cdot 0$.
3. $a \cdot 0 + a \cdot 0 = a \cdot 0$ (z rozdzielności T6).
4. Dodajemy $-(a \cdot 0)$ do obu stron:
   $(a \cdot 0 + a \cdot 0) + (-(a \cdot 0)) = a \cdot 0 + (-(a \cdot 0))$.
5. Z łączności i def. elementu przeciwnego:
   $a \cdot 0 + 0 = 0$.
6. $a \cdot 0 = 0$. $\blacksquare$

### 2.3 Twierdzenie: Mnożenie przez -1
**Teza:** $(-1) \cdot a = -a$.
**Dowód:**
Musimy pokazać, że $(-1)a$ jest elementem przeciwnym do $a$, czyli że ich suma to $0$.

$$a + ((-1) \cdot a)$$

1. Zapiszmy $a$ jako $1 \cdot a$ (z T5):
   $$1 \cdot a + (-1) \cdot a$$

2. Z prawa rozdzielności (T6 wyciągamy $a$):
   $$(1 + (-1)) \cdot a$$

3. Z definicji elementu przeciwnego ($1 + (-1) = 0$):
   $$0 \cdot a$$

4. Z twierdzenia 2.2:
   $$0$$

Skoro suma wynosi $0$, to $(-1)a$ jest elementem przeciwnym do $a$, czyli $-a$. $\blacksquare$

### 2.4 Twierdzenie: Iloczyn liczb ujemnych
**Teza:** $(-1) \cdot (-1) = 1$.
**Dowód:**

1. Z twierdzenia 2.3 wiemy, że $(-1) \cdot a = -a$.
2. Podstawmy $a = -1$. Wtedy lewa strona to $(-1) \cdot (-1)$.
3. Prawa strona to $-(-1)$ (element przeciwny do $-1$).
4. Czym jest element przeciwny do $-1$? To taka liczba $x$, że $(-1) + x = 0$.
5. Wiemy, że $(-1) + 1 = 0$ (przemienność dodawania).
6. Zatem elementem przeciwnym do $-1$ jest $1$.
7. Stąd: $(-1) \cdot (-1) = 1$. $\blacksquare$

---

## III. Liczby Wymierne ($\mathbb{Q}$)

Konstruujemy $\mathbb{Q}$ jako rozszerzenie $\mathbb{Z}$, aby umożliwić dzielenie.

### 3.1 Aksjomat Elementu Odwrotnego
Rozszerzamy $\mathbb{Z}$ do ciała $\mathbb{Q}$. Dla każdego $a \in \mathbb{Q}, a \neq 0$ istnieje element odwrotny $a^{-1}$, taki że:

$$a \cdot a^{-1} = 1$$

### 3.2 Definicja Ułamka
Ułamek nie jest nowym bytem, jest notacją.

$$\frac{a}{b} := a \cdot b^{-1}$$

### 3.3 Lemat: Odwrotność iloczynu
Zanim pomnożymy ułamki, musimy znać własność odwrotności iloczynu.
**Teza:** $(x \cdot y)^{-1} = x^{-1} \cdot y^{-1}$.
**Dowód:**
Musimy pokazać, że $(x^{-1}y^{-1})$ pomnożone przez $(xy)$ daje $1$.

$$(x^{-1} \cdot y^{-1}) \cdot (x \cdot y)$$

1. Z przemienności i łączności mnożenia (T3, T4):
   $$(x^{-1} \cdot x) \cdot (y^{-1} \cdot y)$$

2. Z definicji elementu odwrotnego:
   $$1 \cdot 1$$

3. $$1$$

Zatem $(x^{-1}y^{-1})$ jest odwrotnością $(xy)$. $\blacksquare$

### 3.4 Twierdzenie: Mnożenie Ułamków
**Teza:** $\frac{a}{b} \cdot \frac{c}{d} = \frac{a \cdot c}{b \cdot d}$.
**Dowód:**

1. Z definicji notacji (3.2):
   $$(a \cdot b^{-1}) \cdot (c \cdot d^{-1})$$

2. Z przemienności i łączności mnożenia:
   $$(a \cdot c) \cdot (b^{-1} \cdot d^{-1})$$

3. Korzystając z Lematu 3.3 (podstawiając $x=b, y=d$):
   $$(a \cdot c) \cdot (b \cdot d)^{-1}$$

4. Z definicji notacji (traktując $(a \cdot c)$ jako licznik i $(b \cdot d)$ jako mianownik):
   $$\frac{a \cdot c}{b \cdot d}$$

$\blacksquare$

### 3.5 Twierdzenie: Rozszerzanie Ułamka
Potrzebne do dodawania.
**Teza:** $\frac{a}{b} = \frac{a \cdot k}{b \cdot k}$ dla $k \neq 0$.
**Dowód:**
Prawa strona z definicji mnożenia ułamków (Twierdzenie 3.4 odwrotnie) to:

$$\frac{a}{b} \cdot \frac{k}{k}$$

Z definicji ułamka $\frac{k}{k} = k \cdot k^{-1} = 1$.
Zatem:

$$\frac{a}{b} \cdot 1 = \frac{a}{b}$$

$\blacksquare$

### 3.6 Twierdzenie: Dodawanie Ułamków
**Teza:** $\frac{a}{b} + \frac{c}{d} = \frac{ad + bc}{bd}$.
**Dowód:**

1. Rozszerzamy pierwszy ułamek przez $d$, a drugi przez $b$ (na mocy Twierdzenia 3.5):
   $$\frac{ad}{bd} + \frac{cb}{db}$$

2. Ponieważ mnożenie w $\mathbb{Z}$ jest przemienne, $db = bd$:
   $$\frac{ad}{bd} + \frac{cb}{bd}$$

3. Z definicji notacji:
   $$ad \cdot (bd)^{-1} + cb \cdot (bd)^{-1}$$

4. Z rozdzielności mnożenia względem dodawania (T6 - wyciągamy czynnik $(bd)^{-1}$):
   $$(ad + cb) \cdot (bd)^{-1}$$

5. Z definicji notacji:
   $$\frac{ad + bc}{bd}$$

$\blacksquare$

### 3.7 Definicja i Twierdzenie o Dzieleniu
**Definicja:** $x : y$ to wynik mnożenia $x$ przez odwrotność $y$ (czyli $x \cdot y^{-1}$).

**Teza:** $\frac{a}{b} : \frac{c}{d} = \frac{a}{b} \cdot \frac{d}{c}$.
**Dowód:**

1. Z definicji dzielenia:
   $$\frac{a}{b} \cdot (\frac{c}{d})^{-1}$$

2. Czym jest odwrotność ułamka $(\frac{c}{d})^{-1}$? Szukamy liczby, która po pomnożeniu przez $\frac{c}{d}$ da $1$.
   Sprawdźmy $\frac{d}{c}$:
   $$\frac{c}{d} \cdot \frac{d}{c} = \frac{cd}{dc} = 1$$
   Zatem $(\frac{c}{d})^{-1} = \frac{d}{c}$.

3. Podstawiamy do punktu 1:
   $$\frac{a}{b} \cdot \frac{d}{c}$$

$\blacksquare$