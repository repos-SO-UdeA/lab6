
# Ejemplo 8

Hacer un programa que lea un archivo que contenga varios numeros enteros (uno por fila) y obtenga la suma y el promedio de estos los imprima en pantalla y los lleve a un archivo.

**Solución**: El archivo [read_write_line3.c](read_write_line3.c) contiene la sulucion. A continuacion se muestra este por comodidad:

```C
#include <stdio.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main() {
  char inFilename[80];
  char outFilename[80] = "inventario_";
  int tam = 0;
  long long sum = 0;
  int num;
  double prom;
  FILE *inFile;
  FILE *outFile;
  printf("Ingrese el nombre del archivo: ");
  fflush(stdin);
  scanf("%[^\n]s",inFilename); // Formato para que la entrada pueda aceptar espacios
  inFile = fopen(inFilename,"r");
  if (inFile == NULL) {
    printf("Error al abrir el archivo %s\n", inFilename);
    exit(-1);
  }
  while(fscanf(inFile,"%d",&num)!=EOF) {
    printf("%d\n",num);
    tam++;
    sum += num;

  }
  fclose(inFile);
  strcat(outFilename,inFilename);  
  printf("\nSuma: %lld\n", sum);
  prom = (double)sum/tam;
  printf("Promedio: %.2lf\n", prom);
  outFile = fopen(outFilename,"w");
  fprintf(outFile, "Suma: %lld\n", sum);
  fprintf(outFile, "Promedio: %.2lf\n", prom);
  fclose(outFile);
  exit(0);
}
```
