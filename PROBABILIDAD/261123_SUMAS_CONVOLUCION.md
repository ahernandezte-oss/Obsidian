# 📘 CHEATSHEET — PROBABILIDAD · 23/11/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `261123_SUMAS_CONVOLUCION.md`
> - **Fecha de transcripción:** 23/11/2026 (`AAMMDD` = `261123`)
> - **Tema principal:** DISTRIBUCIÓN DE LA SUMA DE VARIABLES INDEPENDIENTES — convolución discreta y continua · producto de FGM · combinaciones lineales de normales
> - **Fuentes:** transcripción de la clase del 23/11 + apuntes del estudiante + Liliana Blanco, cap. 5 (§5.4 y §5.6). Lo complementado va con `➕`.
> - **Continuidad:** viene de `261118_INDEPENDENCIA`. Aquí se usa la independencia para **sumar** variables; la próxima clase abre covarianza.
> - **Formato de las plantillas:** cadena de igualdades con justificación por renglón (§4.0).
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `261123_SUMAS_CONVOLUCION` §2.A».

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿Piden la distribución de $Z=X_1+\cdots+X_n$?** → sí: convolución (discreta §2.A, continua §2.B) o FGM (§2.C).
2. **Paso 1 — ¿Las variables son independientes?** Si no lo son, **no** se puede usar convolución ni producto de FGM: hay que integrar la conjunta.
3. **Paso 2 — ¿Discretas o continuas?** Suma de masas vs. integral de convolución.
4. **Paso 3 — ¿Piden solo una probabilidad $P(X+Y\ge k)$, no toda la distribución?** → integrar la conjunta sobre la región (§2.B + §4.C); suele ser más corto que la convolución.

| Si el enunciado dice… | Objeto | Fórmula base | 👉 Ir a |
|---|---|---|---|
| "$Z=X+Y$", ambas **discretas** e independientes | **convolución discreta** | $p_Z(z)=\sum_x p_X(x)p_Y(z-x)$ | **§2.A** + **§4.A** |
| "$Z=X+Y$", ambas **continuas** e independientes | **convolución continua** | $f_Z(z)=\int f_Y(z-x)f_X(x)\,dx$ | **§2.B** + **§4.B** |
| "suma de **Poisson** independientes" | **Poisson** | $\mathrm{P}(\lambda)+\mathrm{P}(\mu)=\mathrm{P}(\lambda+\mu)$ | **§2.A** |
| "suma de **exponenciales** con el **mismo** $\lambda$" | **Gamma** | $\mathrm{Exp}(\lambda)^{\ast n}=\Gamma(n,\lambda)$ | **§2.B** |
| "suma de **normales** independientes" | **normal** | $\mu$ se suma, $\sigma^2$ se suma | **§2.D** |
| "**combinación lineal** de normales" | **normal** | $\sum a_iX_i\sim N(\sum a_i\mu_i,\ \sum a_i^2\sigma_i^2)$ | **§2.D** + **§4.D** |
| "**media muestral** de normales" | **normal** | $\bar X\sim N(\mu,\sigma^2/n)$ | **§2.D** + **§4.E** |
| "halle la **FGM** de una suma" | **producto** | $m_Z(t)=\prod m_{X_i}(t)$ | **§2.C** + **§4.D** |
| "$P(X+Y\ge k)$" con densidades dadas | **región** | $\iint_{\{x+y\ge k\}} f$ | **§4.C** |
| "¿$g(X_1)$ y $h(X_2)$ son independientes?" | **bloques disjuntos** | funciones de bloques disjuntos son independientes | **§2.E** |

> 🗣️ **Frases del profe (literales) → método**
> - "Esta fórmula se conoce como la convolución de $X$ y $Y$." → §2.A–§2.B.
> - "Si yo sumo Poisson independientes, la distribución de esa suma también será Poisson y el parámetro será la suma." → §2.A.
> - "La suma de variables aleatorias independientes exponenciales con el mismo parámetro $\lambda$ es Gamma." → §2.B.
> - "La distribución de la suma se puede hallar si conocemos las funciones generadoras de momentos individuales, simplemente multiplicándolas." → §2.C.
> - "Entre más grande usted coja la muestra, la varianza se va a hacer más pequeña." → $\bar X\sim N(\mu,\sigma^2/n)$ (§2.D).

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Convolución discreta

