# 🎯 PLAN DE ESTUDIO — PARCIAL DE PROBABILIDAD · lunes 16/11/2026

> **🧾 FICHA**
> - **Archivo:** `261116_PLAN_PARCIAL.md` (generado el jueves 12/11/2026)
> - **Parcial:** lunes 16/11/2026, **en la tarde**
> - **Alcance (solo esto se evalúa):** componente **«Variables aleatorias»** + componente **«Modelos de distribuciones de probabilidad»** del plan de asignatura.
> - **Correspondencia en el libro (Liliana Blanco, 3.ª ed.):** capítulos **2, 3 y 4**.
> - **Tiempo total disponible:** $2+5+3+5=15$ horas en 4 días.
> - **Cheatsheets propias:** `261014`, `261019`, `261026`, `261028`, `261104`, `261109`.
> - **Material de apoyo (2.º orden):** diapositivas del profe (`Variables aleatorias reales.pdf`, `Valor esperado.pdf`, `Diapositivas MODELOS DISCRETOS.pdf`, `Diapositivas MODELOS CONTINUOS.pdf`).

---

## 📌 1. QUÉ ENTRA Y QUÉ NO

### ✅ SÍ se evalúa (los dos componentes del plan)

| Componente | Tópicos textuales del plan |
|---|---|
| **Variables aleatorias** | Concepto · Caracterización de una VA · VA discretas · VA continuas · **Distribución de una función de una VA** · Valor esperado de una función de VA · Casos particulares: **momentos**, **función generadora de momentos**, **función característica** |
| **Modelos de distribuciones** | **Discretas:** uniforme, binomial, Bernoulli, binomial negativa, hipergeométrica, Poisson · **Continuas:** uniforme, gamma, normal, beta, **Weibull** |

### ❌ NO se evalúa (no gastar tiempo aquí)
- Vectores aleatorios: distribución conjunta, independencia de vectores, covarianza, correlación, normal multivariada.
- Probabilidad y esperanza condicional (densidad condicional, esperanza condicional).
- Teoremas límites: convergencia, leyes de los grandes números, teorema central del límite.

> ⚠️ Si algún ejercicio "situacional" menciona dos variables a la vez, es del capítulo 5: **no entra**. Si menciona "dado que", suele ser probabilidad condicional de *eventos* (capítulo 1) o falta de memoria de la exponencial (capítulo 4), que **sí** entra.

---

## 🗺️ 2. MAPA DE COBERTURA (plan → cheatsheet → libro)

| Tema | Cheatsheet | Libro (Blanco) | Diapositivas | Estado |
|---|---|---|---|---|
| Concepto, distribución y FDA de una VA | `261014` §2.A (parcial) | §2.1–2.2 | Variables aleatorias §1–4 | 🔶 **repasar** |
| VA discretas / continuas (masa vs densidad) | `261014` §2.A | §2.1–2.2 | Variables aleatorias §4 | ✅ |
| **Función de una VA (transformación)** | — | **§2.3** (Teo. 2.38) | Variables aleatorias §5 | ❌ **HUECO** |
| Valor esperado de $g(X)$ | `261014` §2.A | §2.4 | Valor esperado §1 | ✅ |
| Momentos y varianza | `261014` §2.B | §2.4 | Valor esperado §2–3 | ✅ |
| FGM | `261019` §2.B–§2.C | §2.4 | Valor esperado §4 | ✅ |
| **Función característica** | — | §2.4 | Valor esperado §5 | ❌ **HUECO** |
| **Uniforme discreta** | — | **§3.1** | Discretos §1 | ❌ **HUECO** |
| Bernoulli y binomial | `261026` §2.E | §3.1 | Discretos §2 | ✅ |
| Binomial negativa y geométrica | `261026` §2.A–§2.C | §3.3 | Discretos §2 | ✅ |
| Hipergeométrica | `261026` §2.D | §3.2 | Discretos §3 | ✅ |
| Poisson | `261028` §2.A | §3.2 | Discretos §4 | ✅ |
| Uniforme continua | `261028` §2.B | §4.1 | Continuos §1 | ✅ |
| Gamma, Erlang, ji-cuadrado, exponencial | `261028` §2.D, `261104` §2.A | §4.3 | Continuos §2 | ✅ |
| Normal, estandarización, tabla | `261109` §2.A–§2.D | §4.2 | Continuos §4 | ✅ |
| Beta | `261104` §2.D | §4.4 | Continuos §3 | ✅ |
| **Weibull** | — | **§4.5** (Def. 4.34) | — | ❌ **HUECO** |
| Aproximaciones (bin→normal, bin→Poisson, hiperg→bin) | `261026` §3, `261109` §2.E | §3–4 | — | ✅ |

