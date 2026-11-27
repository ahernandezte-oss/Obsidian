# 📘 CHEATSHEET — PROBABILIDAD · 25/11/2026

> **🧾 FICHA DEL ARCHIVO**
> - **Archivo:** `261125_COVARIANZA_CORRELACION.md`
> - **Fecha de transcripción:** 25/11/2026 (`AAMMDD` = `261125`)
> - **Tema principal:** COVARIANZA Y CORRELACIÓN — covarianza, propiedades, varianza de la suma, coeficiente de correlación lineal
> - **Fuentes:** transcripción de la clase del 25/11 + apuntes del estudiante. Complementos con `➕` (Liliana Blanco, §5.3).
> - **Continuidad:** viene de `261123_SUMAS_CONVOLUCION`. Aquí se mide la **relación** entre variables, no su suma.
> - **Método de las plantillas:** inverso (destino → requisitos → cálculo), §4.0.
> - **Cómo citarla al resolver ejercicios:** «📘 Cheatsheet `261125_COVARIANZA_CORRELACION` §2.C».

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar)

**Decisión en orden:**

1. **Paso 0 — ¿Piden una medida de relación entre dos variables?** → covarianza (§2.A) o correlación (§2.D).
2. **Paso 1 — ¿Piden la varianza de una suma?** → §2.C: varianzas + $2$ covarianzas.
3. **Paso 2 — ¿Piden decidir independencia?** → eso **no** se hace con la covarianza: se compara $p$ o $f$ (§3 Regla 5).
4. **Paso 3 — ¿La relación es lineal?** → correlación; si $|\rho|=1$, hay relación lineal exacta (§2.D).

| Si el enunciado dice… | Objeto | Fórmula base | 👉 Ir a |
|---|---|---|---|
| "calcule la covarianza" con tabla | **covarianza discreta** | $E(XY)-E(X)E(Y)$ | **§2.A** + **§4.A** |
| "calcule la covarianza" con $f(x,y)$ | **covarianza continua** | $\iint xy\,f$ | **§2.A** + **§4.A** |
| "¿están incorreladas?" | **$Cov=0$** | $Cov(X,Y)=0$ | **§2.B** |
| "¿son independientes?" | **criterio de factorización** | $p=p_Xp_Y$ | **§3 Regla 5** |
| "halle $Var(X+Y)$" | **varianza de la suma** | $VarX+VarY+2Cov$ | **§2.C** + **§4.C** |
| "halle $Var(X_1+\cdots+X_n)$" | **doble suma** | $\sum Var+2\sum_{i<j}Cov$ | **§2.C** + **§4.C** |
| "calcule el coeficiente de correlación" | **$\rho$** | $Cov/(\sigma_X\sigma_Y)$ | **§2.D** + **§4.B** |
| "¿qué cambia si traslado o escalo?" | **propiedades** | $\rho(aX+b,Y)=\operatorname{sign}(a)\rho$ | **§2.D** |
| "¿la relación es lineal perfecta?" | **$|\rho|=1$** | $Y=aX+b$ c.s. | **§2.D** |

> 🗣️ **Frases del profe (literales) → método**
> - "La covarianza no es otra cosa que la esperanza del producto menos el producto de las esperanzas." → §2.A.
> - "Si $X$ y $Y$ son independientes, la covarianza es cero. La afirmación recíproca no es cierta." → §3 Regla 5.
> - "Las unidades de medida impiden su interpretación… hay que quitárselas." → §2.D (por eso se divide entre $\sigma_X\sigma_Y$).
> - "La varianza de la suma es la suma de las varianzas más dos veces la covarianza." → §2.C.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Covarianza

$$
Cov(X,Y)=E\left[(X-E X)(Y-E Y)\right]=E(XY)-E(X)E(Y)
$$

- **Cálculo:**
$$
E(XY)=\sum_x\sum_y xy\,p(x,y)\quad\text{(discreto)},\qquad
E(XY)=\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}xy\,f(x,y)\,dx\,dy\quad\text{(continuo)}
$$
- **Existencia:** basta $E(X^2)<\infty$ y $E(Y^2)<\infty$ (variables de cuadrado integrable).

