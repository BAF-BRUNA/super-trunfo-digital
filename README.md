# super-trunfo-digital
Jogo de Super Trunfo Digital – Nível Aventureiro”
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

typedef struct {
    char nome[50];
    int populacao;
    float area;
    float pib;
    int pontosTuristicos;
    int ataque;
} Carta;

int main() {
    Carta c1 = {"Brasil", 214000000, 8515767, 22400, 5000, 80};
    Carta c2 = {"Portugal", 10300000, 92212, 270, 250, 70};
    Carta c3 = {"Holanda", 17000000, 41543, 912, 60, 75};

    int escolhaJogador, escolhaComputador, opcao;

    srand(time(NULL)); 
    escolhaComputador = rand() % 3 + 1; // escolha aleatória do computador

    // Menu de cartas
    printf("==== SUPER TRUNFO DIGITAL - NÍVEL AVENTUREIRO ====\n\n");
    printf("Cartas disponíveis:\n");
    printf("1 - %s | Pop: %d | Área: %.0f | PIB: %.0f | Pontos: %d | Ataque: %d\n", 
           c1.nome, c1.populacao, c1.area, c1.pib, c1.pontosTuristicos, c1.ataque);
    printf("2 - %s | Pop: %d | Área: %.0f | PIB: %.0f | Pontos: %d | Ataque: %d\n", 
           c2.nome, c2.populacao, c2.area, c2.pib, c2.pontosTuristicos, c2.ataque);
    printf("3 - %s | Pop: %d | Área: %.0f | PIB: %.0f | Pontos: %d | Ataque: %d\n\n", 
           c3.nome, c3.populacao, c3.area, c3.pib, c3.pontosTuristicos, c3.ataque);

    // Jogador escolhe a carta
    printf("Escolha sua carta (1, 2 ou 3): ");
    scanf("%d", &escolhaJogador);

    Carta jogador, computador;

    switch (escolhaJogador) {
        case 1: jogador = c1; break;
        case 2: jogador = c2; break;
        case 3: jogador = c3; break;
        default: printf("Escolha inválida! Usando Brasil.\n"); jogador = c1; break;
    }

    switch (escolhaComputador) {
        case 1: computador = c1; break;
        case 2: computador = c2; break;
        case 3: computador = c3; break;
    }

    printf("\nCarta do jogador: %s\n", jogador.nome);
    printf("Carta do computador: %s\n\n", computador.nome);

    // Menu de atributos
    printf("Escolha o atributo para comparação:\n");
    printf("1 - População\n2 - Área\n3 - PIB\n4 - Pontos turísticos\n5 - Ataque\n6 - Densidade demográfica (menor vence)\n");
    printf("Opção: ");
    scanf("%d", &opcao);

    float valor1 = 0, valor2 = 0;

    switch(opcao) {
        case 1:
            valor1 = jogador.populacao;
            valor2 = computador.populacao;
            printf("\nPopulação: %.0f x %.0f\n", valor1, valor2);
            break;
        case 2:
            valor1 = jogador.area;
            valor2 = computador.area;
            printf("\nÁrea: %.2f x %.2f\n", valor1, valor2);
            break;
        case 3:
            valor1 = jogador.pib;
            valor2 = computador.pib;
            printf("\nPIB: %.2f x %.2f\n", valor1, valor2);
            break;
        case 4:
            valor1 = jogador.pontosTuristicos;
            valor2 = computador.pontosTuristicos;
            printf("\nPontos turísticos: %.0f x %.0f\n", valor1, valor2);
            break;
        case 5:
            valor1 = jogador.ataque;
            valor2 = computador.ataque;
            printf("\nAtaque: %.0f x %.0f\n", valor1, valor2);
            break;
        case 6: // Densidade demográfica
            valor1 = jogador.populacao / jogador.area;
            valor2 = computador.populacao / computador.area;
            printf("\nDensidade demográfica: %.2f x %.2f\n", valor1, valor2);
            break;
        default:
            printf("Opção inválida!\n");
            return 0;
    }

    // Comparação geral
    if(opcao == 6) { // regra invertida para densidade
        if(valor1 < valor2)
            printf("%s venceu! (menor densidade)\n", jogador.nome);
        else if(valor2 < valor1)
            printf("%s venceu! (menor densidade)\n", computador.nome);
        else
            printf("Houve um empate!\n");
    } else {
        if(valor1 > valor2)
            printf("%s venceu!\n", jogador.nome);
        else if(valor2 > valor1)
            printf("%s venceu!\n", computador.nome);
        else
            printf("Houve um empate!\n");
    }

    printf("\n🎯 Fim do jogo! Obrigado por jogar o Super Trunfo Digital!\n");

    return 0;
}