**Resultado: 5 huecos.** Todo lo demás ya está en las cheatsheets.

---

## 🧩 3. LOS 5 HUECOS, EN UNA SOLA PÁGINA

### Hueco 1 — FDA y caracterización
$$
F_X(x)=P(X\le x),\qquad P(a<X\le b)=F(b)-F(a)
$$
- No decreciente, continua por la derecha, $\lim_{x\to-\infty}F=0$, $\lim_{x\to+\infty}F=1$.
- Discreta: escalera (saltos en los valores de $p_X$). Continua: sin saltos, $F'=f$.

### Hueco 2 — Función de una VA (transformación)
- **Discreta:** se reúnen los valores que colisionan:
$$
p_Y(y)=P(g(X)=y)=\sum_{x:\,g(x)=y}p_X(x)
$$
- **Continua y $h$ estrictamente monótona y derivable (Teo. 2.38):**
$$
f_Y(y)=f_X\!\left(h^{-1}(y)\right)\left|\frac{d}{dy}h^{-1}(y)\right|
$$
- **No monótona (ej. $Y=X^{2}$, $Y=\lvert X\rvert$):** método de la FDA →
$$
F_Y(y)=P\left(g(X)\le y\right)\quad\text{y luego derivar}
$$
- Regla práctica: **siempre se puede** con la FDA; la fórmula del jacobiano es un atajo para $h$ monótona.

### Hueco 3 — Uniforme discreta $X\sim\text{UD}(n)$
$$
P(X=x)=\frac{1}{n},\quad x=1,2,\dots,n;\qquad E(X)=\frac{n+1}{2};\qquad V(X)=\frac{n^{2}-1}{12}
$$
$$
m_X(t)=\frac{1}{n}\sum_{x=1}^{n}e^{xt}
$$
- Se usa cuando hay $n$ resultados **igualmente probables**: dado, ruleta, sorteo, tarjeta al azar.

### Hueco 4 — Weibull $X\sim W(a,\beta)$ (notación de Blanco)
$$
f(x)=a\beta\,x^{\beta-1}e^{-a x^{\beta}}\quad(x\ge 0),\qquad F(x)=1-e^{-a x^{\beta}}
$$
$$
E(X)=a^{-1/\beta}\,\Gamma\!\left(1+\frac{1}{\beta}\right),\qquad
V(X)=a^{-2/\beta}\left[\Gamma\!\left(1+\frac{2}{\beta}\right)-\Gamma^{2}\!\left(1+\frac{1}{\beta}\right)\right]
$$
- Se usa para **tiempos de vida / duración** con riesgo variable (a diferencia de la exponencial, aquí la tasa de falla no es constante).
- ⚠️ **Notación:** Ross y otros escriben $f(x)=\frac{\beta}{\eta}\left(\frac{x}{\eta}\right)^{\beta-1}e^{-(x/\eta)^{\beta}}$; equivalencia $a=\eta^{-\beta}$. Si el ejercicio da "escala $\eta$", pasa a $a$ antes de usar la fórmula de Blanco.

