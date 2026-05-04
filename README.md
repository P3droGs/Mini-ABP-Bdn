Sistema de Gestão de Leads (MongoDB)
Projeto desenvolvido para a disciplina de Banco de Dados Não Relacional, com o objetivo de modelar e implementar um sistema de gestão de leads utilizando MongoDB.

Tecnologias Utilizadas
MongoDB (mongosh)

JavaScript (scripts de banco)

Modelagem NoSQL

Estrutura do Banco
Banco de dados: leads_db

Coleções:

users: usuários do sistema (admin, gerente, atendente)

stores: lojas/unidades

customers: clientes

leads: oportunidades de contato

negotiations: negociação dos leads

logs: registro de ações no sistema

Modelagem
Referencing (Relacionamentos)
Utilizado para conectar entidades independentes:

leads.customerId -> customers

leads.storeId -> stores

leads.attendantId -> users

customers.createdBy -> users

negotiations.leadId -> leads

logs.userId -> users

Motivo: evitar duplicação e permitir reutilização dos dados.

Embedding (Documento embutido)
Utilizado na coleção negotiations:

JSON
history: [
  {
    stage: "contato_inicial",
    status: "aberta",
    changedAt: Date,
    changedBy: ObjectId
  }
]
Motivo:

Histórico pertence apenas à negociação

Sempre será consultado junto

Melhora a performance

Regras de Negócio
Cada lead está vinculado a um cliente

Cada lead pertence a uma loja e um atendente

Apenas uma negociação por lead

Registro de histórico de negociação (embedding)

Controle de status e estágio

Dados Inseridos
5 usuários

3 lojas

5 clientes

10 leads

10 negociações

10 logs

Consultas Implementadas
$and: múltiplas condições

$or: alternativas

$gt / $lt: intervalos

$exists: verificação de campo

Projeção: seleção de campos

sort: ordenação

skip + limit: paginação

Aggregations (Dashboard)
Foram criados pipelines utilizando:

$match

$group

$sort

$project

Métricas:

Leads por origem

Leads por status

Taxa de conversão

Leads por atendente

Leads por importância

Como Executar
Abrir o MongoDB (mongosh)

Executar o comando: use leads_db

Rodar os scripts na ordem:

Criação das coleções

Inserção de dados

Consultas

Aggregations

Objetivo do Projeto
Demonstrar o uso prático de:

Modelagem NoSQL

Referencing vs Embedding

Operações CRUD

Consultas avançadas

Aggregation Framework

Conclusão
O projeto demonstra como o MongoDB permite uma modelagem flexível e eficiente, combinando referencing e embedding para atender diferentes necessidades de desempenho e organização.
