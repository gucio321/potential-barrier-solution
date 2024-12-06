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

# Rozwiązanie

Z niezalego od czasu røwnania Schrödingera mamy:

$$
- \frac{\hbar^2}{2m} \frac{\partial^2 \psi}{\partial x^2} + V \psi = E \psi \\
- \frac{\hbar^2}{2m} \frac{\partial^2 \psi}{\partial x^2} = (E - V) \psi \\
\frac{\partial^2 \psi}{\partial x^2} = - \frac{2m}{\hbar^2} (E - V) \psi \\
\frac{\partial^2 \psi}{\partial x^2} = \frac{2m}{\hbar^2} (V - E) \psi \\
\frac{\partial^2 \psi}{\partial x^2} - \frac{2m}{\hbar^2} (V - E) \psi  = 0\\
$$ (rs)

```{important}
Zdefiniujmy stałe $k_1$ i $k_2$ w następujący sposób:

$$
k_1^2 = \frac{2m}{\hbar^2} E \\
k_2^2 = \frac{2m}{\hbar^2} (V_0 - E) \\
$$ (k)
```

## 3 przypadki

Rozważmy następujący rysunek.

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

$V_0 = 0$, więc (biorąc pod uwagę {eq}`k`) mamy:

$$
\frac{\partial^2 \psi}{\partial x^2} + k_1^2 \psi  = 0\\
$$

Rozwiązaniem tak zdefiniowanego równania jest  jest funcja w postaci:

$$
\psi_1(x) = A e^{i k_1 x} + B e^{-i k_1 x}
$$ (psi1)

Warto zauważyć, że wyraz $A e^{i k_1 x}$ odpowiada za ruch cząstki w prawo (ku barierze potencjału),
natomiast $B e^{-i k_1 x}$ opisuje falę odbitą.

