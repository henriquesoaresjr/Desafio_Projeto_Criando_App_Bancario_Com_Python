# Desafio_Projeto_Criando_App_Bancario_Com_Python

# Criando um Aplicativo Bancário Simples em Python

Neste artigo, vou descrever uma atividade de projeto de uma formação da DIO, atividade esta que seria criar um aplicativo bancário simples em Python. O aplicativo permitirá que os usuários realizem operações básicas, como depósito, saque e consulta de saldo.

## Funcionalidades do Aplicativo

1. *Depósito (d):* O usuário pode depositar um valor na conta. Se o valor for válido (maior que zero), ele é adicionado ao saldo.
2. *Saque (s):* O usuário pode sacar um valor da conta. Existem algumas verificações:
   - Verificamos se o saldo é suficiente para o saque.
   - Verificamos se o valor do saque não excede o limite.
   - Verificamos se o número de saques diários não foi excedido.
   Se todas as verificações passarem, o valor é subtraído do saldo.
3. *Extrato (e):* O usuário pode consultar o extrato, que exibe todas as transações realizadas.
4. *Terminar (t):* O usuário pode encerrar o aplicativo.

## Implementação

1. Inicializamos as variáveis saldo, limite, extrato e numero_saques.
2. Usei um loop while True para manter o aplicativo em execução até que o usuário escolha terminar.
3. Dentro do loop, apresento o menu de opções e lemos a escolha do usuário.
4. Para cada opção, realizamos as operações correspondentes (depósito, saque, extrato ou término).
5. O extrato é atualizado com cada transação.
6. As verificações são feitas para garantir que as operações sejam válidas.

```
menu = """


[d] Depositar
[s] Sacar
[e] Extrato
[t] Terminar


"""

saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3

while True:
    opcao = input(menu)

    if opcao == "d":
        valor = float(input("Informe o valor a ser depositado: "))

        if valor > 0:
            saldo += valor
            extrato += f"Depósito: R$ {valor:.2f}\n"

        else:
            print("Operação negada! O valor informado é inválido.")

    elif opcao == "s":
        valor = float(input("Informe o valor para saque: "))

        excedeu_saldo = valor > saldo

        excedeu_limite = valor > limite

        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print("Operação negada! Saldo suficiente.")

        elif excedeu_limite:
            print("Operação negada! O valor do saque excede o limite.")

        elif excedeu_saques:
            print("Operação negada! Número de saques diarios excedido.")

        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saques += 1

        else:
            print("Operação negada! O valor informado é inválido.")

    elif opcao == "e":
        print("\n================ EXTRATO ================")
        print("Não há movimentações realizadas." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("==========================================")

    elif opcao == "t":
        break

    else:
        print ("Opção não localizada, selecione novamente a opção desejada")
```

## Conclusão

Este aplicativo bancário simples foi para mim uma ótima introdução à programação em Python. Estarei agora, conforme avanço nos estudos, procurando melhorar suas funcionalidades, como adicionar autenticação de usuário e melhorar a interface para torná-lo mais robusto e intuitivo. 
