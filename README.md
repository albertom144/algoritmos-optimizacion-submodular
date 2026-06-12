# algoritmos-optimizacion-submodular

Este repositorio contiene los cuadernos de prácticas en Python desarrollados para el Trabajo de Fin de Grado (TFG). Se centran en el modelado matemático, la optimización combinatoria y la aplicación de la submodularidad en problemas estadísticos.


## 1. Modelado de Baterías (`baterias.ipynb`)

Se modela y optimiza la gestión de carga y descarga de una batería a lo largo del tiempo mediante programación lineal.

Se define el poliedro factible $\mathcal{F}_T$ para los perfiles de potencia y energía. Dado que $\mathcal{F}_T$ es un **polimatroide generalizado**, el problema combinatorio se puede resolver de forma avariciosa. Se discuten los dos algoritmos:
* **Algoritmo de Edmonds:** Solución exacta y eficiente que aprovecha la estructura paramodular del problema.
* **Método Simplex (Solver *HiGHS*):** Solución estándar utilizando la librería `scipy.optimize.linprog`.

El análisis empírico demuestra que el algoritmo de Edmonds es **dos órdenes de magnitud más rápido** que el solver estándar.

---

## 2. Selección de Variables y Observaciones (`seleccion-vino.ipynb`)

Se resuelven problemas de selección óptima bajo restricciones de cardinalidad ($\max \{f(A) : |A| = k\}$) utilizando las propiedades de las funciones submodulares. Cuenta con la garantía teórica de la *Cota de Nemhauser* $(1 - 1/e)$.

Se utiliza el *Wine Quality Dataset* para resolver los dos problemas siguientes:

* **Selección de Variables:** Maximización del log-determinante de la matriz de covarianzas ($\log\det \Sigma_S$) para identificar los componentes químicos más significativos del vino.
* **Selección de Observaciones:** Criterio D-óptimo para regresión lineal mediante la maximización de $\log \det (I + X_S'X_S)$, seleccionando las muestras (botellas) más informativas.

Para ello, discutimos dos algoritmos:

* **Algoritmo Greedy:** Enfoque voraz clásico.
* **Algoritmo Lazy Greedy:** Variante optimizada que utiliza una cola de prioridad (`heapq`) para evitar evaluaciones redundantes.

Se comprueba además, que el algoritmo *Lazy Greedy* reduce drásticamente el número de ejecuciones de la función objetivo.

---

## Requisitos del Sistema

Los cuadernos han sido desarrollados en **Python 3.12** y requieren las siguientes librerías científicas básicas:

```
numpy scipy matplotlib pandas seaborn
```
