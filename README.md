# 📊 Pipeline de Análisis de Inventario - Metodología Medallion

## Descripción
Pipeline completo de análisis de inventario implementado en Databricks usando arquitectura medallion (Bronze → Silver → Gold). Incluye dashboard interactivo y conexión con Power BI.

## 🎯 Características

- **Arquitectura Medallion**: Datos estructurados en 3 capas
- **Optimizado para Serverless**: Conversión de Excel a CSV para evitar limitaciones
- **Tablas Gold**: Pre-agregadas y optimizadas para BI
- **Dashboard**: Visualizaciones interactivas en Databricks
- **Power BI Ready**: Tablas diseñadas para conexión directa
- **Automatizado**: Job programado para actualización diaria

## 📁 Estructura del Proyecto

```
Inventory_medallion/
├── Notebook/
│   └── Pipeline_Inventario_Completo.ipynb
├── Data/
│   ├── Inventario Databricks.xlsx (fuente)
│   └── inventario_staging.csv (generado)
└── README.md
```

## 🛠️ Arquitectura de Datos

### Capas Medallion

**🟫 Bronze** (`workspace.bronze.inventario_bronze`)
- Datos crudos sin transformación
- Normalización de nombres de columnas
- Metadatos de auditoría

**🥈 Silver** (`workspace.silver.inventario_silver`)
- Limpieza y validación de datos
- Eliminación de duplicados
- Campos calculados
- Tipado correcto

**🏆 Gold** (múltiples tablas)
- `inventario_kpis_unidad_negocio`: KPIs por unidad de negocio
- `inventario_detalle_producto`: Métricas por producto
- `inventario_categoria_provision`: Análisis de provisión

## 🚀 Cómo Ejecutar

### Requisitos
- Databricks workspace con Unity Catalog
- Compute: Serverless (recomendado) o cluster interactivo
- Archivo fuente: Excel en `/Workspace/.../Data/`

### Ejecución Manual

1. Abrir notebook: `Notebook/Pipeline_Inventario_Completo.ipynb`
2. Ejecutar todas las celdas en secuencia
3. El pipeline creará:
   - Esquemas en Unity Catalog
   - Archivo CSV staging
   - Tablas Bronze, Silver y Gold

### Ejecución Automatizada

1. Crear Job desde el notebook (botón Schedule)
2. O usar configuración JSON incluida en el notebook
3. Programación sugerida: Diaria a las 6:00 AM

## 📊 Dashboard y Power BI

### Queries del Dashboard

El notebook incluye queries SQL optimizadas para:
- KPIs principales
- Análisis por unidad de negocio
- Distribución de categorías de provisión
- Top productos

### Conexión a Power BI

**Tablas recomendadas**:
- `workspace.gold.inventario_kpis_unidad_negocio`
- `workspace.gold.inventario_detalle_producto`
- `workspace.gold.inventario_categoria_provision`

**Pasos de conexión**: Ver sección "Integración Power BI" en el notebook

## 📝 Documentación

Toda la documentación paso a paso está incluida en el notebook principal. Cada celda incluye:
- 🎯 Objetivos claros
- 📝 Explicaciones detalladas
- ⚙️ Código comentado
- ✅ Verificaciones de calidad

## 👥 Autor

Analista de Datos - Implementación reproducible

## 📝 Licencia

Uso interno de la empresa