### Hueco 5 — Función característica
$$
\varphi_X(t)=E\left(e^{itX}\right)
$$
- **Siempre existe** (a diferencia de la FGM) y **caracteriza** la distribución.
- $\varphi(0)=1$, $|\varphi(t)|\le 1$.
- Momentos: $\varphi^{(r)}(0)=i^{r}E(X^{r})$, es decir $E(X)=\dfrac{\varphi'(0)}{i}$, $E(X^{2})=-\varphi''(0)$.
- En la práctica del curso: **saber qué es, que siempre existe y que identifica la distribución**. No te van a pedir integrales complejas.

---

## 🕐 4. EL PLAN, DÍA POR DÍA

### 🗓️ DÍA 1 — Jueves 12/11 (HOY) · 2 h · *Base conceptual*

| Bloque | Tiempo | Qué hacer | Fuente |
|---|---|---|---|
| 1.1 Diagnóstico | 15 min | Resolver 5 preguntas de "¿qué modelo es?" sin calcular (ver §6). Anotar fallos. | este plan |
| 1.2 VA y FDA | 40 min | Leer y resumir: concepto, distribución, FDA, clasificación discreta/continua. Cerrar el Hueco 1. | Diapositivas *VA reales* §1–4; Blanco §2.1–2.2 |
| 1.3 Esperanza y varianza | 35 min | $E[g(X)]$ discreta y continua, linealidad, $V(X)=E(X^{2})-[E(X)]^{2}$, propiedades. | `261014` §2.A–§2.B; Blanco §2.4 |
| 1.4 Micro‑ejercicios | 30 min | 4 cálculos: $P(X\le k)$ desde $f$, desde $F$, $E(X)$, $V(X)$. Verificar a mano. | `261014` §4 |

**Cierre del día:** escribir de memoria (1 hoja) las definiciones de $f$, $F$, $E$, $V$ para discreta y continua. Si no sale, es lo primero que se repasa mañana.

---

### 🗓️ DÍA 2 — Viernes 13/11 · 5 h · *Discretas completas + transformación*

| Bloque | Tiempo | Qué hacer | Fuente |
|---|---|---|---|
| 2.1 Uniforme discreta + Bernoulli + binomial | 45 min | PMF, $E$, $V$, FGM; **cuándo** se usa cada una. Cerrar Hueco 3. | Blanco §3.1; Discretos §1–2 |
| 2.2 Binomial negativa y geométrica | 45 min | Las **dos parametrizaciones** (intentos vs fracasos), $X=Y+k$, $E$, $V$. Traducir eventos entre ellas. | `261026` §2.A–§2.C |
| 2.3 Hipergeométrica y Poisson | 45 min | Sin reemplazo vs tasa constante; factor $\frac{N-n}{N-1}$; ajuste de $\lambda$ por unidades. | `261026` §2.D; `261028` §2.A |
| ☕ Pausa | 20 min | — | — |
| 2.4 **Transformación de una VA** | 60 min | Método FDA + Teo. 2.38. Resolver los ejemplos del libro ($Y=X^{2}$, $Y=\lvert X\rvert$, $Y=e^{X}$, $Y=aX+b$). Cerrar Hueco 2. | Blanco §2.3 |
| 2.5 Ejercicios situacionales | 60 min | **10 enunciados sin decir el modelo**: identificar + resolver. Priorizar los del profe. | `Ejercicios_MD.pdf`; `261026` §4 |
| 2.6 Cierre y errores | 25 min | Lista de "trampas" propias: rango de NB, corrección por continuidad, sin/con reemplazo. | `261026` §3 |

**Cierre del día:** tabla de las 6 discretas (modelo · parámetros · $E$ · $V$ · frase que la delata) escrita a mano, sin mirar.

---

### 🗓️ DÍA 3 — Domingo 15/11 · 3 h · *Continuas completas*

| Bloque | Tiempo | Qué hacer | Fuente |
|---|---|---|---|
| 3.1 Uniforme, exponencial, gamma/Erlang/ji‑cuadrado | 45 min | PDF, FDA, cola $e^{-\lambda x}$, falta de memoria, $E=r/\lambda$, $V=r/\lambda^{2}$. | `261028` §2.B–§2.D; `261104` §2.A–§2.B |
| 3.2 Normal | 45 min | Densidad, estandarización $Z=\frac{X-\mu}{\sigma}$, tabla $\Phi$, percentiles inversos, regla empírica. | `261109` §2.A–§2.D |
| 3.3 Beta + **Weibull** | 45 min | Beta para proporciones ($B(a,b)$, $E=\frac{a}{a+b}$). **Weibull**: densidad, $E$, $V$, cuándo se usa. Cerrar Hueco 4. | `261104` §2.D; Blanco §4.5 |
| 3.4 Aproximaciones | 30 min | Binomial→normal **con $\pm0{,}5$**, binomial→Poisson ($\lambda=np$), hipergeométrica→binomial. | `261026` §3; `261109` §2.E |
| 3.5 Hueco 5 | 15 min | Función característica: qué es, siempre existe, caracteriza, relación con momentos. | Blanco §2.4; *Valor esperado* §5 |

**Cierre del día:** resolver **2 ejercicios de continuas de punta a punta** sin mirar fórmulas, y al final contrastar con la cheatsheet.

---

### 🗓️ DÍA 4 — Lunes 16/11 · 5 h · *Integración y simulacro* (parcial en la tarde)

| Bloque | Tiempo | Qué hacer |
|---|---|---|
| 4.1 Mapa de decisión | 30 min | Repasar la tabla maestra (§5) y escribir la **hoja de bolsillo** (1 cara): 12 distribuciones con PMF/PDF, $E$, $V$ y "frase que la delata". |
| 4.2 **Simulacro 1** | 90 min | 8 ejercicios situacionales variados, cronometrados, **sin** indicar el modelo. Como el parcial. |
| 4.3 Corrección | 45 min | Corregir y clasificar cada error: (a) identificación, (b) parámetros, (c) unidades, (d) cálculo, (e) redacción de la probabilidad. |
| ☕ Pausa | 20 min | — |
| 4.4 **Simulacro 2 express** | 60 min | 5 ejercicios **solo de los temas flojos** detectados en 4.3. |
| 4.5 Repaso de huecos | 30 min | Transformación, Weibull, uniforme discreta, característica: solo las fórmulas y un ejemplo de cada uno. |
| 4.6 Logística | 25 min | Checklist final (§7), materiales, calculadora, horario. **No** estudiar temas nuevos. |

> ⚠️ **Regla del día del examen:** si un tema no está en la hoja de bolsillo a las 12:00, ya no entra. Lo que gana puntos es **identificar bien el modelo**, no memorizar integrales.

---

## 🧠 5. COMO EL PROFESOR PREGUNTA: PROTOCOLO DE 5 PASOS

Los enunciados son **situaciones**, no "calcule $P(X=3)$ con $\lambda=2$". El examen es de **traducción**. Protocolo:

1. **¿Qué se mide?**
   - Un **conteo** (cuántos) → discreta (binomial, Poisson, hipergeométrica, NB).
   - Un **tiempo o longitud** → continua (exponencial, gamma, Weibull, uniforme).
   - Una **proporción entre 0 y 1** → beta.
   - Un **valor simétrico alrededor de una media** con datos de promedio y dispersión → normal.
2. **¿El experimento se repite?** ¿Ensayos independientes con $p$ constante? ¿Se **fija $n$** (binomial) o se **espera hasta $k$** (NB/geométrica)?
3. **¿Hay reemplazo?** Sin reemplazo de población finita → hipergeométrica. Con reemplazo / población enorme → binomial.
4. **¿Hay tasa por unidad de tiempo?** → Poisson (conteo) o exponencial/gamma (tiempo). Ajustar $\lambda$ a las unidades pedidas.
5. **¿Dice "dado que ya…"?** → falta de memoria (exponencial) o condicional.

**Tabla maestra de bolsillo:**

| Frase del enunciado | Modelo | Fórmula base | $E$ | $V$ |
|---|---|---|---|---|
| $n$ resultados equiprobables | UD$(n)$ | $\frac{1}{n}$ | $\frac{n+1}{2}$ | $\frac{n^{2}-1}{12}$ |
| $n$ ensayos, $p$ constante | Bin$(n,p)$ | $\binom{n}{x}p^{x}(1-p)^{n-x}$ | $np$ | $np(1-p)$ |
| hasta el $k$-ésimo éxito | NB$(k,p)$ | $\binom{x-1}{k-1}p^{k}(1-p)^{x-k}$ | $\frac{k}{p}$ | $\frac{k(1-p)}{p^{2}}$ |
| hasta el primer éxito | Geom$(p)$ | $p(1-p)^{x-1}$ | $\frac{1}{p}$ | $\frac{1-p}{p^{2}}$ |
| muestra sin reemplazo | Hiperg$(n,N,K)$ | $\frac{\binom{K}{x}\binom{N-K}{n-x}}{\binom{N}{n}}$ | $n\frac{K}{N}$ | $n\frac{K}{N}\left(1-\frac{K}{N}\right)\frac{N-n}{N-1}$ |
| conteo con tasa constante | Poisson$(\lambda)$ | $\frac{e^{-\lambda}\lambda^{x}}{x!}$ | $\lambda$ | $\lambda$ |
| valor constante en $[a,b]$ | $U(a,b)$ | $\frac{1}{b-a}$ | $\frac{a+b}{2}$ | $\frac{(b-a)^{2}}{12}$ |
| tiempo hasta el 1.er evento | Exp$(\lambda)$ | $\lambda e^{-\lambda x}$ | $\frac{1}{\lambda}$ | $\frac{1}{\lambda^{2}}$ |
| tiempo hasta el $r$-ésimo evento | Gamma$(r,\lambda)$ | $\frac{\lambda^{r}}{\Gamma(r)}x^{r-1}e^{-\lambda x}$ | $\frac{r}{\lambda}$ | $\frac{r}{\lambda^{2}}$ |
| simétrico con $\mu$ y $\sigma$ | $N(\mu,\sigma)$ | $\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^{2}}{2\sigma^{2}}}$ | $\mu$ | $\sigma^{2}$ |
| proporción en $(0,1)$ | Beta$(a,b)$ | $\frac{x^{a-1}(1-x)^{b-1}}{B(a,b)}$ | $\frac{a}{a+b}$ | $\frac{ab}{(a+b)^{2}(a+b+1)}$ |
| duración con riesgo variable | $W(a,\beta)$ | $a\beta x^{\beta-1}e^{-a x^{\beta}}$ | $a^{-1/\beta}\Gamma\!\left(1+\frac{1}{\beta}\right)$ | ver Hueco 4 |

