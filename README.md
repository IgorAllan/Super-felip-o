menu = input

d = "Depositar"
s = "Sacar"
e = "Extrato"
q = "sair"


saldo = 0
limite = 500
extrato = " "
numero_saques = 0
limite_saques = 3

while True:
    opcao = input(menu)

    if opcao == "d":
        valor = float(input("informe o valor do deposito: "))

        if valor > 0:
            saldo += valor
            extrato += f"Deposito: R$ {valor:.2f}\n"

        else:
            print("Operação falhou! O valor informado é invalido")

    elif opcao == "s":
        valor = float(input("Informe o valor do saque: "))

        excedeu_saldo = valor > saldo

        excedeu_limite = valor > limite

        excedeu_saques = numero_saques >= limite_saques

        if excedeu_saldo:
            print("Operação falhou! Você não tem saldo suficiente")

        elif excedeu_limite:
            print("Operação falhou! O valor do saque excede o limite")

        elif excedeu_saques:
            print("Operação falhou! Número maximo de saques excedido")

        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R${valor:.2f}\n"
            numero_saques += 1

        else:
            print("Operação falhou! o valor informado é inválido.")

    elif opcao == "e":
        print("\n================== EXTRATO ==================")
        print("Não foram realizados movimentações" if not extrato else extrato)
        print(numero_saques)
        print(f"\nSaldo: R${saldo:.2f}")
        print("===============================================")

    elif opcao == "q":
      break

    else:
        print("Operação invalida, Selecione novamente a opção desejada")
