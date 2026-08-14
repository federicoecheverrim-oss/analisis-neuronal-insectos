# Bitácora de prompts — lab 1

## Prompt 1
> Trabajo en Python dentro de Google Colab. Tengo un DataFrame de pandas llamado datos con las columnas neurona (texto), estimulo (texto: "viento" o "silencio"), ensayo (entero) y n_spikes (entero). Son registros extracelulares del sistema cercal de un grillo. Quiero un gráfico de barras del promedio de n_spikes por estimulo, con barras de error de desviación estándar. Incluye labels de los ejes con unidades, un título corto y colores pálidos. Explícame qué hace cada línea con un comentario.
# TODO: pega aqui el codigo que te dio la IA y ejecutalo
import pandas as pd                  # Importa pandas para trabajar con el DataFrame
import matplotlib.pyplot as plt      # Importa matplotlib para hacer el gráfico

resumen = datos.groupby("estimulo")["n_spikes"].agg(["mean", "std"]).reset_index()
# Agrupa los datos según el estímulo y calcula el promedio (mean) y la desviación estándar (std)

plt.figure(figsize=(6, 4))
# Define el tamaño de la figura

plt.bar(
    resumen["estimulo"],             # Coloca "viento" y "silencio" en el eje X
    resumen["mean"],                 # Usa el promedio de n_spikes como altura de las barras
    yerr=resumen["std"],             # Añade la desviación estándar como barras de error
    capsize=5,                       # Añade pequeñas líneas en los extremos de las barras de error
    color=["#B8CDE8", "#C8E6C9"]     # Usa colores pálidos para las barras
)

plt.xlabel("Estímulo")
# Etiqueta el eje X

plt.ylabel("Número de spikes (spikes/ensayo)")
# Etiqueta el eje Y e indica la unidad de medida

plt.title("Respuesta neuronal al estímulo")
# Añade un título corto al gráfico

plt.tight_layout()
# Ajusta automáticamente los elementos para evitar que se corten

plt.show()

**Qué me devolvió:** grafíco
**Qué tuve que corregir:** nada 