```{raw} latex
\begin{figure}[H]
\centering
\begin{tikzpicture}
\fill[gray!20!white] (2,0) rectangle (3, 2);
\draw (0,0) -- (2,0) -- (2,2) -- (3, 2) -- (3,0) -- (5,0);
\node[anchor=north] at (2, 0) {0};
\node[anchor=north] at (3, 0) {a};
\node at (6, 2.5) {$V_0$};
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
\psi_2(x) = C e^{i k_2 x} + D e^{-i k_2 x}
$$ (psi2)

### $x > a$

Dla tego przypadku otrzymamy rozwiązanie analogiczne do {eq}`psi1`.
Zapiszmy je w postaci

$$
\psi_3(x) = F e^{i k_1 x} + G e^{-i k_1 x}
$$

Zauważmy, że w tym przypadku nie może istnieć fala odbita, dlatego $G = 0$.

$$
\psi_3(x) = F e^{i k_1 x} 
$$ (psi3)

## Warunki brzegowe

Z założeń mechaniki kwantowej wiemy, że funkcja falowa musi być ciągła.
Ponatdo pierwsza pochodna funkcji falowej względem zmiennej $x$ również musi być ciągła.
Z tych założeń możemy zapisać następujące równania:

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

## Współczynnik transmisji

```{admonition} Definicja
Współćzynnik transmisji $T$ to 
stosunek amplitudy fali po przejściu przez barierę do jej amplitudy przed nią $T = \left|\frac{F}{A}\right|^2$.
```

Z układu {eq}`warunki-brzegowe` dodajmy równanie 3 i 4:

$$
C e^{k_2 a} + D e^{-k_2 a} + C e^{k_2 a} - D e^{-k_2 a} &=
F e^{i k_1 a} + i \frac{k_1}{k_2} F e^{ik_1 a} \\
2 C e^{k_2 a} &=
F e^{i k_1 a} \left(1 + i \frac{k_1}{k_2}\right) \\
C &= \frac{F}{2} e^{i k_1 a} e^{-k_2 a} \left(1 + i \frac{k_1}{k_2}\right) \\
$$ (c)

Następnie odejmijmy równanie 4 od równania 3:

$$
C e^{k_2 a} + D e^{-k_2 a} - C e^{k_2 a} + D e^{-k_2 a} &= F e^{i k_1 a} - i \frac{k_1}{k_2} F e^{ik_1 a} \\
2 D e^{-k_2 a} &= F e^{i k_1 a} \left(1 - i \frac{k_1}{k_2}\right) \\
D &= \frac{F}{2} e^{i k_1 a} e^{k_2 a} \left(1 - i \frac{k_1}{k_2}\right) \\
$$ (d)

Następnie podstawmy {eq}`c` i {eq}`d` do równania 1 z układu {eq}`warunki-brzegowe`:

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

Dodaję równania {eq}`ab1` i {eq}`ab2`:

$$
1 + \frac{B}{A} + 1 - \frac{B}{A} &= \frac{F}{A} e^{i k_1 a} \left(cosh\left(k_2 a\right) - i \frac{k_1}{k_2} sinh \left(k_2 a\right) \right) + \frac{F}{A} e^{i k_1 a} \left(i \frac{k_2}{k_1} sinh\left(k_2 a\right) + cosh \left(k_2 a\right)\right) \\
2 &= \frac{F}{A} e^{i k_1 a} \left(cosh\left(k_2 a\right) - i \frac{k_1}{k_2} sinh \left(k_2 a\right) + i \frac{k_2}{k_1} sinh\left(k_2 a\right) + cosh \left(k_2 a\right)\right) \\
2 &= \frac{F}{A} e^{i k_1 a} \left(2 cosh\left(k_2 a\right) + i \left(\frac{k_2}{k_1} - \frac{k_1}{k_2}\right) sinh \left(k_2 a\right) \right) \\
2 &= \frac{F}{A} e^{i k_1 a} \left(2 cosh\left(k_2 a\right) + i \frac{k_2^2 - k_1^2}{k_1 k_2} sinh \left(k_2 a\right) \right) \\
\frac{F}{A} &= 2 e^{-i k_1 a} \left(2 cosh\left(k_2 a\right) + i \frac{k_2^2 - k_1^2}{k_1 k_2} sinh \left(k_2 a\right) \right)^{-1} \\
$$

Podstawiam powyższy wynik do definicji T:

$$
T &= \left|\frac{F}{A}\right|^2 \\
T &= \left(\frac{F}{A}\right) \left(\frac{F}{A}\right)^* \\
T &= 2 e^{-i k_1 a} \left(2 cosh\left(k_2 a\right) + i \frac{k_2^2 - k_1^2}{k_1 k_2} sinh \left(k_2 a\right) \right)^{-1} 2 e^{i k_1 a} \left(2 cosh\left(k_2 a\right) - i \frac{k_2^2 - k_1^2}{k_1 k_2} sinh \left(k_2 a\right) \right)^{-1} \\
T &= 4 \cancel{e^{-i k_1 a}} \left(2 cosh\left(k_2 a\right) + i \frac{k_2^2 - k_1^2}{k_1 k_2} sinh \left(k_2 a\right) \right)^{-1} \cancel{e^{i k_1 a}} \left(2 cosh\left(k_2 a\right) - i \frac{k_2^2 - k_1^2}{k_1 k_2} sinh \left(k_2 a\right) \right)^{-1} \\
T &= 4 \left(4 cosh^2\left(k_2 a\right) + \left(\frac{k_2^2 - k_1^2}{k_1 k_2}\right)^2 sinh^2 \left(k_2 a\right) \right)^{-1} \\
$$

```{tip}
W poniższym przekształceniu wykorzystałem tzw jedynkę hiperboliczną

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
Za za wyrażenie z $k_1$ i $k_2$ można podstawić wartości z definicji {eq}`k`.

$$
\left(\frac{k_2^2 + k_1^2}{2 k_1 k_2}\right) =  \\
\frac{\left(k_1^2 + k_2^2\right)^2}{4 k_1^2 k_2^2} = \\
\frac{\left(\frac{2m}{\hbar^2} E +\frac{2m}{\hbar^2} (V_0 - E) \right)^2}{4 \frac{2m}{\hbar^2} E \frac{2m}{\hbar^2} (V_0 - E)} = \\
\frac{\left(\frac{2m}{\hbar^2} V_0 \right)^2}{16 \frac{m^2}{\hbar^4} E (V_0 - E)} = \\
\frac{V_0^2}{16 E (V_0 - E)}
$$
```


W ostatecznej formię wzór na T można zapisać w następującej postaci:

$$
T &= \left(1  + sinh^2\left(k_2 a\right) \frac{V_0^2}{16 E (V_0 - E)} \right)^{-1} \\
$$ (wzor-koncowy)

_Analogiczną postać wzoru przedstawia równanie 6-45 książki Eisberg'a i Restnick'a [literatura](#literatura)._

# Literatura

- wyprowadzenie: For the Love of Physics - Quantum Tunneling - [https://youtu.be/78Sp1KboLtI?list=PLRN3HroZGu2mCtdalEmZAM2nr1xBWAtUn](https://www.youtube.com/watch?v=78Sp1KboLtI&list=PLRN3HroZGu2mCtdalEmZAM2nr1xBWAtUn&index=38) dostęp 05.12.2024 16:26
- sprawdzenie: Quantum Physics of Atoms, Molecules, Solids, Nuclei, and Particles, R. Resnick, R. Eisberg

_Źródło dokumentu: https://github.com/gucio321/potential-barrier-solution_
