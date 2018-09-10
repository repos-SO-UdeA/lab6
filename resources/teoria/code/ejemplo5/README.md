# Ejemplo 5

Hacer un programa que lea una cadena de ADN de un archivo cualquiera y genere la cadena complementaria en otro archivo con **complemento_nombreArchivo** como nombre. Tenga en cuenta que en una cadena de ADN los pares complementarios son: 'A' con 'T' y 'G' con 'C'. Por ejemplo, si la cadena se llama **adn1.txt** y tiene el siguiente contenido:

```
AGTTTCTTAAGCCG
```

El resultado será una cadena llamada **complemento_adn1.txt** con el siguiente contenido:

```
TCAAAGAATTCGGC
```

**Solución**: El archivo [read_write_line1.c](read_write_line1.c) contiene la sulucion. A continuacion se muestra este por comodidad:

```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void complementar(char *cad);

int main() {
  char inFilename[80];
  char outFilename[80] = "complemento_";
  char adn_string[21];
  FILE *inFile;
  FILE *outFile;
  printf("Ingrese el nombre de la cadena de ADN a generar: ");
  fflush(stdin);
  scanf("%[^\n]s",inFilename); // Formato para que la entrada pueda aceptar espacios
  strcat(outFilename,inFilename);
  inFile = fopen(inFilename,"r");
  outFile = fopen(outFilename,"w");
  if (inFile == NULL) {
    printf("Error al abrir el archivo %s\n", inFilename);
    exit(-1);
  }
  while(fgets(adn_string, 21, inFile)!=NULL) {
    complementar(adn_string);
    fputs(adn_string, outFile);
  }
  fclose(inFile);
  fclose(outFile);
  exit(0);
}

void complementar(char *cad) {
  while(*cad != '\0') {
    switch(*cad) {
      case 'A':
        *cad = 'T';
        break;
      case 'T':
        *cad = 'A';
        break;
      case 'G':
        *cad = 'C';
        break;
      case 'C':
        *cad = 'G';
        break;
    }
    cad++;
  }
}
```