$$
p_Z(z)=P(X+Y=z)=\sum_{x\in R_X}p_X(x)\,p_Y(z-x)
$$
con la convención $p_Y(z-x)=0$ si $z-x\notin R_Y$.

**Resultado clave:**
$$
X\sim\mathrm{P}(\lambda),\ Y\sim\mathrm{P}(\mu),\ X\perp Y\ \Longrightarrow\ Z=X+Y\sim\mathrm{P}(\lambda+\mu)
$$
y se generaliza a $n$ sumandos: $\sum_{i=1}^{n}\mathrm{P}(\lambda_i)=\mathrm{P}\left(\sum_i\lambda_i\right)$.

> **🔤 Diccionario:**
> - $z$: valor de la suma (fijo); $x$: valor que se le asigna a $X$; $z-x$: lo que debe valer $Y$ para que la suma dé $z$.
> - $R_X,R_Y$: recorridos; la suma recorre solo los $x$ que dejan $z-x$ dentro de $R_Y$.
> - $\lambda,\mu$: tasas de Poisson; se **suman** al sumar variables.
> - La convolución es conmutativa: $p_X*p_Y=p_Y*p_X$.

---

### B. Convolución continua

- **Por la f.d.a.c.:**
$$
F_Z(z)=P(X+Y\le z)=\int_{-\infty}^{\infty}F_Y(z-x)\,f_X(x)\,dx
$$
- **Derivando (densidad):**
$$
f_Z(z)=\int_{-\infty}^{\infty}f_Y(z-x)\,f_X(x)\,dx=(f_X*f_Y)(z)
$$
- **Resultado clave:**
$$
X,Y\sim\mathrm{Exp}(\lambda)\ \text{iid}\ \Longrightarrow\ Z=X+Y\sim\Gamma(2,\lambda),\qquad f_Z(z)=\lambda^{2}z\,e^{-\lambda z}\ (z>0)
$$
y en general $n$ exponenciales iid: $\Gamma(n,\lambda)$.

| Suma (independientes) | Resultado |
|---|---|
| $\mathrm{P}(\lambda)+\mathrm{P}(\mu)$ | $\mathrm{P}(\lambda+\mu)$ |
| $\mathrm{Exp}(\lambda)+\mathrm{Exp}(\lambda)$ | $\Gamma(2,\lambda)$ |
| $\mathrm{Exp}(\lambda)^{\ast n}$ | $\Gamma(n,\lambda)$ |
| $\mathrm{N}(\mu_1,\sigma_1^2)+\mathrm{N}(\mu_2,\sigma_2^2)$ | $\mathrm{N}(\mu_1+\mu_2,\ \sigma_1^2+\sigma_2^2)$ |
| ➕ $\mathrm{Bin}(n,p)+\mathrm{Bin}(m,p)$ | $\mathrm{Bin}(n+m,p)$ |
| ➕ $\Gamma(r,\lambda)+\Gamma(s,\lambda)$ | $\Gamma(r+s,\lambda)$ |

> **🔤 Diccionario:**
> - $f_Z$: densidad de la suma; **no** es $F_Z$ (a $F_Z$ se llega integrando, a $f_Z$ derivando).
> - El integrando se anula fuera del soporte: por eso $\int_{-\infty}^{\infty}$ se vuelve $\int_{0}^{z}$ con exponenciales.
> - $\Gamma(n,\lambda)$: forma $n$, tasa $\lambda$; $\mathrm{Exp}(\lambda)=\Gamma(1,\lambda)$.
> - **Trampa:** exponenciales con **distinto** $\lambda$ **no** dan Gamma (es una hipoexponencial).

---

### C. Producto de funciones generadoras de momentos

