# Aula 04_Atividade Individual _Prompt 'Mestre' (18/03)
*Tema escolhido: Funções*

# Variação 1: 🚀✅

# Funções em Python 📝

Funções são blocos de código que realizam tarefas específicas e podem ser **reutilizadas** várias vezes. Elas ajudam a organizar o programa e evitar repetição.

## Sintaxe básica 📦

```python
def nome_da_funcao(parametros):
    # código a ser executado
    return resultado  # opcional
Exemplo
def soma(a, b):
    return a + b

print(soma(3, 5))  # Saída: 8
Como funciona
Definição: def cria a função.
Parâmetros: valores que a função recebe para processar.
Corpo: conjunto de instruções que executa a tarefa.
Return: envia um resultado de volta (não obrigatório).
Chamada: usar a função pelo nome com argumentos, se necessário.
```


# Variação 2:
# Funções em Python — 🎯

Funções são **blocos de código que você pode usar várias vezes**. Elas podem receber **parâmetros** e opcionalmente retornar um valor.

Por exemplo, vamos criar uma função que soma dois números: ✅

```python
def soma(a, b):
    return a + b

Aqui a e b são os parâmetros. Para usar a função, chamamos pelo nome e passamos os valores:

resultado = soma(3, 7)
print(resultado)  # Saída: 10

Funções também podem não retornar nada, apenas executar uma ação. Por exemplo, mostrar uma mensagem:

def ola_mundo():
    print("Olá, mundo!")

ola_mundo()  # Saída: Olá, mundo!

Você pode criar quantas funções quiser, cada uma com uma tarefa específica, e chamá-las quando precisar.

Por fim, o return é opcional: se você quiser que a função devolva algo para usar depois, use return; se não, apenas escreva o código dentro da função.
```
# Variação 3: 🔧
# Funções em Python — Explicação Simples✅

Uma **função** é como uma pequena máquina dentro do seu programa: você dá algo para ela (entrada), ela faz algo e pode devolver um resultado (saída). Isso evita repetir código e deixa o programa mais organizado.

Por exemplo, se quisermos criar uma função que cumprimente alguém, podemos fazer assim:

```python
def cumprimentar(nome):
    print(f"Olá, {nome}!")

Aqui, nome é a informação que a função recebe. Quando chamamos a função, ela executa o que está dentro dela:

cumprimentar("João")

Saída:

Olá, João!

Funções também podem retornar valores, permitindo usar o resultado em outras partes do programa:

def dobro(numero):
    return numero * 2

Se chamarmos dobro(5), o resultado será 10.

Em resumo:

def → cria a função.
Parâmetros → são os dados que entram na função.
return → envia algo de volta (opcional).
Funções ajudam a economizar tempo e manter o código limpo.

```
# Reflexão Crítica : ✨

Percebi que, dependendo das instruções que eu dava, a resposta mudava bastante. Quando pedi explicações curtas e objetivas, o
foco ficou só no código, o que ajudou a ver a estrutura rapidamente, mas não me dava muito contexto. Quando pedi mais texto e menos código, 
consegui entender melhor o raciocínio por trás das funções e como elas funcionam na prática. Para o meu aprendizado,
a versão que misturava texto explicativo com trechos curtos de código foi a mais útil, porque me permitiu conectar a teoria à prática sem me perder nos detalhes.
Acho que posso aplicar essa técnica no dia a dia da programação criando tutoriais ou notas:
primeiro explico o conceito em palavras, depois mostro um exemplo mínimo de código. Isso ajuda a fixar o conhecimento e facilita consultar depois.
