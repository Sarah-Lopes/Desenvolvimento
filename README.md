## DESENVOLVIMENTO ##
Repositório criado para armazenar atividades de teste em cursos/bootcamp

# 📦 DESAFIO 1 Bootcampo Suzano DIO - E-commerce Data Model
Descrição do Desafio - refinamento de um Projeto Conceitual de banco de dados de um E-Commerce
O esquema deverá ser adicionado a um repositório do Github para futura avaliação do desafio de projeto. Adicione ao Readme a descrição do projeto conceitual para fornecer o contexto sobre seu esquema.

## 📌 Objetivo
Refine o modelo apresentado acrescentando os seguintes pontos:
- Cliente PJ e PF – Uma conta pode ser PJ ou PF, mas não pode ter as duas informações;
- Pagamento – Pode ter cadastrado mais de uma forma de pagamento;
- Entrega – Possui status e código de rastreio.

Agora é a sua vez de ser o protagonista! Implemente o desafio sugerido pela expert e suba seu projeto para um repositório próprio, com isso, você aumentará ainda mais seu portfólio de projetos no GitHub!

---

## 📌 Visão Geral
O modelo de dados representa a estrutura de um sistema de e-commerce, cobrindo os principais aspectos da operação, desde a gestão de produtos e vendedores até o processamento de pedidos e pagamentos. O foco principal é garantir escalabilidade, flexibilidade e rastreabilidade dos pedidos e pagamentos, proporcionando uma estrutura robusta para suportar diversos cenários de compra e transação.

---

## 🏗️ Estrutura de Modelagem

A modelagem de dados foi projetada com base nos seguintes princípios:  
- **Normalização**: Reduzindo redundância e assegurando integridade dos dados.  
- **Escalabilidade**: Preparando o sistema para múltiplos métodos de pagamento e reprocessamento e aumentos no volume de pedidos e transações.  
- **Auditabilidade**: Facilitando o rastreamento de tentativas de pagamento, reembolsos e falhas.
- **Flexibilidade**: Suporte a múltiplos métodos de pagamento.  
- **Segurança**: Melhor controle e rastreabilidade de transações.  
- **Manutenção Simples**: Facilita atualizações no fluxo de pagamentos sem impactar a lógica principal de pedidos.  

---

## 🗂️ Modelagem Conceitual / Estrutura e Relacionamentos
🔖 Entidades Principais:

1.Cliente (Cliente)
**Descrição**: Armazena informações dos clientes do e-commerce.
**Principais Campos**: 
idCliente – Identificador único.
Nome – Nome do cliente.
Identificação – Documento de identificação (CPF/CNPJ).

2.Pedido (Pedido) 🛒
**Descrição**: Representa um pedido realizado por um cliente.
**Principais Campos**: 
idPedido – Identificador do pedido.
Data do pedido – Data de realização.
Descrição – Descrição do pedido.
Status do Pedido – Status atual (ex.: Processando, Enviado, Pendente, Cancelado).
Cliente_idCliente – FK para o cliente que realizou o pedido.
Frete – Valor do frete.
Valor_total – Valor total do pedido.

3.Detalhes do Pedido (Det_Pedido)
**Descrição**: Armazena os itens de cada pedido.
**Principais Campos**: 
idDet_Pedido – Identificador do item.
Item_pedido – Descrição do item.
Status_item – Status do item (ex.: Disponível, Indisponível).
Código de Rastreio – Código para rastreamento.

4.Pagamento (Pagamento) 💳
**Descrição**: Registra os detalhes do pagamento do pedido.
**Principais Campos**: 
idPagamentos – Identificador do pagamento.
Parcela – Número de parcelas.
Valor – Valor total do pagamento.
Forma de Pagamento – Método utilizado (ex.: Cartão, PIX, Boleto).
Data do Pagamento – Data de efetivação.
Pedido_idPedido – FK para o pedido correspondente.

5.Produto (Produto)
**Descrição**: Cadastro de produtos disponíveis no e-commerce.
**Principais Campos**: 
idProduto – Identificador do produto.
Categoria – Categoria do produto.
Descrição – Descrição do item.
Valor – Preço do produto.

---

## ⚙️ Relacionamentos  
- 1 Pedido → N Pagamentos**: Um pedido pode ter múltiplos pagamentos associados (parciais, complementares ou estornos).  
- **Pagamentos Independentes**: A tabela de pagamentos opera de forma autônoma, permitindo callbacks de gateways e atualizações sem modificar diretamente os dados do pedido.
    
- Cliente ↔ Pedido:
** Um cliente pode ter vários pedidos (1:N).

- Pedido ↔ Detalhes do Pedido:
** Um pedido possui múltiplos itens (1:N).

- Pedido ↔ Pagamento:
** Um pedido pode ter múltiplos pagamentos associados (parciais, complementares ou estornos). (1:N).

- Produto ↔ Detalhes do Pedido:
** Produtos estão associados aos itens do pedido (N:M).

