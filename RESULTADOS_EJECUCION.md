# Resultados - Pipeline Multi-Agente ML

## Dataset

| Atributo | Valor |
|----------|-------|
| Archivo | Student_Performance_Teaching_Effectiveness.csv |
| Filas | 1000 |
| Columnas | 15 |
| Columna objetivo | `Projects_Submitted` |
| Tipo de problema | Classification |

**Columnas disponibles:**
Student_ID, Age, Gender, Attendance_Percentage, Assignments_Completed, Class_Participation, Midterm_Grade, Final_Grade, Study_Hours_per_Week, Projects_Submitted, Teaching_Clarity, Teaching_Helpfulness, Feedback_Timeliness, Student_Performance, Teaching_Effectiveness

---

## Agente 1 — Preprocesador

| Configuración | Valor |
|---------------|-------|
| Estrategia imputación | mean |
| Escalado | standard |
| Codificación | One-Hot |

**Variables numéricas detectadas (10):**
Age, Attendance_Percentage, Assignments_Completed, Class_Participation, Midterm_Grade, Final_Grade, Study_Hours_per_Week, Teaching_Clarity, Teaching_Helpfulness, Feedback_Timeliness

**Variables categóricas detectadas (4):**
Student_ID, Gender, Student_Performance, Teaching_Effectiveness

**Resultado:**
- X_train: (800, 820)
- X_test: (200, 820)

---

## Agente 2 — Entrenador

Validación cruzada: **5 folds**

### Resultados por modelo

| Modelo | Accuracy | Precision | Recall | F1-Score | CV (mean) | CV (std) |
|--------|----------|-----------|--------|----------|-----------|----------|
| Logistic Regression | 0.1650 | 0.1533 | 0.1650 | **0.1445** | 0.1812 | 0.0172 |
| Random Forest | 0.1600 | 0.1415 | 0.1600 | 0.1297 | 0.1912 | 0.0372 |
| SVM | 0.1500 | 0.1359 | 0.1500 | 0.1100 | 0.1925 | 0.0238 |

### Mejor modelo seleccionado

**Logistic Regression** (f1_score = 0.1445)

---

## Agente 3 — Comunicador (Reporte)

```
=======================================================
REPORTE FINAL DEL PIPELINE MULTI-AGENTE
=======================================================

[Agente 1 - Preprocesador]
-----------------------------------
Estrategia de imputacion numerica: mean
Tipo de escalado: standard
Variables numericas (10): Age, Attendance_Percentage, Assignments_Completed, Class_Participation, Midterm_Grade, Final_Grade, Study_Hours_per_Week, Teaching_Clarity, Teaching_Helpfulness, Feedback_Timeliness
Variables categoricas (4): Student_ID, Gender, Student_Performance, Teaching_Effectiveness
Resultado: Dataset limpio, sin nulos, escalado y codificado.

[Agente 2 - Entrenador]
-----------------------------------
Tipo de problema: Classification
Validacion cruzada: 5 folds
Modelos evaluados: 3

Resultados por modelo:
  - Logistic Regression: accuracy=0.165, precision=0.1533, recall=0.165, f1_score=0.1445 | CV(mean=0.1812, std=0.0172)
  - Random Forest: accuracy=0.16, precision=0.1415, recall=0.16, f1_score=0.1297 | CV(mean=0.1912, std=0.0372)
  - SVM: accuracy=0.15, precision=0.1359, recall=0.15, f1_score=0.11 | CV(mean=0.1925, std=0.0238)

=> MODELO SELECCIONADO: Logistic Regression con score 0.1445

[Resumen Ejecutivo]
-----------------------------------
Se procesaron 14 variables. El mejor modelo fue Logistic Regression
con rendimiento 0.1445. Se recomienda explorar mas modelos o realizar
feature engineering.

=======================================================
FIN DEL REPORTE
=======================================================
```

---

## Preguntas RAG

### Pregunta 1
**P:** Cual fue el mejor modelo y que puntuacion obtuvo?
**R:** Mejor modelo: Logistic Regression con score 0.

### Pregunta 2
**P:** Que variables numericas y categoricas tiene el dataset?
**R:** Variables numericas (10): Age, Attendance_Percentage, Assignments_Completed, Class_Participation, Midterm_Grade, Final_Grade, Study_Hours_per_Week, Teaching_Clarity, Teaching_Helpfulness, Feedback_Timeliness. Variables categoricas (4): Student_ID, Gender, Student_Performance, Teaching_Effectiveness.

### Pregunta 3
**P:** Como se preprocesaron los datos?
**R:** No tengo suficiente informacion para responder eso.

### Pregunta 4
**P:** Que tan confiable es el resultado segun las metricas?
**R:** Modelos evaluados: 3. Modelo Logistic Regression: accuracy=0.165, precision=0.1533, recall=0.165, f1_score=0.1445. Modelo Random Forest: accuracy=0.16, precision=0.1415, recall=0.16, f1_score=0.1297. Modelo SVM: accuracy=0.15, precision=0.1359, recall=0.15, f1_score=0.11.

---

> **Nota:** Las métricas bajas (f1 ~0.14) se deben a que `Projects_Submitted`
> es una variable numérica discreta (cantidad de proyectos, ej: 0-10) y no
> una categoría real. Para este dataset, un enfoque de **regresión** sería
> más adecuado que clasificación.
