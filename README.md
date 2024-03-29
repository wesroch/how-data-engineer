# Bootcamp da How - Engenharia de Dados

## Módulo 01 - Fundamentos de Engenharia de Dados

Na primeira aula, foi apresentado uma breve introdução ao Bootcamp e os fundamentos de engenharia de dados, como as primeiras etapas para realizar uma extração de dados de um site, fazendo um web scrapping do site da caixa, com os seguintes objetivos:

- Ler um arquivo de dados para um dataframe
- Tratar a informação recebida -> mantendo só  oque for necessário para realizar nossa análise
- Selecionar os dados necessários
- Extrair informações dos dados
- Automatizar o processo

Para fim de análise, coletando os dados e levantando as informações da LotoFácil, iremos responder as seguintes questões?

- Qual o número mais sorteado e o menos sorteado?
- Quais combinações de números Pares(p), Ímpares(i) e Primos (np) saem por sorteio?

No arquivo [loterias.ipynb](https://github.com/WesRoch/how-data-engineer/blob/main/01_aula/loterias.ipynb) podemos encontrar a análise realizada, para introduzir os conceitos iniciais, fazendo uma solicitação de uma requisição no site da loto facil, pegando nosso data frame com o pandas, fazendo a limpeza, coleta das informações necessárias, e analisando os possíveis números retirados no sorteio, assim levando a descobrir qual o mais sorteado e o menos sorteado, além das combinações citadas e a probabilidade.

## Módulo 03 - Fundamentos de Ingestão de Dados

### **API Requests**

Aqui iremos ver como funcionam os métodos GET, POST e PUT. Para isso, iremos fazer um request da api de cotações do [Awesome API](https://docs.awesomeapi.com.br/api-de-moedas) utilizando o GET, trazendo o valor do dólar na última cotação, com uma taxa de atualização de 30 segundos.

Cada status de um código http possuem um significado, como 200, 400 e 500.Cada código significa alguma informação para o usuário:

>- [1xx] - Informação
>- [2xx] -  Sucesso
>- [3xx] - Redirecionar
>- [4xx] -  Erro de cliente (client-side error)
>- [5xx] -  Erro de servidor ( server-side error)

### **Try, Except, and Backoff**

Para explicar um pouco sobre a utilização de um Try, um Except e uma biblioteca chamada Backoff, temos como exemplo a seguinte função:

![func_multi_moedas](/assets/images/func-mult-moedas.png)

A função faz a requisição do valor da moeda cotada e apresenta o valor na moeda desejada quando a funçao é chamada:

<code>multi_moedas(20,'USD-BRL')</code>

Obtendo retorno como:

<code>20 USD hoje custam 99.139 BRL</code>

Mas e se no argumento da funcao multi_moedas, por exemplo, for passado uma moeda que não exista, como podemos tratar o erro da melhor maneira possível?  
Podemos utilizar de **Function Decorator**, na qual nos permite modificar (sem ser de forma explícita) uma função por incluir outra função, extendendo o comportamento da função incluida (**wrapping**)  

### **Logs**

Para gerar rastrear os processos do script, ver o que está sendo executado, tipo de erro que é retornado, mostra uma mensagem do que se trata o erro, trackando tudo o que está acontecendo - podemos gerar **logs** utilizando o pacote ***Logging***, como no exemplo abaixo.

```Python
# que informações vamos apresentar
formatter = logging.Formatter(
    '%(asctime)s - %(name)s - %(levelname)s - %(message)s') # time, name = usuario do terminal
```


```Python
ch = logging.StreamHandler() # canal 
ch.setFormatter(formatter) # carregando o formato no canal
log.addHandler(ch) # adicionando o canal de saída a log
```