---

## 📝 6. DIAGNÓSTICO DE ENTRADA (15 min, hoy)

Responder **solo con el nombre del modelo** y los parámetros (sin calcular):

1. En una línea de producción, la probabilidad de que una pieza salga defectuosa es 0,02. Se revisan 50 piezas. ¿Probabilidad de encontrar exactamente 2 defectuosas?
2. Un lote de 40 piezas tiene 5 defectuosas. Se toman 8 al azar **sin** devolverlas. ¿Probabilidad de que haya 2 defectuosas?
3. Llegan llamadas a una central a razón de 6 por hora. ¿Probabilidad de que la próxima llamada tarde más de 20 minutos?
4. Una pareja quiere tener 3 hijos varones, con $p=0{,}51$ en cada nacimiento. ¿Probabilidad de que necesiten más de 5 nacimientos?
5. Una máquina llena envases con media 500 ml y desviación 8 ml. ¿Probabilidad de que un envase tenga menos de 490 ml?
6. El porcentaje de impurezas de un lote es una proporción entre 0 y 1. ¿Qué modelo lo describe?
7. Se sabe que un componente ya funcionó 300 horas. ¿Probabilidad de que funcione al menos 100 más?

**Respuestas:** 1) Bin$(50;0{,}02)$ · 2) Hiperg$(8,40,5)$ · 3) Exp$(6/\mathrm{h})$ en horas → $20$ min $=\frac13$ h · 4) NB$(3;0{,}51)$ · 5) $N(500,8)$ · 6) Beta $(a,b)$ · 7) Exponencial **por falta de memoria**: $P(X>100)$.

