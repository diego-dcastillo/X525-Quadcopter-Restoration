# Diario de Ingeniería - X525 Quadcopter

## Fecha: 22/06/2026
**Fase:** Pruebas de Aviónica en Banco

### 🔧 Trabajos realizados hoy:
1. **Resolución de Protocolo Legacy (MAVLink):** * Se experimentó un fallo `Calibration FAILED` al intentar nivelar el acelerómetro de la APM 2.8 usando la versión moderna de Mission Planner.
   * *Solución:* [Escribe aquí brevemente cómo usamos la v1.3.56 para forzar la escritura de la EEPROM].
2. **Sincronización de Variadores (ESCs):**
   * [Explica brevemente cómo hiciste el reinicio con el gas al 100% para igualar el límite inferior de los motores].
3. **Mapeo de Radio FlySky:**
   * Se identificó un error de lectura en el canal de guiñada (Yaw).
   * *Solución:* [Escribe cómo cambiaste el cable del Canal 4 al pin correcto].

### 📊 Estado actual del sistema:
* Placa configurada y orientada correctamente.
* Los modos de vuelo han sido fijados por seguridad en `Stabilize`.
* **Prueba dinámica completada:** El bucle PID responde perfectamente a las inercias sin estar conectado al PC.