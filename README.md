
# Missão Maestro

## Dia 1

- Aprenda sobre variáveis, tipos de dados, operadores, estruturas de controle (condicionais e loops).
- Entenda como definir funções e utilize bibliotecas padrão como math e random.
- Faça um programa com as funções Fibonacci, Fettucine e Número Perfeito.
- [Video de um cara que acho legal pra saber o minimo de Python](https://www.youtube.com/playlist?list=PLQpSyz5rZmJpFVb1TidOflNMcVnpDdzAn)

## Dia 2

- Explore como manipular e iterar sobre listas e dicionários em Python.
- [Video de estrutura de dados em python](https://www.youtube.com/playlist?list=PLA05yVJtRWYS4mhKqJo_1bZqcetSGjDgU)
- _(PS:Recomendo ver as Aulas: #1, #2, #3, #4)_
- _(PS: Ler e testar na miha opinião é mais rapido que ver video, então aprenda os conceitos e vá testando, pode me chamar que eu falo os conceitos <3)_

### Exemplo de Lista

```python
minha_lista = [1, 2, 3, 4, 5]
primeiro_elemento = minha_lista[0]  # acessa o primeiro elemento (valor: 1)
minha_lista[2] = 10  # altera o terceiro elemento para 10
minha_lista.append(6)  # adiciona o número 6 ao final da lista
for elemento in minha_lista:
    print(elemento)
```

```python
meu_dicionario = {"nome": "João", "idade": 30, "cidade": "São Paulo"}
print(meu_dicionario["nome"])  # imprime o valor associado à chave "nome"
meu_dicionario["idade"] = 31  # altera o valor associado à chave "idade"
meu_dicionario["profissao"] = "Engenheiro"  # adiciona um novo par chave-valor

# Iteração sobre chaves
for chave in meu_dicionario.keys():
    print(chave, meu_dicionario[chave])

# Iteração sobre valores
for valor in meu_dicionario.values():
    print(valor)

# Iteração sobre itens (chave-valor)
for chave, valor in meu_dicionario.items():
    print(chave, valor)
```

## Dia 3

### Manipulação de Datas em Python

Manipular datas em Python é essencial para lidar com timestamps, calcular intervalos de tempo, formatar datas para exibição e muito mais. Aqui estão os principais conceitos e bibliotecas que você precisa conhecer:
_(PS: Melhor forma é perguntar pro GPT ou ler Documentação, é suave, só pra aprender tratamento de datas)_

#### Bibliotecas:

- **datetime**: A biblioteca padrão para manipulação de datas e tempos.
- **dateutil**: Uma extensão da datetime que facilita operações mais avançadas com datas.

#### O que estudar:

- Criar objetos de data e hora.
- Formatando datas para exibição.
- Operações matemáticas com datas (adição, subtração).
- Conversão entre formatos de data e hora.
- Lidar com fusos horários, se necessário.

#### Exemplos de Uso:

```python
from datetime import datetime
from dateutil import parser

# Criando objetos de data e hora
agora = datetime.now()
data_str = '2024-07-05'
data = datetime.strptime(data_str, '%Y-%m-%d')

# Formatando datas
print(agora.strftime('%Y-%m-%d %H:%M:%S'))

# Operações matemáticas com datas
diff = agora - data

# Convertendo strings em objetos de data
data_parseada = parser.parse(data_str)
```

```python
import json

# Convertendo um dicionário para JSON
usuario = {
    'nome': 'João',
    'idade': 30,
    'cidade': 'São Paulo'
}
usuario_json = json.dumps(usuario)

# Escrevendo JSON em um arquivo
with open('usuario.json', 'w') as arquivo:
    json.dump(usuario, arquivo)

# Lendo JSON de um arquivo
with open('usuario.json', 'r') as arquivo:
    usuario_carregado = json.load(arquivo)
```

## Dia 4: Introdução ao SQL

### Fundamentos de SQL:

Aprenda sobre SQL, incluindo SELECT, INSERT, UPDATE, DELETE.
Utilizando SQLite com Python:

_(PS: Não achei nada sobre PIPIPIPI :( )_
## Dia 5: Introdução às Requests em Python

Em Python, a biblioteca requests é amplamente utilizada para realizar requisições HTTP (GET, POST, PUT, DELETE, etc.) para consumir dados de APIs web. Aqui estão os passos básicos para começar:

### Instalação da Biblioteca requests:

Certifique-se de que você tenha a biblioteca requests instalada. Caso não tenha, você pode instalá-la usando pip:

```
pip install requests
```

### Realizando uma Requisição GET:

Para fazer uma requisição GET simples e obter dados de uma API:

```python
import requests

# URL da API de exemplo
url = 'https://jsonplaceholder.typicode.com/posts/1'

# Realizando a requisição GET
response = requests.get(url)

# Verificando se a requisição foi bem-sucedida (código 200)
if response.status_code == 200:
    data = response.json()  # Convertendo a resposta para JSON
    print(data)
else:
    print('Erro ao acessar a API:', response.status_code)
```

### Realizando uma Requisição POST:

Para enviar dados para uma API usando POST:

```python
import requests

# URL da API de exemplo
url = 'https://jsonplaceholder.typicode.com/posts'

# Dados a serem enviados (exemplo)
data = {
    'title': 'foo',
    'body': 'bar',
    'userId': 1
}

# Realizando a requisição POST
response = requests.post(url, json=data)

# Verificando se a requisição foi bem-sucedida (código 201 para criação)
if response.status_code == 201:
    new_post = response.json()
    print('Novo post criado:', new_post)
else:
    print('Erro ao criar o post:', response.status_code)
```


## Dia 6: Webhooks em Python

Um webhook em Python é uma maneira eficaz de receber notificações ou informações em tempo real de serviços externos quando ocorrem eventos específicos. Aqui está como você pode implementar um webhook usando Flask:

### Exemplo de Código:

```python
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/webhook', methods=['POST'])
def webhook():
    # Verifica se a requisição contém dados JSON
    if request.is_json:
        dados = request.json
        print('Dados recebidos do webhook:')
        print(dados)
        return jsonify({'status': 'sucesso'})
    else:
        return jsonify({'status': 'erro', 'message': 'Requisição não contém dados JSON'}), 400

if __name__ == '__main__':
    app.run(debug=True)
```
_(PS: [Literalmente o GOAT dos videos de API](https://www.youtube.com/watch?v=FBLAV1SbJFk))_
## Dia 7: Projetos

### Projeto 1: Webhook

- **Objetivo**: Criar um servidor webhook simples que recebe notificações de eventos externos e processa esses eventos.

- **Descrição**: Implemente um servidor Flask que recebe dados de um webhook e os exibe no console.

### Projeto 2: API

- **Objetivo**: Desenvolver uma API simples que fornece e consome dados JSON.

- **Descrição**: Crie uma API RESTful que permita ao cliente consultar e atualizar dados.

### Projeto 3: Manipulação de JSON Data

- **Objetivo**: Manipular dados JSON, realizar operações como leitura, escrita e modificação.

- **Descrição**: Desenvolva um programa que leia dados de um arquivo JSON, manipule esses dados e salve as modificações de volta no arquivo.

### Projeto 4: Integração dos 3 Conceitos (Webhook, API e JSON Data)

- **Objetivo**: Criar um sistema completo que utilize webhooks para receber dados de uma API externa, manipule esses dados usando JSON e exponha uma API para consultar esses dados.

- **Descrição**: Implemente um sistema que receba notificações via webhook de um serviço externo sempre que novos dados estiverem disponíveis. Os dados recebidos são em formato JSON. O sistema deve armazenar esses dados localmente e fornecer uma API para consulta.

```
