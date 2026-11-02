# ðŸ“˜ CHEATSHEET â€” PROBABILIDAD Â· 28/10/2026

> **ðŸ§¾ FICHA DEL ARCHIVO**
> - **Archivo:** `PROBABILIDAD281026.md`
> - **Fecha de transcripciÃ³n:** 28/10/2026 (`DDMMAA` = `281026`)
> - **Tema:** Modelos continuos â€” Poisson Â· Uniforme continua Â· Gamma (Erlang, Ji-cuadrado, Exponencial)
> - **Fuente:** transcripciÃ³n de clase. Complementos marcados con `âž•`.
> - **CÃ³mo citarla al resolver ejercicios:** Â«ðŸ“˜ Cheatsheet `PROBABILIDAD281026` Â§2.DÂ» (el Â§ y la letra identifican el bloque exacto).

---

## ðŸ§­ 1. PROTOCOLO DE IDENTIFICACIÃ“N (El Radar)

**DecisiÃ³n en orden:**

1. **Paso 0 â€” Â¿QuÃ© se cuenta o quÃ© se mide?**
   - Se cuenta **nÃºmero de eventos** en un intervalo (tiempo, longitud, Ã¡rea, volumen) â†’ **Poisson**.
   - Se mide **tiempo/espacio hasta que ocurran \(r\) eventos** â†’ **Gamma**.
   - Se mide un **valor continuo dentro de un intervalo con densidad constante** â†’ **Uniforme continua**.
2. **Paso 1 â€” Â¿Hay una sola palabra clave en el enunciado?** Aplicar la tabla de abajo.
3. **Paso 2 â€” Â¿QuÃ© unidades tienen el dato y la pregunta?** Si no coinciden, reajustar \(\lambda\) **antes** de calcular.
4. **Paso 3 â€” Â¿La pregunta es "de cola"?** ("mÃ¡s de", "al menos", "por lo menos") â†’ complemento de la FDA.

**Tabla de decisiÃ³n (frase del enunciado â†’ modelo):**

| Si el enunciado diceâ€¦                                                                                               | Modelo                                                 | FÃ³rmula base                                                 |
| ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------ | ------------------------------------------------------------ |
| "nÃºmero de llegadas / accidentes / nacimientos / defectos en un intervalo"                                          | **Poisson**                                            | \(P(X=x)=\dfrac{e^{-\lambda}\lambda^{x}}{x!}\)               |
| "tiempo de espera hasta que ocurran \(r\) eventos"                                                                  | **Gamma**                                              | \(f(x)=\dfrac{\lambda^{r}}{\Gamma(r)}x^{r-1}e^{-\lambda x}\) |
| "tiempo hasta el primer evento" / "tiempo de vida" con tasa constante                                               | **Gamma con \(r=1\)** = **Exponencial**                | \(f(x)=\lambda e^{-\lambda x}\)                              |
| menciona **"Erlang"**                                                                                               | **Gamma** con \(r\) entero positivo                    | \(\Gamma(r)=(r-1)!\)                                         |
| menciona **"Ji-cuadrado" / "Chi-cuadrado"**                                                                         | **Gamma** con \(\lambda=\tfrac12\), \(r=\tfrac{k}{2}\) | \(E(X)=k\), \(V(X)=2k\)                                      |
| "cualquier valor entre \(a\) y \(b\) con la misma probabilidad" / "elegido al azar en \([a,b]\)" / nÃºmero aleatorio | **Uniforme continua**                                  | \(f(x)=\dfrac{1}{b-a}\)                                      |
| "los eventos ocurren de forma independiente y a tasa constante"                                                     | **Poisson** (o **Gamma** si se pregunta por el tiempo) | â€”                                                            |

---

## ðŸ› ï¸ 2. CAJA DE HERRAMIENTAS (FÃ³rmulas y Diccionario)

### A. Poisson (conteo de eventos)

- **CondiciÃ³n:** \(x\) = nÃºmero de ocurrencias en un intervalo.
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

> **ðŸ”¤ Diccionario:**
> - \(x\): nÃºmero de eventos que ocurren en el intervalo evaluado.
> - \(\lambda\) (*lambda*): intensidad o tasa media de eventos **en el intervalo evaluado**; debe estar en las mismas unidades de tiempo/espacio que \(x\).
> - \(e\): constante de Euler (\(\approx 2{,}71828\)).
> - \(k\): Ã­ndice mudo de la sumatoria (todos los conteos \(\le x\)).

---

### B. Uniforme Continua

- **CondiciÃ³n:** \(X\) toma cualquier valor real entre \(a\) y \(b\) con densidad constante.
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

> **ðŸ”¤ Diccionario:**
> - \(a\): lÃ­mite inferior del intervalo (soporte).
> - \(b\): lÃ­mite superior del intervalo (soporte).
> - \(x\): valor especÃ­fico que se estÃ¡ evaluando.
> - \(c,d\): extremos del sub-intervalo cuya probabilidad se pide (\(a\le c<d\le b\)).

