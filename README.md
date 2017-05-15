# prueba-c
#include <stdio.h>
#include <string.h>
#include <unistd.h>
#include <cs50.h>

int min = 1;
int max = 100;
int adivine = 0;
int contador;
string resp, may_men;
void busqueda_binaria(int min, int max);
int evaluacion(void);

int main(void) {
  printf("** contador: %i, adivine %i , min %i, max %i **\n", contador, adivine, min, max);
  contador = 0;
  printf("Piensa en un numero entre 1 y 100\n");
  sleep(2);
  while (adivine==0) {
    busqueda_binaria(min, max);
    adivine = evaluacion();
    if (contador != 0 && adivine != 0) {
      printf("** contador: %i, adivine %i , min %i, max %i **\n", contador, adivine, min, max);
    }
    contador++;
    printf("** contador: %i, adivine %i , min %i, max %i **\n", contador, adivine, min, max);
  }
}

void busqueda_binaria(int min, int max) {
  if (min == max) {
    printf("Pensaste en el numero %i!\n", min);
    resp = "si";
  } else {
    printf("Pensaste en el %i? (si,no)\n", min+(max-min)/2);
    resp = GetString();
  }
}

int evaluacion(void) {
  if (strcmp(resp, "no") == 0) {
    printf("mayor o menor? (mayor, menor)\n");
    may_men = GetString();
    if (strcmp(may_men, "mayor") == 0) {
      min = min + ((max-min)/2) + 1;
      printf("** contador: %i, adivine %i , min %i, max %i **\n", contador, adivine, min, max);
    } else {
      max = min + ((max-min)/2) - 1;
      printf("** contador: %i, adivine %i , min %i, max %i **\n", contador, adivine, min, max);
    }
    return 0;
  } else {
    printf("adivine!\n");
    return 1;
  }
}
