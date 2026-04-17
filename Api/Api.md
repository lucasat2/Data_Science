# Aula 1 – Introdução a APIs, JSON e XML

## 1. Objetivos da aula

Ao final desta aula, o aluno será capaz de:

- Explicar, em suas próprias palavras, o que é uma API.
- Entender o papel das APIs em aplicações web e em Data Science.
- Diferenciar os formatos JSON e XML e saber em que contexto eles aparecem.
- Ler visualmente uma resposta JSON ou XML e identificar campos importantes.
- Compreender conceitos básicos de requisições HTTP (URL, endpoint, método, status code).

---

## 2. Por que falar de APIs em Data Science?

Quando pensamos em Data Science, normalmente lembramos de:

- Planilhas (Excel, CSV).
- Bancos de dados (SQL).
- Arquivos locais (JSON, XML, parquet…).

Mas, cada vez mais, **os dados não estão apenas “parados” em arquivos**, e sim **circulando entre sistemas em tempo real**. É aí que entram as APIs.

### O que uma API resolve na prática?

Imagine que:

- Um aplicativo de clima no celular precisa da temperatura atual da sua cidade.
- Um site de filmes mostra a nota do IMDb ou Rotten Tomatoes.
- Um e-commerce atualiza preços com base em um sistema de estoque central.
- Um analista de dados quer pegar, diariamente, a cotação do dólar.

Em todos esses casos, há **um sistema que possui os dados** (o “servidor”) e **outro sistema que quer consumir esses dados** (o “cliente”).

> **API (Application Programming Interface)** é o “contrato” que permite essa comunicação entre sistemas de forma organizada e padronizada.

Em Data Science, isso é valioso porque:

- Permite **automatizar a coleta de dados** sem ficar baixando arquivos manualmente.
- Permite acessar **dados atualizados** (tempo real ou quase real).
- Facilita a construção de pipelines: API → tratamento → análise → relatório.

---

## 3. Conceitos básicos: Cliente, Servidor e HTTP

Antes de falar de JSON e XML, precisamos de um pouco de contexto sobre como funciona a comunicação na web.

### 3.1 Cliente e Servidor

- **Cliente**: quem faz o pedido. Pode ser:

  - Um navegador (Chrome, Firefox…)
  - Um aplicativo móvel
  - Um script Python (o que nos interessa aqui)
- **Servidor**: quem recebe o pedido e devolve uma resposta. Exemplo: o servidor da API de clima, da API do GitHub, da API do Twitter (X), etc.

A conversa entre eles acontece, na maior parte dos casos, pelo protocolo **HTTP** (ou HTTPS, que é a versão segura).

### 3.2 URL e Endpoint

Uma URL é o endereço que você digita no navegador ou que seu script acessa.  

Exemplo real de URL de API:

`https://jsonplaceholder.typicode.com/users`

Quebrando essa URL:

- `https://` → **protocolo** (HTTP seguro).
- `jsonplaceholder.typicode.com` → **domínio** do servidor (onde a API está hospedada).
- `/users` → **endpoint**: a “porta lógica” que representa um recurso.

Neste caso, é um endpoint que fornece dados de usuários de teste.

Em APIs, **endpoint** é a parte da URL que aponta para um recurso específico (por exemplo: `/users`, `/posts`, `/comments`, etc.).

Você pode até testar essa URL no navegador ou no `curl`/Postman, que ela retorna um JSON válido.

### 3.3 Métodos HTTP (GET, POST, etc.)

Quando o cliente faz uma requisição a um endpoint, ele normalmente usa um **método HTTP**, que indica a intenção da ação:

- `GET` → buscar dados.
- `POST` → enviar dados para criação de um recurso.
- `PUT`/`PATCH` → atualizar um recurso existente.
- `DELETE` → apagar um recurso.

Na maior parte das atividades de Data Science voltadas à leitura de dados, vamos trabalhar principalmente com `GET` (buscar informação).

### 3.4 Status Codes (códigos de resposta)

Toda resposta HTTP vem com um **status code**, que indica se deu certo ou se deu algum problema. Alguns códigos importantes:

- `200` – **OK**: requisição bem-sucedida.
- `201` – Created: algo foi criado (quando usamos POST).
- `400` – Bad Request: requisição malformada (parâmetro errado, por exemplo).
- `401` – Unauthorized: falta autenticação.
- `404` – Not Found: recurso não encontrado.
- `500` – Internal Server Error: erro no servidor.

Como cientista de dados, você precisa **checar o status code** para saber se os dados que está lendo são válidos ou se houve erro.