---

### C. FunciÃ³n Gamma (la base matemÃ¡tica)

- **DefiniciÃ³n:**
$$
\Gamma(r)=\int_{0}^{\infty}x^{r-1}e^{-x}\,dx\qquad r>0
$$
- **Propiedad clave (si \(r\) es entero positivo):** \(\Gamma(r)=(r-1)!\)
- **RecursiÃ³n (siempre):** \(\Gamma(r+1)=r\,\Gamma(r)\)
- **Casos base:** \(\Gamma(1)=1\), \(\Gamma(1/2)=\sqrt{\pi}\)
- **Micro-verificaciÃ³n:** \(\Gamma(4)=3!=6\)

> **ðŸ”¤ Diccionario:**
> - \(r\): argumento de la funciÃ³n gamma (positivo).
> - \(x\): variable de integraciÃ³n (se elimina al integrar).
> - \(\Gamma(r)\): constante normalizadora de la distribuciÃ³n Gamma.

---

### D. DistribuciÃ³n Gamma (tiempo hasta el \(r\)-Ã©simo evento)

- **CondiciÃ³n:** tiempo de espera hasta el \(r\)-Ã©simo evento de un proceso de Poisson de tasa \(\lambda\).
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
- **FDA â†” Poisson (solo para \(r\) entero, caso Erlang):**
$$
P(X> t)=\sum_{k=0}^{r-1}\frac{e^{-\lambda t}(\lambda t)^{k}}{k!}
$$

> **ðŸ”¤ Diccionario:**
> - \(r\): parÃ¡metro de **forma** (nÃºmero de eventos que se esperan); \(r>0\).
> - \(\lambda\): parÃ¡metro de **tasa** (eventos por unidad de tiempo o espacio); \(\lambda>0\).
> - \(\Gamma(r)\): valor de la funciÃ³n gamma evaluada en \(r\).
> - \(x\): tiempo (o longitud) acumulado hasta el \(r\)-Ã©simo evento.
> - \(t\): valor de la FGM (variable de la transformada), no un tiempo fÃ­sico.
> - âš ï¸ **Trampa de notaciÃ³n:** si un libro escribe \(\Gamma(\alpha,\beta)\) con \(\beta\) como **escala**, entonces aquÃ­ \(\lambda=1/\beta\) y \(r=\alpha\).

---

## ðŸ”„ 3. REGLAS DE ORO Y CASOS ESPECIALES

**ðŸŸ¢ Caso 0 â€” Exponencial = Gamma con \(r=1\)**
- \(f(x)=\lambda e^{-\lambda x}\), \(F(x)=1-e^{-\lambda x}\), \(E(X)=1/\lambda\), \(V(X)=1/\lambda^{2}\).
- **Falta de memoria:** \(P(X>s+t\mid X>s)=P(X>t)=e^{-\lambda t}\).
- Si el tiempo ya transcurrido no cambia la probabilidad futura â†’ es Exponencial, no hay que integrar.

**ðŸŸ¢ Caso 1 â€” DistribuciÃ³n Erlang**
- CondiciÃ³n: \(r\) entero positivo (\(r=1,2,3,\dots\)) y \(\lambda>0\).
- AcciÃ³n: mismas fÃ³rmulas de Gamma, pero en la PDF se reemplaza \(\Gamma(r)\) por \((r-1)!\).

**ðŸŸ¢ Caso 2 â€” Ji-cuadrado (Chi-cuadrado)**
- CondiciÃ³n: \(\lambda=1/2\) y \(r=k/2\) (\(k\) = grados de libertad, entero positivo).
- Media: \(E(X)=k\)
- Varianza: \(V(X)=2k\)
- FGM: \(m_X(t)=(1-2t)^{-k/2}\) para \(t<1/2\).

**ðŸ”‘ RelaciÃ³n Poisson â†” Gamma (regla de oro cruzada)**
- Poisson responde *"Â¿cuÃ¡ntos eventos?"*; Gamma responde *"Â¿cuÃ¡ndo llega el \(r\)-Ã©simo?"*.
- Son la misma informaciÃ³n vista al revÃ©s: Â«el \(r\)-Ã©simo evento ocurre despuÃ©s de \(t\)Â» equivale a Â«en \([0,t]\) hubo a lo sumo \(r-1\) eventosÂ».

**âš ï¸ Colas y complementos (aplican a todos los modelos)**
- "mÃ¡s de \(k\)" â†’ \(1-P(X\le k)\)
- "al menos \(k\)" / "por lo menos \(k\)" â†’ \(1-P(X\le k-1)\)
- "entre \(a\) y \(b\)" (extremos incluidos) â†’ \(F(b)-F(a-1)\) en discretas; \(\dfrac{d-c}{b-a}\) en uniforme.

---

