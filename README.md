# 🧩 Desafio: Executando Tarefas Automatizadas com AWS Lambda e S3  

## 🧠 Descrição  
Este projeto tem como objetivo aplicar, na prática, os conceitos de automação de tarefas utilizando **AWS Lambda** e **Amazon S3**, simulando um ambiente de processamento de arquivos com **LocalStack**.  
A proposta demonstra como funções Lambda podem reagir automaticamente a eventos em um bucket S3 — como o upload de arquivos — realizando ações como **processamento**, **registro** e **armazenamento de dados** em uma tabela **DynamoDB**.  

---

## 🧭 Roteiro de Implementação  

### 1. Entendendo o Amazon S3  
O **Amazon S3** é um serviço de armazenamento de objetos utilizado para guardar arquivos (imagens, logs, relatórios, etc.).  
Cada arquivo é chamado de **objeto** e fica dentro de um **bucket**.  
É possível definir **eventos automáticos**, como “executar uma função Lambda quando um novo arquivo for adicionado”.  

💡 *Insight:* “O S3 é o gatilho perfeito para automações: sempre que algo novo chega, algo pode acontecer.”  

---

### 2. Entendendo o AWS Lambda  
O **AWS Lambda** permite executar código sem precisar gerenciar servidores.  
Você escreve uma função, define o evento que a dispara (ex.: upload em um bucket S3) e a AWS cuida de toda a execução.  
O modelo de cobrança é **pay-per-use**, ou seja, você paga apenas pelo tempo de execução.  

💡 *Insight:* “Lambda é o motor invisível das automações na nuvem — ágil, leve e escalável.”  

---

### 3. Upload de Arquivos com Processamento e Registro no DynamoDB  
O fluxo de automação pode ser configurado para que o **Lambda**:  
- Leia o arquivo recém-enviado ao S3;  
- Processe o conteúdo (ex.: extração de metadados);  
- Registre as informações em uma tabela **DynamoDB**.  

---

### 4. Configurando AWS Localmente com LocalStack  
O **LocalStack** permite simular os principais serviços da AWS em ambiente local — sem custos.  
É ideal para testes e desenvolvimento de integrações entre **S3**, **Lambda** e **DynamoDB**.  

**Comandos básicos:**  
```bash
localstack start
awslocal s3 mb s3://meu-bucket
awslocal dynamodb create-table ...

---

### 5. Criando os Recursos

Nesta etapa, são criados os recursos que simulam o ambiente AWS real:

- **Buckets S3** para armazenamento dos arquivos;  
- **Tabelas DynamoDB** para registro das informações processadas;  
- **Funções Lambda** para execução automática das tarefas.

O evento **S3:ObjectCreated:\*** deve ser mapeado para acionar a função Lambda sempre que um novo objeto for adicionado ao bucket.

> 💡 *Insight:* “Cada upload é um disparo de automação — eliminando processos manuais e aumentando a eficiência.”

---

### 6. Trabalhando com LocalStack (Parte 1 e 2)

Com o ambiente configurado, é hora de validar o fluxo completo:

1. Faça o upload de arquivos localmente para o bucket S3 simulado:
   ```bash
   awslocal s3 cp caminho/do/arquivo.pdf s3://meu-bucket

2. Observe se a função Lambda foi executada automaticamente (ver logs do LocalStack / container).

3. Verifique o registro dos dados processados na tabela DynamoDB dentro do ambiente LocalStack:

awslocal dynamodb scan --table-name NomeDaTabela

💡 *Insight:* “Testar localmente é o passo mais seguro antes de levar a automação para a nuvem real.”

---

### 7. Estudo de Caso — Processamento Automático de Currículos

**Cenário:** Sistema automatizado de triagem de currículos.

**Fluxo de automação:**

- Um arquivo .pdf é enviado ao bucket S3;
- A função Lambda é acionada e extrai informações básicas (ex.: nome, e-mail);
- Os dados extraídos são salvos em uma tabela DynamoDB para posterior análise.

💡 *Insight:* “A automação transforma tarefas repetitivas em inteligência operacional — permitindo decisões mais rápidas e precisas.”

---

⚙️ ## Tecnologias Utilizadas

**AWS Lambda**
**Amazon S3**
**Amazon DynamoDB**
**LocalStack**
**Python 3.x**
**AWS CLI / AWS SDK (Boto3)**

---

🚀 ### Como Executar Localmente

1. Inicie o LocalStack:
bash
localstack start

2. Crie o bucket e a tabela (exemplos):
bash
awslocal s3 mb s3://meu-bucket
awslocal dynamodb create-table \
  --table-name Curriculos \
  --attribute-definitions AttributeName=Id,AttributeType=S \
  --key-schema AttributeName=Id,KeyType=HASH \
  --provisioned-throughput ReadCapacityUnits=5,WriteCapacityUnits=5

3. Faça o upload de um arquivo para testar:
bash
awslocal s3 cp arquivo.pdf s3://meu-bucket

4. Verifique logs e registros:

Consulte os logs do Lambda no console/LocalStack;
Confira itens na tabela DynamoDB:
bash
awslocal dynamodb scan --table-name Curriculos

---

✨ **Insight Final:**
“Automatizar é transformar tarefas manuais em reações inteligentes — e o Lambda com S3 é o par perfeito para isso.”

