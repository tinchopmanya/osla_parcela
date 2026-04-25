# ROADMAP — OslaParcela (Inteligencia Agro + Scoring Parcelas)

## Estado actual

MVP conceptual. Requiere integración Sentinel + Landsat + CONEAT + SNIG + ECMWF. ML para yield prediction y disease detection.

---

## Roadmap integrado

### Fase 1 — Yield Prediction MVP (semanas 1-12)

**Entidades canónicas:**
- Predio (CONEAT, coordenadas)
- Parcela (histórico NDVI 50 años)
- Cultivo (tipo, variedad, rotación)
- Ganado (SNIG, densidad)
- Clima (ECMWF histórico + forecast)
- Rendimiento esperado (benchmark local)

**Milestones:**
- **M1:** CONEAT data sync (suelo, productividad por predio)
- **M2:** SNIG integration (inventario ganadero)
- **M3:** Sentinel + Landsat 50 años (NDVI, NDSI, NDMI)
- **M4:** ECMWF climate integration (temperature, precipitation, forecast)
- **M5:** LightGBM yield prediction model (R² 80-95%)
- **M6:** Disease detection CNN (3-4 semanas pre-síntomas)
- **M7:** Land productivity scoring determinístico
- **M8:** Product surface `/product/predio/` (parcel explorer)
- **M9:** Dashboard B2B bancos (lending decision support)
- **M10:** API product (/api/v1/agro/*)
- **M11:** Testing + documentación (80+ test cases)
- **M12:** MVP launch con 3 bancos piloto

**ML Pipeline:**
1. Feature engineering: NDVI histórico (50 años), CONEAT, precipitación, temperaturamedia, pendiente, exposición
2. Yield prediction (LightGBM ensemble con cross-validation): R² 80-95%
3. Disease detection (CNN ResNet50, fine-tuned en imágenes Sentinel): 90%+ F1
4. Scoring determinístico (suelo + NDVI + clima → 0-100)

**Validation criteria:**
- CONEAT sync latency <1 mes (datos públicos, no real-time)
- Sentinel latency <48h (cloud cover dependent)
- Yield prediction R² >0.82 (training)
- Disease detection F1 >0.90 (field validation)
- Lending officer adoption (SUS >72)

---

### Fase 2 — Climate Risk + Enhancement (semanas 12-22)

**Milestones:**
- **M13:** Drought forecasting (LSTM, 6 meses)
- **M14:** Frost/hail risk alerts (ECMWF + historical)
- **M15:** Fertilizer optimization (N-P-K recomendación por NDVI)
- **M16:** Insurance integration (riesgo agroclimático)

**ML enhancements:**
- LSTM climate forecast (RMSE <0.3 precipitation)
- Regression para N-P-K óptimo
- Insurance premium prediction

**Validation criteria:**
- Drought forecast skill >0.6 (6 meses)
- Fertilizer R² >0.65
- Insurance premium MAE <10%

---

### Fase 3 — Scaling + Precision (semanas 22-32)

**Milestones:**
- **M17:** Satellite constellation diversity (Sentinel-2, Landsat, MODIS)
- **M18:** Precision agriculture workflow (drone + satellite fusion)
- **M19:** Mobile app field scout
- **M20:** Regional expansion (Argentina, Brasil agrícola)

**Validation criteria:**
- Multi-satellite fusion latency <24h
- Drone integration latency <6h
- Mobile MAU >100 productores

---

### Fase 4 — Market (meses 8+)

**Milestones:**
- **M21:** Benchmark global pricing (futures markets)
- **M22:** Cooperativas de productores integración
- **M23:** Carbon sequestration measurement

---

## Stack especificación

**Backend:**
```
FastAPI + Pydantic
Postgres 16 + PostGIS (geospatial queries)
Airflow para ETL semanal
Redis para caching
```

**Frontend:**
```
Next.js 15 + 3D.js
Mapbox + Folium para NDVI visualización
D3.js para series temporales
Tailwind CSS
```

**ML & Satellite:**
```
PyTorch CNN (ResNet50 disease detection)
LightGBM (yield + scoring)
TensorFlow LSTM (climate forecast)
rasterio + xarray + rioxarray
GDAL + scipy para análisis espectral
Google Earth Engine Python API
Cloud-Optimized GeoTIFFs (COG)
```

**Data sources:**
```
CONEAT API (MGAP)
SNIG API (MGAP)
Sentinel Hub (ESA, 10m daily)
Landsat (USGS, 30m, 50 años)
ECMWF Copernicus (weather + forecast)
NOAA (precipitation, temperature)
FAOSTAT (production benchmark)
```

---

## Métricas de éxito

| Métrica | Actual | Target M12 | Target M32 |
|--------|--------|------------|------------|
| Predios perfilados | 0 | 1K | 20K |
| Yield prediction R² | N/A | 0.82 | 0.90 |
| Disease detection F1 | N/A | 0.90 | 0.95 |
| Lending decision accuracy | N/A | 85% | 92% |
| Bank pilots active | 0 | 3 | 15 |
| MRR | $0 | $1K | $20K |

---

## Riesgos y mitigaciones

| Riesgo | Probabilidad | Impacto | Mitigación |
|--------|-------------|--------|-----------|
| CONEAT datos incompletos | Baja | Bajo | Validación + manual override |
| Sentinel cloud cover persistente | Media | Medio | Temporal compositing + Landsat backup |
| ECMWF forecast skill variable | Media | Medio | Ensemble con NOAA + local weather station |
| Modelo sesgo a región Pampas | Media | Medio | Training data diversa (norte + este) |
| Competencia de agrotechs globales | Media | Medio | Defensible: UY CONEAT + SNIG monopolio |

---

## Presupuesto estimado (MVP)

| Línea | Costo | Duración |
|-------|-------|----------|
| Ingeniería (3 FTE) | $45K | 6 meses |
| Cloud infra (AWS + GEE) | $2.5K/mes | ongoing |
| Sentinel Hub subscription | $500/mes | ongoing |
| Field validation (viajes) | $3K | 3 meses |
| Testing + banco pilots | $6K | 2 meses |
| **Total MVP** | **~$95K** | **6 meses** |

---

## Hitos clave

- **Week 4:** M1-M2, CONEAT+SNIG fluyendo
- **Week 8:** M3-M4, Sentinel+ECMWF entrenado
- **Week 10:** M5-M6, ML models validados
- **Week 14:** M7-M8, dashboard con scoring
- **Week 16:** M9-M10, API + producto público
- **Week 20:** M11-M12, 3 bancos pilotos activos
