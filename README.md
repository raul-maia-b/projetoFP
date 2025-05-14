# projetoFP



import os
os.system("clear")

lista_nome = []
lista_especie = []
lista_raca = []
lista_data = []
lista_peso = []
eventos = {}
def crud(escolha):
        
     #Apresentar as opções do CRUD para Camila;
        escolha_2 = int(input("Digite: \n 1- Para Registrar \n 2- Visualizar \n 3- Editar \n 4- Excluir \n"))
        #Caso Camila escolha Adicionar;
        if escolha_2 == 1:
            file = open("VidaPet.csv","a")
            #Adicionar todos os dados do registro de um animal;
            nome = str(input("Digite o nome do cachorro: "))
            lista_nome.append(nome)
            especie = str(input("Digite a espécie: "))
            lista_especie.append(especie)
            raca = str(input("Digite a raça: "))
            lista_raca.append(raca)
            data_de_nascimento = str(input("Digite a data de nascimento: "))
            lista_data.append(data_de_nascimento)
            peso = str(input("Digite o peso: "))
            lista_peso.append(peso)
            print("Animal registrado!")
            file.write(f"REGISTROS SALVOS: Nome: {nome} // Espécie: {especie} // Raça: {raca} // Data de Nascimento: {data_de_nascimento} // Peso: {peso}\n")
            file.close()

        #Caso Camila escolha Visualizar;
        elif escolha_2 == 2:
            file = open("VidaPet.csv","r")
            for i in range (len(lista_nome)):
                print("ADIÇÕES RECENTES: \n")
                print(f"REGISTRO SALVO:  NOME: {lista_nome[i]} // ESPÉCIE: {lista_especie[i]} // RAÇA: {lista_raca[i]} // DATA DE NASCIMENTO: {lista_data[i]} // PESO: {lista_peso[i]}\n")
            
            print("ANIMAIS REGISTRADOS: \n")
            print(file.read())
            file.close()
                
           #mostrar todos os cachorros e seus dados;
        
        #Caso Camila escolha Editar;
        elif escolha_2 == 3:
            #Pedir o número do registro dos animal;
            file = open("VidaPet.csv","a")
            print("PARA EDITAR UM REGISTRO ANTERIOR, BASTA ABRIR O ARQUIVO E REESCREVER O DADO!")
            escolha_registro = int(input("Digite o número do registro que você deseja editar as informações: "))
            #Se o registro existir;
            if escolha_registro <= (len(lista_nome) -1 ):
                print(f"REGISTRO #{escolha_registro}:  NOME: {lista_nome[escolha_registro]} // ESPÉCIE: {lista_especie[escolha_registro]} // RAÇA: {lista_raca[escolha_registro]} // DATA DE NASCIMENTO: {lista_data[escolha_registro]} // PESO: {lista_peso[escolha_registro]}")
                mudanca = int(input("O que deseja editar? \n 1- Nome \n 2- Espécie \n 3- Raça \n 4- Data de nascimento \n 5- Peso \n"))
                if mudanca == 1:
                    novo_valor = input("Digite o novo nome: ")
                    lista_nome[escolha_registro] = novo_valor
                    file.write(f"REGISTRO #{escolha_registro}:  NOME: {lista_nome[escolha_registro]} // ESPÉCIE: {lista_especie[escolha_registro]} // RAÇA: {lista_raca[escolha_registro]} // DATA DE NASCIMENTO: {lista_data[escolha_registro]} // PESO: {lista_peso[escolha_registro]}")
                elif mudanca == 2:
                    novo_valor = input("Digite a espécie: ")
                    lista_especie[escolha_registro] = novo_valor
                    file.write(f"REGISTRO #{escolha_registro}:  NOME: {lista_nome[escolha_registro]} // ESPÉCIE: {lista_especie[escolha_registro]} // RAÇA: {lista_raca[escolha_registro]} // DATA DE NASCIMENTO: {lista_data[escolha_registro]} // PESO: {lista_peso[escolha_registro]}")

                elif mudanca == 3:
                    novo_valor = input("Digite a raça: ")
                    lista_raca[escolha_registro] = novo_valor
                    file.write(f"REGISTRO #{escolha_registro}:  NOME: {lista_nome[escolha_registro]} // ESPÉCIE: {lista_especie[escolha_registro]} // RAÇA: {lista_raca[escolha_registro]} // DATA DE NASCIMENTO: {lista_data[escolha_registro]} // PESO: {lista_peso[escolha_registro]}")

                elif mudanca == 4:
                    novo_valor = input("Digite a data de nascimento: ")
                    lista_data[escolha_registro] = novo_valor
                    file.write(f"REGISTRO #{escolha_registro}:  NOME: {lista_nome[escolha_registro]} // ESPÉCIE: {lista_especie[escolha_registro]} // RAÇA: {lista_raca[escolha_registro]} // DATA DE NASCIMENTO: {lista_data[escolha_registro]} // PESO: {lista_peso[escolha_registro]}")

                elif mudanca == 5:
                    novo_valor = input("Digite o peso: ")
                    lista_peso[escolha_registro] = novo_valor
                    file.write(f"REGISTRO #{escolha_registro}:  NOME: {lista_nome[escolha_registro]} // ESPÉCIE: {lista_especie[escolha_registro]} // RAÇA: {lista_raca[escolha_registro]} // DATA DE NASCIMENTO: {lista_data[escolha_registro]} // PESO: {lista_peso[escolha_registro]}")

                else:
                    print("Valor inválido!")
                    while mudanca > 0 and mudanca <= 5:
                        mudanca = int(input("O que deseja editar? \n 1- Nome \n 2- Espécie \n 3- Raça \n 4- Data de nascimento \n 5- Peso"))
            elif escolha_registro > (len(lista_nome) -1):
                print("Valor inválido!")
                while escolha_registro > (len(lista_nome) -1):
                    escolha_registro = int(input("Digite o número do registro que você deseja editar as informações: "))
            file.close()
                
        
        #Caso Camila escolha Excluir;
        elif escolha_2 == 4:
            escolha_excluir = int(input("Digite o número do registro que você deseja excluir: "))
            #Se o registro existir;
            if escolha_excluir <= (len(lista_nome) -1):
                lista_nome.pop(escolha_excluir) 
                lista_especie.pop(escolha_excluir)
                lista_raca.pop(escolha_excluir)
                lista_data.pop(escolha_excluir)
                lista_peso.pop(escolha_excluir)
                print("Registro excluido.")
            elif escolha_excluir > (len(lista_nome)-1):
                print("Valor inválido!")
                while escolha_excluir > (len(lista_nome) - 1):
                    escolha_excluir = int(input("Digite o número do registro que você deseja excluir: "))
        file.close()
        return lista_nome,lista_especie,lista_raca,lista_data,lista_peso

