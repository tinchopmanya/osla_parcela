# Documento de Producto: OslaParcela

## 1. Visión del Producto

OslaParcela es una plataforma de inteligencia agrícola que proporciona **scoring defensible de parcelas** mediante la integración de datos satelitales de 50 años, información edafológica, ganadería y modelado climático. Empodera a instituciones financieras para evaluar garantías agrícolas con precisión científica, y a productores para optimizar decisiones de inversión y gestión de riesgo.

**Score de Viabilidad: 4.1/5**

---

## 2. Problema que Resuelve

Los bancos uruguayos evalúan garantías agrícolas utilizando principalmente:
- CONEAT (clasificación de suelo estática)
- Experiencia y intuición del analista de crédito
- Análisis visual limitado de la parcela

**Brechas críticas:**
- No capturan productividad histórica real de la parcela
- Desconocen patrones de riesgo climático multi-decenal
- No detectan enfermedades en etapas tempranas (semanas antes de síntomas visibles)
- Evaluaciones inconsistentes entre analistas
- Incapacidad para predecir yield bajo distintos escenarios climáticos

**Consecuencias:** Mayor riesgo de crédito no priced, rechazos injustificados de productores viables, o asunción de riesgo inadvertido.

---

## 3. Cliente Ideal (ICP)

**Primario:** Bancos y cooperativas de crédito agrícola en Uruguay
- Carteras de crédito agrícola >USD 100M
- Presión regulatoria por gestión de riesgo
- Necesidad de diferenciación competitiva en scoring

**Secundario:**
- Productores agrícolas (maíz, soja, trigo, ganadería)
- Aseguradoras agrícolas (riesgos climáticos, rendimiento)

**Tamaño ICP:** ~8-12 instituciones financieras en Uruguay con apetito de tecnología.

---

## 4. Propuesta de Valor

### Cluster Agro (3 verticales)
- **Agro (OslaParcela)** + AgroExport (OslaAgroExport) + Precios (OslaPrecios)
- **Cross-sell:** Agro → Precios **70% (strongest synergy detected)**
- **Bundle "Agro Integral":** USD 500/mes (3 verticales)
- **Base cost SNIG+CONEAT integration:** USD 3.000
- **Marginal cost:** USD 400 per additional vertical

### Valor por Stakeholder

| Stakeholder | Valor Entregado |
|---|---|
| **Bancos** | Scoring objetivo de parcelas (+80-95% R² en yield prediction). Reducción de NPL en créditos agrícolas. Aumento de velocidad de análisis (48h → 4h por solicitud). |
| **Productores** | Acceso a intelligence sobre su parcela: NDVI histórico, riesgo de enfermedad, predicción de rendimiento, recomendaciones de insumos. |
| **Aseguradoras** | Pricing más preciso de pólizas agrícolas. Detección temprana de enfermedades para intervención. |

### Defensibilidad vs IA

**Defensibilidad por datos: 5/5 (máxima)** — Histórico listings + catastro + transacciones. Pero cae en ranking anti-LLM porque IA ya replica parcialmente comparables y valuación. Valor sobrevive en sistema persistente de monitoreo por padrón, no en informes one-shot.

### Precio y Bundle


### Plataforma Geoespacial
- SNIG + CONEAT + Catastro como núcleo geoespacial de todas las verticales agro
- Integración única genera economía de escala para Agro + AgroExport + Precios

**Precio:**
- USD 200–400/mes (por banco; modelos por tipo de cultivo)
- Bundle "Agro Integral": USD 500/mes
- SLA 99.5% uptime, integración SWIFT/ISO 20022

---


**Ola 003: Evolución a Pila Madura**
La Ola 003 muestra que Real Estate Intelligence puede pasar de simple AVM a pila madura combinando: precio+expansión urbana+exposición+flood risk+mortgage intelligence. HMDA+HM Land Registry como benchmarks internacionales. El criterio 'monitoring > one-shot' (019) sugiere evolucionar hacia alertas continuas de cambios catastrales.

### Matriz Regulatoria (Scoring #11)

OslaParcela posiciona como **RECOMENDADA** en contexto regulatorio UY:

| Factor | Score | Notas |
|--------|-------|-------|
| **Acceso a Datos** | 9/10 | Catastro (DNC), CONEAT, Sentinel-2, ECMWF, FAOSTAT — todos públicos/abiertos |
| **Restricción Legal** | 2/10 | Bajo riesgo: Catastro explícitamente permite uso comercial (Decreto 54/2017) |
| **Competencia Regulatoria** | 1/10 | No regulador específico; MGAP cooperativo |
| **Enforcement Risk** | 1/10 | Sin precedente de enforcement contra plataformas datos agrícolas UY |
| **Potencial Comercial** | 8/10 | Bancos + aseguradoras + productores = TAM USD 2–3M annual |
| **SCORE TOTAL** | 7/10 | **VERDE — Bajo riesgo + Alto potencial** |

