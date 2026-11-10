# 📘 CHEATSHEET — PROBABILIDAD · 09/11/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `261109_NORMAL_Y_APROX_BINOMIAL.md`
> - **Fecha de transcripción:** 09/11/2026 (`AAMMDD` = `261109`)
> - **Tema principal:** DISTRIBUCIÓN NORMAL Y APROXIMACIÓN NORMAL A LA BINOMIAL — densidad normal · forma de la campana · FGM · estandarización · tabla $\Phi$ · regla empírica · aproximación y corrección por continuidad
> - **Fuentes:** transcripción de clase + apuntes manuscritos del estudiante (extraídos con OCR). Complementos marcados con `➕`.
> - **Continuidad:** cierra el capítulo de variables aleatorias continuas. Viene de `261104_EXPONENCIAL_BETA`.
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `261109_NORMAL_Y_APROX_BINOMIAL` §2.C».

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿La variable es continua y "simétrica alrededor de una media"?** → **Normal**.
2. **Paso 1 — ¿Piden una probabilidad de una normal con $\mu$ y $\sigma$ conocidos?** → **estandarizar** y usar la tabla (§2.C).
3. **Paso 2 — ¿Piden un puntaje o valor a partir de un porcentaje?** ("el 10 % superior", "puntaje mínimo") → **tabla inversa** (§4.C).
4. **Paso 3 — ¿El conteo es discreto (n ensayos) pero $n$ es grande?** → **aproximación normal a la binomial** con **corrección por continuidad** (§2.E + §3 Regla 4).

**Tabla de decisión (frase del enunciado → modelo → bloque donde está la fórmula):**

| Si el enunciado dice… | Modelo | Fórmula clave | 👉 Ir a |
|---|---|---|---|
| "distribución normal", "campana de Gauss", "$X\sim N(\mu,\sigma^{2})$" | **Normal** | $f(x)=\frac{1}{\sqrt{2\pi}\,\sigma}e^{-\frac{(x-\mu)^{2}}{2\sigma^{2}}}$ | **§2.A** |
| "halle $P(a<X<b)$" con $\mu$ y $\sigma$ dados | **Estandarizar** | $Z=\frac{X-\mu}{\sigma}$ | **§2.C** + **§4.A‑B** |
| "el 10 % con mejor puntaje", "puntaje mínimo para…", "percentil" | **Tabla inversa** | $\Phi(z_{0})=1-p$ | **§4.C** |
| "¿qué porcentaje está a 1, 2 o 3 desviaciones de la media?" | **Regla empírica** | $68{,}27\,\%\ ;\ 95{,}45\,\%\ ;\ 99{,}73\,\%$ | **§2.D** |
| "halle la FGM, $E(X)$ o $V(X)$ de una normal" | **FGM** | $m_X(t)=e^{\mu t+\sigma^{2}t^{2}/2}$ | **§2.B** |
| "$X\sim\text{Bin}(n,p)$ con $n$ grande" y piden probabilidad | **Aprox. normal a la binomial** | $N\left(np,\ np(1-p)\right)$ | **§2.E** |
| conteo **discreto** pero se resuelve con la normal | **Corrección por continuidad** | $\pm 0{,}5$ en los extremos | **§3 Regla 4** |
| "¿es válida la aproximación?" | **Criterios** | $np(1-p)$ | **§2.E** |

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Distribución normal

- **Definición:** $X\sim N(\mu,\sigma)$ si y solo si su densidad es
$$
f_X(x)=\frac{1}{\sqrt{2\pi}\,\sigma}\,e^{-\frac{(x-\mu)^{2}}{2\sigma^{2}}}\qquad -\infty<x<\infty
$$
- **Parámetros:**
$$
-\infty<\mu<\infty\ (\text{localización}),\qquad \sigma>0\ (\text{escala})
$$
- **Propiedades de la densidad:**
$$
f_X(x)>0\ \ \forall x,\qquad \int_{-\infty}^{\infty}f_X(x)\,dx=1
$$
- **Resultados de la optimización:**
$$
f_X(x)\neq 0;\qquad \text{máximo global en } x=\mu;\qquad f_X(\mu)=\frac{1}{\sqrt{2\pi}\,\sigma}
$$
$$
\text{puntos de inflexión en } x=\mu\pm\sigma;\qquad f_X(\mu+\sigma)=f_X(\mu-\sigma);\qquad \text{eje de simetría: } x=\mu
$$

