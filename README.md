# Actividad: diagnostica tu árbol de decisión

Práctica de **árboles de decisión para regresión** con scikit-learn. Cada equipo trabaja con la
carpeta de su dataset:

| Carpeta | Se predice |
|---|---|
| `actividad_seguros_medicos/` | gasto médico anual (USD) |
| `actividad_diamantes/` | precio de un diamante (USD) |
| `actividad_abulon/` | edad de un abulón (años) |
| `actividad_ruido_ala_avion/` | ruido de un perfil de ala (dB) |
| `actividad_rentas_brasil/` | renta mensual en Brasil (BRL) |
| `actividad_salarios_1985/` | salario por hora en EUA, 1985 (USD) |

Cada carpeta contiene `actividad.py`, el CSV del dataset y `HOJA_DE_TRABAJO.pdf` con las
preguntas y la rúbrica de evaluación.

## Requisitos

Python 3.10 o más reciente y estas librerías:

```bash
pip install pandas scikit-learn matplotlib
```

Recomendado: usar un entorno virtual.

```bash
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install pandas scikit-learn matplotlib
```

## Cómo ejecutar

Desde la carpeta de tu equipo:

```bash
cd actividad_<tu_dataset>
python actividad.py > salida.txt
```

- Sin argumentos, el script usa el único CSV que hay en la carpeta.
- `python actividad.py archivo.csv` usa otro CSV.
- `--objetivo <columna>` predice otra columna (por defecto, la última). En la actividad no se usa.
- `> salida.txt` guarda la salida de la consola en un archivo. Quítalo si quieres verla en pantalla.
- Las gráficas se guardan en `salidas/<dataset>/`: `arbol_depth3.png`, `real_vs_predicho.png` y
  `curva_profundidad.png`.

**Google Colab:** sube `actividad.py` y el CSV, y ejecuta `!python actividad.py > salida.txt`.

No cambies la semilla ni el código: los resultados deben coincidir con los del profesor.

## Qué hace el script

1. Lee el CSV, elimina filas con datos faltantes y convierte las columnas de texto a 0/1.
2. Separa los datos en 80 % para entrenar y 20 % para probar.
3. Entrena tres árboles: sin límites, con `max_depth=3` y uno ajustado con `GridSearchCV`.
4. Muestra métricas (R², MAE, RMSE), la importancia de variables, las reglas del árbol pequeño, un
   caso para predecir a mano y el R² según la profundidad.

El script solo calcula; la interpretación es parte de la actividad.

## Fuentes de los datos

UCI Machine Learning Repository (Abalone, Airfoil Self-Noise), OpenML (diamonds, Brazilian houses,
CPS 1985 wages) y Lantz, *Machine Learning with R* (seguros médicos). Las columnas se tradujeron al
español.
