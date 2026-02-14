error id: file:///C:/Users/aleja/OneDrive/Desktop/7%20SEMESTRE/PFSD/PrimerTercio/PDFS-TALLER-2/Main.scala:
file:///C:/Users/aleja/OneDrive/Desktop/7%20SEMESTRE/PFSD/PrimerTercio/PDFS-TALLER-2/Main.scala
empty definition using pc, found symbol in pc: 
empty definition using semanticdb
empty definition using fallback
non-local guesses:
	 -t/toUpperCase.
	 -t/toUpperCase#
	 -t/toUpperCase().
	 -scala/Predef.t.toUpperCase.
	 -scala/Predef.t.toUpperCase#
	 -scala/Predef.t.toUpperCase().
offset: 1460
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
    val mayus = t.to@@UpperCase
    //Aplicar patter maching
    
    t match {
      //Cuando es DEBITO
      case t.etiqueta == "DEBITO" %% t.monto > "3000" => t.etiqueta = "ALTORIESGO" 
    }

  }
}

object Main extends App{
    println("Transacciones limpias: ")
    println(limpiarTransacciones(BancoData.transacciones, BancoData.usuarios))
}

```


#### Short summary: 

empty definition using pc, found symbol in pc: 