Si $X_1,\dots,X_n$ son independientes y $Z=X_1+\cdots+X_n$, entonces
$$
m_Z(t)=E\left(e^{tZ}\right)=\prod_{i=1}^{n}m_{X_i}(t)
$$
en todos los $t$ donde existan las $m_{X_i}$.

- La FGM **determina** la distribución: si el producto tiene forma conocida, se identifica la distribución de $Z$.
- Para $aX$: $m_{aX}(t)=m_X(at)$.

> **🔤 Diccionario:**
> - $m_X(t)=E(e^{tX})$: FGM; es una función de $t$, no del azar.
> - El producto **solo** vale con independencia: sin ella, $E(e^{t(X+Y)})\neq E(e^{tX})E(e^{tY})$.
> - La unicidad permite la conclusión inversa: "esta FGM es de una Poisson ⇒ $Z$ es Poisson".

---

### D. Combinaciones lineales de normales

Si $X_i\sim N(\mu_i,\sigma_i^2)$ son independientes y $Y=\sum_{i=1}^{n}a_iX_i$ con $a_i\in\mathbb{R}$, entonces
$$
Y\sim N\left(\sum_{i=1}^{n}a_i\mu_i,\ \sum_{i=1}^{n}a_i^{2}\sigma_i^{2}\right).
$$
En particular, si las $X_i$ son iid $N(\mu,\sigma^2)$:
$$
\bar X=\frac{1}{n}\sum_{i=1}^{n}X_i\sim N\left(\mu,\ \frac{\sigma^{2}}{n}\right).
$$

> **🔤 Diccionario:**
> - $a_i$: coeficientes de la combinación lineal (constantes reales).
> - Las **medias** se combinan con $a_i$; las **varianzas** con $a_i^{2}$.
> - $\bar X$: media aritmética (media muestral); su varianza decrece como $1/n$.
> - La normalidad de la suma es exclusiva de las normales (no vale para otras familias).

---

### E. Independencia de funciones de bloques disjuntos

Si $X_1,\dots,X_n$ son independientes y los índices $\{i_1,\dots,i_k\}$ y $\{j_1,\dots,j_m\}$ son disjuntos, entonces
$$
g(X_{i_1},\dots,X_{i_k})\ \perp\ h(X_{j_1},\dots,X_{j_m})
$$
para funciones medibles $g,h$.

> **🔤 Diccionario:**
> - "Bloques disjuntos": ningún índice se repite entre los dos grupos.
> - Ejemplo: con $X_1,\dots,X_4$ independientes, $X_1+X_2$ es independiente de $X_3X_4$.
> - **No** vale si comparten índices: $X_1$ y $X_1+X_2$ **no** son independientes.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

**🟢 Regla 1 — Sin independencia no hay convolución.** La convolución y el producto de FGM usan $p(x,y)=p_Xp_Y$ o $f=f_Xf_Y$; si hay dependencia, hay que integrar la conjunta.

**🟢 Regla 2 — La convolución respeta el soporte.** Con exponenciales, $x$ va de $0$ a $z$ (no de $-\infty$ a $\infty$); con Poisson, de $0$ a $z$.

**🟢 Regla 3 — Los parámetros que se suman.** Poisson: $\lambda$. Normales: $\mu$ y $\sigma^2$ (no $\sigma$). Exponenciales: solo si el $\lambda$ es el **mismo** (se suman las formas).

**🟢 Regla 4 — $f_Z$ no es $F_Z$.** $F_Z(z)=\int F_Y(z-x)f_X(x)dx$; la densidad se obtiene **derivando** respecto de $z$.

**🟢 Regla 5 — A veces conviene no convolucionar.** Si solo piden $P(X+Y\ge k)$, integrar $f(x,y)$ sobre la región suele ser más corto (§4.C).

**🟢 Regla 6 — FGM: producto solo con independencia, y determina la ley.** Si el producto da $e^{-(\lambda+\mu)}(e^{t}-1)$, es Poisson; si da $e^{\mu t+\sigma^2t^2/2}$, es normal.

