# Ejemplo 3

Hacer un programa que abra un archivo que contiene una cadena de ADN y genere un archivo de salida con el numero de cada uno de los caracteres el alfabeto genetico ('A', 'G', 'G' y 'C') separados por espacio. El nombre del archivo sera **inventario_nombreArchivo**. Asi por ejemplo si se tiene un archivo con el siguiente nombre **secuencia.dat** con el siguiente contenido:

```
AGCTTTTCATTCT
```

La salida sera un archivo llamado **inventario_secuencia.dat** y su contenido será el siguiente:

```
2 1 7 2
```

**Solución**: En [read_write_caracter.c](read_write_caracter.c) se muestra el codigo solución, por comodidad a continuación tambien aparece:

```C
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
    snprintf(cntS,10,"%d", cnt[i]);
    j = 0;
    while(cntS[j] != '\0') {
      putc(cntS[j],outFile);
      j++;
    }
    putc(' ',outFile);
  }
  putc('\0',outFile);
  fclose(outFile);
  exit(0);
}
```

Hay que resaltar que en el codigo anterior, hay algunas funciones que no se han visto pero que pueden ser consultadas en internet, a continuacion como [strcat](https://www.ibm.com/support/knowledgecenter/en/ssw_ibm_i_73/rtref/strcat.htm) y [snprintf](https://www.ibm.com/support/knowledgecenter/en/ssw_ibm_i_73/rtref/snprintf.htm). Lo animamos a que observe la descripcion y ejemplos de los enlaces y comprenda como se usan estos en el programa.