- Fornecedor ↔ Produto:
** Fornecedores disponibilizam produtos para venda (1:N).

- Estoque ↔ Produto:
** Um produto pode estar disponível em múltiplos estoques (N:M).


---
# 📦 DESAFIO 2 Bootcampo Suzano DIO - OFICINA Data Model
Descrição do Desafio - criação de um Projeto Conceitual de banco de dados de uma Oficina

Agora você irá criar um esquema conceitual do zero. A partir da narrativa fornecida você será capaz de criar todas as entidades, relacionamentos e atributos. Caso encontre algo que não foi definido na narrativa, utilize a sua compreensão do contexto e deixe uma descrição no README do seu github. para verificação.

O esquema deverá ser adicionado a um repositório do Github para futura avaliação do desafio de projeto. Adicione ao Readme a descrição do projeto conceitual para fornecer o contexto sobre seu esquema.

*** Objetivo:
Criar o esquema conceitual para o contexto de oficina com base na narrativa fornecida

*** Narrativa:
Sistema de controle e gerenciamento de execução de ordens de serviço em uma oficina mecânica
Clientes levam veículos à oficina mecânica para serem consertados ou para passarem por revisões periódicas
Cada veículo é designado a uma equipe de mecânicos que identifica os serviços a serem executados e preenche uma OS com data de entrega.
A partir da OS, calcula-se o valor de cada serviço, consultando-se uma tabela de referência de mão-de-obra
O valor de cada peça também irá compor a OS
O cliente autoriza a execução dos serviços
A mesma equipe avalia e executa os serviços
Os mecânicos possuem código, nome, endereço e especialidade
Cada OS possui: n°, data de emissão, um valor, status e uma data para conclusão dos trabalhos.

Agora é a sua vez de ser o protagonista! Implemente o desafio sugerido pela expert e suba seu projeto para um repositório próprio, com isso, você aumentará ainda mais seu portfólio de projetos no GitHub!

---
Sistema de Controle de Ordem de Serviço - Oficina Mecânica

## 📌 Visão Geral

Este projeto tem como objetivo desenvolver um sistema de controle e gerenciamento de execução de ordens de serviço em uma oficina mecânica. O sistema permite o cadastro de clientes, seus respectivos veículos, e a geração de ordens de serviço (OS) para manutenções, consertos e revisões. O projeto aborda o fluxo completo, desde a solicitação do serviço até a execução e entrega do veículo.

## 📌 Objetivos do Sistema

- Gerenciamento de Clientes e Veículos: Cadastra e vincula veículos aos respectivos clientes.
- Criação e Controle de Ordens de Serviço: Gera OS com descrição do serviço, peças necessárias, e cálculo de valores com base em tabela de referência de mão de obra.
- Atribuição de Equipes e Mecânicos: Define uma equipe responsável por cada OS, incluindo mecânicos especializados.
- Controle de Peças e Serviços: Permite a adicição de peças e serviços diretamente na OS, gerando um histórico completo.

---

## 🗂️ Modelagem Conceitual / Estrutura e Relacionamentos
🔖 A modelagem de dados segue o diagrama entidade-relacionamento (DER), contemplando as seguintes Entidades Principais:

1. Cliente: **Descrição**: Informações sobre o cliente (nome, telefone, endereço, etc.).
2. Veículo: **Descrição**: Detalhes do veículo, como marca, modelo, ano de fabricação e cliente associado.
3. Ordem de Serviço (OS): **Descrição**: Registra as ordens de serviço com informações como data de emissão, status, e valor total.
4. Peça: **Descrição**: Armazena as peças utilizadas nas ordens de serviço.
5. Tabela de Referência de Mão de Obra: **Descrição**: Descrição e valores de serviços prestados pela oficina.
6. Equipe: **Descrição**: Registro das equipes de trabalho disponíveis para execução das OS.
7. Responsável (Mecânico): **Descrição**: Mecânicos especializados, vinculados a equipes.
8. Detalhes da Ordem de Serviço: **Descrição**: Lista de serviços e peças associados a uma OS.

---

## ⚙️ Relacionamentos

**Um cliente possui vários veículos (1:N).

** Cada veículo pode gerar múltiplas ordens de serviço (1:N).

** Uma ordem de serviço pode ter diversos serviços e peças associados (1:N).

** Cada OS é atribuída a uma equipe de mecânicos (N:1).

** Os serviços são consultados a partir de uma tabela de referência de mão de obra (N:1).

Exemplo de Fluxo do Sistema

- O cliente leva o veículo para revisão.
- O veículo é vinculado a uma OS.
- A equipe de mecânicos realiza o diagnóstico e registra serviços e peças necessárias na OS.
- A OS é aprovada pelo cliente.
- Os serviços são executados e a OS é concluída.
- O veículo é entregue ao cliente, gerando um histórico completo da ordem de serviço.


** Contribuições:

Contribuições são bem-vindas!

