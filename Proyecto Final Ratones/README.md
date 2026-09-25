## 👨‍🔬 Autores
* **Sebastián**
* **David**

---

## 📌 Resumen del Análisis

Se evaluó la actividad electrofisiológica de **277 neuronas** distribuidas en **5 ratones**, analizando respuestas ante estímulos de rejillas en movimiento (*drifting gratings*) y condiciones basales de pantalla gris (*spontaneous*).

### 📊 Resultados Principales
* **Neuronas analizadas:** 277 en el área `VISl`.
* **Total de potenciales de acción (PAs):** 4,153,518.
* **Tasa media evocada:** ~5.55 Hz.
* **Tasa media basal:** ~4.95 Hz.
* **Fracción respondedora global ($Z \ge 2.5$):** **46.2%** (128 / 277 neuronas).

---

## 📈 Fracción Respondedora por Ratón

| ID del Ratón | Neuronas Que Responden | Total Neuronas | Fracción (%) |
| :--- | :---: | :---: | :---: |
| `715093703` | 24 | 42 | **57.1%** |
| `756029989` | 16 | 30 | **53.3%** |
| `760345702` | 32 | 50 | **64.0%** |
| `762120172` | 21 | 77 | **27.3%** |
| `798911424` | 35 | 78 | **44.9%** |
| **Total Area VISl** | **128** | **277** | **46.2%** |

---

## 🔬 Metodología

1. **Carga y Filtrado de Datos:**
   * Filtrado de unidades con etiqueta de área `VISl`.
   * Filtrado de ensayos por tipo (`drifting_gratings` y `spontaneous`).
2. **Emparejamiento Estímulo-Neurona:**
   * Alineación estricta entre la sesión de cada animal y sus correspondientes registros de PAs para evitar sesgos por ensayos no presenciados.
3. **Cálculo de Tasas de Disparo:**
   * **Ventana evocada:** $[0.05, 1.95]\text{ s}$ respecto al inicio del estímulo.
   * **Ventana basal:** $[0.00, 1.00]\text{ s}$ durante la condición de pantalla gris.
4. **Criterio de Respondedora (Z-score):**
   * Se determinó la condición preferida (orientación, frecuencia temporal y espacial) para cada neurona.
   * Se calculó el Z-score de respuesta preferida:
     $$Z = \frac{\bar{r}_{\text{pref}} - \bar{r}_{\text{basal}}}{\text{SE}_{\text{pool}}}$$
   * Criterio de significancia: $Z \ge 2.5$.
