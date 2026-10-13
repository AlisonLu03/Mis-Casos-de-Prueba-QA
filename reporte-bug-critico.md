# 🐛 Reporte de Bug Crítico: Cierre inesperado (Crash) al realizar transferencia interbancaria

## 📌 Información General
* **ID del Bug:** BUG-001
* **Severidad:** Crítica (Bloquea la funcionalidad principal)
* **Prioridad:** Alta
* **Aplicación:** Banca Móvil "MiBanco Perú"
* **Versión de la App:** v4.2.1 (Android)
* **Dispositivo utilizado:** Samsung Galaxy S21 (Android 13)
* **Entorno:** Producción (App en vivo)

---

## 📝 Descripción del Problema
La aplicación se cierra inesperadamente (*crash*) y regresa a la pantalla de inicio del celular en el momento exacto en que el usuario presiona el botón "Confirmar Transferencia" durante una operación interbancaria. No se genera ningún mensaje de error para el usuario y el dinero no es debitado.

---

## 👣 Pasos para Reproducir el Error
1. Iniciar sesión en la aplicación móvil con credenciales válidas.
2. En el menú principal, seleccionar la opción **"Transferencias"**.
3. Seleccionar **"A otras cuentas (Interbancaria)"**.
4. Ingresar un número de CCI válido, seleccionar el banco de destino y digitar un monto de **S/ 50.00 soles**.
5. Presionar el botón **"Continuar"** para ir a la pantalla de revisión.
6. En la pantalla de confirmación, presionar el botón **"Confirmar Transferencia"**.

## ❌ Resultado Esperado
La aplicación debería procesar la transacción, mostrar una pantalla de "Transferencia Exitosa" y generar el comprobante digital en formato PDF.

## 🔴 Resultado Actual
La aplicación se congela durante 2 segundos y se cierra por completo (*se cae*), enviando al usuario a la pantalla de inicio de su teléfono celular.

---

## 📎 Evidencias adjuntas (Simuladas)
* `[VIDEO_MUDO_CRASH.mp4]`: Grabación de pantalla desde el paso 4 hasta el cierre de la app.
* `[LOGS_ERROR_CONEXION.txt]`: Archivo de registro del sistema donde se muestra un error de desbordamiento de memoria (NullPointerException) al conectar con la API de la cámara de validación facial.

---

## 🧑‍💻 Notas del Tester (QA)
* El error se reprodujo **5 de 5 veces** intentadas bajo conexión Wi-Fi y datos móviles Claro 4G.
* El error ocurre únicamente cuando el monto ingresado supera los S/ 20.00 soles, montos menores se procesan correctamente.
*