**Riesgo Principal:** ToS de portales inmobiliarios (no ley). Defensibilidad por datos catastrales públicos UY es robusta.

---

### Anti-LLM Ranking y Evolución de Moat

OslaParcela rankea fuerte en defensibilidad contra IA (máx 5/5 por datos históricos 50 años). Sin embargo, cae en ranking anti-LLM global porque:
- **IA ya replica parcialmente comparables y valuación** via scraping listings + análisis
- Valor sobrevive **solo en sistema persistente de monitoreo por padrón**, no en informes one-shot

**Recomendación:** Evolucionar hacia **monitoring continuo de cambios catastrales** y captura de transacciones reales (no listings). Modelo: HMDA (USA) + HM Land Registry Price Paid Data (UK) como benchmarks internacionales de madurez.


---

## 5. Fuentes de Datos — Calidad y Viabilidad

### Fuentes Uruguayas (Libre Acceso) — 5/5 Viabilidad

| Fuente | Cobertura | Actualización | Calidad | Viabilidad |
|--------|-----------|---------------|---------|-----------|
| **SNIG** | 12M+ bovinos, inventarios | Anual | 5/5 | 5/5 |
| **DICOSE** | Registro enfermedades cultivos | Semanal | 5/5 | 5/5 |
| **CONEAT** | 188 soil groups, clasificación suelo | Estática (~20 años) | 5/5 | 5/5 |
| **Catastro shapefiles** | Límites parcelas geolocalización | Anual | 5/5 | 5/5 |
| **MGAP normativa** | Datos productivos, subsidios | Trimestral | 5/5 | 5/5 |
| **INASE** | Semillas certificadas, variedades | Anual | 4/5 | 4/5 |

### Fuentes Internacionales (Libre/Open Acceso) — 5/5 Viabilidad

| Fuente | Cobertura | Licencia | Viabilidad |
|--------|-----------|----------|-----------|
| **Sentinel-2** | Imágenes multiespectrales 10m, 5–6 días | CC-open | 5/5 |
| **Landsat** | 50 años historial, 30m | CC0 | 5/5 |
| **ECMWF ERA5** | Clima reanalizado 1940–presente | CC BY 4.0 | 5/5 |
| **Google Earth Engine** | Catálogo integrado Sentinel+Landsat+clima | Libre acceso | 5/5 |
| **FAOSTAT** | Series rendimiento por cultivo (FAO) | CC0 | 5/5 |
| **NASA Earthdata** | Elevación, temperatura, humedad | CC0 | 5/5 |
| **NOAA** | Precipitación, radiación solar | CC0 | 5/5 |

**Viabilidad agregada: 5/5 (EXCELENTE)**

**Actualización:** Imágenes satelitales nuevas cada 5–6 días; histórico de 50 años disponible.

---


### Fuentes Internacionales Adicionales (Ola 002-003)
- **Natural Earth** (dominio público): cartografía territorial
- **GeoNames** (CC BY 4.0): normalización de localidades y coordenadas
- **HMDA (USA):** disclosure público préstamos hipotecarios a nivel individual
- **HM Land Registry Price Paid Data (UK):** transacciones inmobiliarias reales, acceso abierto
- **WorldPop:** densidad poblacional
- **GHSL:** expansión urbana
- **Global Surface Water:** riesgo hídrico
- **SRTM:** relieve/elevación
## 6. Modelos ML Defensibles

### 6.1 Yield Prediction (LightGBM)
- **Input:** NDVI histórico (5-10 años), lluvia acumulada pre-siembra/post-siembra, temperatura acumulada, CONEAT, fertilización histórica
- **Output:** Rendimiento esperado (t/ha) con intervalo de confianza 80-95% R²
- **Métrica:** R² 80-95% en validación histórica; RMSE 0.5-1.2 t/ha
- **Ventaja defensible:** Histórico Sentinel+Landsat permite entrenar con 50 años de variabilidad; generalizables a nuevas parcelas con datos base (CONEAT+SNIG)

