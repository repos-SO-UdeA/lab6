# Ejemplo 4

Hacer un programa que lea un archivo y lo muestre en pantalla. Este programa, debera mostrar ademas el numero de linea asociado. Por ejemplo, supongase que se tiene un archivo de texto llamado "frases.txt"

```
La vida es una obra teatral que no importa cuánto haya durado, sino lo bien que haya sido representada.
Séneca

Estar preparado es importante, saber esperar lo es aún más, pero aprovechar el momento adecuado es la clave de la vida.
Arthur Schnitzler

¡Qué pequeñas son mis manos…! En relación con todo lo que la vida ha querido darme.
Ramón J. Sénder

Todo el mundo trata de realizar algo grande, sin darse cuenta de que la vida se compone de cosas pequeñas.
Frank Clark

Sólo le falta el tiempo a quien no sabe aprovecharlo.
Jovellanos

Nuestra mayor gloria no está en no caer nunca, sino en levantarnos cada vez que caemos.
Confucio

La alegría cuanto más se gasta, más queda.
Ralph Waldo Emerson

Se necesitan dos años para aprender a hablar, y sesenta para aprender a callar.
Ernest Hemingway
```
Cuando se muestre en pantalla sera:

```
1   La vida es una obra teatral que no importa cuánto haya durado, sino lo bien que haya sido representada.
2   Séneca
3
4   Estar preparado es importante, saber esperar lo es aún más, pero aprovechar el momento adecuado es la clave de la vida.
5   Arthur Schnitzler
6
7   ¡Qué pequeñas son mis manos…! En relación con todo lo que la vida ha querido darme.
8   Ramón J. Sénder
9  
10  Todo el mundo trata de realizar algo grande, sin darse cuenta de que la vida se compone de cosas pequeñas.
11  Frank Clark
12
13  Sólo le falta el tiempo a quien no sabe aprovecharlo.
14  Jovellanos
15
16  Nuestra mayor gloria no está en no caer nunca, sino en levantarnos cada vez que caemos.
17  Confucio
18
19  La alegría cuanto más se gasta, más queda.
20  Ralph Waldo Emerson
21
22  Se necesitan dos años para aprender a hablar, y sesenta para aprender a callar.
23  Ernest Hemingway
```
**Solucion**: El archivo [read_linea.c](read_linea.c) contiene la sulucion. A continuacion se muestra este por comodidad:

```C
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
  char filename[80];
  char line[201];
  int numLinea = 1;
  FILE *iF;
  printf("Ingrese el nombre del archivo: ");
  fflush(stdin);
  scanf("%[^\n]s",filename); // Formato para que la entrada pueda aceptar espacios
  iF = fopen(filename,"r");
  if (iF == NULL) {
    printf("Error al abrir el archivo %s\n", filename);
    exit(-1);
  }
  while(fgets(line, 201, iF)!=NULL) {
    printf("%-5d",numLinea++);
    printf("%s",line);
  }
  fclose(iF);
  exit(0);
}
```