---

## 4. O que é JSON?

JSON significa **JavaScript Object Notation**. Apesar do nome, hoje ele é um formato **independente de linguagem**, amplamente usado para troca de dados entre sistemas.

### 4.1 Características do JSON

- Baseado em:

  - **Objetos** (chave-valor): equivalem a dicionários em Python.
  - **Listas** (arrays): equivalem a listas em Python.
- É **legível por humanos** e simples de entender.
- É o formato preferido da maioria das APIs modernas.

Exemplo de JSON simples (representando um usuário):

{ "id": 123, "nome": "Ana", "email": "[ana@example.com](mailto:ana@example.com)", "idade": 29, "ativo": true }

Perceba:

- As chaves estão entre aspas (`"id"`, `"nome"`…).
- Os valores podem ser número, string, booleano, null, lista, outro objeto.

### 4.2 JSON com listas

APIs frequentemente devolvem **listas de objetos**. Por exemplo, uma lista de usuários:

[ { "id": 1, "nome": "Ana", "idade": 29 }, { "id": 2, "nome": "Bruno", "idade": 34 }, { "id": 3, "nome": "Carla", "idade": 22 } ]

Para Data Science, isso é excelente porque:

- Essa estrutura bate quase 1:1 com linhas de um **DataFrame**:

  - Cada objeto → uma linha.
  - Cada chave → uma coluna.

### 4.3 JSON aninhado (nested)

Nem sempre o JSON é “retinho”. Muitas vezes temos **objetos dentro de objetos**, ou listas dentro de objetos. Exemplo:

{ "cidade": "Juiz de Fora", "previsao": { "hoje": { "temperatura": 25, "descricao": "Parcialmente nublado" }, "amanha": { "temperatura": 27, "descricao": "Ensolarado" } } }

Aqui, para chegar na temperatura de hoje, por exemplo, você teria que navegar:

- `previsao` → `hoje` → `temperatura`.

É importante saber “ler” essa estrutura antes de transformar em DataFrame — depois entraremos com `pandas.json_normalize` para “achatar” esses dados.

---

## 5. O que é XML?

XML significa **eXtensible Markup Language**. Ele é um formato mais antigo que o JSON, muito usado em sistemas legados, integrações corporativas e em alguns serviços públicos (governo, bancos, NF-e, etc.).

### 5.1 Estrutura básica do XML

O XML usa **tags** (semelhantes a HTML) para representar os dados:

<usuario> <id>123</id> <nome>Ana</nome> <email>ana@example.com</email> <idade>29</idade> <ativo>true</ativo> </usuario>

- Cada abertura de tag `<nome>` tem um fechamento `</nome>`.
- O conteúdo entre as tags é o valor do campo.

### 5.2 Coleções de elementos

Para representar listas, o XML costuma repetir tags dentro de uma tag pai:

<usuarios> <usuario> <id>1</id> <nome>Ana</nome> <idade>29</idade> </usuario> <usuario> <id>2</id> <nome>Bruno</nome> <idade>34</idade> </usuario> <usuario> <id>3</id> <nome>Carla</nome> <idade>22</idade> </usuario> </usuarios>

Aqui, `<usuarios>` é o contêiner, e cada `<usuario>` é um item da lista.

### 5.3 Atributos em tags

O XML também permite informações como **atributos** na própria tag:

<usuario id="123" ativo="true"> <nome>Ana</nome> <email>ana@example.com</email> </usuario>

- `id="123"` e `ativo="true"` são atributos da tag `<usuario>`.

Quando formos transformar isso em dados tabulares, precisaremos extrair tanto o conteúdo das tags quanto seus atributos.

---

## 6. JSON vs XML: qual a diferença na prática?

Característica

JSON

XML

Sintaxe

Objetos e arrays (chave-valor)

Tags hierárquicas

Verbosidade

Mais enxuto

Mais verboso (mais caracteres)

Uso atual

Padrão de fato em APIs modernas

Comum em sistemas legados, governo, bancos

Facilidade em Python

Muito fácil (vira dicionário/lista)

Dá mais trabalho (precisa parsear com bibliotecas)

Leitura humana

Fácil

Fácil, mas mais “poluída” visualmente

No contexto de Data Science:

- Você provavelmente vai lidar **mais com JSON**, especialmente em APIs modernas (Fintechs, plataformas de dados, etc.).
- Mas é importante não ignorar XML, porque muitas fontes oficiais (sobretudo governamentais e sistemas antigos) ainda o utilizam.

---

## 7. APIs REST e formatos de resposta