> **🔤 Diccionario:**
> - $X-E X$ e $Y-E Y$: **desviaciones** respecto a la media.
> - $E(XY)$: se calcula con la **conjunta**, no con las marginales.
> - Unidades: $Cov$ está en unidades de $X$ por unidades de $Y$ (metros·años), por eso no se interpreta sola.

---

### B. Propiedades de la covarianza

1. **Simetría:** $Cov(X,Y)=Cov(Y,X)$.
2. **Consigo misma:** $Cov(X,X)=Var(X)$.
3. **Bilinealidad:** para $a,b\in\mathbb{R}$,
$$
Cov(aX+b,\ Y)=a\,Cov(X,Y),\qquad Cov(X+Y,\ Z)=Cov(X,Z)+Cov(Y,Z)
$$
y en general $Cov(aX+b,\ cY+d)=ac\,Cov(X,Y)$.
4. **Independencia ⇒ covarianza nula:** si $X\perp Y$, entonces $E(XY)=E(X)E(Y)$ y $Cov(X,Y)=0$.

> **🔤 Diccionario:**
> - "Bilineal": lineal en cada argumento por separado.
> - La constante $b$ **desaparece**: trasladar no cambia la covarianza.
> - El signo de $a$ **sí** importa: cambiar de escala negativa invierte el signo.

---

### C. Varianza de una suma

$$
Var(X+Y)=Var(X)+Var(Y)+2\,Cov(X,Y)
$$
$$
Var(X-Y)=Var(X)+Var(Y)-2\,Cov(X,Y)
$$

**Caso general:** si $X_1,\dots,X_n$ tienen segundo momento finito,
$$
Var\left(\sum_{i=1}^{n}X_i\right)=\sum_{i=1}^{n}Var(X_i)+2\sum_{1\le i<j\le n}Cov(X_i,X_j).
$$

**Si son independientes** (o solo incorreladas) todos los términos cruzados se anulan:
$$
Var\left(\sum_{i=1}^{n}X_i\right)=\sum_{i=1}^{n}Var(X_i).
$$

> **🔤 Diccionario:**
> - $2\sum_{i<j}$: cada par se cuenta **una vez** y se duplica (equivale a sumar sobre $i\neq j$).
> - **Aplicación:** $X_i\sim\mathrm{Bern}(p)$ iid ⇒ $Y=\sum X_i$ tiene $Var(Y)=np(1-p)$, que es la varianza binomial.
> - Sin independencia, $Var(X+Y)$ puede ser **menor** que $VarX+VarY$ (covarianza negativa).

---

### D. Coeficiente de correlación lineal

$$
\rho(X,Y)=\frac{Cov(X,Y)}{\sigma_X\,\sigma_Y},\qquad \sigma_X=\sqrt{Var(X)}
$$

**Propiedades:**
1. **Simetría:** $\rho(X,Y)=\rho(Y,X)$.
2. **Acotado:** $-1\le\rho\le1$ (desigualdad de Cauchy-Schwarz: $|Cov|\le\sigma_X\sigma_Y$).
3. **Consigo misma:** $\rho(X,X)=1$.
4. **Signo opuesto:** $\rho(X,-X)=-1$.
5. **Invariancia:** para $a>0$ y $b\in\mathbb{R}$, $\rho(aX+b,\ Y)=\rho(X,Y)$; si $a<0$, cambia de signo.
6. **Igualdad extrema:** $|\rho|=1$ si y solo si existen $a\neq0$ y $b$ con $Y=aX+b$ casi seguramente.

> **🔤 Diccionario:**
> - $\rho$ es **adimensional**: se cancelan las unidades de $X$ con las de $Y$.
> - $\rho=0$: **incorreladas** (sin relación lineal); no significa independientes.
> - $\rho>0$: cuando una crece, la otra tiende a crecer; $\rho<0$: tiende a decrecer.
> - $|\rho|$ mide **cuánto se acerca a una recta**, no la fuerza de cualquier relación.

