# schema.sql
Cadena RetailChain - 2 sucursales

EJERCICIO RETAIL CHAIN:
-- ══════════════════════════════════════════
-- RetailChain — UNION y UNION ALL
-- Autor: Mariano
-- Fecha: 20-10-2026
-- ══════════════════════════════════════════

-- ── CONSULTA 1: UNION ────────────────────
-- Reporte de Catálogo Unificado
-- Pregunta de negocio: ¿Qué productos únicos comercializa la empresa en toda su red de sucursales?
-- Operador: UNION (elimina filas completamente duplicadas)

-- [Tu consulta aquí]
SELECT nombre_producto, categoria FROM inventario_sucursal_norte
UNION
SELECT nombre_producto,categoria FROM inventario_sucursal_sur

Respuesta:
Los productos únicos que comercializa la empresa en toda su red de sucursales son:
-	Auriculares BT Pro
-	Hub USB-C 7p
-	Laptop Basic 14
-	Laptop Pro 15
-	Monitor 4K 27"
-	Mouse Inalámbrico
-	Parlante Bluetooth
-	SSD Externo 1TB
-	Teclado Mecánico
-	Webcam HD 1080p

-- ── CONSULTA 2: UNION ALL ────────────────
-- Auditoría de Stock Total
-- Pregunta de negocio: ¿Cuántos registros físicos de stock existen en total entre ambas sucursales?
-- Operador: UNION ALL (mantiene todos los registros incluyendo duplicados)

-- [Tu consulta aquí]
SELECT SUM(stock) AS total_unidades_stock
FROM (
    SELECT nombre_producto, stock FROM inventario_sucursal_norte
    UNION ALL
    SELECT nombre_producto, stock FROM inventario_sucursal_sur
) AS stock_total;

Respuesta:
El inventario consolidado cuenta con un total de 14 registros físicos (filas) entre ambas sucursales, lo que representa un stock físico real de 200 unidades de producto disponibles en total.

-- ── CONSULTA 3: COMPARACIÓN DE RESULTADOS ─
-- Ejecutá estas dos consultas para comparar cuántas filas
-- devuelve cada operador y explicá la diferencia en tu README

Script: UNION
SELECT COUNT(*) AS filas_union
FROM (
SELECT nombre_producto, categoria FROM inventario_sucursal_norte
UNION
SELECT nombre_producto,categoria FROM inventario_sucursal_sur
) AS resultado_union;
Respuesta:
A través de esta consulta devuelve la cantidad de registros (filas) sin duplicados.


Script: UNION ALL
SELECT COUNT(*) AS filas_union_all
FROM (SELECT nombre_producto, categoria, stock FROM inventario_sucursal_norte
UNION ALL
SELECT nombre_producto,categoria, stock FROM inventario_sucursal_sur
) AS resultado_union_all;
Respuesta:
A través de esta consulta devuelve la cantidad total de registros (filas), incluyendo los duplicados.
