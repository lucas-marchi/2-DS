# Funções em Python: Estruturando o seu código

**Disciplina:** Lógica de Programação I  

Na nossa última aula exploramos [[Matrizes]] e listas. Vimos como varrer e preencher coleções inteiras usando laços de repetição. Hoje, o problema que vamos resolver é outro: a repetição desnecessária de blocos de lógica pelo arquivo.

Imagine que você precise desenhar a interface em texto do seu sistema, ou ainda, imprimir a mesma matriz em cinco lugares diferentes. Você não vai copiar e colar os mesmos três blocos `for` repetidas vezes no seu código de produção. 

Copiar trechos idênticos pelo projeto é uma das piores práticas de desenvolvimento. A regra primária é o D.R.Y (*Don't Repeat Yourself* - Não se repita). Se um pensamento ou estrutura se repete, ele deve ser isolado como uma Função.

---

## O problema da repetição e a anatomia da Função

Uma função opera como uma ferramenta isolada que você empacota para executar um problema bem específico. Uma vez configurada, você a acessa em qualquer ponto do projeto apenas chamando o nome dela.

Linguagens antigas quebravam isso entre estruturas que retornavam valores (funções puras) e estruturas que apenas manipulavam processos (procedimentos). No Python, todas essas rotinas obedecem à mecânica única de definição de função.

Para iniciar, usamos a palavra reservada `def`. O encadeamento de lógica interno dessa função acontece seguindo o recuo, ou a indentação da guia, que vocês já aprenderam.

```python
# Declarando a estrutura - ela não é acionada aqui
def mostrar_cabecalho():
    print("========================")
    print("    SISTEMA ACADÊMICO   ")
    print("========================")

# O corpo real do programa faz a chamada dela
mostrar_cabecalho()
print("Bem-vindo ao sistema de matrícula.")
mostrar_cabecalho() 
```

Percebam que sem o bloco de função, teríamos um código poluído reescrevendo `print` sucessivamente. Aqui basta utilizar uma linha para reaproveitar tudo.

---

## Escopo Local e Comunicação com Parâmetros

A criação anterior resolveu formatação simples, mas não atua sobre uma lógica muito útil. Ao projetar funções funcionais, devemos enviar os parâmetros para serem engolidos pela estrutura lógica. O alerta fundamental aqui é entender o **Escopo Local**. A variável que nasce dentro do `def`, morre nele; ela não contamina outras áreas externas do código.

```python
def registrar_saudacao(nome, estagio):
    # As variáveis 'nome' e 'estagio' orbitam isoladas neste laço
    print(f"Bem-vindo, {nome}. Status de progressão em {estagio}%.")

# O programa base joga diferentes parâmetros pelo parêntese
registrar_saudacao("Arthur", 30)
registrar_saudacao("Beatriz", 70)
```

## Expondo Resultados: O Retorno Computacional (`return`)

Para lógicas numéricas e manipulação matemática, normalmente um núcleo secundário resolve os cálculos para que a esteira principal do seu código decida o que printar. Expomos esse valor da função utilizando o operador `return`, encerrando a sub-rotina imediatamente ali.

Vamos atualizar uma métrica financeira:

```python
def somar_comissao(balanco_atual, fator_bonus):
    novo_balanco = balanco_atual + fator_bonus
    return novo_balanco 

saldo_vendedor = 1200.00
print("Fechando nova venda no sistema...")

# A variável resgata explicitamente a entrega calculada da função
saldo_vendedor = somar_comissao(saldo_vendedor, 150.00) 

print(f"O saldo corrigido é de R$: {saldo_vendedor:.2f}")
```

**Exercício rápido para a estação:**
Abram o Visual Studio Code (ou a IDE padrão). Definam logo no topo do arquivo a função paralela `verificar_par(numero)`. A estrutura deve abrigar um `if` para analisar se o seu módulo contra `2` não possui resto (usando `%`), acionando um `return True` nessa situação. Se for falso, devolva o comando `return False`. Vamos revisar individualmente.

---

## O Encadeamento de Listas

Rotinas complexas como de coleções não impedem de serem passadas via escopo. Nós podemos acionar listas e matrizes inteiras. Retirar processos robustos de tratamento de lista limpa quase todas as camadas indesejadas que afetam o monitoramento do fluxo central.

Reestrutrando a rotina de imprimir relatórios tabulados (matrizes) visto semana passada:

```python
def desenhar_painel_matriz(matriz_entrada):
    for tr em matriz_entrada:
        for elemento in tr:
            print(f"[{elemento}]", end=" ") 
        print() # Impede quebra linear antes de fim de vetor

relatorio_mensal = [
    ["1 Semestre", "Notas Anuais", "Frequência"],
    ["2 Semestre", "Recuperações", "Matrículas"]
]

print("Painel de Visuais Lógicos:")
desenhar_painel_matriz(relatorio_mensal) 
```

O núcleo do programa mantém apenas as variáveis importantes operando. Todos os dois percursos em laços duplos estão enclausurados longe do código de entrada do `main` invisível do seu sistema principal.

---

## Desenvolvimento Dirigido: Laboratório Focado

Na prática do laboratório da vez, a sua responsabilidade é entregar o roteamento isolado de um sistema estrutural de gerenciamento usando chamadas sequenciais, organizadas com `defs`. É altamente recomendável desenvolver os métodos antes da raiz chamadora principal. A atividade pode, e preferencialmente, deve ser articulada em duplas.

O critério do programa é:

1. Elaborem a função lógica `calcular_estatistica(conjunto_notas)` esperando no escopo uma lista numérica qualquer (vetor), fazendo um escaneamento `for` dos itens da lista, agrupando a soma de tudo e lançando da sub-rotina com `return` qual é a média dessa coleção.
2. Formem a estrutura `verificar_aprovacao(nome_candidato, media)` limitando sua função a checar essa pontuação retornada. Imprimam na tela o nome anexado com o "Aprovado" se houver alcance ou margem para 70, escrevendo o reverso para reprovações.  
3. Feitas as regras externas, abram um fluxo `for/while` base que use o comando nativo `input()` para agregar sucessivos valores informados pelo operador, estique sua lista recém preenchida dentro das defs desenhadas e processe tudo usando as vias metodológicas corretas.

Trabalhem bem as indentações, prestem atenção aos escapes indevidos de escopo interno das variáveis recém elaboradas antes de acionar a execução no console, e caso precisem auxílio por bloqueios, as chamadas podem ser concentradas na bancada. Boa jornada a todos!