---

### E. El contraejemplo que hay que recordar (covarianza $0$ sin independencia)

$X$ e $Y$ toman los valores $-2,-1,1,2$ con la tabla conjunta

| $X\backslash Y$ | $-2$ | $-1$ | $1$ | $2$ |
|---|---|---|---|---|
| $-2$ | $\frac1{10}$ | $0$ | $0$ | $0$ |
| $-1$ | $0$ | $0$ | $\frac25$ | $0$ |
| $1$ | $0$ | $\frac25$ | $0$ | $0$ |
| $2$ | $0$ | $0$ | $0$ | $\frac1{10}$ |

- Marginales: $\left(\frac1{10},\frac25,\frac25,\frac1{10}\right)$ para ambas.
- $E(X)=0$, $E(XY)=4\cdot\frac1{10}-\frac25-\frac25+4\cdot\frac1{10}=0$.
- Por lo tanto $Cov(X,Y)=0$, **pero** $p(-2,-2)=\frac1{10}\neq\frac1{10}\cdot\frac1{10}$ ⇒ **dependientes**.

---

## 🔄 3. REGLAS DE ORO Y CASOS ESPECIALES

**🟢 Regla 1 — La covarianza tiene signo y unidades.** El signo informa la dirección de la relación; el valor numérico no se interpreta sin normalizar.

**🟢 Regla 2 — La correlación es la covarianza sin unidades.** Siempre en $[-1,1]$; compara relaciones aunque las escalas sean distintas.

**🟢 Regla 3 — Trasladar no cambia nada; escalar sí (en valor absoluto).** $Cov(aX+b,Y)=a\,Cov$; $\rho$ solo cambia de signo si $a<0$.

**🟢 Regla 4 — Varianza de la suma: primero los signos.** $Var(X-Y)$ lleva $-\,2Cov$; olvidar el signo es el error más común.

**🟢 Regla 5 — Independencia y covarianza no son equivalentes.**
$$
\text{independientes}\ \Longrightarrow\ Cov=0,\qquad Cov=0\ \not\Longrightarrow\ \text{independientes}.
$$
Para probar independencia se comparan $p$ o $f$; para probar dependencia basta un punto.

**🟢 Regla 6 — $\rho$ mide relación lineal, no causalidad ni cualquier relación.** Una relación curva puede tener $\rho\approx0$.

**🟢 Regla 7 — Verificación rápida.**
1. ¿$Cov(X,X)=Var(X)$?
2. ¿$|Cov|\le\sigma_X\sigma_Y$?
3. ¿$|\rho|\le1$?
4. Si son independientes, ¿el término cruzado desapareció?

**⚠️ Trampas típicas**
- Calcular $E(XY)$ con las marginales (solo vale si son independientes).
- Decir "como $Cov=0$, son independientes".
- Sumar varianzas sin independencia.
- Olvidar que $Cov$ cambia de signo al multiplicar por una constante negativa.
- Usar $\sigma_X^2$ en el denominador de $\rho$ en vez de $\sigma_X$.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 📏 4.0 Protocolo: destino → requisitos → cálculo

1. **Destino:** escribe la fórmula final.
2. **Requisitos:** lista lo que esa fórmula necesita.
3. **Cadena hacia atrás:** de dónde sale cada requisito (tabla, marginal, integral, dato).
4. **Cálculo:** en orden, en cadena con justificación por renglón.
5. **Verificación:** $|Cov|\le\sigma_X\sigma_Y$, $|\rho|\le1$, signos coherentes.

---

### 🎯 A. Covarianza desde la conjunta

**Destino:** $Cov(X,Y)=E(XY)-E(X)E(Y)$.
**Requisitos:** $E(XY)$, $E(X)$, $E(Y)$.
**Cadena:** $E(XY)$ sale de la conjunta; $E(X)$, $E(Y)$ de las marginales.

