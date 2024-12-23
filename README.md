# Desenvolvimento
Repositório criado para armazenar atividades de teste em cursos/bootcamp
O desafio 1 do Bootcamp Suzano se refere ao refinamento de um Projeto Conceitual de banco de dados de um E-Commerce

O Item salvo corresponde a esse refinamento, 
Descrição do Desafio
O esquema deverá ser adicionado a um repositório do Github para futura avaliação do desafio de projeto. Adicione ao Readme a descrição do projeto conceitual para fornecer o contexto sobre seu esquema.

Objetivo:
Refine o modelo apresentado acrescentando os seguintes pontos:

Cliente PJ e PF – Uma conta pode ser PJ ou PF, mas não pode ter as duas informações;
Pagamento – Pode ter cadastrado mais de uma forma de pagamento;
Entrega – Possui status e código de rastreio;
Agora é a sua vez de ser o protagonista! Implemente o desafio sugerido pela expert e suba seu projeto para um repositório próprio, com isso, você aumentará ainda mais seu portfólio de projetos no GitHub!

# 📦 E-commerce Data Model
DESAFIO 1
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
Cliente ↔ Pedido:

** Um cliente pode ter vários pedidos (1:N).
Pedido ↔ Detalhes do Pedido:

** Um pedido possui múltiplos itens (1:N).
Pedido ↔ Pagamento:

** Um pedido pode ter múltiplos pagamentos associados (parciais, complementares ou estornos). (1:N).
Produto ↔ Detalhes do Pedido:

** Produtos estão associados aos itens do pedido (N:M).
Fornecedor ↔ Produto:

** Fornecedores disponibilizam produtos para venda (1:N).
Estoque ↔ Produto:

** Um produto pode estar disponível em múltiplos estoques (N:M).
Estoque ↔ Produto:

---
