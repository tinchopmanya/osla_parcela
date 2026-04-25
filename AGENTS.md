# AGENTS.md — OslaParcela

## Identidad del proyecto

- **Nombre**: OslaParcela (Inteligencia Agro + Scoring Parcelas)
- **Ranking InvestigaVert**: — Score 4.1)
- **AshRise project_id**: `agro`
- **Puerto Postgres**: 5454
- **DB**: agro / user: agro
- **ICP primario**: Bancos (evaluación de garantías agro)
- **ICP secundario**: Productores medianos-grandes, aseguradoras agrícolas
- **Pricing target**: USD 200-400/usuario/mes
- **Estado validación**: PENDIENTE — requiere validación con bancos y productores

## Qué es

Plataforma de scoring de parcelas cruzando satellite (Sentinel, Landsat, 50 años) + CONEAT (suelo) + SNIG (ganado) + ECMWF (clima). Yield prediction, NDVI histórico, disease detection precoz. Sistema que convierte imágenes satélite en predicciones agrícolas defensibles para crédito y seguros.

## Problema que resuelve

Banco evalúa garantía de predio agrícola hoy: calcula CONEAT, revisa SNIG si tiene datos, guía en experiencia. Falta visibilidad real de productividad histórica, riesgos climáticos, enfermedades. Sistema que integra satélites + suelo + clima predice rendimiento esperado, alertas de sequía/plagas 3-4 semanas antes de síntomas, y justifica decisiones de crédito con datos.

## Modelos ML defensibles

1. **Yield Prediction** (LightGBM ensemble): predice producción por hectárea. R² 80-95%.
2. **Disease Detection CNN** (3-4 semanas pre-síntomas): detecta infecciones foliares por patrón NDVI.
3. **Land Productivity Scoring**: scoring 0-100 integrando historia NDVI, CONEAT, pendiente, exposición climática.
4. **Climate Risk Forecasting** (LSTM): predice impacto sequía/lluvia en próximos 6 meses.

## Fuentes de datos

### Uruguay
- CONEAT: índice de productividad de suelo por predio (Dirección General Agropecuaria)
- SNIG: inventario ganadero por predio
- DICOSE: sanidad animal
- IDE Uruguay: mapas base, límites jurisdiccionales
- catalogodatos.gub.uy: datos públicos abiertos agrarios

### Internacionales
- Copernicus Sentinel (CC-open): imágenes multiespectrales 10m diarias (NDVI, NDSI, NDMI)
- Landsat (public domain): histórico 50 años 30m
- NASA Earthdata: datos crudos de satélites NOAA
- ECMWF (CC BY 4.0): datos climáticos reanálisis 50 años + forecast 15 días
- NOAA (CC0): precipitación, temperatura global
- Google Earth Engine: interfaz integrada satélites + weather
- FAOSTAT (CC BY 4.0): producción global benchmark

## Acceso a datos compartidos (via FDW)

```sql
SELECT * FROM shared.fx_rates WHERE currency_code = 'USD';
```

## Stack técnico

- Backend: FastAPI (Python)
- Frontend: Next.js 15 + Tailwind
- DB: Postgres 16 + PostGIS (puerto 5454)
- ML: scikit-learn + LightGBM + PyTorch CNN + TensorFlow LSTM
- Satellite: rasterio + xarray + rioxarray + GDAL
- Storage: S3-compatible + Cloud-Optimized GeoTIFFs
- Geospatial: QGIS + Folium + Mapbox

## Reglas de boundary

1. Repo, base de datos, storage y colas propios.
2. No leer ni escribir directo en la base de otra vertical.
3. Compartir datos solo por FDW read-only desde shared-db.
4. Reusar patrones del núcleo reusable (source discovery, document extraction, identity resolution, alerts/tasks).

## Reglas para agentes

1. **No escribir en shared-db** — solo leer vía FDW
2. **Sentinel + CONEAT es fuente de verdad** para estado de parcelas
3. **Evidence-first**: cada predicción deja mapa satélite, índices, confianza temporal
4. **Deterministic-first**: usar CNN pero validar con métricas espectrales directas
5. **No afirmar enfermedad sin evidencia de patrón anómalo en NDVI**

## Variables de entorno

```
ASHRISE_BASE_URL=http://localhost:8080
ASHRISE_TOKEN=<token>
ASHRISE_PROJECT_ID=agro
SENTINEL_HUB_KEY=<key>
ECMWF_KEY=<key>
```

## Documentación del producto

- **[docs/Producto.md](docs/Producto.md)** — Documento completo del producto: visión, ICP, propuesta de valor, fuentes de datos, modelos ML, competencia, arquitectura, roadmap y métricas. Se actualiza cuando una investigación impacta esta vertical.
- **[docs/Investigaciones.md](docs/Investigaciones.md)** — Log cronológico de investigaciones procesadas que impactan esta vertical: si fortalecen o debilitan la tesis, y qué se actualizó en Producto.md como consecuencia.
- **[docs/ROADMAP.md](docs/ROADMAP.md)** — Milestones técnicos de implementación.

## Contrato AshRise

Al iniciar sesión: leer AGENTS.md → docs/ROADMAP.md → GET /state/agro → GET /handoffs/agro?status=open
Al cerrar: emitir ashrise-close con run + state_update.
