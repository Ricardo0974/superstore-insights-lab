# Superstore Insights · Laboratorio de visualización

Dashboard interactivo y análisis reproducible del dataset **Superstore 2012**. Combina Pandas, Matplotlib y Seaborn con un dashboard web adaptable basado en Chart.js.

## Funciones

- Indicadores de ventas, beneficio, pedidos y mercados, con filtro regional.
- Gráficas de tendencia mensual, categorías, beneficio regional, ventas frente a beneficio y correlaciones.
- Laboratorio de carga CSV/XLSX/XLS para explorar otro archivo y generar gráficos en navegador.
- Descarga de informes en PDF, Word, Excel y PowerPoint; incluye descarga del CSV de origen.
- Script reproducible en Python que genera una figura 3×3 de ocho paneles y evidencias independientes para los criterios.

## Abrir en Visual Studio Code

1. Descarga y descomprime superstore-lab-v2.zip; abre la carpeta raíz superstore-lab.
2. En la terminal integrada ejecuta: python -m http.server 8000
3. Abre http://localhost:8000 en el navegador (o usa Live Server). Se necesita internet para las librerías web cargadas por CDN.

## Reproducir análisis Python

El CSV original está incluido en data/.

Comandos PowerShell:

    python -m venv .venv
    .venv\Scripts\Activate.ps1
    pip install -r requirements.txt
    python src/analisis_superstore.py

El análisis genera figures/dashboard_superstore.png, histogramas de Matplotlib y Seaborn, figures/bivariante_seaborn_regplot.png, heatmaps multivariantes de ambas bibliotecas y data/resumen.json.

## Evidencia de evaluación

| Criterio | Implementación | Biblioteca |
|---|---|---|
| Univariante | Histograma con plt.hist y barras con plt.bar | Matplotlib |
| Univariante | Boxplot de beneficio por categoría | Seaborn |
| Bivariante | Dispersión ventas-beneficio y serie temporal | Matplotlib |
| Bivariante | Dispersión y regresión con sns.scatterplot y sns.regplot | Seaborn |
| Multivariante | Heatmap anotado de correlaciones | Matplotlib y Seaborn |
| Composición | Figura 3×3 con ocho paneles y comentarios | Ambas |

La escala logarítmica ayuda a representar ventas muy asimétricas. El boxplot oculta puntos extremos solo para facilitar su lectura; los registros permanecen en el análisis. Correlación y regresión describen asociación, no causalidad.

## Preparación y calidad de datos

Se inspeccionan estructura, tipos y valores nulos. Order Date y Ship Date se interpretan con orden día/mes/año; las columnas numéricas se convierten de forma tolerante a errores. Solo se descartan filas que carecen de fecha de pedido, ventas o beneficio. Faltantes en columnas no esenciales (por ejemplo, código postal en mercados internacionales) se conservan. En el archivo incluido: 4.246 filas procesadas, sin nulos en campos esenciales y sin filas descartadas.

## Uso con otros archivos

En Analiza otro proyecto, carga o arrastra un CSV/XLSX/XLS y pulsa Ejecutar análisis. El navegador muestra resumen, muestra de filas y visualizaciones según las columnas disponibles. Los botones superiores descargan informes en PDF, Word, Excel o PowerPoint.

## Publicar en GitHub Pages

En GitHub abre Settings → Pages, elige la rama principal y la carpeta raíz. Al ser una web estática, Pages sirve index.html, assets/ y data/ sin backend.

## Estructura

- assets/: estilos responsive y dashboard
- data/: dataset original y resumen JSON
- figures/: figuras exportadas
- src/: análisis Python reproducible
- .vscode/tasks.json: tarea de ejecución en VS Code
- index.html: aplicación web
- requirements.txt: dependencias Python
- README.md: guía completa

## Privacidad y atribución

El repositorio es público e incluye el dataset del ejercicio como solicitaste. Verifica las condiciones de redistribución del recurso original antes de reutilizarlo fuera del contexto académico.
