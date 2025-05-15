import os
os.system("clear")

eventos = {}

def update(valor):
    escolha_registro = str(input("Digite o nome do animal que você deseja editar as informações: "))
    file = open(f"{escolha_registro}.txt","r")
    print(file.readline())
    file.close()
    with open(f"{escolha_registro}.txt","r") as file:
        lista = [linha.strip() for linha in file.readlines()]
    palavras = lista[0].split()
    file = open(f"{escolha_registro}.txt","w")
    escolha_edição = int(input("O que deseja editar: \n1-Nome \n2-Espécie \n3-Raça \n4-Data de Nascimento \n5-Peso\n"))
    if escolha_edição == 1:
        novo_dado = str(input("Digite o novo nome: "))
        os.rename(f"{escolha_registro}.txt",f"{novo_dado}.txt")
        lista[0] = f"REGISTRO: Nome: {novo_dado} // Espécie: {palavras[5]} // Raça: {palavras[8]} // Data de Nascimento: {palavras[13]} // Peso: {palavras[16]}\n"
        with open(f"{novo_dado}.txt", "w") as file:
            file.writelines(lista)
    elif escolha_edição == 2:
        novo_dado = str(input("Digite a nova Espécie: "))
        lista[0] = f"REGISTRO: Nome: {palavras[2]} // Espécie: {novo_dado} // Raça: {palavras[8]} // Data de Nascimento: {palavras[13]} // Peso: {palavras[16]}\n"
        with open(f"{escolha_registro}.txt", "w") as file:
            file.writelines(lista)
    elif escolha_edição == 3:
        novo_dado = str(input("Digite a nova Raça: "))
        lista[0] = f"REGISTRO: Nome: {palavras[2]} // Espécie: {palavras[5]} // Raça: {novo_dado} // Data de Nascimento: {palavras[13]} // Peso: {palavras[16]}\n"
        with open(f"{escolha_registro}.txt", "w") as file:
            file.writelines(lista)
    elif escolha_edição == 4:
        novo_dado = str(input("Digite a nova Data de Nascimento: "))
        lista[0] = f"REGISTRO: Nome: {palavras[2]} // Espécie: {palavras[5]} // Raça: {palavras[8]} // Data de Nascimento: {novo_dado} // Peso: {palavras[16]}\n"
        with open(f"{escolha_registro}.txt", "w") as file:
            file.writelines(lista)
    elif escolha_edição == 5:
        novo_dado = str(input("Digite o novo Peso: "))
        lista[0] = f"REGISTRO: Nome: {palavras[2]} // Espécie: {palavras[5]} // Raça: {palavras[8]} // Data de Nascimento: {palavras[13]} // Peso: {novo_dado}\n"
        with open(f"{escolha_registro}.txt", "w") as file:
            file.writelines(lista)
        
    file.close()
    return escolha_edição

def create(valor):
    if valor == 1:
            #Adicionar todos os dados do registro de um animal;
            nome = str(input("Digite o nome do animal: "))
            file = open(f"{nome}.txt","a")
            especie = str(input("Digite a espécie: "))
            raca = str(input("Digite a raça: "))
            data_de_nascimento = str(input("Digite a data de nascimento: "))
            peso = str(input("Digite o peso: "))
            print("Animal registrado!")
            file.write(f"REGISTRO: Nome: {nome} // Espécie: {especie} // Raça: {raca} // Data de Nascimento: {data_de_nascimento} // Peso: {peso}\n")
            file.close()
    return file

def read(valor):
    escolha_arquivo = str(input("Digite o nome do animal: "))
    file = open(f"{escolha_arquivo}.txt","r")
    print(file.read())
    file.close()
    return file

def delete(valor):
     try:
        escolha_excluir = str(input("Digite o nome do animal que você deseja excluir: "))
        os.remove(f"{escolha_excluir}.txt")
        print("Registro excluido.")
     except FileNotFoundError:
         print("Registro não encontrado!")
     return escolha_excluir


def crud(escolha):
        
     #Apresentar as opções do CRUD para Camila;
        escolha_2 = int(input("Digite: \n 1- Para Registrar \n 2- Visualizar \n 3- Editar \n 4- Excluir \n"))
        #Caso Camila escolha Adicionar;
        if escolha_2 == 1:
            create(escolha_2)

        #Caso Camila escolha Visualizar;
        elif escolha_2 == 2:
            read(escolha_2)
                
           #mostrar todos os cachorros e seus dados;
        
        #Caso Camila escolha Editar;
        elif escolha_2 == 3:
            #Pedir o número do registro dos animal;
            update(escolha_2)
                
        
        #Caso Camila escolha Excluir;
        elif escolha_2 == 4:
            delete(escolha_2)
        return escolha_2

def cadastro_eventos(escolha):
    escolha_cadastro = int(input("O que deseja agendar? \n 1- Vacinações \n 2- Consultas Veterinárias \n 3- Aplicações de remédios \n 4- Visualizar eventos \n"))
    if escolha_cadastro == 1:
        registro = str(input("Digite o nome do animal que você deseja agendar: "))
        file = open(f"{registro}.txt","a")
        data = str(input("Digite a data: (XX/XX/XXXX) "))
        file.write(f"DATA DA VACINAÇÃO: {data}\n")
        file.close()
    elif escolha_cadastro == 2:
        registro = str(input("Digite o nome do animal que você deseja agendar: "))
        file = open(f"{registro}.txt","a")
        data = str(input("Digite a data: (XX/XX/XXXX) "))
        file.write(f"DATA DA CONSULTA VETERINÁRIAS: {data}\n")
        file.close()
    elif escolha_cadastro == 3:
        registro = str(input("Digite o nome do animal que você deseja agendar: "))
        file = open(f"{registro}.txt", "a")
        data = str(input("Digite a data: (XX/XX/XXXX) "))
        file.write(f"DATA DAS APLICAÇÕES DE REMÉDIOS: {data}")
        file.close()
    elif escolha_cadastro == 4:
        registro = str(input("Digite o nome do animal que você deseja ver o enventos cadastrados: "))
        with open(f"{registro}.txt","r") as file:
            linhas = file.readlines()
            print(linhas[1])



while True:
    try:
    #Primeira interação do programa, perguntar o que Camila quer fazer;
        escolha_funcao = int(input("Digite: \n 1- CRUD de animais \n 2- Cadastro de Cuidados e Eventos \n 3- Metas de Saúde e Bem-Estar \n 4- Sugestões Personalizadas \n 5- Função Extra\n"))
        if escolha_funcao == 1:
            crud(escolha_funcao)
    
        elif escolha_funcao == 2:
            cadastro_eventos(escolha_funcao)
    except ValueError: 
        print("Siga as instruções!")


