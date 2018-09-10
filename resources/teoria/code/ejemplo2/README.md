# Ejemplo 2

Hacer un programa que lea un archivo de texto caracter por caracter y lo imprima en pantalla.

**Solucion**: [read_caracter.c](read_caracter.c) es el codigo solucion. Por comodidad se muestra este codigo a continuación:

```C
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
  srand(time(NULL)); // Inicializacion del generador
  char filename[80];
  int tam;
  char ch;
  FILE *inputFile;
  printf("Ingrese el nombre de la cadena de ADN a generar: ");
  scanf("%[^\n]s",filename); // Formato para que la entrada pueda aceptar espacios
  inputFile = fopen(filename,"r");
  if (inputFile == NULL) {
    printf("Error al abrir el archivo %s\n", filename);
    exit(-1);
  }
  do {
    ch = getc(inputFile);
    printf("%c", ch);
  } while(ch != EOF);
  printf("\n");
  fclose(inputFile);
  exit(0);
}
```
