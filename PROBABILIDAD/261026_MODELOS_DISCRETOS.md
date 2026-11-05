# 📘 CHEATSHEET — PROBABILIDAD · 26/10/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `261026_MODELOS_DISCRETOS.md`
> - **Fecha de transcripción:** 26/10/2026 (`AAMMDD` = `261026`)
> - **Tema principal:** MODELOS DISCRETOS — binomial negativa · geométrica · hipergeométrica · aproximaciones (hipergeométrica → binomial → Poisson)
> - **Fuente:** transcripción de clase. Complementos marcados con `➕`.
> - **Continuidad:** viene de `261019_FGM_Y_VARIANZA`. Cierra el capítulo de variables discretas: antecede a `261028_MODELOS_CONTINUOS`.
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `261026_MODELOS_DISCRETOS` §2.D».

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿Se fija el número de ensayos o se espera hasta un número de éxitos?**
   - Ensayos **fijos** $n$ → **binomial** (con reemplazo / $p$ constante).
   - Se espera **hasta el $k$-ésimo éxito** → **binomial negativa** (y **geométrica** si $k=1$).
2. **Paso 1 — ¿La extracción es con o sin reemplazo?** Sin reemplazo de una población **finita** → **hipergeométrica**.
3. **Paso 2 — ¿La población es enorme frente a la muestra?** Entonces la hipergeométrica se **aproxima** por binomial.
4. **Paso 3 — ¿$n$ grande con $p$ muy pequeño?** Entonces la binomial se aproxima por **Poisson** con $\lambda=np$.

**Tabla de decisión (frase del enunciado → modelo → bloque donde está la fórmula):**

| Si el enunciado dice… | Modelo | PMF | 👉 Ir a |
|---|---|---|---|
| "hasta obtener $k$ éxitos", "en qué intento aparece el $k$-ésimo", "total de nacimientos para tener $k$…" | **Binomial negativa (intentos)** | $\binom{x-1}{k-1}p^{k}(1-p)^{x-k}$ | **§2.A** |
| "en qué intento aparece el **primer** éxito" | **Geométrica** ($k=1$) | $p(1-p)^{x-1}$ | **§2.B** |
| "cantidad de **fracasos** antes del $k$-ésimo éxito" | **Binom. negativa (fracasos)** | $\binom{k+y-1}{y}p^{k}(1-p)^{y}$ | **§2.C** |
| "muestra de tamaño $n$ de un lote de $N$", "**sin reemplazo**", "control de calidad", "urna" | **Hipergeométrica** | $\frac{\binom{K}{x}\binom{N-K}{n-x}}{\binom{N}{n}}$ | **§2.D** |
| "con **reemplazo**" o "ensayos **independientes**" con $p$ constante | **Binomial** | $\binom{n}{x}p^{x}(1-p)^{n-x}$ | **§2.E** |
| "$N$ y $K$ muy grandes con $K/N\approx p$" | **Hipergeométrica ≈ Binomial** | — | **§3 Regla 3** |
| "$n$ grande y $p$ pequeña" (éxitos raros) | **Binomial ≈ Poisson**, $\lambda=np$ | $\frac{e^{-\lambda}\lambda^{x}}{x!}$ | **§3 Regla 4** |

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Binomial negativa — por **intentos**

- **Condición:** proceso de Bernoulli; $X$ = intento en el que ocurre el $k$-ésimo éxito.
- **PMF:**
$$
P(X=x)=\binom{x-1}{k-1}p^{k}(1-p)^{x-k}\qquad x=k,\ k+1,\ k+2,\dots
$$
- **Media:** $E(X)=\dfrac{k}{p}$
- **Varianza:** $V(X)=\dfrac{k(1-p)}{p^{2}}$

> **🔤 Diccionario:**
> - $X$: número **total de intentos** hasta el $k$-ésimo éxito (incluye los éxitos).
> - $k$: número de éxitos que se quieren acumular.
> - $p$: probabilidad de éxito en cada intento (constante).
> - $\binom{x-1}{k-1}$: los $k-1$ éxitos previos se reparten en los $x-1$ intentos anteriores.
> - Rango: empieza en $x=k$ (no en $0$).

---

### B. Geométrica — caso particular $k=1$

