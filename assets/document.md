# Cel ćwiczenia

Proszę rozwiązać problem (tzn. znaleźć funkcje falowe) cząstki o energii E > 0 padającej na barierę potencjału o wysokości $V_0$ i szerokości d:

$$
V(x) = \left\{
\begin{array}{ll}
0 & \text{dla } x < 0 \text{ i } x > d \\
V_0 & \text{dla } 0 \leq x \leq d
\end{array}
\right.
$$

Dodatkowo proszę znaleźć współczynniki transmisji T i odbicia R cząstki padającej na barie-
rę. Własnoręcznie zapisane rozwiązania należy oddać na zajęciach, będą one ocenione jako
aktywność (0-3 pkt.).

# Rozważenia wstępne

Przekształcam niezależne od czasu równanie Schrödingera:

$$
- \frac{\hbar^2}{2m} \frac{\partial^2 \psi}{\partial x^2} + V \psi = E \psi \\
- \frac{\hbar^2}{2m} \frac{\partial^2 \psi}{\partial x^2} = (E - V) \psi \\
\frac{\partial^2 \psi}{\partial x^2} = - \frac{2m}{\hbar^2} (E - V) \psi \\
\frac{\partial^2 \psi}{\partial x^2} = \frac{2m}{\hbar^2} (V - E) \psi \\
\frac{\partial^2 \psi}{\partial x^2} - \frac{2m}{\hbar^2} (V - E) \psi  = 0\\
$$ (rs)

```{important}
Definiuję stałe $k_1$ i $k_2$ w następujący sposób:

$$
k_1^2 = \frac{2m}{\hbar^2} E \\
k_2^2 = \frac{2m}{\hbar^2} (V_0 - E) \\
$$ (k)
```

## Ogólne rozwiązanie równania Schrödingera

Rozważam następujący rysunek.

```{raw} latex
\begin{figure}[H]
\centering
\begin{tikzpicture}
\fill[gray!20!white] (5,0) rectangle (7, 5);
\draw (0,0) -- (5,0) -- (5,5) -- (7, 5) -- (7,0) -- (12,0);
\node[anchor=north] at (5, 0) {0};
\node[anchor=north] at (7, 0) {a};
\node at (6, 2.5) {$V_0$};
\end{tikzpicture}
\caption{Bariera potencjału}
\end{figure}
```

Należy zapisać Równanie {eq}`rs` dla trzech przypadków:

### $x < 0$

$V = 0$, więc (biorąc pod uwagę {eq}`k`) jest:

$$
\frac{\partial^2 \psi}{\partial x^2} + k_1^2 \psi  = 0\\
$$

Rozwiązaniem tak zdefiniowanego równania jest funcja w postaci:

$$
\psi_1(x) = A e^{i k_1 x} + B e^{-i k_1 x}
$$ (psi1)

Warto zauważyć, że wyraz $A e^{i k_1 x}$ odpowiada jest za ruch cząstki w prawo (ku barierze potencjału),
natomiast $B e^{-i k_1 x}$ opisuje falę odbitą.

```{raw} latex
\begin{figure}[H]
\centering
\begin{tikzpicture}
\fill[gray!20!white] (2,0) rectangle (3, 2);
\draw (0,0) -- (2,0) -- (2,2) -- (3, 2) -- (3,0) -- (5,0);
\node[anchor=north] at (2, 0) {0};
\node[anchor=north] at (3, 0) {a};
\node at (2.5, 1) {$V_0$};
    \draw[domain=0:2, samples=100]
        plot (\x, {0.3*sin(10 * \x r) + 1})
        plot (\x, {0.1*sin(15 * \x r) + 0.5});
    \draw[<-] (0.1, 0.2) -- (0.5, 0.2);
    \draw[->] (0.1, 1.5) -- (0.5, 1.5);
\end{tikzpicture}
\caption{Fala padająca i odbita}
\end{figure}
```

### $x \in [0, a]$

Dla tego przypadku równanie {eq}`rs` przyjmuje postać:

$$
\frac{\partial^2 \psi}{\partial x^2} - k_2^2 \psi  = 0\\
$$

Takie równanie ma rozwiązanie w postaci:

$$
\psi_2(x) = C e^{k_2 x} + D e^{-k_2 x}
$$ (psi2)

### $x > a$

Dla tego przypadku otrzymuję rozwiązanie analogiczne do {eq}`psi1`.
Zapisuję je w postaci:

$$
\psi_3(x) = F e^{i k_1 x} + G e^{-i k_1 x}
$$

Zauważam, że w tym przypadku nie może istnieć fala odbita, dlatego $G = 0$.

$$
\psi_3(x) = F e^{i k_1 x} 
$$ (psi3)

## Warunki brzegowe

Z założeń mechaniki kwantowej wiem, że funkcja falowa musi być ciągła.
Ponadto pierwsza pochodna funkcji falowej względem zmiennej $x$ również musi być ciągła.
Z tych założeń mogę zapisać następujące równania:

$$
&\left\{
    \begin{array}{ll}
        \psi_1(0) = \psi_2(0) \\
        \frac{\partial \psi_1}{\partial x}(0) = \frac{\partial \psi_2}{\partial x}(0) \\
        \psi_2(a) = \psi_3(a) \\
        \frac{\partial \psi_2}{\partial x}(a) = \frac{\partial \psi_3}{\partial x}(a) \\
    \end{array}
\right. \\
&\left\{
    \begin{array}{ll}
        A + B = C + D \\
        i k_1 (A - B) = k_2 (C - D) \\
        C e^{k_2 a} + D e^{-k_2 a} = F e^{i k_1 a} \\
        k_2 \left(C e^{k_2 a} - D e^{-k_2 a}\right) = F i k_1 e^{ik_1 a} \\
    \end{array}
\right. \\
&\left\{
    \begin{array}{ll}
        A + B = C + D \\
        A - B = -i \frac{k_2}{k_1} (C - D) \\
        C e^{k_2 a} + D e^{-k_2 a} = F e^{i k_1 a} \\
        C e^{k_2 a} - D e^{-k_2 a} = i \frac{k_1}{k_2} F e^{ik_1 a} \\
    \end{array}
\right.
$$ (warunki-brzegowe)

(wt)=
# Współczynnik Transmisji

```{admonition} Definicja
Współćzynnik transmisji $T$ to 
kwadrat stosunku amplitudy fali po przejściu przez barierę do jej amplitudy przed nią

$$
T = \left|\frac{F}{A}\right|^2
$$ (Tdef)
```

Z układu {eq}`warunki-brzegowe` dodaję równanie 3 i 4:

$$
C e^{k_2 a} + D e^{-k_2 a} + C e^{k_2 a} - D e^{-k_2 a} &=
F e^{i k_1 a} + i \frac{k_1}{k_2} F e^{ik_1 a} \\
2 C e^{k_2 a} &=
F e^{i k_1 a} \left(1 + i \frac{k_1}{k_2}\right) \\
C &= \frac{F}{2} e^{i k_1 a} e^{-k_2 a} \left(1 + i \frac{k_1}{k_2}\right) \\
$$ (c)

Następnie odejmiję równanie 4 od równania 3:

$$
C e^{k_2 a} + D e^{-k_2 a} - C e^{k_2 a} + D e^{-k_2 a} &= F e^{i k_1 a} - i \frac{k_1}{k_2} F e^{ik_1 a} \\
2 D e^{-k_2 a} &= F e^{i k_1 a} \left(1 - i \frac{k_1}{k_2}\right) \\
D &= \frac{F}{2} e^{i k_1 a} e^{k_2 a} \left(1 - i \frac{k_1}{k_2}\right) \\
$$ (d)

Następnie podstawiam {eq}`c` i {eq}`d` do równania 1 z układu {eq}`warunki-brzegowe`:

$$
A + B &= \frac{F}{2} e^{i k_1 a} e^{k_2 a} \left(1 - i \frac{k_1}{k_2}\right) + \frac{F}{2} e^{i k_1 a} e^{-k_2 a} \left(1 + i \frac{k_1}{k_2}\right) \\
A + B &= \frac{F}{2} e^{i k_1 a} \left( e^{k_2 a} \left(1 - i \frac{k_1}{k_2}\right) + e^{-k_2 a} \left(1 + i \frac{k_1}{k_2}\right)\right) \\
A + B &= \frac{F}{2} e^{i k_1 a} \left( e^{k_2 a} + e^{-k_2 a} - i \frac{k_1}{k_2} \left(e^{k_2 a} - e^{-k_2 a}\right) \right) \\
A + B &= \frac{F}{2} e^{i k_1 a} \left( 2 cosh\left(k_2 a\right) - 2 i \frac{k_1}{k_2} sinh \left(k_2 a\right) \right) \\
A + B &= F e^{i k_1 a} \left(cosh\left(k_2 a\right) - i \frac{k_1}{k_2} sinh \left(k_2 a\right) \right) \\
1 + \frac{B}{A} &= \frac{F}{A} e^{i k_1 a} \left(cosh\left(k_2 a\right) - i \frac{k_1}{k_2} sinh \left(k_2 a\right) \right) \\
$$ (ab1)

Analogiczne działania wykonuję dla równania 2 z układu {eq}`warunki-brzegowe`:

$$
A - B &= -i \frac{k_2}{k_1} \left(\frac{F}{2} e^{i k_1 a} e^{-k_2 a} \left(1 + i \frac{k_1}{k_2}\right) - \frac{F}{2} e^{i k_1 a} e^{k_2 a} \left(1 - i \frac{k_1}{k_2}\right)\right) \\
A - B &= -i \frac{k_2}{k_1} \frac{F}{2} e^{i k_1 a} \left(e^{-k_2 a} \left(1 + i \frac{k_1}{k_2}\right) - e^{k_2 a} \left(1 - i \frac{k_1}{k_2}\right)\right) \\
A - B &= -i \frac{k_2}{k_1} \frac{F}{2} e^{i k_1 a} \left(e^{-k_2 a} - e^{k_2 a} + i \frac{k_1}{k_2} \left(e^{k_2 a} + e^{k_2 a} \right)\right) \\
A - B &= -i \frac{k_2}{k_1} \frac{F}{2} e^{i k_1 a} \left(- 2 sinh\left(k_2 a\right) + 2 i \frac{k_1}{k_2} cosh \left(k_2 a\right)\right) \\
A - B &= i \frac{k_2}{k_1} F e^{i k_1 a} \left(sinh\left(k_2 a\right) - i \frac{k_1}{k_2} cosh \left(k_2 a\right)\right) \\
A - B &= F e^{i k_1 a} \left(i \frac{k_2}{k_1} sinh\left(k_2 a\right) + cosh \left(k_2 a\right)\right) \\
1 - \frac{B}{A} &= \frac{F}{A} e^{i k_1 a} \left(i \frac{k_2}{k_1} sinh\left(k_2 a\right) + cosh \left(k_2 a\right)\right) \\
$$ (ab2)

Sumuję równania {eq}`ab1` i {eq}`ab2`:

$$
1 + \frac{B}{A} + 1 - \frac{B}{A} &= \frac{F}{A} e^{i k_1 a} \left(cosh\left(k_2 a\right) - i \frac{k_1}{k_2} sinh \left(k_2 a\right) \right) + \frac{F}{A} e^{i k_1 a} \left(i \frac{k_2}{k_1} sinh\left(k_2 a\right) + cosh \left(k_2 a\right)\right) \\
2 &= \frac{F}{A} e^{i k_1 a} \left(cosh\left(k_2 a\right) - i \frac{k_1}{k_2} sinh \left(k_2 a\right) + i \frac{k_2}{k_1} sinh\left(k_2 a\right) + cosh \left(k_2 a\right)\right) \\
2 &= \frac{F}{A} e^{i k_1 a} \left(2 cosh\left(k_2 a\right) + i \left(\frac{k_2}{k_1} - \frac{k_1}{k_2}\right) sinh \left(k_2 a\right) \right) \\
2 &= \frac{F}{A} e^{i k_1 a} \left(2 cosh\left(k_2 a\right) + i \frac{k_2^2 - k_1^2}{k_1 k_2} sinh \left(k_2 a\right) \right) \\
\frac{F}{A} &= 2 e^{-i k_1 a} \left(2 cosh\left(k_2 a\right) + i \frac{k_2^2 - k_1^2}{k_1 k_2} sinh \left(k_2 a\right) \right)^{-1} \\
$$ (fa)

Podstawiam powyższy wynik do definicji T {eq}`Tdef`:

$$
T &= \left|\frac{F}{A}\right|^2 \\
T &= \left(\frac{F}{A}\right) \left(\frac{F}{A}\right)^* \\
T &= 2 e^{-i k_1 a} \left(2 cosh\left(k_2 a\right) + i \frac{k_2^2 - k_1^2}{k_1 k_2} sinh \left(k_2 a\right) \right)^{-1} 2 e^{i k_1 a} \left(2 cosh\left(k_2 a\right) - i \frac{k_2^2 - k_1^2}{k_1 k_2} sinh \left(k_2 a\right) \right)^{-1} \\
T &= 4 \cancel{e^{-i k_1 a}} \left(2 cosh\left(k_2 a\right) + i \frac{k_2^2 - k_1^2}{k_1 k_2} sinh \left(k_2 a\right) \right)^{-1} \cancel{e^{i k_1 a}} \left(2 cosh\left(k_2 a\right) - i \frac{k_2^2 - k_1^2}{k_1 k_2} sinh \left(k_2 a\right) \right)^{-1} \\
T &= 4 \left(4 cosh^2\left(k_2 a\right) + \left(\frac{k_2^2 - k_1^2}{k_1 k_2}\right)^2 sinh^2 \left(k_2 a\right) \right)^{-1} \\
$$

```{tip}
W poniższym przekształceniu wykorzystuję tzw. jedynkę hiperboliczną

$$
cosh^2(x) - sinh^2(x) = 1
$$
```

$$
T &= 4 \left(4  + 4 sinh^2\left(k_2 a\right) + \left(\frac{k_2^2 - k_1^2}{k_1 k_2}\right)^2 sinh^2 \left(k_2 a\right) \right)^{-1} \\
T &= 4 \left(4  + sinh^2\left(k_2 a\right)\left(4 + \left(\frac{k_2^2 - k_1^2}{k_1 k_2}\right)^2\right) \right)^{-1} \\
T &= 4 \left(4  + sinh^2\left(k_2 a\right)\left(\frac{4 k_1^2 k_2^2 + k_2^4 - 2 k_1^2 k_2^2 + k_1^4}{k_1^4 k_2^4}\right) \right)^{-1} \\
T &= 4 \left(4  + sinh^2\left(k_2 a\right)\left(\frac{k_2^2 + k_1^2}{k_1 k_2}\right)^2 \right)^{-1} \\
T &= \left(1  + sinh^2\left(k_2 a\right)\left(\frac{k_2^2 + k_1^2}{2 k_1 k_2}\right)^2 \right)^{-1} \\
$$

```{note}
Za wyrażenie z $k_1$ i $k_2$ można podstawić wartości z definicji {eq}`k`.

$$
\left(\frac{k_2^2 + k_1^2}{2 k_1 k_2}\right)^2 =  \\
= \frac{\left(k_1^2 + k_2^2\right)^2}{4 k_1^2 k_2^2} = \\
= \frac{\left(\frac{2m}{\hbar^2} E +\frac{2m}{\hbar^2} (V_0 - E) \right)^2}{4 \frac{2m}{\hbar^2} E \frac{2m}{\hbar^2} (V_0 - E)} = \\
= \frac{\left(\frac{2m}{\hbar^2} V_0 \right)^2}{16 \frac{m^2}{\hbar^4} E (V_0 - E)} = \\
= \frac{V_0^2}{16 E (V_0 - E)}
$$ (k-podst)
```

W ostatecznej formię wzór na T można zapisać w następującej postaci:

$$
T &= \left(1  + sinh^2\left(k_2 a\right) \frac{V_0^2}{16 E (V_0 - E)} \right)^{-1} \\
T &= \left(1  + sinh^2\left(\sqrt{\frac{2m}{\hbar^2} (V_0-E)} a\right) \frac{V_0^2}{16 E (V_0 - E)} \right)^{-1} \\
$$ (wzor-koncowy)

_Analogiczną postać wzoru przedstawia równanie 6-45 książki Eisberg'a i Restnick'a [literatura](#literatura)._

# Współczynnik Odbicia

```{admonition} Definicja
Analogicznie do [współczynnika Transmisji](#wt),
Współczynnik odbicia $R$ definiuję jako:

$$
R = \left|\frac{B}{A}\right|
$$ (R)
```

Do równania {eq}`ab1` podstawiam {eq}`fa`:

$$
1 + \frac{B}{A} &= \cancel{e^{i k_1 a}} \left(cosh\left(k_2 a\right) - i \frac{k_1}{k_2} sinh \left(k_2 a\right) \right) 2 \cancel{e^{-i k_1 a}} \left(2 cosh\left(k_2 a\right) + i \frac{k_2^2 - k_1^2}{k_1 k_2} sinh \left(k_2 a\right) \right)^{-1} \\
\frac{B}{A} &= 2 \frac{cosh\left(k_2 a\right) - i \frac{k_1}{k_2} sinh \left(k_2 a\right)}{2 cosh\left(k_2 a\right) + i \frac{k_2^2 - k_1^2}{k_1 k_2} sinh \left(k_2 a\right)} - 1 \\
\frac{B}{A} &= \frac{cosh\left(k_2 a\right) - i \frac{k_1}{k_2} sinh \left(k_2 a\right)}{cosh\left(k_2 a\right) + i \frac{k_2^2 - k_1^2}{2 k_1 k_2} sinh \left(k_2 a\right)} - 1 \\
$$

```{admonition} Przekształcenie
Sprowadzam powyższe ułamki do wspólnego mianownika i obliczam końcową postać licznika:

$$
cosh\left(k_2 a\right) - i \frac{k_1}{k_2} sinh \left(k_2 a\right) - cosh\left(k_2 a\right) - i \frac{k_2^2 - k_1^2}{2 k_1 k_2} sinh \left(k_2 a\right) = \\
= - i \frac{k_1}{k_2} sinh \left(k_2 a\right) - i \frac{k_2^2 - k_1^2}{2 k_1 k_2} sinh \left(k_2 a\right) = \\
= - i\left(\frac{k_1}{k_2} + \frac{k_2^2 - k_1^2}{2 k_1 k_2} \right) sinh \left(k_2 a\right) = \\
= - i \frac{2 k_1^2 + k_2^2 - k_1^2}{2 k_1 k_2} sinh \left(k_2 a\right) = \\
= - i \frac{k_2^2 + k_1^2}{2 k_1 k_2} sinh \left(k_2 a\right) = \\
$$
```

$$
\frac{B}{A} &= \frac{- i \frac{k_2^2 + k_1^2}{2 k_1 k_2} sinh \left(k_2 a\right)}{cosh\left(k_2 a\right) + i \frac{k_2^2 - k_1^2}{2 k_1 k_2} sinh \left(k_2 a\right)} \\
$$

Następnie podstawiam do {eq}`R`:

$$
R &= \frac{- i \frac{k_2^2 + k_1^2}{2 k_1 k_2} sinh \left(k_2 a\right)}{cosh\left(k_2 a\right) + i \frac{k_2^2 - k_1^2}{2 k_1 k_2} sinh \left(k_2 a\right)} \frac{i \frac{k_2^2 + k_1^2}{2 k_1 k_2} sinh \left(k_2 a\right)}{cosh\left(k_2 a\right) - i \frac{k_2^2 - k_1^2}{2 k_1 k_2} sinh \left(k_2 a\right)} \\
R &= \frac{\frac{\left(k_2^2 + k_1^2\right)^2}{4 k_1^2 k_2^2} sinh^2 \left(k_2 a\right)}{cosh^2 \left(k_2 a\right) + \frac{\left(k_2^2 - k_1^2\right)^2}{4 k_1^2 k_2^2} sinh^2 \left(k_2 a\right)} \\
R &= \frac{\frac{\left(k_2^2 + k_1^2\right)^2}{4 k_1^2 k_2^2} sinh^2 \left(k_2 a\right)}{1 + \left(1 + \frac{\left(k_2^2 - k_1^2\right)^2}{4 k_1^2 k_2^2}\right) sinh^2 \left(k_2 a\right)} \\
R &= \frac{\frac{\left(k_2^2 + k_1^2\right)^2}{4 k_1^2 k_2^2} sinh^2 \left(k_2 a\right)}{1 + \frac{\left(k_1^2 + k_2^2\right)^2}{4 k_1^2 k_2^2} sinh^2 \left(k_2 a\right)} \\
R &= \frac{\left(k_2^2 + k_1^2\right)^2}{4 k_1^2 k_2^2} sinh^2 \left(k_2 a\right) T \\
$$

Po podstawieniu {eq}`k-podst` otrzymuję:

$$
R &= \frac{V_0^2}{16E(V_0 - E)} sinh^2 \left(k_2 a\right) T \\
R &= \frac{V_0^2}{16E(V_0 - E)} T sinh^2\left(\sqrt{\frac{2m}{\hbar^2} (V_0-E)} a\right)
$$

```{raw} latex
\newpage
```

# Podsumowanie

Jak widać z {eq}`wzor-koncowy` wsþółczynnik Transmisji jest niezerowy, co
oznacza, że cząstka o niewystarczającej energii może mimo to przeniknąć przez barierę potencjału.

Poniższy wykres przedstawia zależności $T(a)$ dla 2 przykładowch potancjałów.

```{plot} gnuplot
:caption: Zależność współczynnika transmisji od szerokości bariery.

set xrange [0:3.5]
set ylabel "T - współczynnik transmisji"
set xlabel "a - szerokość bariery"

m=1
hbar=1
E = 1

f(a, V) = (1  + sinh(sqrt((2*m)/(hbar**2) * (V-E)) * a)**2 * (V**2)/(16*E*(V - E)) )**(-1)

plot f(x, 2) lw 4 title "T(a, V_0 = 2 j.u.)", \
     f(x, 4) lw 4 title "T(a, V_0 = 4 j.u.)",
```

```{attention}
Wielkości na powyższym wykresie są przedstawione w tzw. Jednostkach Umownych ($m = \hbar = E = 1$) - nie mają
one związku z rzeczywistymi wartościami współczynników - powyższy wykres przedstawia jedynie
kształt zależności.
```

# Literatura

- wyprowadzenie: For the Love of Physics - Quantum Tunneling - [https://youtu.be/78Sp1KboLtI?list=PLRN3HroZGu2mCtdalEmZAM2nr1xBWAtUn](https://www.youtube.com/watch?v=78Sp1KboLtI&list=PLRN3HroZGu2mCtdalEmZAM2nr1xBWAtUn&index=38) dostęp 05.12.2024 16:26
- sprawdzenie: Quantum Physics of Atoms, Molecules, Solids, Nuclei, and Particles, R. Resnick, R. Eisberg

_Źródło dokumentu: https://github.com/gucio321/potential-barrier-solution_
