#include <stdio.h>
#include <string.h>
#include <stdbool.h>

// --- Estrutura da Carta ---
typedef struct {
    char name[50];
    int speed;
    int power;
    // Adicione mais atributos conforme necessário
} Card;

// --- Funções do Jogo ---

// Exibe a carta atual
void displayCard(Card card) {
    printf("\n--- %s ---\n", card.name);
    printf("1. Velocidade: %d km/h\n", card.speed);
    printf("2. Potencia: %d HP\n", card.power);
    printf("-------------------\n");
}

// Compara as cartas com base no atributo escolhido
// Retorna 1 se card1 vence, -1 se card2 vence, 0 se for empate
int compareCards(Card card1, Card card2, int attributeChoice) {
    switch (attributeChoice) {
        case 1: // Velocidade
            if (card1.speed > card2.speed) return 1;
            if (card1.speed < card2.speed) return -1;
            return 0; // Empate
        case 2: // Potencia
            if (card1.power > card2.power) return 1;
            if (card1.power < card2.power) return -1;
            return 0; // Empate
        default:
            return 0; // Atributo inválido ou empate
    }
}

int main() {
    // Definindo as duas cartas
    Card cardPlayer1;
    strcpy(cardPlayer1.name, "Ferrari F8 Tributo");
    cardPlayer1.speed = 340;
    cardPlayer1.power = 710;

    Card cardPlayer2;
    strcpy(cardPlayer2.name, "Porsche 911 GT3 RS");
    cardPlayer2.speed = 312;
    cardPlayer2.power = 525;

    printf("Bem-vindo ao Super Trunfo Simplificado!\n");
    printf("Voce tem a seguinte carta:\n");
    displayCard(cardPlayer1);

    int choice;
    printf("Escolha um atributo para jogar (1 para Velocidade, 2 para Potencia): ");
    scanf("%d", &choice);

    printf("\n--- Comparando as Cartas ---\n");
    printf("Sua carta: %s\n", cardPlayer1.name);
    printf("Carta do oponente: %s\n", cardPlayer2.name);

    printf("\nAtributo escolhido: ");
    switch (choice) {
        case 1: printf("Velocidade\n"); break;
        case 2: printf("Potencia\n"); break;
        default: printf("Invalido!\n"); break;
    }

    printf("---------------------------\n");

    int result = compareCards(cardPlayer1, cardPlayer2, choice);

    if (result == 1) {
        printf("\nParabens! Sua carta (%s) venceu a carta do oponente (%s)!\n", cardPlayer1.name, cardPlayer2.name);
    } else if (result == -1) {
        printf("\nQue pena! A carta do oponente (%s) venceu sua carta (%s).\n", cardPlayer2.name, cardPlayer1.name);
    } else {
        printf("\nEmpate! As cartas tem o mesmo valor no atributo escolhido.\n");
    }

    return 0;
}
