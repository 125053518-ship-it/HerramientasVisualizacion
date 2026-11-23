# Tablero del SIE de Banxico — Prueba de implementación

Emiliano Rivas de la Vega · IDIA-222 · 125053518
Herramientas de Visualización · Parcial III

Versión propia a partir del repositorio base del docente:
https://github.com/BOWadapter/HerramientasVisualizacion

## Cómo correrlo

```bash
pip install -r requirements.txt
streamlit run dashboard_banxico.py
```

Sin token también abre: trae un modo de ejemplo para probar.
Con token muestra los datos reales del SIE.

## Cómo poner el token (cuando lo tengas)

1. Pídelo gratis en https://www.banxico.org.mx/SieAPIRest/service/v1/token
2. Crea la carpeta `.streamlit` junto a `dashboard_banxico.py`
3. Dentro crea `secrets.toml` con esta línea:
   `banxico_token = "tu-token"`
4. Ese archivo nunca se sube a GitHub.

## Qué cambié y por qué

**Quité: "Promedio por mes y año" (mapa de calor).**
Repetía el nivel que ya muestra la gráfica de la serie y su tendencia.
Como el tipo de cambio tiene tendencia, el color casi solo subía con
el tiempo, y el promedio mensual escondía la volatilidad diaria.
Además solo usaba la primera serie, no servía al comparar varias.

**Añadí: "Volatilidad móvil (30 días)".**
Es la desviación estándar móvil de la variación diaria, con la misma
ventana del slider de media móvil. Ninguna gráfica del tablero original
mostraba cómo cambia la inestabilidad en el tiempo: el boxplot solo
la resume por año. Esta muestra cuándo hubo picos de inestabilidad.

Las demás gráficas se quedan igual: serie y tendencia, cambio mensual
y boxplot por año.

## Archivos

- `dashboard_banxico.py` — el tablero modificado
- `requirements.txt` — lo que hay que instalar
- `README.md` — este archivo
