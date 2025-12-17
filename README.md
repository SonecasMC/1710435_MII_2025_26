# 1710435_MII_2025_26
#include <stdio.h>
#include <string.h>

#define MAX 100

// Estrutura da encomenda
typedef struct {
	int id;
	char cliente[50];
	char produto[50];
	int quantidade;
	float preco;
} Encomenda;

Encomenda encomendas[MAX];
int totalEncomendas = 0;

// Função para cadastrar encomenda
void cadastrarEncomenda() {
	if (totalEncomendas >= MAX) {
		printf("Limite de encomendas atingido!\n");
		return;
	}

	Encomenda e;
	e.id = totalEncomendas + 1;

	printf("Nome do cliente: ");
	scanf(" %[^\n]", e.cliente);

	printf("Produto: ");
	scanf(" %[^\n]", e.produto);

	printf("Quantidade: ");
	scanf("%d", &e.quantidade);

	printf("Preço unitario: ");
	scanf("%f", &e.preco);

	encomendas[totalEncomendas] = e;
	totalEncomendas++;

	printf("Encomenda cadastrada com sucesso!\n");
}

// Função para listar encomendas
void listarEncomendas() {
	if (totalEncomendas == 0) {
		printf("Nenhuma encomenda cadastrada.\n");
		return;
	}

	for (int i = 0; i < totalEncomendas; i++) {
		printf("\nID: %d", encomendas[i].id);
		printf("\nCliente: %s", encomendas[i].cliente);
		printf("\nProduto: %s", encomendas[i].produto);
		printf("\nQuantidade: %d", encomendas[i].quantidade);
		printf("\nPreço unitário: R$ %.2f", encomendas[i].preco);
		printf("\nTotal: R$ %.2f\n",
		       encomendas[i].quantidade * encomendas[i].preco);
	}
}

// Função para calcular o valor total das encomendas
void calcularTotal() {
	float total = 0;

	for (int i = 0; i < totalEncomendas; i++) {
		total += encomendas[i].quantidade * encomendas[i].preco;
	}

	printf("Valor total de todas as encomendas: R$ %.2f\n", total);
}

// Função principal
int main() {
	int opcao;

	do {
		printf("\n=== Sistema de Encomendas Online ===\n");
		printf("1 - Cadastrar encomenda\n");
		printf("2 - Listar encomendas\n");
		printf("3 - Calcular valor total\n");
		printf("0 - Sair\n");
		printf("Escolha uma opção: ");
		scanf("%d", &opcao);

		switch (opcao) {
		case 1:
			cadastrarEncomenda();
			break;
		case 2:
			listarEncomendas();
			break;
		case 3:
			calcularTotal();
			break;
		case 0:
			printf("Saindo do sistema...\n");
			break;
		default:
			printf("Opção invalida!\n");
		}

	} while (opcao != 0);

	return 0;
}
