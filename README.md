Desafio: Executando Tarefas Automatizadas com AWS Lambda e S3
🧠 Descrição

Este projeto tem como objetivo aplicar, na prática, os conceitos de automação de tarefas utilizando AWS Lambda e Amazon S3, simulando um ambiente de processamento de arquivos com LocalStack.
A proposta demonstra como funções Lambda podem reagir automaticamente a eventos em um bucket S3 — como o upload de arquivos — realizando ações como processamento, registro e armazenamento de dados em uma tabela DynamoDB.

🧭 Roteiro de Implementação
1. Entendendo o Amazon S3

O Amazon S3 é um serviço de armazenamento de objetos utilizado para guardar arquivos (imagens, logs, relatórios, etc.).
Cada arquivo é chamado de objeto e fica dentro de um bucket.
É possível definir eventos automáticos, como “executar uma função Lambda quando um novo arquivo for adicionado”.

💡 Insight: “O S3 é o gatilho perfeito para automações: sempre que algo novo chega, algo pode acontecer.”