> **🔤 Diccionario:**
> - $\mu$: **localización**; es a la vez la media, la mediana, la moda y la abscisa del eje de simetría.
> - $\sigma$: **escala**; determina qué tan "ancha" es la campana (y coincide con la desviación estándar).
> - $f_X(\mu)$: altura máxima de la campana; **depende de $\sigma$**.
> - $x=\mu\pm\sigma$: abscisas donde cambia la concavidad (de cóncava a convexa).
> - $e$: constante de Euler ($\approx 2{,}71828$).

---

### B. FGM y momentos de la normal

- **FGM:**
$$
m_X(t)=e^{\mu t+\frac{\sigma^{2}t^{2}}{2}}\qquad t\in\mathbb{R}
$$
- **Derivadas:**
$$
m_X'(t)=\left(\mu+\sigma^{2}t\right)e^{\mu t+\frac{\sigma^{2}t^{2}}{2}},\qquad
m_X''(t)=\left[\sigma^{2}+\left(\mu+\sigma^{2}t\right)^{2}\right]e^{\mu t+\frac{\sigma^{2}t^{2}}{2}}
$$
- **Momentos:**
$$
E(X)=m_X'(0)=\mu,\qquad E(X^{2})=m_X''(0)=\sigma^{2}+\mu^{2},\qquad V(X)=\sigma^{2}
$$

> **🔤 Diccionario:**
> - $t$: variable de la transformada (no es un dato del problema).
> - $m_X'(0)$: derivada evaluada en $t=0$ → primer momento al origen.
> - La FGM existe **para todo $t$ real** (caso raro: la mayoría solo en un entorno de $0$).

---

### C. Normal estándar y estandarización

- **Normal estándar:** $Z\sim N(0,1)$
$$
\varphi(z)=\frac{1}{\sqrt{2\pi}}e^{-\frac{z^{2}}{2}},\qquad \Phi(z)=P(Z\le z)=\int_{-\infty}^{z}\varphi(u)\,du
$$
- **Teorema de estandarización:** si $X\sim N(\mu,\sigma)$, entonces
$$
Z=\frac{X-\mu}{\sigma}\sim N(0,1)
$$
- **Cómo se usa (con la tabla $\Phi$):**
$$
P(X\le a)=\Phi\!\left(\frac{a-\mu}{\sigma}\right),\qquad
P(X>a)=1-\Phi\!\left(\frac{a-\mu}{\sigma}\right)
$$
$$
P(a<X<b)=\Phi\!\left(\frac{b-\mu}{\sigma}\right)-\Phi\!\left(\frac{a-\mu}{\sigma}\right)
$$
- **Simetría de la tabla (no hay valores negativos):**
$$
\Phi(-z)=1-\Phi(z),\qquad P(Z>z)=1-\Phi(z),\qquad P(Z>-z)=\Phi(z)
$$

> **🔤 Diccionario:**
> - $Z$: variable estandarizada, **sin unidades** (unidades divididas entre unidades).
> - $\varphi$: densidad de la normal estándar; $\Phi$: su función de distribución acumulada.
> - $z_0$: percentil estandarizado; la tabla devuelve el área **a la izquierda**.
> - $a,b$: extremos originales (en unidades de $X$: puntos, gramos, horas…).

---

### D. Regla empírica (a una, dos y tres desviaciones)

Para cualquier $X\sim N(\mu,\sigma)$, sin importar los valores de $\mu$ y $\sigma$:
$$
P(\mu-\sigma<X<\mu+\sigma)=P(-1<Z<1)\approx 0{,}6827
$$
$$
P(\mu-2\sigma<X<\mu+2\sigma)=P(-2<Z<2)\approx 0{,}9545
$$
$$
P(\mu-3\sigma<X<\mu+3\sigma)=P(-3<Z<3)\approx 0{,}9973
$$

> **🔤 Diccionario:**
> - $k\sigma$: distancia a la media medida en desviaciones estándar.
> - $\mu\pm k\sigma$: intervalo simétrico alrededor de la media.
> - Fuera de $3\sigma$ queda $\approx 0{,}27\,\%$ (por eso las tablas llegan hasta $3$ o $3{,}9$).

---

### E. Aproximación normal a la binomial

- **Teorema (de Moivre‑Laplace):** si $X\sim\text{Bin}(n,p)$ y $n$ es grande, entonces
$$
X\;\approx\;N\left(np,\ np(1-p)\right)\qquad\Longleftrightarrow\qquad \frac{X-np}{\sqrt{np(1-p)}}\approx N(0,1)
$$
- **Criterios de validez (los del tablero):**

| Caso | Condición |
|---|---|
| $0<p<\frac12$ | $np(1-p)>9$ **o** $np<5$ |
| $\frac12<p<1$ | $np(1-p)>5$ |
| $p\approx\frac12$ | funciona para **cualquier** $n$ |

