# 📘 TABLA MAESTRA — MODELOS DE PROBABILIDAD (pocket reference)

> **🧾 FICHA**
> - **Archivo:** `261115_TABLA_MAESTRA_MODELOS.md`
> - **Uso:** hoja de bolsillo para identificación + cálculo. Creada 15/11/2026 para el parcial del 16/11.
> - **Cómo se cita:** «📘 `261115_TABLA_MAESTRA_MODELOS` §1».

---

## 🧠 1. LA LÓGICA ÚNICA (esto es lo que hay que entender, no memorizar)

**Se memoriza UNA sola cosa por modelo: su fórmula base**, $P(X=x)$ (discreta) o $f(x)$ (continua).
Todo lo demás sale de dos operaciones: **sumar** o **restar**.

| Si es… | Base | Acumular | Cola | Intervalo |
|---|---|---|---|---|
| **Discreta** | $P(X=x)$ | $F(x)=\sum_{t\le x}P(X=t)$ | $P(X>k)=1-\sum_{t=0}^{k}P(X=t)$ | $P(a\le X\le b)=\sum_{t=a}^{b}P(X=t)$ |
| **Continua** | $f(x)$ | $F(x)=\int_{-\infty}^{x}f$ | $P(X>k)=1-F(k)$ | $P(a<X<b)=F(b)-F(a)$ |

**Atajo de decisión:** ¿la cola deja **pocos** términos? Suma directo. ¿Deja **muchos o infinitos**? Complemento.

**Las tres conversiones (aplican a todo):**
$$
P(X>a)=1-F(a),\qquad P(a<X\le b)=F(b)-F(a),\qquad P(X\le b)=F(b)
$$

---

## 📦 2. TABLA MAESTRA — DISCRETAS

| Modelo | Datos | § Cheatsheet | Probabilidad base | $E(X)$ | $V(X)$ | Truco |
|---|---|---|---|---|---|---|
| **UD$(n)$** | $n$ resultados equiprobables | ➕ plan §3 Hueco 3 | $\frac{1}{n}$, $x=1,\dots,n$ | $\frac{n+1}{2}$ | $\frac{n^{2}-1}{12}$ | contar casos favorables |
| **Bernoulli$(p)$** | 1 ensayo, $p$ | `261026` §2.E | $p^{x}(1-p)^{1-x}$, $x\in\{0,1\}$ | $p$ | $p(1-p)$ | es Bin$(1,p)$ |
| **Binomial$(n,p)$** | $n$ fijo, $p$ constante, independientes | `261026` §1 y §2.E | $\binom{n}{x}p^{x}(1-p)^{n-x}$ | $np$ | $np(1-p)$ | "al menos 1" $=1-(1-p)^{n}$ |
| **Geométrica$(p)$** | hasta el **1.er** éxito | `261026` §2.B | $p(1-p)^{x-1}$, $x\ge1$ | $\frac{1}{p}$ | $\frac{1-p}{p^{2}}$ | $P(X>k)=(1-p)^{k}$ sin sumar |
| **NB$(k,p)$** | hasta el **$k$-ésimo** éxito | `261026` §2.A y §2.C | $\binom{x-1}{k-1}p^{k}(1-p)^{x-k}$, $x\ge k$ | $\frac{k}{p}$ | $\frac{k(1-p)}{p^{2}}$ | $P(\text{NB}\le n)=P(\text{Bin}(n,p)\ge k)$ |
| **Hipergeométrica$(n,N,K)$** | muestra **sin reemplazo** | `261026` §2.D | $\frac{\binom{K}{x}\binom{N-K}{n-x}}{\binom{N}{n}}$, $0\le x\le\min(K,n)$ | $n\frac{K}{N}$ | $n\frac{K}{N}\left(1-\frac{K}{N}\right)\frac{N-n}{N-1}$ | si $N\gg n$ → binomial |
| **Poisson$(\lambda)$** | conteo con tasa constante | `261028` §2.A | $\frac{e^{-\lambda}\lambda^{x}}{x!}$, $x\ge0$ | $\lambda$ | $\lambda$ | reajustar $\lambda$ a las unidades |