- **Condición:** binomial negativa con $k=1$; $X$ = intento del **primer** éxito.
- **PMF:**
$$
P(X=x)=p(1-p)^{x-1}\qquad x=1,2,3,\dots
$$
- **Media:** $E(X)=\dfrac{1}{p}$
- **Varianza:** $V(X)=\dfrac{1-p}{p^{2}}$

> **🔤 Diccionario:**
> - $p$: probabilidad de éxito.
> - $1-p$: probabilidad de fracaso en cada intento.
> - $x-1$: número de fracasos **antes** del éxito.

---

### C. Binomial negativa — por **fracasos** (parametrización alternativa)

- **Definición:** $Y$ = número de fracasos **antes** del $k$-ésimo éxito.
- **Relación con $X$:**
$$
Y=X-k\quad\Longleftrightarrow\quad X=Y+k
$$
- **PMF (sustituyendo en §2.A):**
$$
P(Y=y)=\binom{k+y-1}{y}p^{k}(1-p)^{y}\qquad y=0,1,2,\dots
$$
- **Media:** $E(Y)=\dfrac{k(1-p)}{p}$
- **Varianza:** $V(Y)=\dfrac{k(1-p)}{p^{2}}$ (**la misma** que $X$)

> **🔤 Diccionario:**
> - $Y$: fracasos antes del $k$-ésimo éxito (no cuenta los éxitos).
> - Rango: empieza en $y=0$ (puede no haber ningún fracaso).
> - ⚠️ **Aviso de nomenclatura:** varios libros y software llaman "binomial negativa" a **esta** parametrización (la de fracasos) y reservan otro nombre (Pascal) para la de intentos. Decide cuál usa el enunciado y **traduce el evento**.

---

### D. Hipergeométrica — muestreo **sin reemplazo**

- **Condición:** población finita de tamaño $N$ con $K$ elementos de la característica de interés; se extrae una muestra de tamaño $n$ **sin reemplazo**; $X$ = número de elementos con la característica en la muestra.
- **PMF:**
$$
P(X=x)=\frac{\binom{K}{x}\binom{N-K}{n-x}}{\binom{N}{n}}\qquad x=0,1,\dots,\min(K,n)
$$
- **Media:** $E(X)=n\,\dfrac{K}{N}$
- **Varianza:**
$$
V(X)=n\,\frac{K}{N}\left(1-\frac{K}{N}\right)\frac{N-n}{N-1}
$$
- **Notación de la clase:** $X\sim H(n,\,N,\,K)$

> **🔤 Diccionario:**
> - $N$: tamaño de la **población** (o del lote).
> - $K$: cuántos elementos de la población **tienen** la característica (defectuosos, marcados…).
> - $n$: tamaño de la **muestra** extraída.
> - $x$: cuántos de la muestra tienen la característica.
> - $\binom{N}{n}$: total de muestras posibles de tamaño $n$.
> - Rango: $0\le x\le\min(K,n)$ — no puede haber más marcados que $K$ ni que $n$.
> - $\frac{N-n}{N-1}$: factor de corrección por **población finita** (desaparece si $n=1$).
> - Requiere **conocer los tres** parámetros: $n$, $N$ y $K$.

---

### E. Tabla comparativa de las cuatro discretas

| Modelo | Se fija | Reemplazo | Parámetros | Media |
|---|---|---|---|---|
| Binomial | $n$ ensayos | sí / $p$ constante | $n$, $p$ | $np$ |
| Binomial negativa | $k$ éxitos | sí / $p$ constante | $k$, $p$ | $\frac{k}{p}$ |
| Geométrica | 1 éxito | sí / $p$ constante | $p$ | $\frac{1}{p}$ |
| Hipergeométrica | $n$ extracciones | **no** | $n$, $N$, $K$ | $n\frac{K}{N}$ |

> **🔤 Diccionario:**
> - "Se fija" = qué se decide de antemano (el número de ensayos o el número de éxitos).
> - "Reemplazo" = si la probabilidad de éxito se mantiene constante o cambia al extraer.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

**🟢 Regla 1 — Las dos parametrizaciones de la binomial negativa**
- $X$ (intentos) y $Y$ (fracasos) difieren en la constante $k$: $X=Y+k$.
- Por linealidad: $E(X)=E(Y)+k$; y como sumar una constante **no** cambia la varianza: $V(X)=V(Y)$.
- Para pasar un evento de una a otra: «más de $t$ intentos» $\iff$ «más de $t-k$ fracasos».