## ðŸš€ 4. ALGORITMOS DE RESOLUCIÃ“N

### ðŸ§© Algoritmo general (cualquier problema)
1. **Identifica** el modelo con el Radar (Â§1).
2. **Extrae parÃ¡metros:** \(\lambda\), \(r\), \(a\), \(b\), \(x\).
3. **Traduce:** convierte el texto a probabilidad (usa la tabla de colas de Â§3).
4. **Aplica fÃ³rmula:** sustituye y calcula la sumatoria o la integral.
5. **Verifica:** unidades de \(\lambda\) iguales a las de \(x\); resultado en \([0,1]\); rango de \(x\) dentro del soporte.

**Plantilla mÃ­nima:** Â«tasa \(30\) por hora, se piden \(3\) minutosÂ» â†’ \(\lambda=\frac{30\cdot 3}{60}=1{,}5\) â†’ aplicar Poisson con \(\lambda=1{,}5\).

---

### ðŸ§® Algoritmo Poisson (cuando el tiempo cambia)
1. Identifica la tasa base (ej.: \(30\) llamadas por hora).
2. Mira el intervalo que pide el problema (ej.: \(3\) minutos).
3. **Regla de 3 para \(\lambda\):**
$$
\lambda_{\text{nuevo}}=\lambda_{\text{base}}\cdot\frac{\text{intervalo pedido}}{\text{intervalo base}}
$$
4. Sustituye en \(P(X=x)=\dfrac{e^{-\lambda}\lambda^{x}}{x!}\), o acumula con la FDA si pide "a lo sumo".
5. Si pide cola: "mÃ¡s de \(k\)" â†’ \(1-P(X\le k)\); "al menos \(k\)" â†’ \(1-P(X\le k-1)\).

**Plantilla mÃ­nima:** \(P(X=2)\) con \(\lambda=1{,}5\) â†’ \(\dfrac{e^{-1{,}5}(1{,}5)^{2}}{2!}\).

---

### ðŸ“ Algoritmo Uniforme (lÃ­mites)
1. Identifica \(a\) y \(b\) (extremos del soporte).
2. Si pide un intervalo \(P(c\le X\le d)\) â†’ \(\dfrac{d-c}{b-a}\).
3. Si pide un punto exacto \(P(X=k)\) â†’ **siempre \(0\)**.
4. Si el evento cae fuera de \([a,b]\): probabilidad \(0\) (evento imposible) o \(1\) (evento seguro); nunca se integra fuera del soporte.

**Plantilla mÃ­nima:** \(X\sim U(2,10)\) â†’ \(P(4\le X\le 7)=\dfrac{7-4}{10-2}=\dfrac{3}{8}\).

---

### â±ï¸ Algoritmo Gamma (tiempo de espera y momentos)
1. **Verifica el radar:** tiempo hasta el \(r\)-Ã©simo evento â†’ Gamma.
2. **Ajusta \(\lambda\)** a la unidad de tiempo de la pregunta (igual que en Poisson).
3. Si piden **esperanza o varianza** directo: usa \(\dfrac{r}{\lambda}\) y \(\dfrac{r}{\lambda^{2}}\). **No integres.**
4. Si piden **usar la FGM**: deriva \(m_X(t)\), evalÃºa en \(t=0\) para \(E(X)\); deriva dos veces y evalÃºa en \(t=0\) para \(E(X^{2})\).
5. Cierra con:
$$
V(X)=E(X^{2})-\left[E(X)\right]^{2}
$$
6. Si piden una probabilidad y \(r\) es **entero**: usa la suma de Poisson de Â§2.D; si \(r\) no es entero, integra la PDF o usa la ji-cuadrado.

**Plantilla mÃ­nima (momentos por FGM):**
$$
m_X'(0)=\frac{r}{\lambda}=E(X),\qquad
E(X^{2})=m_X''(0)=\frac{r(r+1)}{\lambda^{2}},\qquad
V(X)=\frac{r(r+1)}{\lambda^{2}}-\frac{r^{2}}{\lambda^{2}}=\frac{r}{\lambda^{2}}
$$

---

## âœ… 5. CHECKLIST FINAL (30 segundos antes de entregar)

- [ ] Â¿El modelo elegido responde **cuÃ¡ntos** (Poisson) o **cuÃ¡ndo** (Gamma) o **quÃ© valor** (uniforme)?
- [ ] Â¿\(\lambda\) estÃ¡ en las **mismas unidades** que el intervalo pedido?
- [ ] Â¿UsÃ© complemento \(1-F(\cdot)\) donde el enunciado dice "mÃ¡s de" / "al menos"?
- [ ] Â¿El resultado estÃ¡ entre \(0\) y \(1\)?
- [ ] Â¿En Gamma usÃ© \(\Gamma(r)=(r-1)!\) solo porque \(r\) es entero?
- [ ] Â¿En uniforme reemplacÃ© la integral solo dentro de \([a,b]\)?