- **➕ Criterio estándar habitual (equivalente en la práctica):**
$$
np\ge 5\quad\text{y}\quad n(1-p)\ge 5
$$
- **Corrección por continuidad (obligatoria):**
$$
P(a\le X\le b)\approx P\left(a-\tfrac12<X<b+\tfrac12\right)
$$

> **🔤 Diccionario:**
> - $n$: número de ensayos; $p$: probabilidad de éxito.
> - $np$: media de la binomial (y de la normal que la aproxima).
> - $np(1-p)$: varianza de la binomial; su raíz es $\sigma$ de la normal.
> - $\pm 0{,}5$: medio punto, porque la normal es continua y la binomial discreta salta de 1 en 1.
> - La aproximación **no** cambia la media ni la varianza: solo cambia la forma.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

**🟢 Regla 1 — De dónde sale la constante $\frac{1}{\sqrt{2\pi}}$**
$$
I=\int_{-\infty}^{\infty}e^{-t^{2}/2}\,dt\;\Longrightarrow\;I^{2}=\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}e^{-\frac{t^{2}+s^{2}}{2}}\,dt\,ds
$$
En coordenadas polares ($t=r\cos\theta$, $s=r\sin\theta$) la integral doble vale $2\pi$, luego $I=\sqrt{2\pi}$. Es la razón por la que la densidad normal integra $1$ y por la que aparece $\sqrt{2\pi}$ en el denominador.

**🟢 Regla 2 — Forma de la campana (leer $\mu$ y $\sigma$)**
- $\mu$ **mueve** la campana: cambia el eje de simetría y el máximo.
- $\sigma$ **ensancha o afila**: $\sigma$ grande → campana ancha y baja; $\sigma$ pequeña → picuda y alta. El **área siempre es 1**, por eso al ensanchar baja.
- Colas: $f_X(x)\to 0$ cuando $x\to\pm\infty$.

**🟢 Regla 3 — Estandarizar es un cambio de unidades**
- A cada valor se le resta $\mu$ y se divide entre $\sigma$: eso elimina las unidades (gramos/gramos, puntos/puntos).
- La forma no cambia (ver $\mu=2,\sigma=4$ es ver $N(0,1)$ desplazada y estirada), así que las **áreas se conservan** y se pueden buscar en la misma tabla.

**🟢 Regla 4 — Corrección por continuidad (la que casi nadie aplica)**
- Al pasar de discreta a continua hay que **estirar** el intervalo medio punto a cada lado: $5\le X\le 15$ pasa a $4{,}5<X<15{,}5$.
- Para "al menos $k$": $P(X\ge k)\approx P(X>k-0{,}5)$.
- Para "a lo sumo $k$": $P(X\le k)\approx P(X<k+0{,}5)$.
- Sin la corrección el resultado queda desviado; con ella coincide casi exactamente con la binomial.

**🟢 Regla 5 — Valores de tabla que se usan todo el tiempo**

| $z$ | $\Phi(z)$ |
|---|---|
| $0{,}50$ | $0{,}6915$ |
| $0{,}98$ | $0{,}8365$ |
| $1{,}00$ | $0{,}8413$ |
| $1{,}28$ | $0{,}8997$ |
| $2{,}00$ | $0{,}9772$ |
| $2{,}61$ | $0{,}9955$ |

**⚠️ Trampas típicas**
- Confundir $V(X)=\sigma^{2}$ con $\sigma$: si el enunciado da $N(550;100^{2})$ la **desviación** es $100$; si da la varianza, hay que sacar raíz.
- Usar la tabla con el área a la **derecha** (algunas tablas vienen así): verificar en el encabezado.
- Olvidar $\Phi(-z)=1-\Phi(z)$ y reportar valores negativos imposibles.
- Aplicar la aproximación normal con $p$ muy pequeño (ahí va **Poisson**, ver `261026_MODELOS_DISCRETOS` §3 Regla 4).

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 📐 A. Probabilidad de cola en una normal

1. **Radar:** $X\sim N(\mu,\sigma)$ y piden $P(X>a)$ o $P(X<a)$.
2. **Estandariza** el extremo: $z=\frac{a-\mu}{\sigma}$.
3. **Ubica** $\Phi(z)$ en la tabla.
4. **Ajusta** según la cola: $P(X>a)=1-\Phi(z)$; si $z<0$, usa $\Phi(-z)$.
5. **Verifica** que el resultado esté en $[0,1]$ y sea coherente con el dibujo.

