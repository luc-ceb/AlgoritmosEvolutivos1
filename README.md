# Optimización de Estrategia de Trading (Mean Reversion) con Algoritmos Evolutivos

Este proyecto implementa y optimiza una estrategia de trading de **Reversión a la Media** basada en el indicador RSI (Relative Strength Index). El núcleo del proyecto reside en el uso de algoritmos metaheurísticos y evolutivos para encontrar la combinación óptima de parámetros que maximice el **Sharpe Ratio**.

## Características
* **Descarga de Datos Automática:** Obtención de datos históricos (OHLCV) mediante `yfinance`.
* **Motor de Backtesting:** Simulación vectorizada de la estrategia.
* **Cálculo Robusto de Métricas:** Implementación del **Sharpe Ratio Anualizado** basado en la curva de equidad diaria (Daily Equity Curve) para evitar sesgos estadísticos.
* **Múltiples Algoritmos de Optimización:**
    * **PSO (Particle Swarm Optimization):** Implementado con `pyswarms`.
    * **Algoritmos Genéticos (GA):** Implementado con la biblioteca `DEAP`.
    * **TLBO (Teaching-Learning Based Optimization):** Implementación personalizada del algoritmo de Rao.
* **Visualización:** Gráficos de convergencia de los optimizadores, curva de capital, drawdowns y señales de entrada/salida.

## La Estrategia
La lógica de trading busca capitalizar condiciones de sobrecompra y sobreventa en el activo:
1.  **Entrada (Compra):** Cuando el `RSI` cae por debajo del `Umbral de Compra` (ej. 30).
2.  **Salida (Venta):** Cuando el `RSI` supera el `Umbral de Venta` (ej. 70).
3.  **Gestión de Riesgo:** Cierre forzado de posición si el precio cae un porcentaje determinado (`Stop Loss %`) desde la entrada.

### Parámetros a Optimizar
El espacio de búsqueda consta de 4 dimensiones:
* `Periodo RSI`: Ventana de tiempo para el cálculo del indicador (Entero).
* `Umbral Compra`: Nivel de sobreventa (Entero).
* `Umbral Venta`: Nivel de sobrecompra (Entero).
* `Stop Loss %`: Porcentaje máximo de pérdida por operación (Flotante).

## Uso
El proyecto está diseñado para ejecutarse en Jupyter Notebooks.
