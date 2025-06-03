# 📊 Sismap-Dashboard API

API para consultar la productividad y el avance de los servicios en el marco de **Burocracia Cero**.

Versión: **1.0.0**  
OpenAPI: **3.1.0**

---

## 🔗 Endpoints

### 🟢 `GET /ping`

**Descripción:**  
Endpoint para comprobar actividad en el servidor.

**Respuesta:**
```json
{
  "status": "ok"
}
```

---

### 🔍 `GET /seguimiento/services`

**Descripción:**  
Obtiene los servicios con información de seguimiento para evaluación de cumplimiento.

**Parámetros de consulta:**

| Nombre                         | Tipo     | Valores posibles                                                | Descripción                                  |
|-------------------------------|----------|------------------------------------------------------------------|----------------------------------------------|
| `search_by`                   | string   | `nombre_institucion`, `sigla_institucion`, `nombre_servicio`, `identificador_unico`, `porcentaje_actual_de_cumplimiento`, `fecha` | Campo por el cual filtrar.                   |
| `search`                      | string   | (texto libre)                                                   | Texto de búsqueda.                           |
| `order_by`                    | string   | *Igual que `search_by`*                                         | Campo por el cual ordenar.                   |
| `order`                       | string   | `asc`, `desc`                                                   | Dirección del ordenamiento.                  |
| `limit`                       | integer  | ≥ 1                                                             | Número máximo de registros.                  |
| `offset`                      | integer  | ≥ 0                                                             | Número de registros a omitir.                |

**Respuesta exitosa (`200`):**
```json
{
  "data": [
    {
      "nombre_institucion": "string",
      "sigla_institucion": "string",
      "nombre_servicio": "string",
      "identificador_unico": "string",
      "porcentaje_actual_de_cumplimiento": 0,
      "fecha": "2025-06-03"
    }
  ],
  "pagination": {
    "limit": 0,
    "offset": 0,
    "total": 0,
    "page": 0
  },
  "message": "string",
  "status": 0
}
```

---

### 📈 `GET /monitoreo/services`

**Descripción:**  
Obtiene los servicios con información de monitoreo para evaluación de cumplimiento.

**Parámetros de consulta:**

| Nombre                         | Tipo     | Valores posibles                                                | Descripción                                  |
|-------------------------------|----------|------------------------------------------------------------------|----------------------------------------------|
| `search_by`                   | string   | `nombre_institucion`, `sigla_institucion`, `nombre_servicio`, `id_externo`, `average_productivity`, `fecha` | Campo por el cual filtrar.                   |
| `search`                      | string   | (texto libre)                                                   | Texto de búsqueda.                           |
| `order_by`                    | string   | *Igual que `search_by`*                                         | Campo por el cual ordenar.                   |
| `order`                       | string   | `asc`, `desc`                                                   | Dirección del ordenamiento.                  |
| `limit`                       | integer  | ≥ 1                                                             | Número máximo de registros.                  |
| `offset`                      | integer  | ≥ 0                                                             | Número de registros a omitir.                |

**Respuesta exitosa (`200`):**
```json
{
  "data": [
    {
      "nombre_institucion": "string",
      "sigla_institucion": "string",
      "nombre_servicio": "string",
      "id_externo": "string",
      "average_productivity": 0,
      "fecha": "2025-06-03"
    }
  ],
  "pagination": {
    "limit": 0,
    "offset": 0,
    "total": 0,
    "page": 0
  },
  "message": "string",
  "status": 0
}
```

---

## ⚠️ Errores de Validación

Si ocurre un error de validación (`422`), la respuesta será:

```json
{
  "detail": [
    {
      "loc": ["query", "limit"],
      "msg": "ensure this value is greater than or equal to 1",
      "type": "value_error.number.not_ge"
    }
  ]
}
```

---

## 📦 Estructura de datos

### SeguimientoServiceData

- `nombre_institucion`: string
- `sigla_institucion`: string
- `nombre_servicio`: string
- `identificador_unico`: string
- `porcentaje_actual_de_cumplimiento`: number
- `fecha`: string (date)

### MonitoreoServiceData

- `nombre_institucion`: string
- `sigla_institucion`: string
- `nombre_servicio`: string
- `id_externo`: string
- `average_productivity`: number
- `fecha`: string (date)

### Pagination

- `limit`: integer | null
- `offset`: integer
- `total`: integer
- `page`: integer