**🟢 Regla 2 — Geométrica = binomial negativa con $k=1$**
$$
P(X=x)=p(1-p)^{x-1},\qquad E(X)=\frac{1}{p},\qquad E(Y)=\frac{1-p}{p}=E(X)-1
$$

**🟢 Regla 3 — Hipergeométrica → Binomial**
- Si $N$ y $K$ crecen **proporcionalmente** con $K/N\to p$, entonces la hipergeométrica **se aproxima** a una binomial de parámetros $n$ y $p$.
- Interpretación operativa: cuando la población es **muy grande** frente a la muestra, ignorar el "sin reemplazo" no cambia el resultado.
- Coherencia: $E=n\frac{K}{N}\to np$ y $V=n\frac{K}{N}\left(1-\frac{K}{N}\right)\frac{N-n}{N-1}\to np(1-p)$ (el factor tiende a $1$).

**🟢 Regla 4 — Binomial → Poisson (éxitos raros)**
- Si $n\to\infty$ y $p\to 0$ con $np=c$ fijo, entonces
$$
\binom{n}{x}p^{x}(1-p)^{n-x}\;\longrightarrow\;\frac{e^{-c}\,c^{x}}{x!}
$$
- **Criterio de la clase:** funciona bien con $n\ge 100$, $p\le 0{,}01$ y $\lambda=np\le 20$.
- Entonces $\lambda=np$ y $X\sim\text{Poisson}(\lambda)$.

**⚠️ Trampas de notación y de rango**

| Trampa | Corrección |
|---|---|
| Rango de la binomial negativa por intentos | empieza en $x=k$ |
| Rango de la de fracasos | empieza en $y=0$ |
| Usar $E(X)=k/p$ con la parametrización de fracasos | es $E(Y)=\frac{k(1-p)}{p}$ |
| Olvidar el factor $\frac{N-n}{N-1}$ en hipergeométrica | la varianza sale mayor de lo que es |
| Aplicar hipergeométrica con reemplazo | ahí va binomial |

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 👶 A. Binomial negativa por intentos

1. **Radar:** "hasta tener $k$…" → NB$(k,p)$; identifica $k$ y $p$.
2. **Anota el rango:** $x=k,k+1,\dots$
3. **Escribe la PMF:** $\binom{x-1}{k-1}p^{k}(1-p)^{x-k}$.
4. **Traduce el evento** (para colas, usa el complemento con $x=k$).
5. **Cierra** con $E(X)=\frac{k}{p}$ y $V(X)=\frac{k(1-p)}{p^{2}}$.

**Plantilla (ejemplo de clase):** $X$ = nacimientos totales para tener $2$ niñas, $k=2$, $p=0{,}53$.
$$
P(X=x)=\binom{x-1}{1}(0{,}53)^{2}(0{,}47)^{x-2}\qquad x=2,3,\dots
$$
$$
P(X\ge 3)=1-P(X=2)=1-(0{,}53)^{2}=1-0{,}2809=0{,}7191\;(71{,}91\,\%)
$$
$$
E(X)=\frac{2}{0{,}53}=3{,}7736,\qquad V(X)=\frac{2(0{,}47)}{0{,}53^{2}}=\frac{0{,}94}{0{,}2809}=3{,}3465
$$
$$
\sigma=\sqrt{3{,}3465}=1{,}8294\;\Longrightarrow\;\text{intervalo } [1{,}94;\ 5{,}60]
$$

---

### 🔁 B. Binomial negativa por fracasos (traducir el evento)

1. **Calcula** $Y=X-k$ y su rango ($0,1,2,\dots$).
2. **Traduce:** "más de $t$ intentos" $\to$ "más de $t-k$ fracasos".
3. **Aplica** $P(Y=y)=\binom{k+y-1}{y}p^{k}(1-p)^{y}$.
4. **Verifica** ambas vías numéricamente: deben coincidir.

**Plantilla (mismo ejemplo):** "más de 3 nacimientos" $\iff$ "$Y\ge 1$ varón antes de la segunda niña":
$$
P(Y\ge 1)=1-P(Y=0)=1-(0{,}53)^{2}=0{,}7191\;\checkmark
$$
$$
E(Y)=\frac{2(0{,}47)}{0{,}53}=1{,}7736=E(X)-2
$$

