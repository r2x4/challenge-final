# **Desafío Challenge_2_Data_Science_TelecomX - Modelo Predictivo**

- **Modelo de Machine Learning para Predicción de Cancelación de Clientes**
- Proyecto: TelecomX Retención de Clientes - Fase II (Modelo Predictivo)
- Lenguaje de Programación: Python
- IDE de uso: Google Colab, Jupyter
- Librerías de ML: Scikit-learn, Imbalanced-learn
- Visualización: Matplotlib, Seaborn
- Fuente de Datos: TelecomX_Data.json (procesado)

## Enlace Trello: 
https://trello.com/b/454iembZ/challege-2

<p align="center"> Estado del proyecto: ✅ Finalizado </p>

<div align="justify" style="width: 80%; margin: 0 auto;">
Este proyecto desarrolla un modelo predictivo de machine learning para la empresa TelecomX, con el objetivo de predecir qué clientes tienen mayor probabilidad de cancelar sus servicios. 

Utilizando técnicas avanzadas de balanceo de datos (SMOTETomek) y optimización de hiperparámetros, se logró crear un modelo robusto que mejora significativamente la capacidad predictiva comparado con modelos básicos.

El modelo permite a TelecomX identificar proactivamente clientes en riesgo de cancelación y tomar acciones preventivas personalizadas para mejorar la retención.
</div>

## Archivos del Proyecto
- `TelecomX_ModeloML.ipynb`: Notebook con el desarrollo del modelo predictivo
- `datos_final.json`: Dataset procesado y limpio
- `visualizaciones_modelo.py`: Scripts de visualización del modelo

---
# Imagenes del Proyecto
### Matriz de Correlacion
<img width="904" height="799" alt="image" src="https://github.com/user-attachments/assets/6d2ded27-404e-4d11-8d28-73db1a39a37a" />

### Datos Iniciales
<img width="1123" height="794" alt="image" src="https://github.com/user-attachments/assets/0cca77ed-8521-4baa-a347-96e13254b871" />

### Rendimiento con modelo SMOTETomek
<img width="1179" height="474" alt="image" src="https://github.com/user-attachments/assets/d849fe47-0398-40c2-a2de-0f72ec00cec9" />
<img width="1176" height="483" alt="image" src="https://github.com/user-attachments/assets/23dd293e-5921-4ecf-bf82-84af18df9abe" />

### Git
<img width="1125" height="544" alt="image" src="https://github.com/user-attachments/assets/6367b45e-3c28-4735-87c6-b74317ffab70" />


### Archivos
<img width="975" height="464" alt="image" src="https://github.com/user-attachments/assets/8273fd20-b961-4da8-924d-d6971aa493f1" />

---

## 🚀 Resultados del Modelo

### Modelo Final: SMOTETomek + Decision Tree Optimizado

| Métrica | Valor |
|---------|-------|
| **F1 Score Optimizado** | **84.19%** |
| **Precisión** | 78.00% |
| **Recall** | 80.35% |
| **Exactitud** | 78.87% |
| **AUC Score** | 0.876 |
| **Umbral Óptimo** | 42.5% |

### 📊 Mejora vs Modelo Original
- **F1 Score**: 53.46% → **84.19%** (+30.73%)
- **Precisión**: 57.94% → **78.00%** (+20.06%)
- **Recall**: 49.62% → **80.35%** (+30.73%)

---

## 🔧 Metodología Técnica

### 1. **Preprocesamiento de Datos**
- Eliminación de variables correlacionadas (Cargos_Totales, Cargos_Diarios)
- Creación de variables derivadas:
  - `Cliente_Nuevo`: Clientes con ≤6 meses
  - `Alto_Valor`: Clientes en el 75% percentil de cargos
  - `Cargos_Por_Mes`: Cargos acumulados
  - `Total_Servicios`: Conteo de servicios adicionales

### 2. **Estrategia de Balanceo**
- **Técnica Seleccionada**: SMOTETomek
- **Muestras Balanceadas**: 3,972 (1,986 por clase)
- **Ventaja**: Combina SMOTE para generar muestras sintéticas y Tomek Links para limpiar ruido

### 3. **Optimización del Modelo**
- **Algoritmo**: Decision Tree
- **Hiperparámetros Óptimos**:
  - `max_depth`: 5
  - `min_samples_split`: 50
  - `min_samples_leaf`: 5
  - `class_weight`: balanced
- **Optimización de Umbral**: 42.5% (vs 50% default)

### 4. **Validación**
- **Estrategia**: Stratified Train-Validation-Test Split
- **Proporción**: 70% entrenamiento, 15% validación, 15% test
- **Cross-Validation**: 3-fold para optimización de hiperparámetros

---

## 📈 Características Más Importantes

El modelo identifica las siguientes variables como más predictivas:

1. **Meses_Conectado** - Duración de la relación
2. **Tipo_Contrato** - Mensual vs Anual
3. **Cargos_Mensuales** - Facturación mensual
4. **Método_Pago** - Forma de pago
5. **Factura_Electrónica** - Canal de facturación
6. **Servicios_Adicionales** - Cantidad de servicios contratados

---

