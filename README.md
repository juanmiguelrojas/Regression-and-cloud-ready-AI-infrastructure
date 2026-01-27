# Stellar Luminosity Modeling: Linear & Polynomial Regression from First Principles

## 1. Contexto del Proyecto y Objetivos
Este repositorio contiene el desarrollo de modelos predictivos para la luminosidad estelar ($L$) basados en propiedades físicas como la Masa ($M$) y la Temperatura ($T$). 

Desde la perspectiva de **Transformación Digital** y **Arquitectura Empresarial**, este proyecto demuestra cómo la inteligencia de datos puede integrarse como un atributo de calidad fundamental en sistemas modernos. No nos limitamos a usar librerías de "caja negra"; construimos los algoritmos desde sus fundamentos matemáticos para garantizar el control total sobre la lógica de decisión del sistema y optimizar su ejecución en entornos productivos.

### Objetivos Técnicos:
* Implementación de **Regresión Lineal Simple** (Notebook 1) y **Regresión Polinomial con Interacciones** (Notebook 2).
* Optimización mediante **Gradiente Descendente** manual y vectorizado utilizando únicamente NumPy.
* Despliegue y validación de ejecución en un entorno gestionado de nube (**AWS SageMaker**).

---

## 2. Desarrollo Técnico y Hallazgos

### Notebook 1: Análisis Univariado (M vs L)
En esta fase, modelamos la luminosidad como una función lineal de la masa ($L = wM + b$). 
* **Análisis de Costo:** La visualización de la superficie de costo $J(w,b)$ confirmó la convexidad del problema, asegurando que el Gradiente Descendente llegaría al mínimo global.
* **Limitación:** Se observó un error sistemático (underfitting) debido a que la relación real Masa-Luminosidad sigue una ley de potencia, lo que motivó la necesidad de modelos de mayor orden.

### Notebook 2: Ingeniería de Características y Multivariabilidad
Introdujimos la Temperatura ($T$) y generamos nuevas dimensiones: términos cuadráticos ($M^2$) e interacciones ($M \cdot T$).
* **Resultado:** El modelo complejo (M3) redujo el error cuadrático medio (MSE) drásticamente en comparación con el modelo lineal.
* **Arquitectura de Datos:** Se demostró que la vectorización permite procesar múltiples características simultáneamente sin pérdida de rendimiento.

---

## 3. AWS SageMaker Execution Evidence
Como parte del enfoque de Arquitectura Empresarial, la validación final se realizó en **AWS SageMaker Studio** para garantizar que el modelo sea agnóstico al hardware local y esté listo para integrarse en pipelines de datos a gran escala.

### Proceso de Implementación:
1.  **Aprovisionamiento:** Creación de una instancia de notebook `ml.t3.medium`.
2.  **Carga de Artefactos:** Importación de notebooks y datasets hard-coded al entorno de nube.
3.  **Validación:** Ejecución completa del flujo de entrenamiento y generación de gráficas en tiempo real.

### Evidencias de Ejecución:

#### A. Entorno de Trabajo en SageMaker
![SageMaker Dashboard](https://via.placeholder.com/800x400?text=Captura+1:+Panel+de+SageMaker+con+archivos+visibles)
*Aquí debe aparecer la captura de pantalla de tu instancia de SageMaker con los archivos .ipynb abiertos.*

#### B. Visualización de Superficie de Costo y Convergencia
![Graficos de Entrenamiento](https://via.placeholder.com/800x400?text=Captura+2:+Grafico+3D+de+costo+o+curva+de+perdida)
*Captura de los plots generados dentro de SageMaker (ej. la superficie 3D del Notebook 1).*

#### C. Inferencia de Resultados
![Output de Inferencia](https://via.placeholder.com/800x400?text=Captura+3:+Prediccion+final+para+M=1.3)
*Captura de la celda de predicción final donde el modelo calcula la luminosidad para una nueva estrella.*

---

## 4. Comparativa: Ejecución Local vs. Cloud
| Atributo | Ejecución Local | AWS SageMaker (Cloud) |
| :--- | :--- | :--- |
| **Consistencia** | Depende de la instalación de Python local. | Entorno pre-configurado y estandarizado. |
| **Escalabilidad** | Limitada por CPU/RAM física. | Capacidad de escalar a instancias de alto rendimiento. |
| **Gobernanza** | Difícil de auditar. | Logs de ejecución y gestión de accesos empresarial. |

---

## 5. Conclusiones
La implementación exitosa en AWS SageMaker demuestra que los modelos de Machine Learning, cuando se construyen correctamente desde sus bases matemáticas, se convierten en componentes de software robustos y predecibles. La capacidad de capturar interacciones complejas (como $M \cdot T$) permite que los sistemas empresariales tomen decisiones más precisas y fundamentadas en datos.
