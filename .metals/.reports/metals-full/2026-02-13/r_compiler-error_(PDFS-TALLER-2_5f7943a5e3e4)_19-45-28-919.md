error id: B15F37312AD4E3B0B7F29AEDBA022757
file:///C:/Users/aleja/OneDrive/Desktop/7%20SEMESTRE/PFSD/PrimerTercio/PDFS-TALLER-2/Main.scala
### java.lang.IndexOutOfBoundsException: 0

occurred in the presentation compiler.



action parameters:
offset: 1586
uri: file:///C:/Users/aleja/OneDrive/Desktop/7%20SEMESTRE/PFSD/PrimerTercio/PDFS-TALLER-2/Main.scala
text:
```scala
import java.time.LocalDate

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
      //Cuando es DEBITO
      case Transaccion(_@@, producto, monto, fecha, tipo, etiqueta, usuario)
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

java.lang.IndexOutOfBoundsException: 0