**🟢 Regla 7 — Verificación rápida.**
1. ¿$f_Z$ integra 1? ¿$p_Z$ suma 1?
2. ¿La media de $Z$ es $\sum E(X_i)$?
3. ¿La varianza (si son independientes) es $\sum Var(X_i)$?

**⚠️ Trampas típicas**
- Sumar desviaciones estándar en vez de varianzas.
- Usar convolución con variables dependientes.
- Poner $\int_{-\infty}^{\infty}$ cuando el soporte es $0<x<z$.
- Creer que $\mathrm{Exp}(\lambda_1)+\mathrm{Exp}(\lambda_2)$ es Gamma.
- Olvidar que $\bar X$ tiene varianza $\sigma^2/n$, no $\sigma^2$.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 📏 4.0 Protocolo de escritura: la cadena

Toda cuenta se escribe como **cadena de igualdades**: una por renglón, cada una con su justificación entre paréntesis, sin saltar pasos, y el último renglón con el resultado.

**Patrón mínimo:**
$$
\begin{aligned}
2^{3} &= 8 && \text{(evaluar la potencia)}\\
&= 2(4) && \text{(factorizar: }8=2\cdot4\text{)}
\end{aligned}
$$

---

### 🎲 A. Convolución discreta (Poisson)

1. **Verifica** independencia y escribe $R_X,R_Y$.
2. **Plantea** $p_Z(z)=\sum_x p_X(x)p_Y(z-x)$.
3. **Sustituye** las masas y factoriza lo que no depende de $x$.
4. **Reconoce** el binomio de Newton.
5. **Identifica** la distribución y su parámetro.

**Plantilla ($X\sim\mathrm{P}(\lambda)$, $Y\sim\mathrm{P}(\mu)$):**
$$
\begin{aligned}
p_Z(z) &= \sum_{x=0}^{z}p_X(x)\,p_Y(z-x) && \text{(convolución)}\\
&= \sum_{x=0}^{z}e^{-\lambda}\frac{\lambda^{x}}{x!}\,e^{-\mu}\frac{\mu^{z-x}}{(z-x)!} && \text{(masas Poisson)}\\
&= \frac{e^{-(\lambda+\mu)}}{z!}\sum_{x=0}^{z}\frac{z!}{x!\,(z-x)!}\lambda^{x}\mu^{z-x} && \text{(sacar }e^{-(\lambda+\mu)}\text{ y }z!/z!)\\
&= \frac{e^{-(\lambda+\mu)}}{z!}\sum_{x=0}^{z}\binom{z}{x}\lambda^{x}\mu^{z-x} && \text{(definición de }\binom{z}{x}\text{)}\\
&= \frac{e^{-(\lambda+\mu)}}{z!}(\lambda+\mu)^{z} && \text{(binomio de Newton)}
\end{aligned}
$$
⇒ $Z\sim\mathrm{P}(\lambda+\mu)$.

---

### 📐 B. Convolución continua (exponencial → Gamma)

1. **Verifica** independencia y soportes.
2. **Plantea** $f_Z(z)=\int f_Y(z-x)f_X(x)\,dx$.
3. **Recorta** los límites al soporte (aquí $0<x<z$).
4. **Integra** y agrupa exponenciales.
5. **Identifica** la densidad resultante.

**Plantilla ($X,Y\sim\mathrm{Exp}(\lambda)$ iid):**
$$
\begin{aligned}
f_Z(z) &= \int_{-\infty}^{\infty}f_X(x)\,f_Y(z-x)\,dx && \text{(convolución)}\\
&= \int_{0}^{z}\lambda e^{-\lambda x}\,\lambda e^{-\lambda(z-x)}\,dx && \text{(soportes }0<x<z\text{)}\\
&= \lambda^{2}e^{-\lambda z}\int_{0}^{z}dx && \text{(sumar exponentes)}\\
&= \lambda^{2}z\,e^{-\lambda z},\qquad z>0 && \text{(integrar)}
\end{aligned}
$$
⇒ $Z\sim\Gamma(2,\lambda)$ (forma 2, tasa $\lambda$).

---

### 🎯 C. Probabilidad de una región para $X+Y$

