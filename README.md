*Antes de empezar nuestro **curso** , conozcamos un poco de la **herramienta***

<img src="IMAGENES\Logo Excel Macros.png" width="400" height="200">

# Introducción a Excel y VBA Macros

**Microsoft Excel** es una herramienta poderosa y versátil que se utiliza ampliamente para la creación, organización y análisis de datos. A medida que trabajas con conjuntos de datos más grandes y complejos, es fundamental optimizar tu flujo de trabajo para ahorrar tiempo y minimizar errores. Aquí es donde entran en juego las macros y VBA.

## ¿Qué es una macro en Excel?

Una **macro en Excel** es una serie de instrucciones y comandos que se pueden grabar y automatizar para realizar tareas repetitivas de manera eficiente. Imagina que tienes que realizar la misma secuencia de acciones en una hoja de cálculo una y otra vez, como aplicar un formato específico, realizar cálculos o generar informes. En lugar de hacerlo manualmente cada vez, puedes grabar una macro que reproduzca esas acciones automáticamente.

## Introducción a VBA (Visual Basic for Applications)

**VBA** es un lenguaje de programación que se integra directamente en las aplicaciones de Microsoft Office, incluido Excel. Te permite crear scripts personalizados para automatizar tareas, manipular datos y personalizar la funcionalidad de Excel. Con VBA, puedes tener un control mucho más avanzado sobre lo que puedes lograr con las macros.

## Ventajas de usar macros y VBA en Excel

1. **Eficiencia:** Automatizar tareas repetitivas ahorra tiempo y reduce el riesgo de errores humanos.
2. **Personalización:** Puedes adaptar Excel a tus necesidades específicas creando funciones y herramientas personalizadas.
3. **Consistencia:** Las macros y scripts garantizan que las tareas se realicen de la misma manera cada vez.
4. **Análisis avanzado:** Puedes procesar y analizar grandes cantidades de datos de manera más rápida y efectiva.
5. **Compatibilidad:** Las macros y VBA son ampliamente utilizadas en el entorno empresarial, lo que te brinda habilidades valiosas en el mercado laboral.

## Primeros pasos con macros y VBA

1. **Grabar una macro:** Puedes grabar una secuencia de acciones en Excel y luego reproducirla con un solo clic. Esto es especialmente útil para tareas sencillas.
2. **Editar una macro:** Después de grabar una macro, puedes editar el código VBA resultante para ajustar y personalizar la funcionalidad.
3. **Crear macros desde cero:** Si las tareas son más complejas, puedes aprender a escribir tus propias macros desde cero utilizando el lenguaje VBA.

## Conclusión

Las macros y VBA en Excel te brindan el poder de automatizar tareas, mejorar la eficiencia y tener un control más preciso sobre tus hojas de cálculo. A medida que explores este mundo, descubrirás que hay un sinfín de posibilidades para personalizar Excel y convertirte en un usuario más eficiente y capaz. ¡Prepárate para desbloquear el potencial oculto de tus datos con las macros y VBA en Excel!

## PruebasBasicas()
*Este subprocedimiento contiene ejemplos que demuestran cómo trabajar con celdas, hojas y libros en Excel utilizando VBA.*

