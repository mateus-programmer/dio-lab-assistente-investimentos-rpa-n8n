# 🤖 Assistente de Investimentos com RPA no n8n

Projeto desenvolvido como parte do desafio prático da **Digital Innovation One (DIO)**: *Criando um Processo de RPA com N8N e Python*. 

A automação realiza a extração de dados de clientes a partir de uma página HTML, lê opções de investimentos de um arquivo CSV, cruza as informações com base no perfil de risco de cada cliente e dispara recomendações personalizadas via e-mail.

---

## 🛠️ Tecnologias Utilizadas

* **[n8n](https://n8n.io/)**: Plataforma de automação de fluxo de trabalho (Open Source / Execução Local).
* **JavaScript (Node.js)**: Processamento e manipulação de arrays e objetos JSON dentro dos nós `Code`.
* **HTML Content Extraction**: Leitura e parsing de seletores CSS para dados de páginas web.
* **Gmail API / OAuth 2.0**: Integração para disparo automatizado de e-mails em lote.

---

## 🔄 Fluxo da Automação

O workflow é composto pelas seguintes etapas encadeadas:

1. **Gatilho Manual (`When clicking 'Execute workflow'`)**: Inicia a execução do processo sob demanda.
2. **Requisição do CSV (`HTTP Request`)**: Obtém a lista de produtos financeiros atualizada.
3. **Formatação do CSV (`Code in JavaScript`)**: Converte o texto bruto do CSV em objetos JSON com os campos `perfil`, `produto`, `minimo` e `rentabilidade`.
4. **Requisição do HTML (`HTTP Request1`)**: Consome a página web contendo a tabela de clientes da instituição.
5. **Extração de Dados (`HTML`)**: Aplica seletores CSS (`table tr td:nth-child(...)`) para estruturar `nome`, `email`, `saldo` e `perfil`.
6. **Cruzamento de Dados (`Code in JavaScript1`)**: Realiza o filtro dos investimentos compatíveis com o perfil de cada cliente individual.
7. **Disparo de Recomendações (`Gmail / Send a Message`)**: Envia um e-mail individualizado para cada cliente com os produtos recomendados.

---

## 🚀 Como Importar e Executar no Seu n8n

1. Instale e execute o n8n localmente (`n8n start` ou via Docker).
2. Na tela inicial do n8n, crie um novo workflow.
3. Clique no menu do canto superior direito **`...`** > **Import from File**.
4. Selecione o arquivo `workflow.json` disponível neste repositório.
5. Configure suas credenciais da API do Gmail no último nó.
6. Clique em **Execute workflow** para testar a automação.

---

## 🔗 Links e Recursos Úteis

* **Página HTML dos Clientes (Fonte de dados)**: [GitHub Pages - DIO Lab](https://digitalinnovationone.github.io/dio-lab-assistente-investimentos-rpa-n8n/)
* **Perfil do Autor**: [GitHub - mateus-programmer](https://github.com/mateus-programmer)
