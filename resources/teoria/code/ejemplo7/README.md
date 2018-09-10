# Ejemplo 7

Hacer un programa que abra un archivo que contiene una cadena de ADN y genere un archivo de salida con el numero de cada uno de los caracteres el alfabeto genetico ('A', 'G', 'G' y 'C') separados por espacio. El nombre del archivo sera **inventario_nombreArchivo**. Asi por ejemplo si se tiene un archivo con el siguiente nombre **secuencia.dat** con el siguiente contenido:

```
AGCTTTTCATTCT
```

La salida sera un archivo llamado **inventario_secuencia.dat** y su contenido será el siguiente:

```
2 1 7 2
```

**Solucion**: Este ejercicio en el ya se realizo en el [ejemplo 3](../ejemplo3) empleando **putc**, pero para propositos de comparacion se va a realizar con **fprintf**. En [read_write_line2.c](read_write_line2.c) se muestra el codigo solución, por comodidad a continuación tambien aparece.

```C
#include <stdio.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main() {
  char inFilename[80];
  char outFilename[80] = "inventario_";
  char cntS[10];
  int tam;
  char ch;
  int cnt[] = {0,0,0,0};
  FILE *inFile;
  FILE *outFile;
  int i, j;
  printf("Ingrese el nombre de la cadena de ADN a generar: ");
  scanf("%[^\n]s",inFilename); // Formato para que la entrada pueda aceptar espacios
  inFile = fopen(inFilename,"r");
  if (inFile == NULL) {
    printf("Error al abrir el archivo %s\n", inFilename);
    exit(-1);
  }
  do {
    ch = getc(inFile);
    if(ch == 'A') {
      cnt[0]++;
    }
    else if(ch == 'G') {
      cnt[1]++;
    }
    else if(ch == 'T') {
      cnt[2]++;
    }
    else if(ch == 'C') {
      cnt[3]++;
    }
  } while(ch != EOF);
  fclose(inFile);
  strcat(outFilename,inFilename);
  outFile = fopen(outFilename,"w");
  for(i = 0; i < 4; i++) {
    fprintf(outFile, "%d ", cnt[i]);    

  }
  fclose(outFile);
  exit(0);
}
```