### 6.2 Disease Detection (CNN - PyTorch)
- **Input:** Stack Sentinel-2 multiespectrales (bandas rojo, infrarrojo cercano, borde rojo)
- **Output:** Anomalía de enfermedad, severidad (0-100%), ubicación en parcela
- **Métrica:** Detección 3-4 semanas pre-síntomas visibles; precisión 92%+ en cultivos entrenados
- **Ventaja defensible:** Entrenable con imágenes públicas etiquetadas (FAOSTAT, estudios agrícolas); modelos específicos por región/cultivo imposibles de replicar sin datos históricos

### 6.3 Land Productivity Scoring (Ensemble)
- **Input:** NDVI temporal (10 años), pendiente, cobertura, CONEAT, histórico de cultivos
- **Output:** Score 0-100 de productividad relativa de parcela
- **Métrica:** Correlación 0.75+ con rendimientos observados
- **Ventaja defensible:** Agregación de múltiples señales históricas; competencia dificultada por acceso a datos de 50 años

### 6.4 Climate Risk (LSTM - TensorFlow)
- **Input:** Series temporales ECMWF (precip, temp, ETP) para parcela; calendario agrícola
- **Output:** Probabilidad riesgo climático severo (estrés hídrico, helada, extremo térmico) en próximas 12-36 semanas

### Modelos Integrales Ola 003
- **Score inmobiliario integrando WorldPop (densidad), GHSL (expansión urbana), WorldCover (uso suelo), Global Surface Water (flood risk), SRTM (relieve) y ERA5 (clima)**
- **Benchmark de mortgage intelligence usando HMDA como modelo de referencia para capa hipotecaria UY**
- **Métrica:** AUROC 0.82+
- **Ventaja defensible:** Modelos capturan autocorrelación climática; específicos a región y cultivo

---

## 7. Competencia y Diferenciación

**Score Competitivo: 4.1 (Highest en Datos, pero NO en Top 10 Anti-LLM)**

### Competidores Directos Locales
- **InfoCasas**: Domina listings; sin scoring defensible
- **Mensus**: Tasación; sin histórico satelital
- **AVALUOS.uy, KiteProp, TASAR**: Valuación genérica
- **Brokers premium** (Workplace, Kleos): Manual, sin AI

### Amenaza IA Frontier (Gemini, Claude)
- **IA ya replica comparables y valuación parcialmente** via scraping listings + análisis
- Defensibilidad cae cuando se limita a one-shot reports
- Solo sobrevive como **sistema de monitoreo continuo** por padrón

### Diferenciación Defensible

| Aspecto | OslaParcela | Competidores |
|--------|-----------|--------------|
| **Histórico 50 años** | Landsat + Sentinel integrados | Máx 10 años |
| **Datos catastrales Uruguay** | DNC + tasaciones + transacciones | Parcial |
| **Scoring ML** | Ensemble 5 modelos + clima | Valuación puntual |
| **Defensa contra LLMs** | Históricos limpios por padrón | Débil (IA replica rápido) |

### Riesgo: Ranking Final (019)

Real Estate Intelligence **NO aparece en top 10 anti-LLM**. Moat depende de datos catastrales locales UY (DNC, catastro, IT). Evolucionar hacia **monitoring continuo de cambios catastrales** para mayor resiliencia vs. LLMs.

### Métricas de Mercado

| Métrica | Buyer | WTP | Saturado | Defensa | Ticket | Ciclo |
|---------|-------|-----|----------|---------|--------|-------|
| **Scoring Predial** | 4/5 | 4/5 | 3/5 | 5/5 | USD 150/mes | 45d |

### Fuentes Internacionales Ampliadas (Ola 002-003)

Para evolucionar a pila madura: Copernicus Sentinel (expansión urbana, CC comercial), Landsat (dominio público, 50 años histórico), U.S. Census (demografía, segmentación), WorldPop (densidad), GHSL (expansión urbana), Global Surface Water (flood risk), SRTM (relieve), ERA5 (clima).



## 8. Arquitectura Técnica

### Stack Principal
- **Backend:** FastAPI + Gunicorn + Nginx
- **Datos Espaciales:** PostGIS (PostgreSQL 16) + rasterio + xarray + GDAL 3.x
- **Procesamiento Satelital:** Rasterio + xarray + Dask (paralelización)
- **ML - Yield/Productivity:** LightGBM + scikit-learn + Optuna (tuning)
- **ML - Enfermedad:** PyTorch CNN + torchvision (ResNet50 backbone)
- **ML - Clima:** TensorFlow LSTM + Keras
- **Descarga de Datos:** Google Earth Engine API + Copernicus Data Hub SDK
- **Frontend:** Next.js 15 + Mapbox + Plotly (visualización)
- **Orquestación:** Airflow (DAG: descarga satelital → procesamiento → scoring)
- **Cache/Queue:** Redis (resultados cachés, cola de cálculos)
- **Monitoreo:** Prometheus + Grafana

