# Projeto-gerador-de-senhas-seguras
Com o aumento do número de contas online, a criação de senhas fortes se tornou fundamental para garantir a segurança dos usuários. Este projeto tem como objetivo desenvolver uma aplicação simples que gere senhas seguras e aleatórias com base em critérios definidos pelo usuário, como o tamanho da senha e o tipo de caracteres utilizados.

TECNOLOGIAS UTILIZADAS:
Linguagem: Python 3

Bibliotecas padrão: random, string
Interface (opcional): CLI (linha de comando) ou GUI com tkinter (opcional)
Sistema operacional: multiplataforma

FUNCIONALIDADES IMPLEMENTADAS
Escolha do tamanho da senha
Inclusão/exclusão de:
Letras maiúsculas
Letras minúsculas
Dígitos
Símbolos
Geração de senha aleatória com base nas opções
Exibição da senha gerada
Validação de entrada do usuário

CODIGO:

import random
import string

def gerar_senha(tamanho, usar_maiusculas=True, usar_minusculas=True, usar_digitos=True, usar_simbolos=True):
    """Gera uma senha segura baseada nos critérios definidos."""
    caracteres = ''
    
    if usar_maiusculas:
        caracteres += string.ascii_uppercase
    if usar_minusculas:
        caracteres += string.ascii_lowercase
    if usar_digitos:
        caracteres += string.digits
    if usar_simbolos:
        caracteres += string.punctuation

    if not caracteres:
        raise ValueError("Pelo menos um tipo de caractere deve ser selecionado.")

    senha = ''.join(random.choice(caracteres) for _ in range(tamanho))
    return senha

def main():
    print("=== Gerador de Senhas Seguras ===")
    try:
        tamanho = int(input("Digite o tamanho da senha: "))
        usar_maiusculas = input("Incluir letras maiúsculas? (s/n): ").lower() == 's'
        usar_minusculas = input("Incluir letras minúsculas? (s/n): ").lower() == 's'
        usar_digitos = input("Incluir dígitos? (s/n): ").lower() == 's'
        usar_simbolos = input("Incluir símbolos? (s/n): ").lower() == 's'

        senha = gerar_senha(tamanho, usar_maiusculas, usar_minusculas, usar_digitos, usar_simbolos)
        print(f"\nSenha gerada: {senha}")

    except ValueError as e:
        print(f"Erro: {e}")

if __name__ == "__main__":
    main()


 EXPLICAÇÂO TECNICA DO CODIGO
string.ascii_uppercase, ascii_lowercase, digits, punctuation são conjuntos de caracteres prontos.

random.choice(caracteres) seleciona aleatoriamente um caractere.

A senha final é construída com uma compreensão de lista usando join.

Há tratamento de erro para o caso do usuário não selecionar nenhum tipo de caractere.

EXEMPLO DE USO

=== Gerador de Senhas Seguras ===
Digite o tamanho da senha: 12
Incluir letras maiúsculas? (s/n): s
Incluir letras minúsculas? (s/n): s
Incluir dígitos? (s/n): s
Incluir símbolos? (s/n): s

Senha gerada: qG$1V!m9W@jX

 FONTES E REFERÊNCIAS
Documentação oficial Python: https://docs.python.org/3/library/string.html

OWASP Password Recommendations: https://owasp.org/www-community/password-special-characters

Segurança em senhas: https://haveibeenpwned.com/
