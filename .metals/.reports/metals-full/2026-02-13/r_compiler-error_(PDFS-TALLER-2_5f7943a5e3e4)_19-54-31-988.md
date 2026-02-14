error id: B15F37312AD4E3B0B7F29AEDBA022757
file:///C:/Users/aleja/OneDrive/Desktop/7%20SEMESTRE/PFSD/PrimerTercio/PDFS-TALLER-2/Main.scala
### java.lang.IndexOutOfBoundsException: 2

occurred in the presentation compiler.



action parameters:
offset: 8166
uri: file:///C:/Users/aleja/OneDrive/Desktop/7%20SEMESTRE/PFSD/PrimerTercio/PDFS-TALLER-2/Main.scala
text:
```scala
import java.time.LocalDate


//MODELO DE DATOS
// 1. Catálogo de Productos
case class Producto(idProducto: String, nombre: String, tasaInteres: Double)

// 2. Registro de Transacciones
case class Transaccion(id: String, producto: String, monto: Double, fecha: LocalDate, tipo: String, etiqueta: String, usuario:String)

// 3. Entidad de Usuario
case class Usuario(id: String, nombre: String,  ciudad: String, productos: List[String])

// 4. Reporte Consolidado
case class ReporteCliente(nombreCliente: String, saldoTotal: Double, alertaRiesgo: Boolean)

//DATASET


object BancoData {

    val productos = List(
        Producto("P001", "Tarjeta Crédito Infinite", 0.36),
        Producto("P002", "Tarjeta Crédito Clásica", 0.45),
        Producto("P003", "Tarjeta Crédito Oro", 0.38),
        Producto("P004", "Tarjeta Crédito Platinum", 0.29),
        Producto("P005", "Tarjeta Crédito Black", 0.44),
        Producto("P006", "Tarjeta Crédito LifeMiles", 0.41),
        Producto("P007", "Tarjeta Crédito Signature", 0.44)
    )

    val usuarios = List(
        Usuario("U001", "Carlos Pérez", "Bogotá", List("P001", "P002", "P007")),
        Usuario("U002", "Ana López", "Medellín", List("P001", "P004", "P003", "P006")),
        Usuario("U003", "Juan Lozano", "Cali", List("P001", "P004", "P003", "P006")),
        Usuario("U004", "Enrique Prieto", "Bogotá", List("P002", "P004", "P003", "P005")),
        Usuario("U005", "Manuel Medina", "Cartagena", List("P007", "P005")),
        Usuario("U006", "Maria Gomez", "Pereira", List("P006", "P003")),
        Usuario("U007", "Claudia Gonzalez", "Bogotá", List("P001", "P004", "P003", "P006", "P002")),
        Usuario("U008", "Nicolas Rodriguez", "Medellín", List("P001", "P004", "P003", "P006")),
        Usuario("U009", "Estefania Lemus", "Cali", List()),
        Usuario("U010", "Sandra Vasquez", "Bogotá", List( "P006"))
   )

    val transacciones = List(
    Transaccion("T1", "P001", 2500.0, LocalDate.now(), "CREDITO", "Nomina", "U009"),
    Transaccion("T2", "P001", 120.50, LocalDate.now(), "DEBITO", "Cajero", "U001"),
    Transaccion("T3", "P002", 450.0, LocalDate.now(), "DEBITO", "Supermercado", "U003"),
    Transaccion("T4", "P001", 50.0, LocalDate.now(), "DEBITO", "Transporte", "U005"),
    Transaccion("T5", "P003", 1500.0,LocalDate.now(), "CREDITO", "Transferencia", "U006"),
    Transaccion("T6", "P001", 3000.0, LocalDate.now(), "CREDITO", "Nomina", "U001"),
    Transaccion("T7", "P001", 800.0,LocalDate.now(), "DEBITO", "Alquiler", "U007"),
    Transaccion("T8", "P003", -100.0,LocalDate.now(), "DEBITO", "ERROR_SISTEMA", "U002"),
    Transaccion("T9", "P005", 50.0, LocalDate.now(), "DEBITO", "Cajero", "U008"),
    Transaccion("T10", "P001", 20.0, LocalDate.now(), "DEBITO", "Cajero", "U002"),
    Transaccion("T11", "P005", 500.0, LocalDate.now(),"DEBITO", "Cuota_Mes", "U001"),
    Transaccion("T12", "P003", 500.0, LocalDate.now(),"DEBITO", "Cuota_Mes", "U004"),
    Transaccion("T13", "P006", 2000.0, LocalDate.now(),"CREDITO", "Abono_Extra", "U009"),
    Transaccion("T14", "P003", 0.0, LocalDate.now(),"CREDITO", "", "U008"),
    Transaccion("T15", "P006", 500.0, LocalDate.now(),"DEBITO", "Cuota_Mes", "U001"),
    Transaccion("T16", "P002", 6000.0, LocalDate.now(),"DEBITO", "ALTO_RIESGO_LUJO", "U008"),
    Transaccion("T17", "P007", 150.0, LocalDate.now(),"DEBITO", "Restaurante", "U008"),
    Transaccion("T18", "P003", 1200.0, LocalDate.now(),"DEBITO", "Cuota_Mes", "U007"),
    Transaccion("T19", "P007", 45.0, LocalDate.now(),"DEBITO", "Suscripcion", "U005"),
    Transaccion("T20", "P007", 200.0, LocalDate.now(),"CREDITO", "Reembolso", "U004"),
    Transaccion("T21", "P001", 1100.0, LocalDate.now(),"CREDITO", "Nomina", "U008"),
    Transaccion("T22", "P001", 300.0, LocalDate.now(),"DEBITO", "Cajero", "U003"),
    Transaccion("T23", "P002", 15.0, LocalDate.now(),"DEBITO", "Cafe", "U005"),
    Transaccion("T24", "P001", 200.0, LocalDate.now(),"DEBITO", "Servicios", "U003"),
    Transaccion("T25", "P001", 400.0, LocalDate.now(),"CREDITO", "Transferencia", "U003"),
    Transaccion("T26", "P005", 500.0, LocalDate.now(),"DEBITO", "Cuota_Mes", "U004"),
    Transaccion("T27", "P006", 850.0, LocalDate.now(),"DEBITO", "Viajes", "U006"),
    Transaccion("T28", "P004", 12.0, LocalDate.now(),"DEBITO", "Transporte", "U002"),
    Transaccion("T29", "P005", 1100.0, LocalDate.now(),"CREDITO", "Nomina", "U008"),
    Transaccion("T30", "P006", 90.0, LocalDate.now(),"DEBITO", "Farmacia", "U008"),
    Transaccion("T31", "P004", 500.0, LocalDate.now(),"CREDITO", "Venta_Garage", "U002"),
    Transaccion("T32", "P013", 500.0, LocalDate.now(),"DEBITO", "Cuota_Mes", "U003"),
    Transaccion("T33", "P001", 200.0, LocalDate.now(),"DEBITO", "Cajero", "U004"),
    Transaccion("T34", "P002", 1200.0, LocalDate.now(),"DEBITO", "Electronica", "U009"),
    Transaccion("T35", "P001", 100.0, LocalDate.now(),"DEBITO", "Restaurante", "U001"),
    Transaccion("T36", "P003", 500.0, LocalDate.now(),"DEBITO", "Cuota_Mes", "U007"),
    Transaccion("T37", "P002", 30.0, LocalDate.now(),"DEBITO", "Cine", "U006"),
    Transaccion("T38", "P007", 1500.0, LocalDate.now(),"CREDITO", "Nomina", "U011"),
    Transaccion("T39", "P007", 250.0, LocalDate.now(),"DEBITO", "Gimnasio", "U008"),
    Transaccion("T40", "P006", 2000.0, LocalDate.now(),"CREDITO", "Abono_Capital", "U007"),
    Transaccion("T41", "P001", 45.0, LocalDate.now(),"DEBITO", "Transporte", "U004"),
    Transaccion("T42", "P004", 3000.0, LocalDate.now(),"DEBITO", "ALTO_RIESGO_JOYAS", "U008"),
    Transaccion("T43", "P001", 100.0, LocalDate.now(),"DEBITO", "Cajero", "U003"),
    Transaccion("T44", "P004", 500.0, LocalDate.now(),"DEBITO", "Cuota_Mes", "U005"),
    Transaccion("T45", "P002", 150.0, LocalDate.now(),"DEBITO", "Supermercado", "U002"),
    Transaccion("T46", "P001", 1100.0, LocalDate.now(),"CREDITO", "Nomina", "U004"),
    Transaccion("T47", "P005", 10.0, LocalDate.now(),"DEBITO", "App_Store", "U002"),
    Transaccion("T48", "P003", 500.0, LocalDate.now(),"DEBITO", "Cuota_Mes", "U009"),
    Transaccion("T49", "P005", 75.0, LocalDate.now(),"DEBITO", "Restaurante", "U003"),
    Transaccion("T50", "P999", 1000.0, LocalDate.now(),"CREDITO", "ERROR_PRODUCTO", "U012"),
    Transaccion("T51", "P005", 75.0, LocalDate.now(),"DEBITO", "Restaurante", "U003"),
    Transaccion("T52", "P005", 75.0, LocalDate.now(),"DEBITO", "Restaurante", "U003")
    )
}


//Fase 1: Saneamiento y limpieza de información
//Objetivo: Eliminar datos corruptos.
//1.	Crear una función que reciba la lista de 50 transacciones.
//2.	Filtrar solo aquellas con montos positivos.
//3.	Eliminar las transacciones duplicadas (omitiendo el identificador).
//4.	Eliminar las transacciones que no tengan usuarios válidos
def limpiarTransacciones(transacciones:  List[Transaccion], usuarios: List[Usuario] ): List[Transaccion] = {
  //filtrar montos positivos
  val filtroMontosPositivos = transacciones.filter(_.monto > 0) 
  //distinctBy para eliminar duplicados omitiendo el identificador, manteniendo el primer elemento encontrado
  val filtroTransaccionesUnicas = filtroMontosPositivos.distinctBy(t => (t.producto, t.monto, t.fecha, t.tipo, t.etiqueta, t.usuario))
  //obtener lista de usuarios validos
  val filtroUsuariosValidos = filtroTransaccionesUnicas.filter(t => usuarios.exists(u => u.id == t.usuario))
  //return con transaccions limpias
  filtroUsuariosValidos
}

//Fase 2: Enriquecimiento
//Objetivo: Normalizar categorías.
//1.	Asegurar que todas las etiquetas estén en Mayúsculas.
//2.	Si una transacción es de tipo "DEBITO" y supera los $3.000, cambiar su etiqueta a "ALTO_RIESGO".
//3.	Si una transacción es de tipo “CREDITO”, calcule el interés de cada compra
def enriqueser(transacciones: List[Transaccion]) = {
  transacciones.map{ t =>
    //Pasar las etiquetas a mayuscula
    val etiquetaMayus = t.etiqueta.toUpperCase()
    //Aplicar patter maching
    
    t match {
      //Cuando es DEBITO, se crea una copia al ser inmutable y se asigna la etiqueta
      case Transaccion(_, _, monto, _, "DEBITO", _, _) if monto > 3000 => t.copy(etiqueta = "ALTO_RIESGO")
      //Cuando es CREDITO
      case Transaccion(_, _, _@@, _, "DEBITO", _, _) =>
        val producto = BancoData.productos.find(_.idProducto == )

    }

  }
}

object Main extends App{
    println("Transacciones limpias: ")
    println(limpiarTransacciones(BancoData.transacciones, BancoData.usuarios))
}

```