---

### 🎯 C. Geométrica ($k=1$)

1. **Radar:** "primer éxito" → geométrica.
2. **PMF:** $p(1-p)^{x-1}$ con $x=1,2,\dots$
3. **Momentos:** $E=\frac{1}{p}$, $V=\frac{1-p}{p^{2}}$.
4. **Verifica** la relación $E(X)=E(Y)+1$.

**Plantilla (misma $p=0{,}53$):**
$$
E(X)=\frac{1}{0{,}53}=1{,}8868,\qquad V(X)=\frac{0{,}47}{0{,}53^{2}}=1{,}6730,\qquad \sigma=1{,}2934
$$

---

### 📦 D. Hipergeométrica (control de calidad)

1. **Identifica** $N$ (población), $K$ (defectuosos), $n$ (muestra) — los tres.
2. **Anota el rango:** $x=0,\dots,\min(K,n)$.
3. **Escribe** $P(X=x)=\frac{\binom{K}{x}\binom{N-K}{n-x}}{\binom{N}{n}}$.
4. **Suma solo los valores que cumplen el evento** (no hace falta sumar todo el rango).
5. **Cierra** con $E(X)=n\frac{K}{N}$ y $V=n\frac{K}{N}\left(1-\frac{K}{N}\right)\frac{N-n}{N-1}$.

**Plantilla (ejemplo de clase):** lote de $N=50$ con $K=3$ defectuosos, muestra $n=8$, se rechaza si hay $\ge 2$ defectuosos. Aquí el máximo posible es $x=3$:
$$
P(\text{rechazar})=P(X=2)+P(X=3)=\frac{\binom{3}{2}\binom{47}{6}+\binom{3}{3}\binom{47}{5}}{\binom{50}{8}}
$$
$$
P(\text{rechazar})=\frac{3(10\,737\,573)+1(1\,533\,939)}{536\,878\,650}=\frac{33\,746\,658}{536\,878\,650}\approx 0{,}0629\;(6{,}29\,\%)
$$
$$
E(X)=8\cdot\frac{3}{50}=0{,}48,\qquad V(X)=8\left(\frac{3}{50}\right)\left(\frac{47}{50}\right)\frac{42}{49}=0{,}3867,\qquad \sigma=0{,}6218
$$

---

### 🎈 E. Aproximación binomial → Poisson

1. **Verifica el criterio:** $n\ge 100$, $p\le 0{,}01$, $\lambda=np\le 20$.
2. **Calcula** $\lambda=np$.
3. **Sustituye** en la PMF de Poisson: $\frac{e^{-\lambda}\lambda^{x}}{x!}$.
4. **Para colas:** $1-P(X\le k-1)$.
5. **➕ Verifica** comparando con la binomial exacta cuando sea posible.

**Plantilla (ejemplo de clase):** auditorio con $n=135$, $p=\frac{1}{365}$.
$$
\lambda=np=\frac{135}{365}=0{,}3699
$$
$$
P(X\ge 2)=1-P(0)-P(1)=1-e^{-\lambda}(1+\lambda)=1-0{,}69079(1{,}3699)\approx 0{,}0537\;(5{,}37\,\%)
$$

---

## ✅ 5. CHECKLIST FINAL (30 segundos antes de entregar)

- [ ] ¿Se fija el número de **ensayos** (binomial) o se espera hasta $k$ **éxitos** (NB)?
- [ ] ¿Hay reemplazo? Sin reemplazo en población finita → **hipergeométrica**.
- [ ] ¿Identifiqué $N$, $K$ y $n$ (los tres) antes de calcular?
- [ ] ¿Cuál parametrización de NB usa el enunciado: **intentos** o **fracasos**?
- [ ] ¿Revisé el **rango** (empieza en $k$, en $1$ o en $0$ según el modelo)?
- [ ] ¿Apliqué el factor $\frac{N-n}{N-1}$ en la varianza hipergeométrica?
- [ ] ¿Justifiqué la aproximación ($N\gg n$ o $n\ge100,\ p\le0{,}01$)?
- [ ] ¿Traduje el evento entre parametrizaciones (intentos $\leftrightarrow$ fracasos)?
