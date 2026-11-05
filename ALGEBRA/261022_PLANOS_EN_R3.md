# 📘 CHEATSHEET — ÁLGEBRA LINEAL · 22/10/2026

| Ficha | Valor |
|---|---|
| **Archivo** | `261022_PLANOS_EN_R3.md` |
| **Tema principal** | Planos en $\mathbb{R}^3$: normal, ecuación cartesiana, posiciones relativas e intersección con rectas |
| **Fecha base** | 22/10/2026 (transcripción de clase) |
| **Fuente** | Transcripción `261022` + teoría estándar (Grossman cap. 4) |
| **Cómo citarla** | «📘 Cheatsheet `261022_PLANOS_EN_R3` §2.A» |
| **Notación** | $n=(a,b,c)$ vector normal · $P=(x_0,y_0,z_0)$ punto del plano · $Q=(x,y,z)$ punto genérico · $\mathcal{P}$ plano · $L$ recta · $v$ vector director · $t,s$ parámetros |
| **No repite** | rectas en $\mathbb{R}^3$ (vectorial, paramétricas, simétricas) están en `261020`; producto punto y cruz, en `261015` |

> ➕ = añadido/sintetizado (no literal de la fuente).

---

## 🧭 1. PROTOCOLO DE IDENTIFICACIÓN (El Radar) ➕

**Paso 0 — ¿Piden un plano, la relación entre planos, o dónde corta una recta?**
- Ecuación del plano → §2.A, §2.B · §4.1, §4.2.
- Paralelo / perpendicular / contiene una recta → §2.C · §4.3.
- Intersección recta–plano → §2.D · §4.4.
- Posición de dos rectas → §2.E · §4.5.

**Paso 1 — ¿Qué pide exactamente?**

| Si el enunciado dice… | Método | Fórmula / concepto base | 👉 Ir a |
|---|---|---|---|
| "Halle la ecuación del plano con punto $P$ y normal $n$" | Producto punto nulo | $n\cdot(Q-P)=0$ | §2.A · §4.1 |
| "Halle el plano que pasa por tres puntos" | Producto cruz de dos diferencias | $n=(Q-P)\times(R-P)$ | §2.B · §4.2 |
| "¿Cuál es el vector normal de $ax+by+cz=d$?" | Leer coeficientes | $n=(a,b,c)$ | §2.A · §3 Caso 1 |
| "¿El punto $Q$ está en el plano?" | Evaluar y comparar | $ax+by+cz\overset{?}{=}d$ | §3 Caso 2 |
| "Plano paralelo a otro" | Misma normal | misma $(a,b,c)$, otro $d$ | §2.C · §4.3 |
| "Plano perpendicular a una recta" | Normal = director | $n=v$ | §2.C · §4.3 |
| "Plano que contiene una recta" | Punto de la recta + $n\cdot v=0$ | $n\cdot v=0$ | §2.C · §3 Caso 6 |
| "Plano con una variable ausente" | Coeficiente $0$ | $3x+2y=d$ ⇒ normal $(3,2,0)$ | §3 Caso 3 |
| "¿Dónde corta la recta al plano?" | Sustituir paramétricas | reemplazar y despejar $t$ | §2.D · §4.4 |
| "¿Las dos rectas se cortan?" | Comparar y resolver | cortan / paralelas / se cruzan | §2.E · §4.5 |

**Frases literales del profe → método**
- *"Un punto y un vector normal a todos los vectores que van a pasar por ese plano"* → definición de plano.
- *"El producto punto entre ese vector y el normal sea igual a cero"* → $n\cdot(Q-P)=0$.
- *"$D$ es $AX_0+BY_0+CZ_0$"* → el término independiente es $n\cdot OP$.
- *"Si falta la $Z$, el $Z$ está libre"* → plano paralelo al eje $z$.
- *"En $\mathbb{R}^3$ dos rectas pueden no cortarse y no ser paralelas"* → rectas que se cruzan.

---

## 🛠️ 2. CAJA DE HERRAMIENTAS (Fórmulas y Diccionario)

### A. Ecuación del plano con punto y normal
$$n\cdot(Q-P)=0$$
$$a(x-x_0)+b(y-y_0)+c(z-z_0)=0$$
$$\text{forma general: } ax+by+cz=d,\qquad d=ax_0+by_0+cz_0=n\cdot OP$$
**🔤 Diccionario:** $n=(a,b,c)$ normal (perpendicular al plano) · $P$ punto dado · $Q$ punto genérico · $d$ término independiente · $d=0$ ⇒ el plano pasa por el origen.

### B. Plano que pasa por tres puntos no colineales
$$n=(Q-P)\times(R-P)$$
y luego se aplica la forma general con cualquiera de los tres puntos.

**🔤 Diccionario:** $P,Q,R$ los tres puntos · $Q-P$ y $R-P$ vectores del plano · si $n=0$ los puntos son colineales y **no** determinan plano.

### C. Posiciones relativas de planos y rectas

| Situación | Condición sobre la normal |
|---|---|
| Dos planos paralelos | normales proporcionales |
| Dos planos perpendiculares | $n_1\cdot n_2=0$ |
| Plano perpendicular a recta | $n=v$ |
| Plano contiene a la recta | $n\cdot v=0$ y el punto de la recta está en el plano |
| Coeficiente de una variable nulo | plano paralelo a ese eje |

**🔤 Diccionario:** $n_1,n_2$ normales de dos planos · $v$ director de la recta · "proporcional" = $(a_1,b_1,c_1)=k(a_2,b_2,c_2)$.

