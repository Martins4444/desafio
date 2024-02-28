menu = """

[d] depositar
[s] sacar
[e] extrato
[q] exit

=> """

saldo = 0
limite = 500
extrato = ""
numeros_de_saques = 0
LIMITE_DE_SAQUES = 3

while True:

    opção = input(menu)

    if opção == "d":
        valor = float(input("informe o valor de deposito:"))

        if valor > 0:
            saldo += valor
            extrato += f"deposito: R$ {valor:.2f}\n"
        else:
            print("operação falhou! Informe um valor valido.")

    elif opção == "s":
        valor = float(input("Informe o valor que deseja sacar:"))

        excedeu_saldo = valor > saldo
        excedeu_limite = valor > limite
        excedeu_saques = numeros_de_saques >= LIMITE_DE_SAQUES

        if excedeu_saldo:
            print("operação falhou! Você não possui saldo suficiente.")
        elif excedeu_limite:
            print("operação falhou! O valor inserido ultrapassa o valor limite de saque.")
        elif excedeu_saques:
            print("operação falhou! Você atingiu o limite de saques diários.")
        elif valor > 0:
            saldo -= valor
            extrato += f"saque: R$ {valor:.2f}\n"
            numeros_de_saques += 1
        else:
            print("A operação falhou! O valor informado não é válido.")

    elif opção == "e":
        print("\n========EXTRATO========")
        print("Não foram realizadas movimentações em sua conta." if not extrato else extrato)
        print(f"\n saldo: R$ {saldo:.2f}")
        print("=========================")

    elif opção == "q":
        break

    else:
        print("Operação inválida, por favor selecione novamente a opção que deseja e tente novamente.")