### Flujo de Datos (Alto Nivel)
1. Usuario carga parcela (coordenadas o shapefile)
2. Backend consulta Sentinel/Landsat para últimos 50 años (GEE)
3. Preprocesamiento: ortorectificación, normalización, cálculo NDVI/índices
4. Ejecución en paralelo: Yield Prediction, Disease Detection, Productivity Score, Climate Risk
5. Agregación de resultados; reporte visual (Mapbox + gráficos Plotly)
6. API REST expone scores; integración con sistemas bancarios (XML/JSON)

### Escalabilidad
- Rasterio + xarray + Dask para procesamiento distribuido (parcelas múltiples en paralelo)
- PostgreSQL + PostGIS tunning para queries espaciales frecuentes
- Redis para cachés de scores (TTL 7 días)
- Airflow para orquestación robusta

---

## 9. Roadmap Resumido

### Fase 1 (Meses 1-2): MVP - Maíz
- Yield Prediction + Disease Detection (CNN) para maíz
- Integración Sentinel-2 + Landsat + ECMWF
- Dashboard básico (mapa, score, gráficos)
- API REST, autenticación básica
- 2-3 pilotos con bancos

### Fase 2 (Meses 3-4): Extensión a Cultivos
- Soja, trigo, arroz
- Land Productivity Scoring
- Climate Risk LSTM
- Reportes PDF descargables
- Mobile-friendly UI

### Fase 3 (Meses 5-6): Integración Bancaria + B2B
- API con estándares SWIFT/ISO 20022
- Integración Twilio/email para alertas
- Admin panel: usuarios, cuotas, reportes de uso
- SLA 99.5% uptime

### Fase 4 (Post-MVP): Avances
- Integración SNIG en tiempo real (alertas ganadería)
- Modelos por suelo específico (CONEAT + propiedades físico-químicas)
- Marketplace de datos (productores pueden vender "historiales" anónimos)
- Expansion regional (Argentina, Brasil)

---

## 10. Métricas de Éxito

| Métrica | Target | Timeline |
|---|---|---|
| **R² Yield Prediction** | >85% en validación histórica | Mes 2 |
| **Precisión Disease Detection** | >92% en muestras de validación | Mes 2 |
| **Cobertura de Parcelas** | 50K pa
---

## 11. Riesgos y Mitigaciones (Ola 002-003)

**Riesgo Overall: 1.8/5 (YELLOW)**

| Riesgo | Probabilidad | Impacto | Mitigación |
|---|---|---|---|
| **ALERTA FRED** | Media-Alta | Alto | **NO usar FRED para modelos de pricing inmobiliario ni ML (Ola 002).** Datos agregados sin granularidad suficiente para casos de uso. |
| **Ranking final (019)** | Alta | Alto | Real Estate no aparece entre verticales top. Moat depende de datos catastrales locales UY (DNC, catastro, IT). Evolucionar hacia monitoring continuo para mayor resiliencia. |

### IA Residencial Global (Investigación 025)
IA residencial global (025): Zillow AI Mode (mar 2026), Redfin conversational search (ene 2026). Riesgo alto de producto demasiado parecido a IA+scrape+mapa. La IA ya lee listings, resume propiedades, explica zonas y arma comparables preliminares.

### IA Agéntica 2026 y Evolución Recomendada (Investigaciones 025, 031)
- IA agéntica 2026: Real Estate Intelligence queda debilitada. No conviene abrir primero. Oportunidad solo si baja a histórico limpio, series por zona/padrón y riesgo/trazabilidad con datos catastrales UY.
- Categoría menos blindada que Customs, Company o Agro Export porque IA mejora comparables, valuación asistida y lectura de oferta rápidamente.

### Amenaza IA Real Estate Detallada (Investigación 032)

Restb.ai leader en computer vision RE, 1M+ agentes inmobiliarios (26 MLSs, abr 2026). EliseAI para property managers. BrokerBot como digital teammate. PropTech market: USD 36.55B (2024), IA atrayendo USD 3.2B VC. Gemini + datos públicos = 80% due diligence inmobiliaria. Defensibilidad RE: solo 2/5.

---

### Riesgo de Defensibilidad vs IA (Investigación 032)

**Defensibilidad vs IA: 2/5 POCO DEFENDIBLE**

Registros propiedad UY accesibles (DNC). Gemini+Restb.ai ya ofrecen MVP compelling.

**Margen de defensa:** Históricos 5+ años UY, datos alquileres privados, integración notarios/escribanos.
