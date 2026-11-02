# 📘 CHEATSHEET — PROBABILIDAD · 28/10/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `PROBABILIDAD281026.md`
> - **Fecha de transcripción:** 28/10/2026 (`DDMMAA` = `281026`)
> - **Tema:** Modelos continuos — Poisson · Uniforme continua · Gamma (Erlang, Ji-cuadrado, Exponencial)
> - **Fuente:** transcripción de clase. Complementos marcados con `➕`.
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `PROBABILIDAD281026` §2.D» (el § y la letra identifican el bloque exacto).

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿Qué se cuenta o qué se mide?**
   - Se cuenta **número de eventos** en un intervalo (tiempo, longitud, área, volumen) → **Poisson**.
   - Se mide **tiempo/espacio hasta que ocurran \(r\) eventos** → **Gamma**.
   - Se mide un **valor continuo dentro de un intervalo con densidad constante** → **Uniforme continua**.
2. **Paso 1 — ¿Hay una sola palabra clave en el enunciado?** Aplicar la tabla de abajo.
3. **Paso 2 — ¿Qué unidades tienen el dato y la pregunta?** Si no coinciden, reajustar \(\lambda\) **antes** de calcular.
4. **Paso 3 — ¿La pregunta es "de cola"?** ("más de", "al menos", "por lo menos") → complemento de la FDA.

**Tabla de decisión (frase del enunciado → modelo):**

| Si el enunciado dice… | Modelo | Fórmula base |
|---|---|---|
| "número de llegadas / accidentes / nacimientos / defectos en un intervalo" | **Poisson** | \(P(X=x)=\dfrac{e^{-\lambda}\lambda^{x}}{x!}\) |
| "tiempo de espera hasta que ocurran \(r\) eventos" | **Gamma** | \(f(x)=\dfrac{\lambda^{r}}{\Gamma(r)}x^{r-1}e^{-\lambda x}\) |
| "tiempo hasta el primer evento" / "tiempo de vida" con tasa constante | **Gamma con \(r=1\)** = **Exponencial** | \(f(x)=\lambda e^{-\lambda x}\) |
| menciona **"Erlang"** | **Gamma** con \(r\) entero positivo | \(\Gamma(r)=(r-1)!\) |
| menciona **"Ji-cuadrado" / "Chi-cuadrado"** | **Gamma** con \(\lambda=\tfrac12\), \(r=\tfrac{k}{2}\) | \(E(X)=k\), \(V(X)=2k\) |
| "cualquier valor entre \(a\) y \(b\) con la misma probabilidad" / "elegido al azar en \([a,b]\)" / número aleatorio | **Uniforme continua** | \(f(x)=\dfrac{1}{b-a}\) |
| "los eventos ocurren de forma independiente y a tasa constante" | **Poisson** (o **Gamma** si se pregunta por el tiempo) | — |

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Poisson (conteo de eventos)

- **Condición:** \(x\) = número de ocurrencias en un intervalo.
- **PMF:**
$$
P(X=x)=\frac{e^{-\lambda}\lambda^{x}}{x!}
$$
- **Rango:** \(x=0,1,2,\dots\)
- **FDA:**
$$
F(x)=P(X\le x)=\sum_{k=0}^{x}\frac{e^{-\lambda}\lambda^{k}}{k!}
$$
- **Media:** \(E(X)=\lambda\)
- **Varianza:** \(V(X)=\lambda\)

> **🔤 Diccionario:**
> - \(x\): número de eventos que ocurren en el intervalo evaluado.
> - \(\lambda\) (*lambda*): intensidad o tasa media de eventos **en el intervalo evaluado**; debe estar en las mismas unidades de tiempo/espacio que \(x\).
> - \(e\): constante de Euler (\(\approx 2{,}71828\)).
> - \(k\): índice mudo de la sumatoria (todos los conteos \(\le x\)).

---

### B. Uniforme Continua

- **Condición:** \(X\) toma cualquier valor real entre \(a\) y \(b\) con densidad constante.
- **PDF:**
$$
f(x)=\frac{1}{b-a}\quad\text{para } a\le x\le b,\qquad f(x)=0 \text{ fuera}
$$
- **FDA:**
$$
F(x)=\frac{x-a}{b-a}\quad\text{para } a\le x\le b
$$
- **Probabilidad de un intervalo:**
$$
P(c\le X\le d)=\frac{d-c}{b-a}
$$
- **Media:** \(E(X)=\dfrac{a+b}{2}\)
- **Varianza:** \(V(X)=\dfrac{(b-a)^{2}}{12}\)

> **🔤 Diccionario:**
> - \(a\): límite inferior del intervalo (soporte).
> - \(b\): límite superior del intervalo (soporte).
> - \(x\): valor específico que se está evaluando.
> - \(c,d\): extremos del sub-intervalo cuya probabilidad se pide (\(a\le c<d\le b\)).