---

## 🌊 3. TABLA MAESTRA — CONTINUAS

| Modelo | Datos | § Cheatsheet | Probabilidad base | $E(X)$ | $V(X)$ | Truco |
|---|---|---|---|---|---|---|
| **$U(a,b)$** | extremos $a,b$ | `261028` §2.B | $f=\frac{1}{b-a}$; $F=\frac{x-a}{b-a}$ | $\frac{a+b}{2}$ | $\frac{(b-a)^{2}}{12}$ | intervalo = longitud favorable / total |
| **Exp$(\lambda)$** | tasa $\lambda$ o media $1/\lambda$ | `261104` §2.A | $f=\lambda e^{-\lambda x}$; $F=1-e^{-\lambda x}$ | $\frac{1}{\lambda}$ | $\frac{1}{\lambda^{2}}$ | $P(X>t)=e^{-\lambda t}$; **falta de memoria** `261104` §2.B |
| **Gamma$(r,\lambda)$** | eventos $r$, tasa $\lambda$ | `261028` §2.D | $f=\frac{\lambda^{r}}{\Gamma(r)}x^{r-1}e^{-\lambda x}$; con $r$ entero $F=1-\sum_{j=0}^{r-1}\frac{e^{-\lambda x}(\lambda x)^{j}}{j!}$ | $\frac{r}{\lambda}$ | $\frac{r}{\lambda^{2}}$ | $r=1$ → exponencial; Erlang `261028` §3 Caso 1; ji² $\lambda=\frac12$, $r=\frac{k}{2}$ |
| **$N(\mu,\sigma)$** | media y desviación | `261109` §2.A, §2.C | $P(X\le a)=\Phi\left(\frac{a-\mu}{\sigma}\right)$ | $\mu$ | $\sigma^{2}$ | $\Phi(-z)=1-\Phi(z)$; percentil: $x=\mu+z\sigma$ |
| **Beta$(a,b)$** | $a,b>0$ | `261104` §2.D | $f=\frac{x^{a-1}(1-x)^{b-1}}{B(a,b)}$; $x\in(0,1)$ | $\frac{a}{a+b}$ | $\frac{ab}{(a+b)^{2}(a+b+1)}$ | es para **proporciones**; $E(X^{r})=\frac{\Gamma(r+a)\Gamma(a+b)}{\Gamma(r+a+b)\Gamma(a)}$ |
| **Weibull$(a,\beta)$** | forma $\beta$, escala $a$ | ➕ plan §3 Hueco 4 | $f=a\beta x^{\beta-1}e^{-ax^{\beta}}$; $F=1-e^{-ax^{\beta}}$ | $a^{-1/\beta}\Gamma\!\left(1+\frac{1}{\beta}\right)$ | $a^{-2/\beta}\left[\Gamma\!\left(1+\frac{2}{\beta}\right)-\Gamma^{2}\!\left(1+\frac{1}{\beta}\right)\right]$ | $P(X>x)=e^{-ax^{\beta}}$; riesgo **variable** (desgaste) |

> ⚠️ **Weibull:** si el enunciado da **escala $\eta$** (forma Ross), entonces $a=\eta^{-\beta}$.

---

## 🔗 4. APROXIMACIONES

| De | A | Cuándo | Parámetros | § Cheatsheet |
|---|---|---|---|---|
| Hipergeométrica$(n,N,K)$ | Binomial$(n,p)$ | $N,K\to\infty$ con $K/N\to p$ (población enorme) | $p=K/N$ | `261026` §3 Regla 3 |
| Binomial$(n,p)$ | Poisson$(\lambda)$ | $n\ge100$, $p\le0{,}01$, $\lambda=np\le20$ | $\lambda=np$ | `261026` §3 Regla 4 |
| Binomial$(n,p)$ | $N\left(np,\ np(1-p)\right)$ | $n$ grande, $p$ no extrema | con **corrección $\pm0{,}5$** | `261109` §2.E |

