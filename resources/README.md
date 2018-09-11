# Ejercicios de repaso

**Manejo de archivos**: Hacer un programa que permita obtener las siguientes estadisticas de un archivo de texto:
1. Numero de caracteres del archivo.
2. Numero de lineas.
3. Numero de palabras (cada palabra es separada por un whitespace o una nueva linea).
4. Numero de whitespaces (caracteres espacio ' ' o tab '\n')
5. Numero de letras en mayuscula.
6. Numero de letras en minuscula.
7. Numero de digitos.

El ejecutable (compilelo como textstats) debera complir los siguientes requerimientos:
1. Recibir argumentos de entrada por linea de comandos. Cada uno de los argumentos sera un archivo el nombre de un archivo de entrada. Por ejemplo, suponga que tiene un archivo llamado **texto1.txt**, de modo que la invocación del ejecutable será **./textstats texto1.txt**. Asi mismo se espera una salida como la siguiente.

```
./textstats texto1.txt
Obteniendo estadisticas...
- texto1.txt --> generando reporte texto1_stats.txt
Estadisticas culminadas
```

2. Suponiendo que el archivo de entrada **texto1.txt** tuviera un contenido como el mostrado a continuación.

```
1234 56
hello this is a word
Finally this line !
```

El archivo generado (**texto1_stats.txt**) deberá tener un contenido como el siguiente:

```
chars: 49 
words: 11 
lines: 3 
whitespaces: 8
uppercase: 1 
lowercase: 30 
digits: 6
```

El nombre del archivo de texto asociado a las estadisticas, deberá contener el nombre del archivo antes de la extención seguido por la cadena **stats.txt**. Asi, si el archivo se llamara file.dat, el archivo generado asociado a las estadisticas **seria file_stats.dat**. 

3. La información asociada a las estadisticas deberá estar agrupada en una estructura en la que cada uno de los miembros hará referencia una estadistica particular.

**Tips y recomendaciones**:
1. Recuerde, para la solución de este problema el tema estrella es el manejo de archivos. En caso de olvidar cosas vistas en el laboratorio, se recomienda que entienda los ejemplos vistos antes de empezar ([teoria](https://github.com/repos-SO-UdeA/lab6/tree/master/resources/teoria) y [ejemplos resueltos](https://github.com/repos-SO-UdeA/lab6/tree/master/resources/teoria/code)). 
2. Para el paso de argumentos por linea de comandos se recomienda que haga un repaso de ejemplos mas basicos. A continuación se muestran los codigos para facilitar el trabajo:

**Codigo 1**:

```C
#include <stdio.h>
#include <stdlib.h>
#define N 20

int edad_en_meses(int);

int main(int argc, char *argv[])
{
  int edad = atoi(argv[1]);
  int meses = edad_en_meses(edad);
  printf("Edad %d \n", meses);
  return 0;
}

int edad_en_meses(int anios){
  int mes = anios * 12; 
  return mes;
}
```
**Codigo 2**:

```C
#include "stdio.h"
#include "string.h"

// Codigo tomado de: http://bluefever.net/Downloads/BeginC/ch51.c

int main(int argc, char *argv[]) {	
  printf("\nmain() : argc : %d \n", argc);
  int index = 0;
  for(index = 0; index < argc; ++index) {
    // printf("main() : argv[%d] : %s\n",index,argv[index]);
    if( strncmp( argv[index], "debug", 5) == 0 ) {
      printf("main() : PROGRAM DEBUG MODE\n");
    } else if ( strncmp( argv[index], "-file", 5) == 0 ) {
      printf("main() : PROGRAM READ FILENAME : %s\n", argv[index + 1]);
    }
  }
  printf("\nmain(): Program Quit\n");
  return 0;
}
```

Su trabajo consistirá en entender y adaptar codigo como este al problema.

3. Crear una estructura en la cual cada uno de los campos se asocie a la información a desplegar. Se recomienda en caso de ser necesario repasar la [teoria](https://github.com/repos-SO-UdeA/laboratorios/blob/master/lab1/teoria/parte4/estructuras.ipynb), el [taller resuelto](https://github.com/repos-SO-UdeA/lab3/tree/master/talleres/parte_teorica2) y los [ejercicios de programación resueltos](https://github.com/repos-SO-UdeA/lab3/tree/master/talleres/ejercicios_resueltos).
4. Enfoquese en hacer el programa lo mas modular posible creando funciones que manejen incluso estructuras. Recuerde los ejemplos analizados en el laboratorio donde se pasan o se retornan estructuras en funciones.
