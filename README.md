<div align="center">

# 🛡️ ARGOS

### Motor de Detección de Anomalías en Transacciones Financieras

[![Python](https://img.shields.io/badge/Python-3.12+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)
[![Status](https://img.shields.io/badge/Status-In_Development-yellow?style=for-the-badge)](https://github.com/ibardev/Argos)

*Un sistema end-to-end de detección de fraude financiero con procesamiento distribuido, streaming en tiempo real y explicabilidad integrada.*

[Características](#-características) • [Arquitectura](#-arquitectura) • [Stack Tecnológico](#-stack-tecnológico) • [Roadmap](#-roadmap) • [Por Qué Argos](#-por-qué-argos)

---

</div>

## 🎯 ¿Qué es Argos?

Argos es un **sistema de producción completo** que detecta fraude en transacciones financieras combinando:

- 🔍 **Análisis en tiempo real** con Apache Kafka y procesamiento streaming
- 🧠 **Múltiples modelos de ML** (supervisados, no supervisados, deep learning)
- 📊 **Explicabilidad total** con SHAP values para cada decisión
- 🏗️ **Arquitectura escalable** con PySpark para procesamiento distribuido
- 🔄 **MLOps automatizado** con retraining continuo y monitoreo de drift
- 🛡️ **Ética by design** con auditoría de sesgos y privacidad diferencial

**No es un ejercicio académico.** Cada componente existe porque el dominio de detección de fraude lo exige.

---

## ✨ Características

### Para Data Scientists
```python
# Detecta fraude con explicabilidad integrada
prediction = argos.predict(transaction)
# -> {
#   "fraud_score": 0.87,
#   "decision": "block",
#   "explanation": [
#     "Monto inusual: +0.3 SHAP",
#     "Horario nocturno: +0.2 SHAP",
#     "País nuevo: +0.15 SHAP"
#   ]
# }
```

### Para ML Engineers
- **Pipeline automatizado**: Airflow orquesta ingesta → procesamiento → retraining → deploy
- **Validación de datos**: Great Expectations bloquea datos corruptos antes del modelo
- **Monitoreo en producción**: Detección automática de drift con alertas configurables

### Para Software Engineers
- **API REST documentada** con Flask + OpenAPI
- **CI/CD completo** con GitHub Actions (lint → test → deploy)
- **Containerizado** con Docker Compose (todo el stack corre localmente)
- **Type safety** con mypy en modo strict

---

## 🏛️ Arquitectura

```
┌─────────────┐      ┌─────────────┐      ┌─────────────┐
│   Kafka     │─────▶│  PySpark    │─────▶│ Feature     │
│  (Stream)   │      │ Processor   │      │  Store      │
└─────────────┘      └─────────────┘      └──────┬──────┘
                                                  │
┌─────────────┐                                   ▼
│ Data Lake   │                          ┌─────────────────┐
│ (Parquet)   │◀─────────────────────────│   ML Models     │
└─────────────┘                          │ • Isolation F.  │
       ▲                                 │ • XGBoost       │
       │                                 │ • Autoencoder   │
┌──────┴──────┐                          └────────┬────────┘
│   Airflow   │                                   │
│ Orchestrator│                                   ▼
└─────────────┘                          ┌─────────────────┐
                                         │  Flask API      │
┌─────────────┐                          │  /predict       │
│  Monitoring │                          │  /explain       │
│  • Drift    │◀─────────────────────────│  /drift         │
│  • Metrics  │                          └─────────────────┘
└─────────────┘
```

**Arquitectura Lambda:** Procesamiento batch (históricos) + streaming (tiempo real) con serving layer unificado.

---

## 🛠️ Stack Tecnológico

<div align="center">

### Core

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)

### Big Data & Streaming

![Apache Spark](https://img.shields.io/badge/Apache%20Spark-E25A1C?style=flat&logo=apache-spark&logoColor=white)
![Apache Kafka](https://img.shields.io/badge/Apache%20Kafka-231F20?style=flat&logo=apache-kafka&logoColor=white)
![Apache Airflow](https://img.shields.io/badge/Apache%20Airflow-017CEE?style=flat&logo=apache-airflow&logoColor=white)

### ML & Deep Learning

![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat&logo=tensorflow&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-337AB7?style=flat&logoColor=white)
![SHAP](https://img.shields.io/badge/SHAP-FF6B6B?style=flat&logoColor=white)

### DevOps & Infrastructure

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat&logo=github-actions&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat&logo=terraform&logoColor=white)

</div>

---

## 🗺️ Roadmap

El proyecto se construye en **11 fases progresivas**, cada una desbloqueando la siguiente:

| Fase | Tema | Output Clave |
|------|------|--------------|
| ✅ **0** | Fundamentos Python | Generador de transacciones sintéticas |
| 🔄 **1** | Estructuras de datos | Catálogos y modelos de datos |
| 📋 **2** | Funciones y módulos | Pipeline de procesamiento modular |
| 🏗️ **3** | Programación Orientada a Objetos | Modelo de dominio (Transaction, Account, Alert) |
| 🛡️ **4** | Manejo de errores y archivos | Logging, I/O robusto, configuración por entorno |
| 🧪 **5** | Testing e ingeniería | pytest, mypy, asyncio |
| 📊 **6** | Análisis de datos | EDA, feature engineering, simulaciones Montecarlo |
| 🌊 **7** | Big Data | PySpark, Kafka, Data Lake |
| 🔄 **8** | Orquestación | Airflow, Great Expectations |
| 🤖 **9** | Machine Learning | Modelos + SHAP explainability |
| 🚀 **10** | MLOps | API, Docker, CI/CD, monitoreo |
| ⚖️ **11** | Ética y compliance | Auditoría de sesgos, privacidad diferencial |

**Tiempo estimado:** 8-9 meses (dedicación parcial)

[Ver roadmap completo](.roadmap_argos.md) →

---

## 💡 Por Qué Argos

### El Problema Real

Las instituciones financieras enfrentan:
- **Fraude creciente**: 3.5% de transacciones son fraudulentas (y creciendo)
- **Costos asimétricos**: Bloquear una transacción legítima cuesta, pero perder fraude cuesta 10x más
- **Regulación estricta**: Deben explicar cada decisión y demostrar ausencia de sesgos
- **Datos masivos**: Millones de transacciones diarias, con patrones que cambian constantemente

### La Solución

Argos resuelve esto con:
1. **Múltiples modelos** para diferentes patrones de fraude
2. **Explicaciones automáticas** que cumplen regulaciones (SHAP values)
3. **Procesamiento escalable** que maneja volúmenes de producción
4. **Monitoreo continuo** que detecta cuando el modelo se degrada
5. **Privacidad by design** con privacidad diferencial y k-anonimidad

---

## 📚 Recursos de Aprendizaje

Este proyecto es también un **viaje de formación completo**. Cada fase incluye:
- ✅ Tareas específicas con criterios de éxito claros
- 📖 Documentación de conceptos practicados
- 🎯 Justificación de por qué ese concepto importa en el sistema
- 🔗 Referencias a las mejores prácticas de la industria

Es perfecto para:
- Reactivar fundamentos de Python trabajando en un sistema real
- Aprender ML Engineering con un caso de uso complejo
- Entender arquitecturas de datos en producción
- Construir un portfolio que demuestre habilidades end-to-end

---

## 🚀 Inicio Rápido

```bash
# Clonar el repositorio
git clone https://github.com/ibardev/Argos.git
cd Argos

# Crear entorno virtual
python -m venv venv
source venv/bin/activate  # Linux/Mac

# Instalar dependencias
pip install -e .

# Generar transacciones de prueba
python -m argos.generator.transactions

# (Próximamente) Levantar el stack completo
docker-compose up
```

---

## 📈 Estado del Proyecto

**Actualmente en:** Fase 0 — Cimientos

**Próximos hitos:**
- [ ] Generador de transacciones sintéticas v1
- [ ] Modelado de datos con estructuras complejas
- [ ] Pipeline de procesamiento modular
- [ ] Modelo de dominio con POO

---

## 🤝 Contribuciones

Este es un proyecto personal de aprendizaje, pero las sugerencias son bienvenidas. Si encontrás algo que se puede mejorar, abrí un issue o PR.

---

## 📄 Licencia

MIT License - ver [LICENSE](LICENSE) para detalles.

---

<div align="center">

**Built with 🧠 by [ibardev](https://github.com/ibardev)**

*"En mitología griega, Argos Panoptes era un gigante con cien ojos que todo lo veía. Este sistema aspira a ese nivel de vigilancia sobre transacciones financieras."*

[⬆ Volver arriba](#-argos)

</div>
