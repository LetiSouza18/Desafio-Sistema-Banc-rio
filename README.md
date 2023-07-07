
# Curso Formação Python na Dio
# Desafio: Criando um Sistema Bancário

menu = """

[d] Depositar 
[s] Sacar
[e] Extrato
[q] Sair 

=> """

saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3


while True:

    opcao = input(menu)

    if opcao == "d":
        valor = float(input("Informe o valor do depósito: "))

        if valor > 0:
            saldo += valor 
            extrato += f"Depósito: R$ {valor:.2f}\n"

        else:
            print("Operação falhou! O valor informado é inválido.")


    elif opcao == "s":
        valor = float(input("Informe o valor do saque: "))

        excedeu_saldo = valor > saldo 

        excedeu_limite = valor > limite 

        excedeu_saques = numero_saques >= LIMITE_SAQUES 

        if excedeu_saldo:
            print("Operação falhou! Saldo insuficiente.")

        elif excedeu_limite:
            print("Operação falhou! O valor do saque excede o limite.")

        elif excedeu_saques:
            print("Operação falhou! Número máximo de saques excedido.")

        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2}\n"
            numero_saques += 1
        

        else: print("Operação falhou! O valor informado é inválido")
    
    elif opcao == "e":
        print("\n EXTRATO")
        print("Não foram realizadas movimentações." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2}")

    elif opcao == "q":
        break
    else:
        print("Operação inválida. Selecione novamente a opção desejada.")


            
