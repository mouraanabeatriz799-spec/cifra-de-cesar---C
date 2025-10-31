# cifra de cesar | C | prof rodrigo e assis 
meu primeiro repositorio
#include <stdio.h>
#include <string.h>
#include <ctype.h>
#define TAM 200

int primos[9] = {2, 3, 5, 7, 11, 13, 17, 19, 23};

void cifraCesar(char texto[], int chave) {
    for (int i = 0; texto[i] != '\0'; i++) {
        char c = texto[i];
        if (isupper(c)) {
            texto[i] = ((c - 'A' + chave) % 26) + 'A';
        } else if (islower(c)) {
            texto[i] = ((c - 'a' + chave) % 26) + 'a';
        }
    }
}

void converterParaPrimosLimitado(char texto[]) {
    printf("Texto convertido em primos (até 23): ");
    for (int i = 0; texto[i] != '\0'; i++) {
        char c = texto[i];
        if (isalpha(c)) {
            int pos = tolower(c) - 'a';
            if (pos >= 0 && pos <= 8) {
                printf("%d ", primos[pos]);
            } else {
                printf("0 ");
            }
        } else {
            printf("0 ");
        }
    }
    printf("\n");
}

int main() {
    char texto[TAM];
    printf("Digite o texto: ");
    fgets(texto, TAM, stdin);
    texto[strcspn(texto, "\n")] = '\0';
    cifraCesar(texto, 3);
    printf("Texto após cifra de César (+3): %s\n", texto);
    converterParaPrimosLimitado(texto);
    return 0;
}