---

### C. Función Gamma (la base matemática)

- **Definición:**
$$
\Gamma(r)=\int_{0}^{\infty}x^{r-1}e^{-x}\,dx\qquad r>0
$$
- **Propiedad clave (si \(r\) es entero positivo):** \(\Gamma(r)=(r-1)!\)
- **Recursión (siempre):** \(\Gamma(r+1)=r\,\Gamma(r)\)
- **Casos base:** \(\Gamma(1)=1\), \(\Gamma(1/2)=\sqrt{\pi}\)
- **Micro-verificación:** \(\Gamma(4)=3!=6\)

> **🔤 Diccionario:**
> - \(r\): argumento de la función gamma (positivo).
> - \(x\): variable de integración (se elimina al integrar).
> - \(\Gamma(r)\): constante normalizadora de la distribución Gamma.

---

### D. Distribución Gamma (tiempo hasta el \(r\)-ésimo evento)

- **Condición:** tiempo de espera hasta el \(r\)-ésimo evento de un proceso de Poisson de tasa \(\lambda\).
- **PDF:**
$$
f(x)=\frac{\lambda^{r}}{\Gamma(r)}\,x^{r-1}e^{-\lambda x}\quad\text{para } x>0,\qquad f(x)=0 \text{ fuera}
$$
- **Media:** \(E(X)=\dfrac{r}{\lambda}\)
- **Varianza:** \(V(X)=\dfrac{r}{\lambda^{2}}\)
- **FGM:**
$$
m_X(t)=\left(1-\frac{t}{\lambda}\right)^{-r}\quad\text{para } t<\lambda
$$
- **Derivadas de la FGM (para llegar a los momentos):**
$$
m_X'(t)=\frac{r}{\lambda}\left(1-\frac{t}{\lambda}\right)^{-(r+1)},\qquad
m_X''(t)=\frac{r(r+1)}{\lambda^{2}}\left(1-\frac{t}{\lambda}\right)^{-(r+2)}
$$
- **FDA ↔ Poisson (solo para \(r\) entero, caso Erlang):**
$$
P(X> t)=\sum_{k=0}^{r-1}\frac{e^{-\lambda t}(\lambda t)^{k}}{k!}
$$

> **🔤 Diccionario:**
> - \(r\): parámetro de **forma** (número de eventos que se esperan); \(r>0\).
> - \(\lambda\): parámetro de **tasa** (eventos por unidad de tiempo o espacio); \(\lambda>0\).
> - \(\Gamma(r)\): valor de la función gamma evaluada en \(r\).
> - \(x\): tiempo (o longitud) acumulado hasta el \(r\)-ésimo evento.
> - \(t\): valor de la FGM (variable de la transformada), no un tiempo físico.
> - ⚠️ **Trampa de notación:** si un libro escribe \(\Gamma(\alpha,\beta)\) con \(\beta\) como **escala**, entonces aquí \(\lambda=1/\beta\) y \(r=\alpha\).

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

**🟢 Caso 0 — Exponencial = Gamma con \(r=1\)**
- \(f(x)=\lambda e^{-\lambda x}\), \(F(x)=1-e^{-\lambda x}\), \(E(X)=1/\lambda\), \(V(X)=1/\lambda^{2}\).
- **Falta de memoria:** \(P(X>s+t\mid X>s)=P(X>t)=e^{-\lambda t}\).
- Si el tiempo ya transcurrido no cambia la probabilidad futura → es Exponencial, no hay que integrar.

**🟢 Caso 1 — Distribución Erlang**
- Condición: \(r\) entero positivo (\(r=1,2,3,\dots\)) y \(\lambda>0\).
- Acción: mismas fórmulas de Gamma, pero en la PDF se reemplaza \(\Gamma(r)\) por \((r-1)!\).

**🟢 Caso 2 — Ji-cuadrado (Chi-cuadrado)**
- Condición: \(\lambda=1/2\) y \(r=k/2\) (\(k\) = grados de libertad, entero positivo).
- Media: \(E(X)=k\)
- Varianza: \(V(X)=2k\)
- FGM: \(m_X(t)=(1-2t)^{-k/2}\) para \(t<1/2\).

**🔑 Relación Poisson ↔ Gamma (regla de oro cruzada)**
- Poisson responde *"¿cuántos eventos?"*; Gamma responde *"¿cuándo llega el \(r\)-ésimo?"*.
- Son la misma información vista al revés: «el \(r\)-ésimo evento ocurre después de \(t\)» equivale a «en \([0,t]\) hubo a lo sumo \(r-1\) eventos».