### D. Intersección recta–plano
Recta $(x,y,z)=(x_1,y_1,z_1)+t(v_1,v_2,v_3)$, plano $ax+by+cz=d$:
$$a(x_1+tv_1)+b(y_1+tv_2)+c(z_1+tv_3)=d$$
Se despeja $t$ y se sustituye en la recta.

**🔤 Diccionario:** $t$ parámetro · una sola solución ⇒ un punto · sin solución ⇒ recta paralela al plano · identidad ⇒ recta contenida en el plano.

### E. Posición relativa de dos rectas en $\mathbb{R}^3$
- **Se cortan:** existe solución común de las paramétricas.
- **Paralelas:** $v_1\parallel v_2$ (producto cruz nulo) y no se cortan.
- **Se cruzan (alabeadas):** no paralelas y sin intersección.

**🔤 Diccionario:** $v_1,v_2$ directores · en $\mathbb{R}^2$ solo hay "se cortan o paralelas"; el tercer caso aparece en $\mathbb{R}^3$ · dos rectas con una componente constante son paralelas a un eje.

---

## 🔄 3. REGLAS DE ORO / CASOS ESPECIALES

- **Caso 0 — Normal vs director:** el plano usa **normal**; la recta usa **director**. Confundirlos es el error clásico.
- **Caso 1 — Leer la normal:** en $ax+by+cz=d$ la normal es $(a,b,c)$; no hace falta despejar nada.
- **Caso 2 — Punto en el plano:** se verifica sustituyendo; si $ax+by+cz\neq d$, el punto no está.
- **Caso 3 — Variable ausente:** si falta $z$, la normal tiene tercera componente $0$ y el plano es paralelo al eje $z$.
- **Caso 4 — Signo de la normal:** multiplicar la ecuación por $-1$ da el mismo plano; la normal cambia de sentido pero no de recta.
- **Caso 5 — Tres puntos:** si son colineales, $n=0$ y no hay plano único.
- **Caso 6 — Plano que contiene una recta:** además de $n\cdot v=0$, el punto de la recta debe satisfacer la ecuación.
- **Caso 7 — Recta y plano paralelos:** $n\cdot v=0$ y el punto de la recta no está en el plano; si está, la recta está contenida.
- **Caso 8 — Rectas que se cruzan:** en $\mathbb{R}^3$ no cortarse no implica ser paralelas.

---

## 🚀 4. ALGORITMOS DE RESOLUCIÓN

### 4.1 Plano con punto y normal
1. Escribir $n=(a,b,c)$ y $P=(x_0,y_0,z_0)$.
2. Plantear $a(x-x_0)+b(y-y_0)+c(z-z_0)=0$.
3. Expandir a $ax+by+cz=d$.
4. Verificar que $P$ satisface la ecuación.

**Plantilla** ($P=(1,2,3)$, $n=(2,-1,4)$):
$$2(x-1)-(y-2)+4(z-3)=0$$
$$2x-y+4z=2-2+12=12$$
Verificación: $2(1)-(2)+4(3)=12$.

### 4.2 Plano por tres puntos
1. Calcular $u=Q-P$ y $w=R-P$.
2. Normal $n=u\times w$.
3. Aplicar la forma general con $P$.
4. Verificar que los tres puntos la cumplen.

**Plantilla** ($P=(1,0,0)$, $Q=(0,1,0)$, $R=(0,0,1)$):
$$u=(-1,1,0),\qquad w=(-1,0,1)$$
$$n=u\times w=(1,1,1)$$
$$(x-1)+y+z=0\;\Rightarrow\;x+y+z=1$$

### 4.3 Plano paralelo o perpendicular
1. Identificar la normal pedida (misma normal si es paralelo; el director si es perpendicular a una recta).
2. Usar el punto dado.
3. Ajustar $d$.

**Plantilla** (paralelo a $2x-y+4z=12$ por $(1,1,1)$):
$$2(x-1)-(y-1)+4(z-1)=0$$
$$2x-y+4z=2-1+4=5$$

### 4.4 Intersección recta–plano
1. Escribir la recta en paramétricas.
2. Sustituir en la ecuación del plano.
3. Despejar $t$.
4. Sustituir $t$ en la recta para el punto.

**Plantilla** (recta $(1,2,3)+t(1,1,1)$, plano $2x-y+4z=12$):
$$2(1+t)-(2+t)+4(3+t)=12$$
$$5t+12=12\;\Rightarrow\;t=0$$
Punto de corte: $(1,2,3)$.

### 4.5 Posición relativa de dos rectas
1. Comparar los directores (producto cruz): si es $0$, son paralelas o coincidentes.
2. Si no, igualar las paramétricas y resolver el sistema.
3. Con solución ⇒ se cortan; sin solución ⇒ se cruzan.

**Plantilla:** $L_1:(1,0,0)+t(1,1,0)$, $L_2:(0,1,0)+s(1,0,1)$.
$$1+t=s,\qquad t=1,\qquad 0=s$$
De la tercera $s=0$ y de la segunda $t=1$, pero la primera da $2=0$: **sin solución** ⇒ se cruzan.

---

## ✅ 5. CHECKLIST FINAL ➕

- [ ] ¿Usé normal (plano) y no director (recta)?
- [ ] ¿Calculé $d=n\cdot OP$ y no lo inventé?
- [ ] ¿Verifiqué que los puntos dados cumplen la ecuación?
- [ ] ¿Revisé si falta alguna variable (plano paralelo a un eje)?
- [ ] ¿Tres puntos no colineales ($n\neq0$)?
- [ ] ¿En recta–plano distinguí punto, paralela y contenida?
- [ ] ¿Consideré el caso "se cruzan" en $\mathbb{R}^3$?
- [ ] ¿Marqué con ➕ lo que añadí fuera de la fuente?