**Plantilla (admisión, $\mu=550$, $\sigma=100$):**
$$
P(X>500)=P\left(Z>\frac{500-550}{100}\right)=P(Z>-0{,}5)=\Phi(0{,}5)=0{,}6915
$$
El $69{,}15\,\%$ de los aspirantes supera los $500$ puntos.

---

### 📏 B. Probabilidad de un intervalo

1. **Estandariza los dos extremos:** $z_1=\frac{a-\mu}{\sigma}$, $z_2=\frac{b-\mu}{\sigma}$.
2. **Aplica** $P(a<X<b)=\Phi(z_2)-\Phi(z_1)$.
3. **Convierte negativos** con $\Phi(-z)=1-\Phi(z)$.
4. **Verifica** que el resultado sea positivo y menor que $1$.

**Plantilla (mismo ejemplo):**
$$
P(450<X<750)=P(-1<Z<2)=\Phi(2)-\Phi(-1)=0{,}9772-0{,}1587=0{,}8185
$$
El $81{,}85\,\%$ de los aspirantes está entre $450$ y $750$ puntos.

---

### 🔎 C. Tabla inversa (percentil dado)

1. **Traduce:** "el $10\,\%$ superior" → $P(X>x_0)=0{,}10$ → $P(X\le x_0)=0{,}90$.
2. **Estandariza:** $\Phi(z_0)=0{,}90$ y busca en el **cuerpo** de la tabla el valor más cercano a $0{,}90$.
3. **Lee** $z_0$ (para $0{,}90$ → $z_0\approx 1{,}28$).
4. **Despeja** $x_0=\mu+z_0\sigma$.
5. **Verifica:** $x_0$ debe estar por encima de $\mu$ (porque es el $10\,\%$ superior).

**Plantilla:**
$$
x_0=550+1{,}28(100)=678
$$
Puntaje mínimo de admisión para el $10\,\%$ superior: **$678$ puntos** ($\approx 670$ redondeando).

---

### 📊 D. Regla empírica

1. **Identifica** $\mu$ y $\sigma$.
2. **Construye** los intervalos $\mu\pm k\sigma$ para $k=1,2,3$.
3. **Asigna** $68{,}27\,\%$, $95{,}45\,\%$, $99{,}73\,\%$.
4. **Complementa** si piden "fuera de": $1-0{,}9545=0{,}0455$ para $2\sigma$.

**Plantilla:** $X\sim N(550,100)$.
$$
P(450<X<650)=P(-1<Z<1)\approx 0{,}6827
$$

---

### 🎲 E. Aproximación normal a la binomial

1. **Verifica el criterio** (§2.E): calcula $np$ y $np(1-p)$.
2. **Fija** $\mu_{N}=np$ y $\sigma_{N}=\sqrt{np(1-p)}$.
3. **Corrige por continuidad**: $a\le X\le b\ \to\ a-0{,}5<X<b+0{,}5$.
4. **Estandariza** los extremos corregidos y usa $\Phi$.
5. **Reporta** y, si se puede, compara con la binomial exacta (➕).

**Plantilla (ejemplo de clase):** $X\sim\text{Bin}(50;\ 0{,}25)$, $P(5\le X\le 15)$.
$$
\mu=np=12{,}5,\qquad \sigma^{2}=np(1-p)=50(0{,}25)(0{,}75)=9{,}375,\qquad \sigma=3{,}0619
$$
$$
P(4{,}5<X<15{,}5)=P\!\left(\frac{4{,}5-12{,}5}{3{,}0619}<Z<\frac{15{,}5-12{,}5}{3{,}0619}\right)=P(-2{,}61<Z<0{,}98)
$$
$$
=\Phi(0{,}98)-\Phi(-2{,}61)=0{,}8365-0{,}0045=0{,}8320\;(83{,}20\,\%)
$$
La binomial exacta da $\approx 0{,}83$: la aproximación con corrección es correcta.

---

## ✅ 5. CHECKLIST FINAL (30 segundos antes de entregar)

- [ ] ¿Me dan $\sigma$ o me dan $\sigma^{2}$? (si es varianza, sacar raíz)
- [ ] ¿Estandaricé **los dos** extremos cuando es un intervalo?
- [ ] ¿Usé $\Phi(-z)=1-\Phi(z)$ en lugar de reportar un área negativa?
- [ ] ¿La tabla que estoy leyendo da el área **a la izquierda**?
- [ ] ¿En el percentil invertí bien: "10 % superior" ⇒ área $0{,}90$ a la izquierda?
- [ ] ¿Apliqué la **corrección por continuidad** al aproximar una binomial?
- [ ] ¿Verifiqué el criterio $np(1-p)$ antes de aproximar?
- [ ] ¿El resultado está en $[0,1]$ y es coherente con el dibujo de la campana?