A maioria das APIs que você verá hoje são APIs **REST** (Representational State Transfer). Sem entrar em todos os detalhes formais, na prática significa:

- Você acessa **recursos** por meio de **URLs** previsíveis, como:

  - `/usuarios`
  - `/produtos`
  - `/pedidos`
- Usa métodos HTTP (`GET`, `POST`, etc.).
- Recebe respostas geralmente em **JSON** ou **XML**.

Exemplo de chamada e resposta (em nível conceitual):

Requisição:  

GET [https://api.exemplo.com/v1/usuarios](https://api.exemplo.com/v1/usuarios)

Resposta:  

Status: 200 OK  

Body (JSON ou XML)

Em Data Science, o que mais nos interessa é o **body** (corpo da resposta), pois é ali que estão os dados que vamos converter para DataFrame.

---

## 8. Onde APIs aparecem no dia a dia do cientista de dados?

Algumas situações típicas:

1. **Coleta de dados externos**
  - Cotação de moedas.
  - Clima, previsão do tempo.
  - Dados de redes sociais (Twitter/X, Instagram via ferramentas, YouTube).
  - Dados de mercado financeiro.
2. **Integração com sistemas internos**
  - API de ERP (sistema de gestão).
  - API de CRM (clientes, vendas, leads).
  - API de plataforma de e-commerce.
3. **Automação de relatórios**
  - Em vez de exportar CSV manualmente todos os dias, seu script faz chamadas à API, trata os dados e gera dashboards ou relatórios automaticamente.
4. **Modelos em produção**
  - Alguns modelos de Machine Learning são expostos como APIs.
  - Seu modelo recebe dados via POST, processa e devolve uma previsão.

Entender APIs é, portanto, um passo essencial para Data Science mais **moderno e automatizado**.

---

## 9. Exemplo conceitual: olhando um JSON no navegador

Mesmo antes de usar Python, você pode experimentar uma API simples diretamente no navegador. Suponha uma URL de exemplo (fictícia):

[https://api.exemplo.com/v1/produtos](https://api.exemplo.com/v1/produtos)

Ao acessar essa URL no navegador, você pode ver algo parecido com:

[ { "id": 10, "nome": "Teclado Mecânico", "preco": 250.0, "categoria": "Periféricos" }, { "id": 11, "nome": "Mouse Gamer", "preco": 150.0, "categoria": "Periféricos" } ]

Mesmo sem saber Python, você já consegue responder:

- Quais campos existem em cada produto? → `id`, `nome`, `preco`, `categoria`.
- Quantos produtos aproximadamente aparecem? → Conte o número de objetos na lista.
- Quais desses campos podem virar colunas de um DataFrame? → Todos.

Na próxima aula, vamos fazer esse mesmo tipo de requisição **usando Python**.

---

## 10. Pequena prévia em Python (sem entrar em detalhes ainda)

Só para conectar teoria e prática, veja um **exemplo simplificado** (sem se preocupar ainda com cada comando):

import requests  # biblioteca para fazer requisições HTTP

url = "[https://api.exemplo.com/v1/produtos](https://api.exemplo.com/v1/produtos)"  

resposta = requests.get(url) print(resposta.status_code) # ex: 200 print(resposta.json()) # imprime o JSON convertido em estruturas Python

- `requests.get(url)` → faz a requisição.
- `resposta.status_code` → mostra o código de status (200, 404, etc.).
- `resposta.json()` → converte o JSON da resposta em dicionários e listas Python.

Na Aula 2, vamos **destrinchar** isso com calma: instalação do `requests`, parâmetros, tratamento de erros, etc.

---

## 11. Resumo da aula (para revisar)

- **API** é uma interface que permite que sistemas conversem entre si. Em Data Science, usamos APIs para **buscar dados de forma automatizada.**
- A comunicação normalmente usa **HTTP/HTTPS**, com:

  - URLs/Endpoints;
  - Métodos (GET, POST…);
  - Status codes (200, 404, 500…).
- **JSON** é o formato mais comum em APIs modernas:

  - Usa chave-valor;
  - Facilmente mapeado para dicionários/listas em Python;
  - É ideal para virar DataFrame.
- **XML** é um formato mais antigo, baseado em tags:

  - Ainda muito usado em sistemas legados e dados governamentais;
  - Requer parsing via bibliotecas específicas.
- Em Data Science, conhecer APIs, JSON e XML permite:

  - Coletar dados externos;
  - Automatizar pipelines;
  - Integrar sistemas;
  - Trabalhar com dados mais atualizados.