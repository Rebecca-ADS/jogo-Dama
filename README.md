# jogo-Dama
#include <stdio.h>

#define TAM 8

char tabuleiro[TAM][TAM];

void inicializar_tabuleiro() {
    for (int i = 0; i < TAM; i++) {
        for (int j = 0; j < TAM; j++) {
            if ((i + j) % 2 != 0) {
                if (i < 3)
                    tabuleiro[i][j] = 'P'; // Peça preta
                else if (i > 4)
                    tabuleiro[i][j] = 'B'; // Peça branca
                else
                    tabuleiro[i][j] = ' ';
            } else {
                tabuleiro[i][j] = ' ';
            }
        }
    }
}

void exibir_tabuleiro() {
    printf("\n   ");
    for (int j = 0; j < TAM; j++) {
        printf(" %d ", j);
    }
    printf("\n");

    for (int i = 0; i < TAM; i++) {
        printf(" %d ", i);
        for (int j = 0; j < TAM; j++) {
            printf("|%c", tabuleiro[i][j]);
        }
        printf("|\n");
    }
}
void mover_peca(int origem_linha, int origem_coluna, int destino_linha, int destino_coluna) {
    if (tabuleiro[origem_linha][origem_coluna] == ' ') {
        printf("Não há peça na posição de origem!\n");
        return;
    }

    if (tabuleiro[destino_linha][destino_coluna] != ' ') {
        printf("A posição de destino já está ocupada!\n");
        return;
    }

    // Movimento válido (simples, sem captura por enquanto)
    tabuleiro[destino_linha][destino_coluna] = tabuleiro[origem_linha][origem_coluna];
    tabuleiro[origem_linha][origem_coluna] = ' ';
}
int main() {
    int ol, oc, dl, dc;

    inicializar_tabuleiro();

    while (1) {
        exibir_tabuleiro();

        printf("\nDigite linha e coluna de origem: ");
        scanf("%d %d", &ol, &oc);
        printf("Digite linha e coluna de destino: ");
        scanf("%d %d", &dl, &dc);

        mover_peca(ol, oc, dl, dc);
    }

    return 0;
}