def cadastro_eventos(escolha):
        file = open("VidaPet.csv", "a")
        #Perguntar o que Camila quer realizar;
        escolha_cadastro = int(input("O que deseja agendar? \n 1- Vacinações \n 2- Consultas Veterinárias \n 3- Aplicações de remédios \n 4- Visualizar eventos \n"))
        if escolha_cadastro == 1:
            #Pedir registro e data para adicionar ao dicionário;
            agendar_animal = int(input("Digite o registro do animal que você desejar alocar: "))
            if agendar_animal <= (len(lista_nome)-1):
                data_agendamento = str(input("Digite a data do agendamento (XX/XX/XXXX): "))
                print("Animal Registrado!")
                eventos[f"VACINAÇÃO // NOME: {lista_nome[agendar_animal]}"] = f"DATA: {data_agendamento}"
                file.write(f"{eventos}\n")
            else:
                print("Registro inválido.")
                while agendar_animal > (len(lista_nome) -1):
                    agendar_animal = int(input("Digite o registro do animal que você desejar alocar: "))
        elif escolha_cadastro == 2:
            #Pedir registro e data para adicionar ao dicionário;
            agendar_animal = int(input("Digite o registro do animal que você desejar alocar: "))
            if agendar_animal <= (len(lista_nome)-1):
                data_agendamento = str(input("Digite a data do agendamento (XX/XX/XXXX): "))
                print("Animal Registrado!")
                eventos[f"CONSULTA VETERINÁRIA // NOME: {lista_nome[agendar_animal]}"] = f"DATA: {data_agendamento}" 
                file.write(f"{eventos}\n") 
            else: 
                print("Registro inválido.")
                while agendar_animal > (len(lista_nome) -1):
                    agendar_animal = int(input("Digite o registro do animal que você desejar alocar: "))
        elif escolha_cadastro == 3:
            #Pedir registro e data para adicionar ao dicionário;
            agendar_animal = int(input("Digite o registro do animal que você desejar alocar: "))
            if agendar_animal <=(len(lista_nome)-1):
                data_agendamento = str(input("Digite a data do agendamento (XX/XX/XXXX): "))
                print("Animal Registrado!")
                eventos[f"APLICAÇÕES DE REMÉDIOS // NOME: {lista_nome[agendar_animal]}"] = f"DATA: {data_agendamento}" 
                file.write(f"{eventos}\n")
            else:
                print("Registro inválido.")
                while agendar_animal > (len(lista_nome) -1):
                    agendar_animal = int(input("Digite o registro do animal que você desejar alocar: "))
        elif escolha_cadastro == 4:
            print(eventos)
        file.close()
        return eventos


while True:
    #Primeira interação do programa, perguntar o que Camila quer fazer;
    escolha_funcao = int(input("Digite: \n 1- CRUD de animais \n 2- Cadastro de Cuidados e Eventos \n 3- Metas de Saúde e Bem-Estar \n 4- Sugestões Personalizadas \n 5- Função Extra\n"))
    if escolha_funcao == 1:
        crud(escolha_funcao)
    
    elif escolha_funcao == 2:
        cadastro_eventos(escolha_funcao)
