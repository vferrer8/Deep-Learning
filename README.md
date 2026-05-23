# 🧠 Deep Learning: Clasificación de Imágenes para Picking Robotizado

Implementación de un pipeline de deep learning completo para clasificación automática de imágenes en tareas de picking robotizado. Utiliza arquitecturas preentrenadas (ResNet18) con fine-tuning sobre CIFAR-10, incluyendo estrategias avanzadas de data augmentation y optimización.

## 🎯 Objetivos

- **Implementar un clasificador de imágenes** basado en redes neuronales convolucionales
- **Optimizar ResNet18 preentrenada** mediante transfer learning y fine-tuning
- **Aplicar data augmentation** para mejorar la generalización del modelo
- **Desarrollar un prototipo funcional** de picking robotizado automático
- **Evaluar y mejorar el rendimiento** del modelo en clasificación multiclase
- **Documentar el proceso** completo de diseño, entrenamiento e implementación

## 🧠 Conceptos Clave

- **Deep Learning**: Aprendizaje profundo con redes neuronales
- **Convolutional Neural Networks (CNN)**: Redes especializadas en visión por computadora
- **Transfer Learning**: Aprovechamiento de pesos preentrenados en ImageNet
- **Fine-tuning**: Adaptación de arquitecturas preentrenadas a tareas específicas
- **Data Augmentation**: Técnicas de aumento sintético de datos (rotación, volteo, variaciones de color)
- **CIFAR-10**: Dataset de 10 clases de imágenes (32×32 píxeles)
- **ResNet (Residual Networks)**: Arquitectura moderna con conexiones residuales
- **Picking Robotizado**: Aplicación industrial de automatización

## ⚙️ Desarrollo

### Metodología
Se implementa un enfoque moderno de deep learning dividido en fases claramente definidas:

1. **Fase 1 - Preparación de Datos**
   - Redimensionamiento de imágenes a 64×64 píxeles
   - Aplicación de data augmentation:
     * Recortes aleatorios
     * Volteo horizontal
     * Variaciones de color e iluminación
   - Normalización con estadísticas de ImageNet
   - División entrenamiento/validación/test

2. **Fase 2 - Diseño de Arquitectura**
   - Selección de **ResNet18 preentrenada** en ImageNet
   - **Congelamiento del backbone** (extractor de características)
   - **Sustitución de cabeza de clasificación** para 10 clases
   - Reducción drástica de parámetros entrenables

3. **Fase 3 - Entrenamiento y Optimización**
   - Estrategia de optimización adaptativa
   - Monitoreo de métricas en validación
   - Early stopping para evitar overfitting
   - Learning rate scheduling

4. **Fase 4 - Evaluación y Prototipo Funcional**
   - Métricas de rendimiento (accuracy, precision, recall, F1)
   - Matriz de confusión y análisis de errores
   - Integración para aplicación en picking robotizado

### Decisiones Importantes
- **Transfer Learning**: Uso de pesos preentrenados acelera convergencia y mejora resultados
- **Frozen Backbone**: Mantiene características genéricas de ImageNet, reduce overfitting
- **Data Augmentation agresiva**: Esencial para prevenir sobreajuste con datasets limitados
- **Redimensionamiento a 64×64**: Balance entre detalle y costo computacional
- **Arquitectura ResNet18**: Ligera pero poderosa, ideal para aplicaciones industriales

## 📊 Resultados

El proyecto entrega:
- **Modelo entrenado** con accuracy superior al 85% en validación
- **Prototipo funcional** listo para integración en sistemas robotizados
- **Análisis de rendimiento** por clase con matriz de confusión
- **Documentación visual** del proceso de entrenamiento
- **Pipeline reproducible** para reentrenamiento con nuevos datos
- **Comparativas** entre arquitecturas y estrategias de fine-tuning

## 🚀 Conclusiones

Este proyecto demuestra la efectividad del transfer learning en visión por computadora:

- **Arquitecturas preentrenadas** ofrecen un excelente punto de partida
- **Fine-tuning selectivo** permite adaptar modelos a tareas especializadas
- **Data augmentation** es crítica para mejorar generalización
- **El deep learning es viable** para automatización industrial

**Mejoras futuras:**
- Explorar arquitecturas más recientes (EfficientNet, Vision Transformers)
- Implementar quantization para despliegue en edge devices
- Crear pipeline de reentrenamiento automático con feedback del robot
- Expandir a múltiples vistas y datos de sensores adicionales

## 📂 Estructura del Proyecto

```
Deep Learning/
├── RAA_Parte1_VictorFerrer.pdf        # Diseño y planificación (RAAC Parte 1)
├── RAA_Parte2_VictorFerrer.ipynb      # Implementación y prototipo funcional
└── README.md                          # Este archivo
```

### Contenido de Archivos
- **RAA_Parte1_VictorFerrer.pdf**: Documentación del diseño conceptual, arquitectura y estrategia
- **RAA_Parte2_VictorFerrer.ipynb**: Código ejecutable con:
  - Carga y preparación de CIFAR-10
  - Implementación de data augmentation
  - Definición de arquitectura ResNet18
  - Loop de entrenamiento y validación
  - Evaluación y visualización de resultados

## 🛠️ Tecnologías Utilizadas

| Tecnología | Uso |
|-----------|-----|
| **Python 3.x** | Lenguaje principal |
| **PyTorch** | Framework de deep learning |
| **torchvision** | Datasets y arquitecturas preentrenadas |
| **NumPy** | Operaciones numéricas |
| **Matplotlib/Seaborn** | Visualización de resultados |
| **Jupyter Notebook** | Desarrollo interactivo |
| **CIFAR-10** | Dataset público de clasificación |

## ✍️ Autor

**Víctor Ferrer**  
Master en Inteligencia Artificial - UTAMED

---

*Este proyecto forma parte del programa de posgrado en Inteligencia Artificial y demuestra competencias avanzadas en deep learning, transfer learning y aplicaciones de visión por computadora para automatización industrial.*
