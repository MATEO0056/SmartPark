# SmartPark · Control de estacionamiento con lógica

Simulador web de un estacionamiento de 10 espacios (E01–E10) cuyas decisiones de ingreso se basan en lógica proposicional y de predicados.
Proyecto ABP de la Unidad 1 de **Modelos Discretos para Ingeniería** (NRC 32798) · Universidad de las Fuerzas Armadas ESPE, Sede Santo Domingo.

## ¿Qué hace?

- Evalúa cada placa con la regla **Ingreso permitido ≡ p ∧ q ∧ r**
  - `p`: existe un espacio libre
  - `q`: la placa está autorizada
  - `r`: el estacionamiento está abierto
- Explica el rechazo con la ley de De Morgan: `¬(p ∧ q ∧ r) ≡ ¬p ∨ ¬q ∨ ¬r`
- Muestra el estado del lote con cuantificadores: `∃x ∈ E: Libre(x)` y `∀x ∈ E: Ocupado(x)`
- Asigna automáticamente el primer espacio libre, registra salidas y guarda un historial (máx. 100 movimientos)
- Valida el formato de placa (3 letras + 4 números) y evita vehículos duplicados

## Cómo usarlo

1. Descargue o clone el repositorio.
2. Abra `index.html` en un navegador. No requiere instalación ni internet.
3. Escriba una placa (por ejemplo `ABC1234`, autorizada de fábrica) y pulse **Evaluar y registrar ingreso**.

## Pruebas rápidas

| Caso | Entrada | Resultado esperado |
|------|---------|--------------------|
| 1 | `ABC1234` con espacio y abierto | Ingreso permitido (E01) |
| 2 | `ABC1234` otra vez | Rechazo: ya está estacionado |
| 3 | `DEF5678` sin autorizar | Rechazo: placa no autorizada |
| 4 | Cerrar y probar una placa no autorizada | Rechazo con dos motivos |
| 5 | Diez espacios ocupados | Rechazo: no hay espacios |
| 6 | `AB123` | Rechazo: formato inválido |
| 7 | Salida con el estacionamiento cerrado | Permitida; el espacio queda libre |
| 8 | Quitar la autorización y reintentar | Rechazo: placa no autorizada |

Para reiniciar los datos: `localStorage.removeItem("smartpark-v1")` en la consola y recargar.

## Estructura

```


## Limitaciones

Es una simulación de software: no hay sensores, barreras, lectura automática de placas ni base de datos compartida. Los datos se guardan solo en el navegador del equipo.

## Integrantes

- Mateo Hidalgo
- Kevin Camacho


Docente: Javier José Cevallos Farías · Grupo G#5
