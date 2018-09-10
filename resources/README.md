# Ejercicios de repaso

1. **Manejo de archivos**: Hacer un programa que permita obtener las siguientes estadisticas de un archivo de texto:
   1. Numero de caracteres del archivo.
   2. Numero de lineas.
   3. Numero de palabras (cada palabra es separada por un whitespace o una nueva linea).
   4. Numero de whitespaces (caracteres espacio ' ' o tab '\n')
   5. Numero de letras en mayuscula.
   6. Numero de letras en minuscula.
   7. Numero de digitos.

El ejecutable (compilelo como textstats) debera complir los siguientes requerimientos:
1. Recibir argumentos de entrada por linea de comandos. Cada uno de los argumentos sera un archivo el nombre de un archivo de entrada. Por ejemplo, suponga que tiene un archivo llamado texto1.txt, de modo que la invocación del ejecutable será 

```
./textstats texto1.txt. Asi mismo se espera una salida como la siguiente.
./textstats texto1.txt
Obteniendo estadisticas...
- texto1.txt --> generando reporte texto1_stats.txt
Estadisticas culminadas
```

2. Suponiendo que el archivo de entrada texto1.txt tuviera un contenido como el mostrado a continuación.

```
1234 56
hello this is a word
Finally this line !
```

El archivo generado (texto1_stats.txt) deberá tener un contenido como el siguiente:

```
chars: 49 
words: 11 
lines: 3 
whitespaces: 8
uppercase: 1 
lowercase: 30 
digits: 6
```

El nombre del archivo de texto asociado a las estadisticas, deberá contener el nombre del archivo antes de la extención seguido por la cadena **stats.txt**. Asi, si el archivo se llamara file.dat, el archivo generado asociado a las estadisticas **seria file_stats.dat**

