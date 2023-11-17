# desafio_projeto_banco
Projeto Banco Desafio DIO


# deposito
# saque
# extrato

menu = """

[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair
 
=> """


saldo = 0
limite = 500
extrato = ""
numero_saque = 0
depositos = []
lista_saques = []
LIMITE_SAQUES = 3

while True:
    
    opcao = input(menu)
    
    if opcao.lower() == "d":
        valor = float(input("Deposite: "))
        
        if valor <= 0:
            print("Falha! Deposito negativo.")
        elif valor > 0:
            saldo += valor
            depositos.append(valor)             
            
    elif opcao.lower() == "s":
        print(f"Saldo atual: R${saldo:.2f}")
        numero_saque += 1
        if saldo <= 0:
            print("Nao sera possivel sacar dinheiro por falta de saldo")
            
        elif LIMITE_SAQUES < numero_saque: 
            print("Limites de saques diarios atingidos.")
            
        else: 
            saque = float(input("Valor de saque: R$ "))
            
            if saque > saldo:
                print("Voce nao tem valor suficiente na conta ")
                
            elif saque > 500:
                print("Voce nao pode sacar um valor maior que R$ 500.00 por transacao.")
                
            else:
                saldo -= saque
                lista_saques.append(saque)
                
    elif opcao.lower() == "e":
        print(" Extrato ".center(20, "#") + "\n")
        
        print(" Depositos ".center(20, "+") + "\n")
        
        for valores in enumerate(depositos):
            print(f"Depositos: {valores[0]+1}: R$ {valores[1]:.2f}\n".center(10, " "))
            
        print(" Saques ".center(20, "-") + "\n")
        
        for valores in enumerate(lista_saques):
            print(f"Saques: {valores[0]+1}: R$ -{valores[1]:.2f}\n".center(10, " "))
        
        print(f"\nSaldo final: R$ {saldo:.2f}")
        
    elif opcao.lower() == "q":
        print("Sair")
        break
    
    else:
        print("Opcao invalida, digite uma opcao valida.")