**Plantilla (tabla del contraejemplo de §2.E):**
$$
\begin{aligned}
E(X) &= -2\cdot\frac1{10}-1\cdot\frac25+1\cdot\frac25+2\cdot\frac1{10} && \text{(marginal)}\\
&= -\frac{2}{10}-\frac{4}{10}+\frac{4}{10}+\frac{2}{10} && \text{(multiplicar)}\\
&= 0 && \text{(sumar)}
\end{aligned}
$$
$$
\begin{aligned}
E(XY) &= 4\cdot\frac1{10}+(-1)\cdot\frac25+(-1)\cdot\frac25+4\cdot\frac1{10} && \text{(conjunta)}\\
&= \frac{4}{10}-\frac{4}{10}-\frac{4}{10}+\frac{4}{10} && \text{(multiplicar)}\\
&= 0 && \text{(sumar)}
\end{aligned}
$$
$$
\begin{aligned}
Cov(X,Y) &= E(XY)-E(X)E(Y) && \text{(fórmula)}\\
&= 0-0\cdot0 && \text{(sustituir)}\\
&= 0 && \text{(calcular)}
\end{aligned}
$$

---

### 📐 B. Coeficiente de correlación

**Destino:** $\rho=Cov/(\sigma_X\sigma_Y)$.
**Requisitos:** $Cov$, $Var(X)$, $Var(Y)$.
**Cadena:** $Cov$ de §4.A; las varianzas de las marginales.

**Plantilla:** con $Cov=3$, $Var(X)=4$, $Var(Y)=9$:
$$
\begin{aligned}
\rho &= \frac{Cov}{\sigma_X\sigma_Y} && \text{(definición)}\\
&= \frac{3}{2\cdot3} && \text{(}\sigma_X=2,\ \sigma_Y=3\text{)}\\
&= \frac12 && \text{(simplificar)}
\end{aligned}
$$

---

### 🧮 C. Varianza de una suma

**Destino:** $Var(X+Y)$.
**Requisitos:** $Var(X)$, $Var(Y)$, $Cov(X,Y)$.
**Cadena:** si son independientes, el requisito $Cov$ es $0$ y no hay que calcularlo.

**Plantilla ($VarX=2$, $VarY=3$, $Cov=1$):**
$$
\begin{aligned}
Var(X+Y) &= VarX+VarY+2Cov && \text{(fórmula)}\\
&= 2+3+2(1) && \text{(sustituir)}\\
&= 7 && \text{(sumar)}
\end{aligned}
$$

**Caso $n$ variables:** suma las varianzas y agrega $2$ por cada par con covarianza no nula.

---

### 🔍 D. ¿Independientes o solo incorreladas?

**Destino:** decidir entre independencia e incorrelación.
**Requisitos:** para independencia, $p(x,y)$ vs $p_Xp_Y$ (o $f$ vs $f_Xf_Y$); para incorrelación, $Cov$.
**Cadena:** si ya calculaste $Cov=0$, **no** puedes concluir independencia; falta comparar la conjunta.

**Plantilla:** tabla de §2.E → $Cov=0$ pero $p(-2,-2)=\frac1{10}\neq\frac1{100}$ ⇒ **dependientes e incorreladas**.

---

## ✅ 5. CHECKLIST FINAL (30 segundos antes de entregar)

- [ ] ¿Usé la conjunta para $E(XY)$ (no las marginales)?
- [ ] ¿Verifiqué $|Cov|\le\sigma_X\sigma_Y$?
- [ ] ¿El término cruzado tiene el signo correcto ($+$ para $X+Y$, $-$ para $X-Y$)?
- [ ] ¿Solo sumé varianzas cuando hay independencia?
- [ ] ¿$\rho$ quedó en $[-1,1]$ y sin unidades?
- [ ] ¿Evité concluir independencia a partir de $Cov=0$?
- [ ] ¿Escribí la cuenta en cadena con su justificación por renglón?