---

## 🧭 5. RADAR DE IDENTIFICACIÓN (frase → modelo)

| Si el enunciado dice… | Modelo |
|---|---|
| $n$ resultados igualmente probables (dado, ruleta, sorteo) | UD$(n)$ |
| "cada uno independientemente", "se toman $n$ al azar", $p$ constante | Binomial$(n,p)$ |
| "hasta que ocurra el primero", "¿cuántos intentos para…?" | Geométrica$(p)$ |
| "hasta obtener $k$ éxitos", "hasta la $k$-ésima vez" | NB$(k,p)$ |
| "sin reemplazo", "lote", "urna", "control de calidad" | Hipergeométrica$(n,N,K)$ |
| "por hora", "por día", "tasa promedio", conteo de eventos | Poisson$(\lambda)$ |
| "cualquier valor entre $a$ y $b$ con igual probabilidad" | $U(a,b)$ |
| "tiempo hasta el próximo evento", "tasa constante", "no importa lo que ya duró" | Exp$(\lambda)$ |
| "tiempo hasta el $r$-ésimo evento", "Erlang", "ji-cuadrado" | Gamma$(r,\lambda)$ |
| "media y desviación estándar" como **dos datos**, "simétrico", "percentil" | $N(\mu,\sigma)$ |
| "proporción", "fracción", "porcentaje" entre 0 y 1 | Beta$(a,b)$ |
| "duración con desgaste", "riesgo que aumenta con el tiempo" | Weibull$(a,\beta)$ |

---

## 🔧 6. TRUCOS TRANSVERSALES

1. **Validar siempre:** $p$ suma 1 o $f$ integra 1. Sirve para despejar constantes ($k$).
2. **Cola larga → complemento.** Cola corta → suma directa.
3. **Intervalo = resta de colas izquierdas**, en cualquier modelo.
4. **Unidades:** reajustar $\lambda$ (Poisson, exponencial, gamma) al intervalo pedido.
5. **Normal:** buscar $z$ en la tabla **en los dos sentidos**; los negativos con $\Phi(-z)=1-\Phi(z)$.
6. **Discreta vs continua:** el punto pesa en discreta ($P(X=a)=$ salto), no pesa en continua.
7. **NB ↔ Binomial:** $P(\text{NB}(k,p)\le n)=P(\text{Bin}(n,p)\ge k)$. Evita sumas largas.
8. **Erlang:** si $r$ es entero, $\Gamma(r)=(r-1)!$ y la FDA es una suma de Poisson.
9. **Exponencial:** si ya duró $s$, lo que importa es $t$ **que falta**: $e^{-\lambda t}$.
10. **Verificar:** probabilidad en $[0,1]$, $V\ge0$, y coherencia con el dibujo.

---

## 🗃️ 7. DÓNDE ESTÁ CADA COSA EN LAS CHEATSHEETS

| Archivo | Contenido |
|---|---|
| `261014_MOMENTOS_Y_VARIANZA` | momentos al origen y centrales, varianza, $\sigma$ |
| `261019_FGM_Y_VARIANZA` | FGM, derivadas, propiedades de la varianza, tabla de FGM |
| `261026_MODELOS_DISCRETOS` | NB, geométrica, hipergeométrica, binomial, aproximaciones |
| `261028_MODELOS_CONTINUOS` | Poisson, uniforme, gamma, Erlang, ji-cuadrado |
| `261104_EXPONENCIAL_BETA` | exponencial, falta de memoria, beta |
| `261109_NORMAL_Y_APROX_BINOMIAL` | normal, estandarización, tabla $\Phi$, regla empírica, aproximación |
| `261116_PLAN_PARCIAL` §3 | huecos: transformación de VA, UD$(n)$, Weibull, característica |