**⚠️ Colas y complementos (aplican a todos los modelos)**
- "más de \(k\)" → \(1-P(X\le k)\)
- "al menos \(k\)" / "por lo menos \(k\)" → \(1-P(X\le k-1)\)
- "entre \(a\) y \(b\)" (extremos incluidos) → \(F(b)-F(a-1)\) en discretas; \(\dfrac{d-c}{b-a}\) en uniforme.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 🧩 Algoritmo general (cualquier problema)
1. **Identifica** el modelo con el Radar (§1).
2. **Extrae parámetros:** \(\lambda\), \(r\), \(a\), \(b\), \(x\).
3. **Traduce:** convierte el texto a probabilidad (usa la tabla de colas de §3).
4. **Aplica fórmula:** sustituye y calcula la sumatoria o la integral.
5. **Verifica:** unidades de \(\lambda\) iguales a las de \(x\); resultado en \([0,1]\); rango de \(x\) dentro del soporte.

**Plantilla mínima:** «tasa \(30\) por hora, se piden \(3\) minutos» → \(\lambda=\frac{30\cdot 3}{60}=1{,}5\) → aplicar Poisson con \(\lambda=1{,}5\).

---

### 🧮 Algoritmo Poisson (cuando el tiempo cambia)
1. Identifica la tasa base (ej.: \(30\) llamadas por hora).
2. Mira el intervalo que pide el problema (ej.: \(3\) minutos).
3. **Regla de 3 para \(\lambda\):**
$$
\lambda_{\text{nuevo}}=\lambda_{\text{base}}\cdot\frac{\text{intervalo pedido}}{\text{intervalo base}}
$$
4. Sustituye en \(P(X=x)=\dfrac{e^{-\lambda}\lambda^{x}}{x!}\), o acumula con la FDA si pide "a lo sumo".
5. Si pide cola: "más de \(k\)" → \(1-P(X\le k)\); "al menos \(k\)" → \(1-P(X\le k-1)\).

**Plantilla mínima:** \(P(X=2)\) con \(\lambda=1{,}5\) → \(\dfrac{e^{-1{,}5}(1{,}5)^{2}}{2!}\).

---

### 📏 Algoritmo Uniforme (límites)
1. Identifica \(a\) y \(b\) (extremos del soporte).
2. Si pide un intervalo \(P(c\le X\le d)\) → \(\dfrac{d-c}{b-a}\).
3. Si pide un punto exacto \(P(X=k)\) → **siempre \(0\)**.
4. Si el evento cae fuera de \([a,b]\): probabilidad \(0\) (evento imposible) o \(1\) (evento seguro); nunca se integra fuera del soporte.

**Plantilla mínima:** \(X\sim U(2,10)\) → \(P(4\le X\le 7)=\dfrac{7-4}{10-2}=\dfrac{3}{8}\).

---

### ⏱️ Algoritmo Gamma (tiempo de espera y momentos)
1. **Verifica el radar:** tiempo hasta el \(r\)-ésimo evento → Gamma.
2. **Ajusta \(\lambda\)** a la unidad de tiempo de la pregunta (igual que en Poisson).
3. Si piden **esperanza o varianza** directo: usa \(\dfrac{r}{\lambda}\) y \(\dfrac{r}{\lambda^{2}}\). **No integres.**
4. Si piden **usar la FGM**: deriva \(m_X(t)\), evalúa en \(t=0\) para \(E(X)\); deriva dos veces y evalúa en \(t=0\) para \(E(X^{2})\).
5. Cierra con:
$$
V(X)=E(X^{2})-\left[E(X)\right]^{2}
$$
6. Si piden una probabilidad y \(r\) es **entero**: usa la suma de Poisson de §2.D; si \(r\) no es entero, integra la PDF o usa la ji-cuadrado.

**Plantilla mínima (momentos por FGM):**
$$
m_X'(0)=\frac{r}{\lambda}=E(X),\qquad
E(X^{2})=m_X''(0)=\frac{r(r+1)}{\lambda^{2}},\qquad
V(X)=\frac{r(r+1)}{\lambda^{2}}-\frac{r^{2}}{\lambda^{2}}=\frac{r}{\lambda^{2}}
$$

---

## ✅ 5. CHECKLIST FINAL (30 segundos antes de entregar)

- [ ] ¿El modelo elegido responde **cuántos** (Poisson) o **cuándo** (Gamma) o **qué valor** (uniforme)?
- [ ] ¿\(\lambda\) está en las **mismas unidades** que el intervalo pedido?
- [ ] ¿Usé complemento \(1-F(\cdot)\) donde el enunciado dice "más de" / "al menos"?
- [ ] ¿El resultado está entre \(0\) y \(1\)?
- [ ] ¿En Gamma usé \(\Gamma(r)=(r-1)!\) solo porque \(r\) es entero?
- [ ] ¿En uniforme reemplacé la integral solo dentro de \([a,b]\)?
