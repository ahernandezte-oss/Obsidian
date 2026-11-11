# 📘 GUÍA DE RESOLUCIÓN GENERAL — CEDO

> **📇 Ficha del archivo**
> - **Archivo:** `GUIA_RESOLUCION_GENERAL.md`
> - **Qué es:** el **mapa único** para atacar cualquier ejercicio del curso. No reemplaza las cheatsheets: dice **cuál** abrir y en **qué orden** trabajar.
> - **Alcance:** los 7 temas vistos (del 14/10 al 11/11).
> - **Cómo usarla:** §1 para clasificar, §2 para el flujo, §5 para verificar, §6 para el examen.

---

## 🧭 1. EL RADAR MAESTRO

Se pregunta **en este orden**. La primera respuesta que encaje manda.

**Pregunta 1 — ¿Cuántas funciones incógnita hay?**

| Respuesta | Camino | 👉 Ir a |
|---|---|---|
| **Una** ($y$, $y'$, $y''$…) | EDO escalar | Pregunta 2 |
| **Varias acopladas** ($x$, $y$, $z$ con sus derivadas) | Sistema | Pregunta 5 |

**Pregunta 2 (escalar) — ¿Es lineal en $y$ y sus derivadas?**

| Señal | Tipo | 👉 Ir a |
|---|---|---|
| $y^2$, $(y')^2$, $e^{y}$, $y\,y''$, $\sqrt{y'}$ | **No lineal** | §3.5 · `261014_NO_LINEALES_ORDEN_SUPERIOR` |
| Todo a la primera potencia, coeficientes funciones de la variable | **Lineal** | Pregunta 3 |

**Pregunta 3 (lineal) — ¿Los coeficientes son constantes?**

| Señal | Tipo | 👉 Ir a |
|---|---|---|
| Números ($3y'' - 2y' + y$) | Coeficientes constantes | Pregunta 4 · `261102_EDO_ORDEN_SUPERIOR` |
| Aparece $x$ multiplicando: $x^2y''$, $xy'$, $(x^2+1)y''$ | Coeficientes variables | §3.3 y §3.4 |

**Pregunta 4 (coeficientes constantes) — ¿Es homogénea?**

| Señal | Qué hacer | 👉 Ir a |
|---|---|---|
| Lado derecho $= 0$ | Solo ecuación característica | `261102_EDO_ORDEN_SUPERIOR` §2.B |
| Lado derecho $= g(x)$ admisible | Característica + coeficientes indeterminados | `261102_EDO_ORDEN_SUPERIOR` §2.E |
| Lado derecho con $\tan$, $\sec$, $\ln$, $\sqrt{\phantom{x}}$, $\frac{1}{x}$ | Característica + variación de parámetros | `261026_VARIACION_PARAMETROS` §4.1 |

**Pregunta 5 (sistema) — ¿Por qué método?**

| Situación | Método | 👉 Ir a |
|---|---|---|
| Se piden **todas** las funciones y la dimensión es $2$ o $3$ | Autovalores (matricial) | `261111_SISTEMAS_AUTOVALORES` §4.1 |
| Conviene despejar una incógnita, o dimensión baja con coeficientes sencillos | Eliminación | `261109_SISTEMAS_LINEALES` §4.1 |

**Regla de desempate:** los **autovalores son los mismos** por los dos caminos. Si no coinciden, hay un error, no una diferencia de método.

### Tabla síntesis

| Si el ejercicio dice… | Tema | Cheatsheet · bloque |
|---|---|---|
| $y'' + 5y' + 6y = 0$ | Constantes homogénea | `261102` §2.B |
| $y'' + 9y = 6xe^{-3x}$ | Constantes + indeterminados | `261102` §2.E |
| $y'' + y = \tan x$ | Variación de parámetros | `261026` §4.1 |
| $x^2y'' - 4xy' + 6y = 0$ | Euler | `261024` §4.1 |
| $(x^2+1)y'' - 2xy' + 2y = 0$, dan $y_1$ | Ostrogradsky–Liouville | `261104` §4.1 |
| $x^2y'' = (y')^2$ | No lineal, falta $y$ | `261014` §4.1 |
| $2yy'' = (y')^2 + 1$ | No lineal, falta $x$ | `261014` §4.2 |
| $\vec\gamma' = A\vec\gamma$ | Sistema por autovalores | `261111` §4.1 |
| $x' = 2x+y,\ y' = 3x+4y$ | Sistema por eliminación | `261109` §4.1 |

---

## 🛠️ 2. EL FLUJO UNIVERSAL (5 pasos, cualquier ejercicio)

Estos cinco pasos **no cambian** de tema a tema. Lo único que cambia es la herramienta de cada uno.

**Paso 1 — CLASIFICAR** (§1). Antes de escribir una sola línea de cálculo.
- Escribe en el margen: *escalar/sistema*, *lineal/no lineal*, *constante/variable*, *orden n*.

**Paso 2 — NORMALIZAR.**
- Escalar: dividir por el coeficiente de la derivada mayor → término principal con coeficiente $1$.
- Sistema: escribir la matriz $A$ (o el sistema en la forma canónica).
- Anotar el **dominio** (denominadores, raíces, $\ln$).

**Paso 3 — HOMOGÉNEA.**
- Ecuación característica → raíces → $y_h$ (o vector solución de la homogénea).
- **Contar las constantes**: deben ser $n$.

**Paso 4 — PARTICULAR** (solo si no es homogénea).
- Elegir la herramienta con el Radar.
- Comprobar **choque** (¿la conjetura ya está en $y_h$?) o **Wronskiano** ($W \neq 0$).
- Resolver los coeficientes.

**Paso 5 — SUMAR Y VERIFICAR.** §5.

**Regla de oro del flujo:** el **orden de las constantes** es igual al **orden de la ecuación** o a la **dimensión del sistema**. Si al final sobran o faltan, el error está en el paso 3 o en el 4.

---

## 🔄 3. QUÉ HERRAMIENTA EN CADA CASO

### 3.1 Coeficientes constantes
- Característica: $a_n\lambda^n + \cdots + a_0 = 0$.
- Tres casos (reales distintas, repetida, complejas) y el caso 4 (complejas repetidas).
- 👉 `261102_EDO_ORDEN_SUPERIOR` §2.B.

### 3.2 Factorizar el polinomio característico
- Grado $\geq 3$: probar divisores del término independiente (**Ruffini**).
- Si solo hay potencias pares: sustituir $u = \lambda^2$.
- Agrupar de dos en dos cuando se ve el patrón.
- 👉 `261102` §2.C.

### 3.3 Ecuación de Euler
- **Síntoma:** la potencia de $x$ coincide con el orden de la derivada ($x^2y''$, $xy'$, $y$).
- Sustituir $y = x^{\lambda}$ → característica en $\lambda$ → potencias $x^{\lambda}$ (no exponenciales).
- 👉 `261024_ECUACION_EULER` §4.1.

### 3.4 Coeficientes variables sin simetría
- **Síntoma:** dan **una** solución $y_1$ conocida.
- Fórmula de Ostrogradsky–Liouville: $y_2 = y_1\int\frac{e^{-\int p\,dx}}{y_1^2}dx$ con $p = \frac{a_1}{a_0}$.
- **Sin $y_1$ no hay método**: hay que proponerla y verificarla.
- 👉 `261104_OSTROGRADSKY_LIOUVILLE` §4.1.

### 3.5 No lineales (reducción de orden)
- **Falta $y$** → $y' = z$.
- **Falta $x$** → $y' = p(y)$, con $y'' = p\frac{dp}{dy}$.
- Objetivo: bajar el orden hasta una EDO de primer orden.
- 👉 `261014_NO_LINEALES_ORDEN_SUPERIOR` §2.B y §2.C.

### 3.6 Sistemas
- Autovalores: $\det(A-\lambda I) = 0$ y luego $(A-\lambda I)\vec v = \vec 0$.
- Eliminación: derivar, sustituir y quedarse con una sola incógnita.
- 👉 `261111` §4.1 · `261109` §4.1.

---

## ✅ 4. VERIFICACIÓN UNIVERSAL (6 comprobaciones)

Se aplican **siempre**, en este orden. Son la diferencia entre entregar y entregar bien.

| # | Comprobación | Cómo | Si falla |
|---|---|---|---|
| 1 | **Sustituir** la solución en la EDO original | Reemplazar y simplificar | Error de coeficiente o de signo |
| 2 | **Contar constantes** | $n$ para escalar de orden $n$; dimensión para sistemas | Se perdió una integración o se duplicó |
| 3 | **Wronskiano** $\neq 0$ (si se usó conjunto fundamental) | Calcular $\det$ | Las soluciones no eran independientes |
| 4 | **Dominio** | Denominadores $\neq 0$, argumentos de $\ln > 0$ | Falta el intervalo de validez |
| 5 | **Coherencia de traza y determinante** (sistemas y característica) | $\text{tr} = \sum\lambda_i$, $\det = \prod\lambda_i$ | Error en la característica |
| 6 | **Unidades y contexto** (si es aplicación) | Revisar qué representa cada variable | Respuesta sin sentido físico |

**Comprobación 5 en detalle:** sirve incluso sin resolver. Si el polinomio característico es $\lambda^2 - (\text{tr})\lambda + \det$, la suma de raíces debe dar la traza y el producto el determinante. **Es un control de un segundo** que atrapa la mayoría de los errores de signo.

---

## ⚠️ 5. ERRORES FRECUENTES Y CÓMO DETECTARLOS

| Error | Cómo se detecta |
|---|---|
| Olvidar la $x$ de la conjetura cuando hay choque | Al sustituir, todo se anula y queda $0 = g(x)$ |
| Poner $x^2$ cuando la raíz es simple | El coeficiente sale $0$ |
| No escribir los dos coeficientes del seno y el coseno | Falta un término y el sistema no cierra |
| Confundir $y_h$ con $y_p$ | Aparece una constante $C$ sin despejar en el resultado |
| Dividir por el coeficiente principal demasiado tarde | La fórmula de variación de parámetros da otro resultado |
| Aplicar Euler a una EDO que no es de Euler | Las potencias de $x$ no coinciden con los órdenes |
| Recuperar $y$ integrando en un sistema | Aparecen constantes nuevas (deben ser exactamente $n$) |
| Usar coeficientes indeterminados con $\tan$, $\ln$, $\sqrt{\phantom{x}}$ | No existe conjetura posible: hay que ir a variación de parámetros |
| Olvidar el intervalo de existencia | Faltan condiciones tipo $x > 0$ o $1 - C_1x \neq 0$ |

---

## 🚀 6. RUTA DE PARCIAL (orden de ataque)

1. **Primeros 2 minutos — clasificar todos los ejercicios** con el Radar (§1). No resolver nada todavía.
2. **Empezar por los de coeficientes constantes homogéneos**: son los más rápidos y dan puntos seguros.
3. **Seguir con los no homogéneos admisibles** (coeficientes indeterminados).
4. **Después Euler y sistemas**: requieren factorizar y resolver sistemas lineales.
5. **Al final, los de coeficientes variables y variación de parámetros**: son los más largos.
6. **Reservar 10 minutos para verificar** (§4). Un ejercicio sin verificar vale menos que uno verificado.

**Presupuesto de tiempo por tipo:** homogénea constante 3 min · no homogénea admisible 6 min · Euler 6 min · sistema 2×2 por autovalores 8 min · variación de parámetros 10 min.

---

## 📚 7. ÍNDICE DE CHEATSHEETS

| Fecha | Archivo | Tema |
|---|---|---|
| 14/10 | `261014_NO_LINEALES_ORDEN_SUPERIOR.md` | No lineales: reducción de orden |
| 24/10 | `261024_ECUACION_EULER.md` | Ecuación de Euler |
| 26/10 | `261026_VARIACION_PARAMETROS.md` | Variación de parámetros (orden $n$) |
| 02/11 | `261102_EDO_ORDEN_SUPERIOR.md` | Lineales de coeficientes constantes |
| 04/11 | `261104_OSTROGRADSKY_LIOUVILLE.md` | Ostrogradsky–Liouville |
| 09/11 | `261109_SISTEMAS_LINEALES.md` | Sistemas por eliminación |
| 11/11 | `261111_SISTEMAS_AUTOVALORES.md` | Sistemas por autovalores |

**Cómo citar en un ejercicio:** «📘 `261102` §2.E» — archivo y bloque, no solo el bloque.

---

**Cita rápida:** 📘 Guía `GUIA_RESOLUCION_GENERAL` — §1 para clasificar, §2 para el flujo, §4 para verificar.
