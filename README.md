# DP-800 Lab 02: Implementación de objetos de programabilidad con SQL

## 🎯 Objetivo
Crear y utilizar objetos principales de programabilidad en SQL Server (vistas, procedimientos almacenados, funciones y triggers) para centralizar la lógica de negocio y mejorar el mantenimiento usando la base de datos de prueba `AdventureWorksLT`.

## 📝 Resumen de Pasos

1. **Verificar la Conexión:** Comprobar el acceso a la base de datos `AdventureWorksLT` realizando consultas básicas (`SELECT TOP 5`) a las tablas `Customer`, `SalesOrderHeader` y `Product`.
2. **Crear una Vista (View):** Crear `SalesLT.vCustomerOrders` para unir la información de clientes y sus pedidos, ocultando la complejidad de los `JOIN` para el código de la aplicación.
3. **Crear un Procedimiento Almacenado (Stored Procedure):** Implementar `dbo.AddOrderLineItem` para insertar nuevos detalles de pedido de forma transaccional. Incluye manejo de errores (`THROW`), inserción de datos y actualización automática del subtotal del pedido.
4. **Crear una Función Escalar (Scalar Function):** Desarrollar `dbo.fnOrderTotal` para encapsular la lógica de cálculo y devolver un único valor (el total del pedido) que puede ser reutilizado en cualquier consulta.
5. **Crear una Función con Valores de Tabla (Inline TVF):** Construir `dbo.GetCustomerOrders` para recibir un parámetro (`@CustomerID`) y devolver una tabla con sus pedidos, ideal para usar con el operador `CROSS APPLY`.
6. **Crear un Disparador (Trigger) y Auditoría:** Crear la tabla `dbo.OrderAudit` y el trigger `SalesLT.trg_LogOrderTotalChange` que se ejecuta automáticamente tras un `INSERT` o `UPDATE` en los detalles del pedido, registrando el total antiguo y el nuevo para mantener un historial.
7. **Pruebas y Limpieza:** Ejecutar datos de prueba tras la creación de cada objeto para validar su funcionamiento y, opcionalmente, eliminar la base de datos al finalizar cerrando las conexiones existentes desde SSMS.