> Si aciertas **6 o 7**: estás listo para practicar; el plan es repaso. Si aciertas **4 o menos**: los días 1 y 2 son la prioridad, y el día 4 va sí o sí con simulacro.

---

## ✅ 7. CHECKLIST FINAL (lunes antes de salir)

- [ ] Hoja de bolsillo de 1 cara con las 12 distribuciones (PMF/PDF, $E$, $V$, frase clave).
- [ ] Sé escribir de memoria $V(X)=E(X^{2})-[E(X)]^{2}$ y $E[g(X)]$ en los dos casos.
- [ ] Sé pasar entre las dos parametrizaciones de la binomial negativa.
- [ ] Sé aplicar la corrección por continuidad $\pm0{,}5$.
- [ ] Sé usar la tabla normal en los dos sentidos (dado $z$ → probabilidad; dada la probabilidad → $z$).
- [ ] Sé hacer una transformación de VA por el método de la FDA.
- [ ] Tengo la fórmula de Weibull y su $E(X)$.
- [ ] Revisé **qué NO entra** (vectores, condicional, teoremas límite) para no perder tiempo.
- [ ] Calculadora, lápiz, borrador, y la hoja de fórmulas.

---

## 📅 RESUMEN EN UNA TABLA

| Día | Fecha | Horas | Foco | Producto del día |
|---|---|---|---|---|
| 1 | Jue 12/11 | 2 h | Base: VA, FDA, esperanza | Hoja de definiciones |
| 2 | Vie 13/11 | 5 h | Discretas + transformación | Tabla de 6 discretas |
| 3 | Dom 15/11 | 3 h | Continuas + Weibull | 2 ejercicios completos |
| 4 | Lun 16/11 | 5 h | Simulacros + repaso | Hoja de bolsillo |
| **Total** | | **15 h** | | **Parcial** |
