#include <stdio.h>
#include <string.h>

// Estrutura da carta
struct Carta {
    char estado[30];
    int codigo;
    char nome[50];
    int populacao;
    float pib;
    float area;
    int pontosTuristicos;
    float densidadePopulacional;
    float pibPerCapita;
};

// Função para calcular dados derivados
void calcularDerivados(struct Carta *c) {
    c->densidadePopulacional = c->populacao / c->area;
    c->pibPerCapita = c->pib / c->populacao;
}

// Função para exibir carta
void exibirCarta(struct Carta c) {
    printf("Nome da Cidade: %s\n", c.nome);
    printf("Estado: %s\n", c.estado);
    printf("Código: %d\n", c.codigo);
    printf("População: %d\n", c.populacao);
    printf("PIB: %.2f\n", c.pib);
    printf("Área: %.2f km²\n", c.area);
    printf("Pontos Turísticos: %d\n", c.pontosTuristicos);
    printf("Densidade Populacional: %.2f hab/km²\n", c.densidadePopulacional);
    printf("PIB per capita: %.2f\n", c.pibPerCapita);
}

// Função para comparar atributos
void compararAtributo(struct Carta c1, struct Carta c2, int atributo) {
    printf("\nComparando...\n");

    switch (atributo) {
        case 1:
            printf("População: %d x %d\n", c1.populacao, c2.populacao);
            (c1.populacao > c2.populacao) ? printf("Jogador 1 venceu!\n") :
            (c1.populacao < c2.populacao) ? printf("Jogador 2 venceu!\n") :
            printf("Empate!\n");
            break;

        case 2:
            printf("PIB: %.2f x %.2f\n", c1.pib, c2.pib);
            if (c1.pib > c2.pib)
                printf("Jogador 1 venceu!\n");
            else if (c1.pib < c2.pib)
                printf("Jogador 2 venceu!\n");
            else
                printf("Empate!\n");
            break;

        case 3:
            printf("Área: %.2f x %.2f\n", c1.area, c2.area);
            if (c1.area > c2.area)
                printf("Jogador 1 venceu!\n");
            else if (c1.area < c2.area)
                printf("Jogador 2 venceu!\n");
            else
                printf("Empate!\n");
            break;

        case 4:
            printf("Pontos Turísticos: %d x %d\n", c1.pontosTuristicos, c2.pontosTuristicos);
            if (c1.pontosTuristicos > c2.pontosTuristicos)
                printf("Jogador 1 venceu!\n");
            else if (c1.pontosTuristicos < c2.pontosTuristicos)
                printf("Jogador 2 venceu!\n");
            else
                printf("Empate!\n");
            break;

        case 5:
            printf("Densidade Populacional: %.2f x %.2f\n", c1.densidadePopulacional, c2.densidadePopulacional);
            printf("%s\n", (c1.densidadePopulacional > c2.densidadePopulacional) ? "Jogador 1 venceu!" :
                           (c1.densidadePopulacional < c2.densidadePopulacional) ? "Jogador 2 venceu!" : "Empate!");
            break;

        case 6:
            printf("PIB per capita: %.2f x %.2f\n", c1.pibPerCapita, c2.pibPerCapita);
            if (c1.pibPerCapita > c2.pibPerCapita)
                printf("Jogador 1 venceu!\n");
            else if (c1.pibPerCapita < c2.pibPerCapita)
                printf("Jogador 2 venceu!\n");
            else
                printf("Empate!\n");
            break;

        default:
            printf("Atributo inválido!\n");
            break;
    }
}

int main() {
    struct Carta carta1 = {"São Paulo", 101, "São Paulo", 12300000, 2300000000.0, 1521.0, 25};
    struct Carta carta2 = {"Rio de Janeiro", 102, "Rio de Janeiro", 6700000, 1300000000.0, 1182.3, 18};

    calcularDerivados(&carta1);
    calcularDerivados(&carta2);

    int opcao;

    do {
        printf("\n=== MENU SUPER TRUNFO CIDADES ===\n");
        printf("1. Exibir carta do Jogador 1\n");
        printf("2. Exibir carta do Jogador 2\n");
        printf("3. Comparar cartas por atributo\n");
        printf("0. Sair\n");
        printf("Escolha uma opção: ");
        scanf("%d", &opcao);

        switch (opcao) {
            case 1:
                printf("\n--- Carta do Jogador 1 ---\n");
                exibirCarta(carta1);
                break;
            case 2:
                printf("\n--- Carta do Jogador 2 ---\n");
                exibirCarta(carta2);
                break;
            case 3:
                printf("\nEscolha o atributo para comparar:\n");
                printf("1. População\n");
                printf("2. PIB\n");
                printf("3. Área\n");
                printf("4. Pontos Turísticos\n");
                printf("5. Densidade Populacional\n");
                printf("6. PIB per capita\n");
                int atributo;
                scanf("%d", &atributo);
                compararAtributo(carta1, carta2, atributo);
                break;
            case 0:
                printf("Encerrando o jogo...\n");
                break;
            default:
                printf("Opção inválida!\n");
        }

    } while (opcao != 0);

    return 0;
}
