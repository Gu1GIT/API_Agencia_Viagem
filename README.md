# API de Agência de Viagens

Este projeto consiste em uma API RESTful desenvolvida com Java e Spring Boot, criada para gerenciar destinos de viagens. A API permite operações CRUD (Create, Read, Update, Delete) básicas em destinos, além de funcionalidades de pesquisa e avaliação.

Este projeto foi desenvolvido como parte de um desafio de desenvolvimento de aplicações.

## Funcionalidades

A API oferece os seguintes endpoints:

* **Cadastrar Destino:** Permite inserir um novo destino de viagem.
    * `POST /api/destinations`
* **Listar Destinos:** Retorna a lista de todos os destinos disponíveis.
    * `GET /api/destinations`
* **Pesquisar Destinos:** Permite pesquisar destinos por nome ou localização.
    * `GET /api/destinations/search?query={termo}`
* **Visualizar Detalhes do Destino:** Retorna informações detalhadas sobre um destino específico por ID.
    * `GET /api/destinations/{id}`
* **Avaliar Destino:** Permite atribuir uma nota (1-10) a um destino, atualizando sua média.
    * `PATCH /api/destinations/{id}/rate?rating={nota}`
* **Atualizar Destino:** Atualiza todas as informações de um destino existente por ID.
    * `PUT /api/destinations/{id}`
* **Excluir Destino:** Remove um destino específico por ID.
    * `DELETE /api/destinations/{id}`

## Tecnologias Utilizadas

* **Java 17+**
* **Spring Boot 3.x**
* **Maven** para gerenciamento de dependências e construção do projeto.

## Pré-requisitos

Para executar este projeto localmente, você precisa ter o seguinte software instalado:

* **Java Development Kit (JDK) 17 ou superior:**
    * Você pode baixar o OpenJDK, Oracle JDK, etc. (ex: [OpenJDK](https://openjdk.org/)).
* **Apache Maven 3.6 ou superior:**
    * Instruções de instalação podem ser encontradas no [site oficial do Maven](https://maven.apache.org/install.html).

## Como Instalar e Rodar

Siga os passos abaixo para configurar e executar a aplicação em sua máquina local:

1.  **Clone o Repositório:**
    ```bash
    git clone https://github.com/Gu1GIT/API_Agencia_Viagem.git
    ```
  
2.  **Navegue até a Pasta do Projeto:**
    ```bash
    cd API_Agencia_Viagem
    ```

3.  **Construa o Projeto com Maven:**
    Este comando compila o código e empacota a aplicação em um arquivo JAR executável.
    ```bash
    mvn clean install
    ```

4.  **Execute a Aplicação Spring Boot:**
    Após a construção bem-sucedida, você pode iniciar a aplicação.
    ```bash
    mvn spring-boot:run
    ```
    A aplicação será iniciada e estará disponível em `http://localhost:8080`.

## Configuração CORS para Testes Locais

A API está configurada para permitir requisições de origens cruzadas (CORS), o que é necessário para testar a API com um front-end (como o arquivo `index.html` fornecido) que é carregado diretamente do sistema de arquivos ou de um servidor de desenvolvimento diferente.

A configuração de CORS está definida na classe `WebConfig.java`, permitindo requisições de `*` (qualquer origem) para todos os endpoints sob `/api/**`.

## Como Testar a API

### 1. Via cURL (Linha de Comando)

Você pode usar o `curl` para testar os endpoints diretamente do seu terminal. Certifique-se de que a aplicação Spring Boot esteja rodando.

* **Cadastrar Destino:**
    ```bash
    curl -X POST http://localhost:8080/api/destinations -H "Content-Type: application/json" -d "{\"name\": \"Praia da Joaquina\", \"location\": \"Florianópolis, Brasil\", \"description\": \"Famosa pelas dunas e surf.\"}"
    ```
* **Listar Todos os Destinos:**
    ```bash
    curl -X GET http://localhost:8080/api/destinations
    ```
* **Pesquisar Destinos (ex: por "Florian"):**
    ```bash
    curl -X GET "http://localhost:8080/api/destinations/search?query=Florian"
    ```
* **Ver Detalhes do Destino (ex: ID 1):**
    ```bash
    curl -X GET http://localhost:8080/api/destinations/1
    ```
* **Avaliar Destino (ex: ID 1 com nota 9):**
    ```bash
    curl -X PATCH "http://localhost:8080/api/destinations/1/rate?rating=9"
    ```
* **Excluir Destino (ex: ID 1):**
    ```bash
    curl -X DELETE http://localhost:8080/api/destinations/1
    ```

### 2. Via HTML Tester

Um arquivo `index.html` simples é fornecido na raiz do projeto para facilitar o teste interativo da API no navegador.

1.  **Abra o arquivo `index.html`** diretamente no seu navegador).
2.  **Certifique-se de que a API está rodando (`mvn spring-boot:run`)**.
3.  Utilize os botões na página para interagir com os endpoints da API. A resposta será exibida na seção "Resposta da API" no topo da página.

## Contribuição

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues ou pull requests.

## Licença

Este projeto está licenciado sob a [Licença MIT](LICENSE).

---