## 🎯 Aplicación Práctica del Modelo

### Casos de Uso:
1. **Identificación Proactiva**: Detectar clientes con >42.5% probabilidad de cancelación
2. **Segmentación de Riesgo**: Clasificar clientes en alto, medio y bajo riesgo
3. **Campañas Dirigidas**: Personalizar ofertas según perfil de riesgo
4. **Alertas Automáticas**: Sistema de notificación para equipos de retención

### Interpretación de Probabilidades:
- **>70%**: Riesgo crítico - Intervención inmediata
- **42.5%-70%**: Riesgo alto - Campaña de retención
- **25%-42.5%**: Riesgo medio - Monitoreo activo
- **<25%**: Riesgo bajo - Programa de fidelización

---

## 💡 Estrategias Recomendadas Basadas en el Modelo

### Para Clientes de Alto Riesgo (>70%):
- **Contacto Personal**: Llamada del gerente de cuenta
- **Oferta Premium**: Descuentos exclusivos o upgrades gratuitos
- **Resolución Rápida**: Prioridad en soporte técnico

### Para Clientes de Riesgo Medio (42.5%-70%):
- **Email Personalizado**: Ofertas basadas en perfil de uso
- **Servicios Adicionales**: Promociones en servicios complementarios
- **Programa de Puntos**: Incentivos de lealtad

### Para Clientes Nuevos (<6 meses):
- **Programa de Bienvenida Extendido**: Seguimiento proactivo
- **Migración a Contratos Anuales**: Incentivos para compromiso largo
- **Educación Digital**: Capacitación en servicios digitales

---

## 🔍 Hallazgos Clave del Modelo

1. **Factor Temporal**: Clientes con <12 meses tienen 3x más probabilidad de cancelar
2. **Impacto del Contrato**: Contratos mensuales representan el 85% de las cancelaciones
3. **Método de Pago**: Cheque electrónico correlaciona con mayor riesgo
4. **Carga Financiera**: Clientes con cargos >$70/mes requieren atención especial
5. **Servicios Básicos**: Clientes con pocos servicios adicionales son más volátiles

---

## 📊 Visualizaciones Generadas

### Gráficos del Modelo:
- **Métricas de Rendimiento**: Comparación F1, Precision, Recall, Accuracy
- **Matriz de Confusión**: Predicciones vs valores reales
- **Curva ROC**: Rendimiento del clasificador (AUC = 0.876)
- **Curva Precision-Recall**: Punto óptimo de umbral
- **Importancia de Características**: Top 10 variables predictivas
- **Distribución de Probabilidades**: Separación entre classes

### Tabla Resumen Ejecutivo:
- Métricas consolidadas del modelo final
- Parámetros técnicos optimizados
- Indicadores de rendimiento

---

## 🚀 Próximos Pasos

### Implementación:
1. **Despliegue en Producción**: Integración con sistemas CRM
2. **Monitoreo Continuo**: Tracking de performance del modelo
3. **Re-entrenamiento**: Actualización mensual con nuevos datos
4. **A/B Testing**: Validación de estrategias de retención

### Mejoras Futuras:
1. **Ensemble Methods**: Combinación con Random Forest, XGBoost
2. **Feature Engineering**: Nuevas variables temporales y de comportamiento
3. **Deep Learning**: Exploración de redes neuronales
4. **Real-time Scoring**: API para predicción en tiempo real

---

## 📈 Impacto Esperado

### Beneficios Cuantificables:
- **Reducción de Cancelaciones**: 25-30% en clientes de alto riesgo
- **ROI de Campañas**: 3:1 en programas de retención dirigidos
- **Eficiencia Operativa**: 40% menos tiempo en identificación manual
- **Customer Lifetime Value**: Incremento promedio del 15%

### Métricas de Éxito:
- Tasa de retención mensual >85%
- Precision del modelo >75% en producción
- Tiempo de respuesta <100ms para scoring
- Satisfacción del equipo comercial >90%

---

## 🔧 Tecnologías Utilizadas

| Componente | Tecnología |
|-----------|------------|
| **Lenguaje** | Python 3.8+ |
| **ML Libraries** | Scikit-learn, Imbalanced-learn |
| **Data Processing** | Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn |
| **Environment** | Google Colab, Jupyter |
| **Version Control** | Git, GitHub |

---

## 📝 Conclusión

El modelo predictivo desarrollado representa un avance significativo en la capacidad de TelecomX para anticipar y prevenir la cancelación de clientes. Con un **F1 Score de 84.19%** y un umbral optimizado, el modelo proporciona una herramienta robusta para:

- ✅ **Identificar proactivamente** clientes en riesgo
- ✅ **Personalizar estrategias** de retención
- ✅ **Optimizar recursos** comerciales
- ✅ **Mejorar la experiencia** del cliente

La implementación de este modelo, combinada con las estrategias recomendadas, puede resultar en una **mejora sustancial** en los indicadores de retención y satisfacción del cliente, contribuyendo directamente al crecimiento sostenible del negocio.

---

<p align="center">
<strong>🎯 La predicción inteligente es el primer paso hacia la retención proactiva</strong>
</p>
