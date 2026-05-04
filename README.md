# Sistema de Gestão de Leads (MongoDB)

Projeto desenvolvido para a disciplina de Banco de Dados Não Relacional, com o objetivo de modelar e implementar um sistema de gestão de leads utilizando MongoDB.

---

## Tecnologias Utilizadas

- MongoDB (mongosh)  
- JavaScript (scripts de banco)  
- Modelagem NoSQL  

---

## Estrutura do Banco

**Banco de dados:** `leads_db`

**Coleções:**

- `users`: usuários do sistema (admin, gerente, atendente)  
- `stores`: lojas/unidades  
- `customers`: clientes  
- `leads`: oportunidades de contato  
- `negotiations`: negociação dos leads  
- `logs`: registro de ações no sistema  

---

## Modelagem

### Referencing (Relacionamentos)

Utilizado para conectar entidades independentes:

- `leads.customerId` → `customers`  
- `leads.storeId` → `stores`  
- `leads.attendantId` → `users`  
- `customers.createdBy` → `users`  
- `negotiations.leadId` → `leads`  
- `logs.userId` → `users`  

**Motivo:**
- Evitar duplicação  
- Permitir reutilização dos dados  

---

### Embedding (Documento Embutido)

Utilizado na coleção `negotiations`:

```json
history: [
  {
    stage: "contato_inicial",
    status: "aberta",
    changedAt: Date,
    changedBy: ObjectId
  }
]