presentation compiler configuration:
Scala version: 3.8.1-bin-nonbootstrapped
Classpath:
<WORKSPACE>\.scala-build\PDFS-TALLER-2_7943a5e3e4\classes\main [exists ], <HOME>\AppData\Local\Coursier\cache\v1\https\repo1.maven.org\maven2\org\scala-lang\scala3-library_3\3.8.1\scala3-library_3-3.8.1.jar [exists ], <HOME>\AppData\Local\Coursier\cache\v1\https\repo1.maven.org\maven2\org\scala-lang\scala-library\3.8.1\scala-library-3.8.1.jar [exists ], <HOME>\AppData\Local\Coursier\cache\v1\https\repo1.maven.org\maven2\com\sourcegraph\semanticdb-javac\0.10.0\semanticdb-javac-0.10.0.jar [exists ], <WORKSPACE>\.scala-build\PDFS-TALLER-2_7943a5e3e4\classes\main\META-INF\best-effort [missing ]
Options:
-Xsemanticdb -sourceroot <WORKSPACE> -Ywith-best-effort-tasty




#### Error stacktrace:

```
scala.collection.LinearSeqOps.apply(LinearSeq.scala:134)
	scala.collection.LinearSeqOps.apply$(LinearSeq.scala:38)
	scala.collection.immutable.List.apply(List.scala:83)
	dotty.tools.pc.InferCompletionType$.inferType(InferExpectedType.scala:94)
	dotty.tools.pc.InferCompletionType$.inferType(InferExpectedType.scala:62)
	dotty.tools.pc.completions.Completions.advancedCompletions(Completions.scala:543)
	dotty.tools.pc.completions.Completions.completions(Completions.scala:131)
	dotty.tools.pc.completions.CompletionProvider.completions(CompletionProvider.scala:139)
	dotty.tools.pc.ScalaPresentationCompiler.complete$$anonfun$1(ScalaPresentationCompiler.scala:197)
	scala.meta.internal.pc.CompilerAccess.withSharedCompiler(CompilerAccess.scala:149)
	scala.meta.internal.pc.CompilerAccess.$anonfun$1(CompilerAccess.scala:93)
	scala.meta.internal.pc.CompilerAccess.onCompilerJobQueue$$anonfun$1(CompilerAccess.scala:210)
	scala.meta.internal.pc.CompilerJobQueue$Job.run(CompilerJobQueue.scala:153)
	java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1144)
	java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:642)
	java.base/java.lang.Thread.run(Thread.java:1583)
```
#### Short summary: 

java.lang.IndexOutOfBoundsException: 2