```vbnet
Sub PruebasBasicas()

    ' ****************************** CELDAS ***********************************

    ' Usando el objeto "Range" (Rango)

    ' Seleccionar la celda nombrada entre comillas
    Range("A5").Select

    ' Seleccionar un rango simple de celdas mencionadas entre comillas
    Range("A5:A14").Select

    ' Seleccionar celdas individuales no contiguas mencionadas entre comillas
    Range("A5,B7,C9").Select

    ' Seleccionar un rango formado por subrangos de celdas no contiguas nombradas entre comillas
    Range("A5:B5,A7:C7,A9:C10").Select

    -----------------------------------------------------------------------------
    
    ' Usando el objeto "Cells" (Celda)

    ' Seleccionar la celda donde coincide la FILA 1 y la COLUMNA 1 (A1)
    Cells(1, 1).Select

    ' Seleccionar la celda donde coincide la FILA 5 y la COLUMNA 1 (A5)
    Cells(5, 1).Select

    ' Seleccionar A1:A14 usando el objeto Cells (Celdas)
    Range(Cells(5, 1), Cells(14, 1)).Select

    ' Propiedad ACTIVECELL (Celda Activa)

    ' Poner en negrita la fuente de la celda activa
    ActiveCell.Font.Bold = True

    -----------------------------------------------------------------------------
    
    'La propiedad OFFSET (Desplazamiento)

    'Selecciona el desplazamiento de una celda desde una celda específica
    'se escribe OFFSET (FILA, COLUMNA)...
    'Los números negativos desplazan hacia ARRIBA (FILA), o IZQUIERDA (COLUMNA)
    Range("A5").Offset(1, 0).Select
    'También aplica a la celda activa
    ActiveCell.Offset(0, 1).Select

    ------------------------------------------------------------------------------

    'La propiedad END (moviéndose dinámicamente)

    'MOVERSE A LA DERECHA
    'Moverse hasta el final del rango
    Range("A5").Select
    Selection.End(xlToRight).Select
    'Lo mismo pero estableciendo la celda inicial en la misma línea de código
    Range("A5").End(xlToRight).Select
    'Lo mismo pero invocando la celda activa
    ActiveCell.End(xlToRight).Select

    'MOVERSE A LA IZQUIERDA
    'Moverse hasta el comienzo del rango
    Range("D5").Select
    Selection.End(xlToLeft).Select
    'Lo mismo pero estableciendo la celda inicial en la misma línea de código
    Range("D5").End(xlToLeft).Select
    'Lo mismo pero invocando la celda activa
    ActiveCell.End(xlToLeft).Select

    'MOVERSE HACIA ARRIBA
    'Moverse hasta la parte superior del rango
    Range("D5").Select
    Selection.End(xlUp).Select
    'Lo mismo pero estableciendo la celda inicial en la misma línea de código
    Range("D5").End(xlUp).Select
    'Lo mismo pero invocando la celda activa
    ActiveCell.End(xlUp).Select

    'MOVERSE HACIA ABAJO
    'Moverse hasta la parte inferior del rango
    Range("D5").Select
    Selection.End(xlDown).Select
    'Lo mismo pero estableciendo la celda inicial en la misma línea de código
    Range("D5").End(xlDown).Select
    'Lo mismo pero invocando la celda activa
    ActiveCell.End(xlDown).Select

    'Seleccionar la última FILA
    Range("A1048576").End(xlUp).Select

    'Seleccionar la primera fila vacía después de la última fila
    Range("A1048576").End(xlUp).Offset(1, 0).Select

    'Selección de Rango Dinámico

    'Seleccionando hacia ABAJO
    'Seleccionar desde una celda específica (A5), hasta...
    '...la de más ABAJO del rango.
    Range("A5").Select
    Range(Selection, Selection.End(xlDown)).Select
    'Lo mismo, pero usando "Range("A5")" COMO la selección
    Range(Range("A5"), Range("A5").End(xlDown)).Select
    'Lo mismo, pero usando LA CELDA ACTIVA como la selección
    '...ActiveCell es cualquier celda que actualmente está seleccionada
    Range(ActiveCell, ActiveCell.End(xlDown)).Select

    'Seleccionando hacia ARRIBA
    'Seleccionar desde una celda específica (A5), hasta...
    '...la de más ARRIBA del rango
    Range("A10").Select
    Range(Selection, Selection.End(xlUp)).Select
    'Lo mismo, pero usando "Range("A5")" COMO la selección
    Range(Range("A10"), Range("A10").End(xlUp)).Select
    'Lo mismo, pero usando LA CELDA ACTIVA como la selección
    '...ActiveCell es cualquier celda que actualmente está seleccionada
    Range(ActiveCell, ActiveCell.End(xlUp)).Select

    'Seleccionando hacia la DERECHA
    'Seleccionar desde una celda específica (A5), hasta...
    '...la de más a la DERECHA del rango
    Range("A5").Select
    Range(Selection, Selection.End(xlToRight)).Select
    'Lo mismo, pero usando "Range("A5")" COMO la selección
    Range(Range("A5"), Range("A5").End(xlToRight)).Select
    'Lo mismo, pero usando LA CELDA ACTIVA como la selección
    '...ActiveCell es cualquier celda que actualmente está seleccionada
    Range(ActiveCell, ActiveCell.End(xlToRight)).Select

    'Seleccionando hacia la IZQUERDA
    'Seleccionar desde una celda específica (A5), hasta...
    '...la de más a la IZQUIERDA del rango
    Range("D5").Select
    Range(Selection, Selection.End(xlToLeft)).Select
    'Lo mismo, pero usando "Range("A5")" COMO la selección
    Range(Range("D5"), Range("D5").End(xlToLeft)).Select
    'Lo mismo, pero usando LA CELDA ACTIVA como la selección
    '...ActiveCell es cualquier celda que actualmente está seleccionada
    Range(ActiveCell, ActiveCell.End(xlToLeft)).Select

   ----------------------------------------------------------------------------

    'La propiedad CURRENT REGION (Región Actual)

    'Selecciona el rango actual alrededor de la selda elegida
    Range("A5").CurrentRegion.Select
    'Hace lo mismo utilizando CELLS
    Cells(5, 1).CurrentRegion.Select
    'Hace lo mismo basado en la celda actualmente activa
    ActiveCell.CurrentRegion.Select

   --------------------------------------------------------------------------------

    'Método SELECT Vs. método ACTIVATE
    'A veces ambos métodos hacen lo mismo
    'Haz una selección desde A5 hasta A14  luego ejecuta este código
    Range("A9").Select
    'Haz una selección desde A5 hasta A14  luego ejecuta este código
    Range("A9").Activate
    'A9 se transforma en la celda activa, sin salir de la selección del rango


    '******************************** HOJAS ***************************************

    ' Propiedades NEXT (siguiente) y PREVIOUS (anterior)

    ' Moverse entre hojas
    ' Moverse desde la hoja activa hasta la siguiente a la DERECHA
    ActiveSheet.Next.Select
    ' Moverse desde la hoja activa hasta la siguiente a la IZQUIERDA
    ActiveSheet.Previous.Select

    'Seleccionar una hoja usando el nombre VB CODE (Definido en la ventana de “propiedades”) Hoja2.Select

    ---------------------------------------------------------------------------------
    
    'Objeto SHEETS Vs. objeto WORKSHEETS
    'Una WORKSheet es la hoja regular de EXCEL
    'Una SHEET es CUALQUIER tipo de hoja
    'Ve a Excel, presiona F11 para agregar un gráfico, y luego ejecuta este código

    'Esto funciona porque "Sheets" reconoce a todos los elementos “hoja”
    Sheets("Sales Data").Select
    'Esto funciona porque "Sheets" reconoce a todos los elementos “hoja”
    Sheets("Gráfico1").Select
    'Esto funciona porque "Sales Data" es una hoja regular de Excel
    Worksheets("Sales Data").Select
    'Esto NO funciona porque "Gráfico1" NO es una hoja regular de Excel
    Worksheets("Gráfico1").Select

    '******************************** LIBROS****************************************

    'Activar el libro actual (donde reside el código)
    ThisWorkbook.Activate

    'Activar el libro mencionado (no reconoce mayúsculas, se puede omitir la extensión)
    Workbooks("Mi-Libro-de-Macros").Activate
    'Activa el libro en la posición de índice 1
    'Observa que el índice número 1 es el orden en que abriste los libros
    Workbooks(1).Activate

    'NOTA: debes ACTIVAR un libro diferente, antes de poder seleccionar sus hojas
    'Esto funcionará bien...
    'Activa el libro mencionado (no reconoce mayúsculas)
    Workbooks("Libro1").Activate     'Activa el otro libro...
    Sheets("Hoja2").Select         'LUEGO selecciona la hoja (NOTA: NO necesitas especificar
                                        'el nombre del libro otra vez ya que ahora es el libro ACTIVO)
    'Esto NO funcionará...
    Workbooks("Libro1").Sheets("Hoja2").Select


    '*********************** ESCRIBIR EN LAS CELDAS *******************************

    'La propiedad VALUE (Valor)

    'Escribir en una celda usando su ubicación
    Range("A1").Value = "Hola Mundo"

    'Escribir en un rango usando su ubicación
    Range("B2:G11").Value = "Hola Mundo 2"

    'Escribir en una celda usando CELLS
    Cells(13, 1).Value = "Esto es A13"

    'Ingresar un número (NOTA: no se necesitan las comillas)
    Range("A1").Value = 1234

    'Escribir en una celda usando la nombre código VB de la hoja y la ubicación de la celda
    DV.Range("A1").Value = "¡Hice esto desde la hoja 1!"

    'Escribir en una celda de otro libro (observa la jerarquía)
    Workbooks("Libro1.xlsx"). _
        Sheets("Hoja1"). _
            Range("A1").Value = "¡Hice esto desde otro Libro!"

    'Escribir el valor de una variable en una celda
    'Aquí defines la variable
    MiPrimeraVariable = "Es un lindo día :)"
    'Escribe ese valor en la celda A1
    Range("A1").Value = MiPrimeraVariable


    '************ LEER Y ESCRIBIR VALORES EN LAS CELDAS ************

    'Escribir el valor de una celda en otra celda
    Range("B1").Value = Range("A1").Value

    'Escribir el valor de un rango en otro rango
    Range("B1:B5").Value = Range("A1:A5").Value

    'Escribir el valor de una variable en una celda
    'La variable contendrá el valor de la celda activa
    MiSegundaVariable = ActiveCell.Value
    'Escribe ese valor en la celda G18
    Range("G18").Value = MiSegundaVariable

    '******************* PROPIEDADES UTILIZADAS FRECUENTEMENTE ******************

    'La propiedad FONT (Fuente)

    'Establecer la fuente de A1 como negrita
    Range("A1").Font.Bold = True
    Range("A1").Font.Bold = False

    'Establecer la fuente de A1 como negrita
    Range("A1").Font.FontStyle = "Bold"
    'Establecer la fuente de A1 como regular
    Range("A1").Font.FontStyle = "Regular"
    'Establecer más de un atributo usando FontStyle
    Range("A1").Font.FontStyle = "Bold italic"


    'La propiedad INTERIOR
    Range("A1").Interior.Color = vbRed


    '*********************MÁS PROPIEDADES ÚTILES **********************************

    'La propiedad ADDRESS (Ubicación)

    'Obtener la ubicación de la celda activa
    LaUbicaciónDeMiCelda = ActiveCell.Address

    'Obtener la ubicación de la última celda del rango DEBAJO de A5
    LaUbicaciónDeLaUltimaFila = Range("A5").End(xlDown).Address

    'Obtener la ubicación de la última celda en el rango a la DERECHA de A5
    LaUbicaciónDeLaUltimaColumna = Range("A5").End(xlToRight).Address

    'Obtener la ubicación de la última fila comenzando desde abajo y hacia arriba
    LaUbicaciónDeLaFilaFinal = Range("A1048576").End(xlUp).Address

    'Obtener la ubicación de la primera fila vacía DESPUÉS de la última fila
    LaPrimeraUbicacionVacia = Range("A1048576").End(xlUp).Offset(1, 0).Address

    ---------------------------------------------------------------------------------

    'La Propiedad ROW (Fila)

    'Obtener el número de fila de la celda activa
    NúmeroDeFila = ActiveCell.Row

    'Obtener el número de la última fila de un rango, moviendo hacia abajo desde A5
    MiUltimaFila = Range("A5").End(xlDown).Row

    ----------------------------------------------------------------------------------

    'La propiedad COLUMN (Columna)

    'Obtener el numero de columna de la celda activa
    NumeroDeColumna = ActiveCell.Column

    'Obtener el número de la última fila de un rango, moviendo hacia la derecha desde A5
    MiUltimaColumna = Range("A5").End(xlToRight).Column

    ------------------------------------------------------------------------------------

    'Obtener la LETRA de la columna de la celda activa
    LaLetraDeLaColumna = Split(ActiveCell.Address, "$")(1)

    'Obtener el número de fila de la celda activa (método alternativo)
    NumeroDeFila = Split(ActiveCell.Address, "$")(2)

    '*************************** AÚN MÁS PROPIEDADES ÚTILES ***************************

    'Obtener el nombre de usuario de Windows
    MiNombreDeUsuario = Environ$("UserName")

    'Obtener el nombre del libro activo (Nota: “activo” no necesariamente es ESTE libro)
    NombreDelLibroActivo = ActiveWorkbook.Name

    'Obtener el nombre de ESTE libro (No necesariamente el libro activo)
    NombreDeEsteLibro = ThisWorkbook.Name

    'Obtener la ruta del libro activo
    MiRuta = ActiveWorkbook.Path

    'Obtener la ruta de este libro
    MiRuta = ThisWorkbook.Path

    'Obtener la ruta del libro activo y adjuntar el nombre del libro
    NombreCompletoDelLibro = ActiveWorkbook.FullName

    'Obtener la ruta a este libro y adjuntar el nombre del libro
    NombreCompletoDelLibro = ThisWorkbook.FullName

    'Obtener el nombre de la hoja actual
    NombreDeLaHoja = ActiveSheet.Name

    'Obtener la ubicación de la celda activa
    MiCelda = ActiveCell.Address

    'Obtener distintas propiedades del libro activo
    'Nombre de la aplicación
    DistintasPropiedades = ActiveWorkbook.BuiltinDocumentProperties("Application Name")
    'Autor
    DistintasPropiedades = ActiveWorkbook.BuiltinDocumentProperties("Author")
    'Compañía
    DistintasPropiedades = ActiveWorkbook.BuiltinDocumentProperties("Company")
    'Fecha de creación
    DistintasPropiedades = ActiveWorkbook.BuiltinDocumentProperties("Creation Date")
    'Último autor
    DistintasPropiedades = ActiveWorkbook.BuiltinDocumentProperties("Last Author")
    'Última fecha de grabación
    DistintasPropiedades = ActiveWorkbook.BuiltinDocumentProperties("Last Save Time")

    'Obtener el conteo del número total de hojas del libro
    MiCuenta = ActiveWorkbook.Sheets.Count      'o
    MiCuenta = Sheets.Count                     '...si sabes que estás en el libro correcto

    'Obtener el índice de la hoja actual
    ElNumeroDeHoja = ActiveSheet.Index

    'Obtener el conteo del número de libros abiertos
    ConteoDeLibrosAbiertos = Application.Workbooks.Count

    '****************************** ABRIR Y CERRAR LIBROS *******************************
    'Abriendo libros

    'Abrir un libro
    Workbooks.Open Filename:="C:\Users\Fede\Escritorio\Libro1.xlsx"

    'Abrir un libro en modo solo lectura
    Workbooks.Open Filename:= _
        "C:\Users\Fede\Escritorio\Libro1.xlsx", ReadOnly:=True

    'Abrir un libro protegido con contraseña
    Workbooks.Open Filename:= _
        "C:\Users\Fede\Escritorio\LibroProtegido.xlsx", Password:="hola"
        
    'Parámetros adicionales cuando abres libros
    'Separar con comas (se pueden combinar)
    '
    'UpdateLinks:=0         ‘NO actualiza ningúna referencia o link externo (por defecto)
    'UpdateLinks:=3         ‘SI actualiza referencias externas o links
    '
    'Notify:=True           ‘Si está protegido, lo abre como solo lectura, y notifica cuando se libera
    'Notify:=False          ‘Por defecto… no hace lo anterior
    '
    'AddtoMRU:=True         'Agrega el archivo abierto a la lista de "Usados Recientemente" 'AddtoMRU:=False        'No lo agrega

    ------------------------------------------------------------------------------------
    'Cerrar libros

    'Cierra el libro activo (preguntará si guardas los cambios) about changes)
    ActiveWorkbook.Close

    'Cierra los libros según índice (el orden en que fue abierto)
    Workbooks(1).Close

    'Cierra el libro activo (guardará los cambios)
    ActiveWorkbook.Close SaveChanges:=True

    'Cierra el libro activo (NO guardará los cambios)
    ActiveWorkbook.Close SaveChanges:=False
End Sub ```


Tarea

Tu tarea consiste en realizar 3 subrutinas: `PintaArcoIris`, `EscribirArcoiris` y `ColorearFuenteArcoIris`.

1. **PintaArcoIris**: En esta subrutina, debes pintar el interior de 7 celdas con 7 colores distintos, creando un arco iris.

2. **EscribirArcoiris**: En esta subrutina, debes escribir dentro de las 7 celdas el nombre del color correspondiente.

3. **ColorearFuenteArcoIris**: En esta subrutina, debes cambiar el color de fuente de la letra en las celdas.

### Recursos

- [Posible Solución en Video](VIDEOS/Macros%201.mp4)
- [Conceptos y Guía Adicional](README.md)


