## Fase 4: Preguntas

### 1. Si el dataset creciera de 50 registros a 50 millones en un sistema distribuido,  ¿la implementación realizada sería la ideal? ¿Por qué?

**No, no sería la ideal por las siguientes razones:**

#### Limitaciones de la implementación actual:

1. **Datos en memoria local**  
   - El dataset se encuentra almacenado localmente en memoria
   - 50 millones de registros sobrepasarían la capacidad de la JVM
   - **Solución necesaria:** Base de datos externa

2. **Procesamiento secuencial**  
   - Las transacciones se ejecutan en un solo hilo sin concurrencia
   - El rendimiento sería muy lento
   - **Solución necesaria:** Procesamiento paralelo o distribuido 

3. **Múltiples recorridos de datos**  
   - Varias funciones recorren la misma estructura repetidamente
   - Consume recursos innecesariamente
   - **Solución necesaria:** Optimizar con un solo recorrido

4. **Ejecucion centralizada**  
   - Todo se ejecuta en una única máquina
   - No hay distribución de carga
   - **Solución necesaria:** Sistema distribuido

#### Ejemplo del problema actual:

```scala
// ACTUAL: Multiples recorridos sobre los mismos datos
val transaccionesLimpias = limpiarTransacciones(transacciones, usuarios)      // Recorrido 1
val transaccionesEnriquecidas = enriqueser(transaccionesLimpias)              // Recorrido 2
val (movimientos, utilidad, ...) = agregarTransacciones(transaccionesEnriquecidas) // Recorrido 3
```

### 2. Si un proceso de cierre de mes falla a mitad de camino, ¿por qué es más fácil recuperarse usando el paradigma funcional que el imperativo?

**Respuesta:** Debido a la **inmutabilidad** y la **ausencia de efectos secundarios**, el paradigma funcional tiene ventajas significativas en recuperación de fallos.

#### Ventajas del paradigma funcional:

1. **Datos originales intactos**  
   - Los datos nunca se modifican, siempre se crean copias
   - En caso de fallo, los datos originales permanecen intactos

2. **Sin estado mutable**  
   - No hay estado intermedio corrupto
   - Cada transformación es independiente

3. **Idempotencia**  
   - Ejecutar la misma función N veces produce el mismo resultado
   - Reintento seguro

4. **No requiere rollback**  
   - No hay estado anterior que deshacer
   - Solo es necesario reintentar desde el punto de fallo

#### Tabla comparativa:

| Aspecto | Imperativo | Funcional |
|---------|-----------|-----------|
| **Datos originales** | Modificados (mutables) | Intactos (inmutables) |
| **Estado intermedio** | Impredecible, puede estar corrupto | No existe estado mutable |
| **Recuperación** | Rollback complejo + limpiar + reanudar | Solo reintentar desde cero |
| **Tiempo perdido** | tiempo del rollback y reintento | Checkpoint y reanudar |
| **Complejidad código** | Alta (logs, rollback, cleanup) | Baja (retry simple) |
| **Garantías** | Difícil garantizar consistencia | Consistencia garantizada |
| **Testing** | Complejo (simular estados corruptos) | Simple (funciones puras) |