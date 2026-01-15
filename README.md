# 🔄 Exercício AJAX - Consumo de API Assíncrona

![Status](https://img.shields.io/badge/Status-Finalizado-green)
![JavaScript](https://img.shields.io/badge/Code-JavaScript_(ES6+)-F7DF1E?logo=javascript&logoColor=black)
![API](https://img.shields.io/badge/Connect-REST_API-blue)
![JSON](https://img.shields.io/badge/Data-JSON-lightgrey)

> Uma aplicação prática demonstrando a capacidade de comunicar o Frontend com serviços externos, carregando dados dinamicamente sem a necessidade de "refresh" na página.

## 🎯 Motivação e Propósito

A web moderna não é estática. Aplicações reais precisam buscar dados em servidores (Backend) constantemente. O propósito deste projeto foi dominar a técnica de **AJAX (Asynchronous JavaScript and XML)**.

Este repositório resolve o problema de "interatividade estática". Ele implementa a lógica necessária para ir buscar informações em uma fonte externa (API), aguardar a resposta (Promise) e renderizar esses dados na tela do usuário instantaneamente, conceito base para Single Page Applications (SPAs).

## 🛠️ Tecnologias Utilizadas

A stack foca na lógica de programação e protocolos web:

* **[JavaScript (Vanilla JS / jQuery)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript):**
    * **Fetch API / $.ajax:** Métodos utilizados para realizar as requisições HTTP (GET).
    * **Promises / Async Await:** Controle do fluxo assíncrono (esperar os dados chegarem antes de tentar usá-los).
    * **DOM API:** Inserção dos dados recebidos no HTML.
* **[HTML5](https://developer.mozilla.org/pt-BR/docs/Web/HTML):** Estrutura da interface.
* **[CSS3](https://developer.mozilla.org/pt-BR/docs/Web/CSS):** Estilização dos elementos de resposta e estados de carregamento (loading).

## ✨ Funcionalidades

O código implementa o seguinte fluxo de dados:

1.  **Gatilho de Evento:** O usuário interage com a interface (ex: carrega a página ou clica em um botão).
2.  **Requisição HTTP:** O script dispara um pedido para um *Endpoint* (URL da API).
3.  **Tratamento de Erros:** O sistema verifica se a requisição foi bem sucedida (Status 200).
4.  **Parsing de Dados:** Transforma a resposta bruta em formato JSON manipulável.
5.  **Renderização:** Atualiza campos específicos da página (Imagens, Textos, Listas) com as informações vindas do servidor.

## 📦 Instalação e Execução

Como é um projeto focado em Client-Side, a execução é simples.

### Pré-requisitos
* Navegador Web atualizado.
* Conexão ativa com a Internet (Crucial, pois a API é externa).

### Passo a Passo

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/DouglassenG/exercicio_ajax.git](https://github.com/DouglassenG/exercicio_ajax.git)
    ```

2.  **Acesse o diretório:**
    ```bash
    cd exercicio_ajax
    ```

3.  **Execução:**
    * Localize o arquivo `index.html`.
    * Abra-o no navegador.
    * *Nota:* Algumas APIs bloqueiam requisições vindas do protocolo de arquivo (`file://`). Se os dados não carregarem, recomenda-se usar uma extensão como "Live Server" no VS Code para simular um servidor local (`http://127.0.0.1...`).

## 💻 Uso e Exemplos

O código destaca o entendimento de como manipular Promises.

**Exemplo Conceitual (Fluxo implementado):**

```javascript
// Exemplo da lógica utilizada para buscar dados
fetch('[https://api.exemplo.com/dados](https://api.exemplo.com/dados)')
    .then(resposta => {
        if (!resposta.ok) throw new Error("Erro na rede");
        return resposta.json(); // Converte para Objeto JS
    })
    .then(dados => {
        // Manipulação do DOM
        document.getElementById('nome').innerText = dados.name;
        document.getElementById('avatar').src = dados.avatar_url;
    })
    .catch(erro => {
        console.error("Falha na requisição:", erro);
        alert("Não foi possível carregar os dados.");
    })
    .finally(() => {
        // Remove spinner de carregamento
    });
