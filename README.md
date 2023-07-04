# AtividadePDS
//Controle Farmacêutico
//Linguagem: Python












class Produto:
    def __init__(self, nome, lote, validade, fornecedor, quantidade):
        self.nome = nome
        self.lote = lote
        self.validade = validade
        self.fornecedor = fornecedor
        self.quantidade = quantidade

class ControleFarmaceutico:
    def __init__(self):
        self.produtos = []

    def cadastrar_produto(self, nome, lote, validade, fornecedor, quantidade):
        produto = Produto(nome, lote, validade, fornecedor, quantidade)
        self.produtos.append(produto)
        print("Produto cadastrado com sucesso!")

    def buscar_produto(self, nome):
        for produto in self.produtos:
            if produto.nome == nome:
                print("Produto encontrado:")
                print("Nome:", produto.nome)
                print("Lote:", produto.lote)
                print("Validade:", produto.validade)
                print("Fornecedor:", produto.fornecedor)
                print("Quantidade:", produto.quantidade)
                return
        print("Produto não encontrado.")

    def exibir_estoque(self):
        print("Estoque:")
        for produto in self.produtos:
            print("Nome:", produto.nome)
            print("Quantidade:", produto.quantidade)
            print("-----")

    def registrar_venda(self, nome, quantidade):
        for produto in self.produtos:
            if produto.nome == nome:
                if produto.quantidade >= quantidade:
                    produto.quantidade -= quantidade
                    print("Venda registrada com sucesso!")
                    return
                else:
                    print("Quantidade insuficiente em estoque.")
                    return
        print("Produto não encontrado.")

    def gerar_relatorio(self):
        print("Relatório de Estoque:")
        for produto in self.produtos:
            print("Nome:", produto.nome)
            print("Lote:", produto.lote)
            print("Validade:", produto.validade)
            print("Fornecedor:", produto.fornecedor)
            print("Quantidade:", produto.quantidade)
            print("-----")

def exibir_menu():
    print("=== Menu ===")
    print("1. Cadastrar Produto")
    print("2. Buscar Produto")
    print("3. Exibir Estoque")
    print("4. Registrar Venda")
    print("5. Gerar Relatório")
    print("6. Sair")

controle = ControleFarmaceutico()

while True:
    exibir_menu()
    opcao = input("Selecione uma opção: ")

    if opcao == "1":
        nome = input("Digite o nome do produto: ")
        lote = input("Digite o número do lote: ")
        validade = input("Digite a data de validade: ")
        fornecedor = input("Digite o nome do fornecedor: ")
        quantidade = int(input("Digite a quantidade: "))
        controle.cadastrar_produto(nome, lote, validade, fornecedor, quantidade)
        print()

    elif opcao == "2":
        nome = input("Digite o nome do produto: ")
        controle.buscar_produto(nome)
        print()

    elif opcao == "3":
        controle.exibir_estoque()
        print()

    elif opcao == "4":
        nome = input("Digite o nome do produto: ")
        quantidade = int(input("Digite a quantidade vendida: "))
        controle.registrar_venda(nome, quantidade)
        print()

    elif opcao == "5":
        controle.gerar_relatorio()
        print()

    elif opcao == "6":
        print("Encerrando o programa...")
        break

    else:
        print("Opção inválida. Tente novamente.")
        print()
