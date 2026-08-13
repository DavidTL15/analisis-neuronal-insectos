# Bitácora de prompts — lab 1

## Prompt 1
rabajo en Python dentro de Google Colab. Tengo un DataFrame de pandas llamado datos con las columnas neurona (texto), estimulo (texto: "viento" o "silencio"), ensayo (entero) y n_spikes (entero). Son registros extracelulares del sistema cercal de un grillo. Quiero un gráfico de barras del promedio de n_spikes por estimulo, con barras de error de desviación estándar. Incluye labels de los ejes con unidades, un título corto y colores pálidos. Explícame qué hace cada línea con un comentario.

**Qué me devolvió:** import pandas as pd
import matplotlib.pyplot as plt

# Calcula el promedio y la desviación estándar de n_spikes para cada estímulo.
resumen = datos.groupby("estimulo")["n_spikes"].agg(["mean", "std"])

# Define el orden en que aparecerán los estímulos en el gráfico.
resumen = resumen.reindex(["silencio", "viento"])

# Crea la figura y el eje donde se dibujará el gráfico.
fig, ax = plt.subplots(figsize=(6, 4))

# Dibuja las barras con el promedio y la desviación estándar como barras de error.
ax.bar(
    resumen.index,                 # Nombres de los estímulos en el eje X.
    resumen["mean"],               # Promedio de spikes para cada estímulo.
    yerr=resumen["std"],           # Desviación estándar como barra de error.
    capsize=5,                     # Tamaño de las pequeñas líneas en los extremos del error.
    color=["#BFD7EA", "#CDE8C5"],  # Colores pálidos para las barras.
    edgecolor="black"              # Borde negro para distinguir mejor las barras.
)

# Etiqueta el eje X indicando que contiene el tipo de estímulo.
ax.set_xlabel("Estímulo")

# Etiqueta el eje Y indicando que n_spikes corresponde a spikes por ensayo.
ax.set_ylabel("Número de spikes (spikes/ensayo)")

# Añade un título corto al gráfico.
ax.set_title("Respuesta neuronal al estímulo")

# Ajusta automáticamente los márgenes para que las etiquetas no queden cortadas.
plt.tight_layout()

# Muestra el gráfico.
plt.show()

# La primer celda calcula los valores que se usaran en la grafica (promedio y desviación), la siguiente ajusta el
