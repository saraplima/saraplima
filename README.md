import random

def jogar():
    print("********************************")
    print("Bem-vindo ao Jogo de Adivinhação!")
    print("********************************")

    numero_secreto = random.randint(1, 100)
    total_de_tentativas = 0
    pontos = 100

    print("Níveis de dificuldade:")
    print("(1) Fácil (20 tentativas)")
    print("(2) Médio (10 tentativas)")
    print("(3) Difícil (5 tentativas)")

    nivel = int(input("Escolha o nível: "))

    if nivel == 1:
        total_de_tentativas = 20
    elif nivel == 2:
        total_de_tentativas = 10
    else:
        total_de_tentativas = 5

    for rodada in range(1, total_de_tentativas + 1):
        print(f"Tentativa {rodada} de {total_de_tentativas}")
        chute = int(input("Digite um número entre 1 e 100: "))

        if chute < 1 or chute > 100:
            print("Você deve digitar um número entre 1 e 100!")
            continue

        acertou = chute == numero_secreto
        maior = chute > numero_secreto
        menor = chute < numero_secreto

        if acertou:
            print(f"Parabéns! Você acertou e fez {pontos} pontos!")
            break
        else:
            if maior:
                print("Você errou! O seu chute foi maior que o número secreto.")
            elif menor:
                print("Você errou! O seu chute foi menor que o número secreto.")
            pontos_perdidos = abs(numero_secreto - chute)
            pontos -= pontos_perdidos

    print(f"O número secreto era {numero_secreto}")
    print("Fim do jogo!")

if __name__ == "__main__":
    jogar()