1. **Escribe** la región en desigualdades.
2. **Dibuja** y fija el orden de integración.
3. **Integra** $f$ sobre la región (no hace falta convolucionar).
4. **Verifica** que el resultado esté en $[0,1]$.

**Plantilla ($X\sim U(0,2)$, $Y\sim\mathrm{Exp}(1)$ independientes, $P(X+Y\ge5/2)$):**
$$
\begin{aligned}
P\left(X+Y\ge\tfrac52\right) &= \int_{0}^{2}\!\!\int_{5/2-x}^{\infty}\frac12 e^{-y}\,dy\,dx && \text{(región y densidad conjunta)}\\
&= \int_{0}^{2}\frac12 e^{-(5/2-x)}\,dx && \text{(integrar en }y\text{)}\\
&= \frac12 e^{-5/2}\left[e^{x}\right]_{0}^{2} && \text{(primitiva en }x\text{)}\\
&= \frac12\left(e^{-1/2}-e^{-5/2}\right) && \text{(evaluar)}\\
&\approx 0{,}2622 && \text{(calcular)}
\end{aligned}
$$

---

### 🔗 D. FGM para identificar la distribución

1. **Verifica** independencia.
2. **Escribe** $m_Z(t)=\prod m_{X_i}(t)$ (con $m_{aX}(t)=m_X(at)$).
3. **Multiplica** las exponenciales (sumando exponentes).
4. **Compara** con la FGM conocida.
5. **Concluye** la distribución y sus parámetros.

**Plantilla ($Y=\sum a_iX_i$, $X_i\sim N(\mu_i,\sigma_i^2)$ independientes):**
$$
\begin{aligned}
m_Y(t) &= \prod_{i=1}^{n}m_{X_i}(a_it) && \text{(FGM de la suma)}\\
&= \prod_{i=1}^{n}\exp\left(\mu_i a_i t+\frac{\sigma_i^{2}a_i^{2}t^{2}}{2}\right) && \text{(FGM normal evaluada en }a_it\text{)}\\
&= \exp\left(t\sum_{i=1}^{n}\mu_i a_i+\frac{t^{2}}{2}\sum_{i=1}^{n}\sigma_i^{2}a_i^{2}\right) && \text{(producto de exponenciales)}
\end{aligned}
$$
⇒ $Y\sim N\left(\sum a_i\mu_i,\ \sum a_i^{2}\sigma_i^{2}\right)$.

---

### 📊 E. Media muestral de una normal

1. **Identifica** $X_i$ iid $N(\mu,\sigma^2)$.
2. **Escribe** $\bar X=\frac1n\sum X_i$ como combinación lineal con $a_i=1/n$.
3. **Aplica** §2.D.
4. **Verifica:** $E(\bar X)=\mu$ y $Var(\bar X)=\sigma^2/n$.

**Plantilla:**
$$
\begin{aligned}
\bar X &= \frac{1}{n}\sum_{i=1}^{n}X_i && \text{(definición)}\\
&\sim N\left(\sum_{i=1}^{n}\frac{1}{n}\mu,\ \sum_{i=1}^{n}\frac{1}{n^{2}}\sigma^{2}\right) && \text{(combinación lineal normal)}\\
&= N\left(\mu,\ \frac{\sigma^{2}}{n}\right) && \text{(sumar }n\text{ términos iguales)}
\end{aligned}
$$

---

## ✅ 5. CHECKLIST FINAL (30 segundos antes de entregar)

- [ ] ¿Verifiqué independencia antes de convolucionar?
- [ ] ¿Recorté los límites al soporte ($0<x<z$, no $-\infty<x<\infty$)?
- [ ] ¿Diferencié $F_Z$ de $f_Z$?
- [ ] ¿Sumé **varianzas** y no desviaciones?
- [ ] ¿El $\lambda$ de las exponenciales es el mismo? Si no, no es Gamma.
- [ ] ¿La densidad o masa final suma/integra 1?
- [ ] ¿La media de $Z$ coincide con la suma de medias?
- [ ] ¿Escribí la cuenta como **cadena** con su justificación por renglón?
