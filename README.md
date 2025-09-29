#  Teste Prático DTI – Simulador de Entregas com Drones

Este projeto simula a operação de drones urbanos para entrega de pedidos, conforme proposto no Desafio Técnico da DTI.  
Foi desenvolvido com **Node.js + Express** no backend e um **frontend simples** para testes diretos, sem necessidade de Postman.

---

##  1. Funcionalidades Principais

-  **Criação de pedidos** com coordenadas, peso e prioridade  
-  **Fila de entregas priorizada** (Alta → Média → Baixa)  
-  **Alocação automática** de pedidos em drones disponíveis  
-  **Cálculo de tempo de entrega** com base na distância  
-  **Métricas de desempenho** (tempo médio e total de entregas)  
-  **Frontend completo** e testes unitários com Jest

---

##  2. Tecnologias Utilizadas

| Camada        | Tecnologias                       |
|--------------|------------------------------------|
| Backend      | Node.js, Express                   |
| Frontend     | HTML + JS simples (sem frameworks) |
| Testes       | Jest                              |
| Simulação    | Fila com prioridade + loop 2s     |

---

##  3. Como Executar o Projeto

###  Pré-requisitos

- [Node.js](https://nodejs.org/) (v16 ou superior)  
- npm (já vem incluso com Node)

###  Instalação

```bash
npm install
```

## Executar o servidor

```bash
npm run dev
```

Acesse no navegador:
 http://localhost:3000

Você verá a interface para criar pedidos, acompanhar drones, métricas e logs.

---

## 4. Executar Testes Unitários

O projeto contém testes unitários com Jest, cobrindo as principais regras de negócio:

. calcTempoEntrega → cálculo de distância/tempo

. filaPrioridade → ordenação correta da fila

. droneCapacidade → rejeição de pedidos acima da capacidade

### Rodar testes

```bash
npm test
```

###Saída esperada

```bash
 PASS  tests/calcTempo.test.js
 PASS  tests/filaPrioridade.test.js
 PASS  tests/droneCapacidade.test.js

Test Suites: 3 passed, 3 total
Tests:       5 passed, 5 total
```

---

## 5. Regras de Negócio e Cálculos

### Coordenadas e Distância

Cada pedido possui coordenadas (x, y) no plano cartesiano.

A base dos drones fica em (0, 0).

A distância é calculada com Pitágoras:

<img width="231" height="63" alt="image" src="https://github.com/user-attachments/assets/7893f4fe-c4b5-41a9-bb6c-79951c16e96f" />

Exemplo:
Pedido em (3,4) → Distância = √(3² + 4²) = 5 unidades

⏱️ Tempo de Entrega
Tempo estimado = distância arredondada para cima (Math.ceil)

A simulação roda acelerada (500 ms por entrega) para fins de teste.

### Fila de Pedidos

Prioridades:

Prioridade	Valor
Alta	1
Média	2
Baixa	3

A fila é ordenada por prioridade e depois FIFO (ordem de chegada).
Exemplo:
[ Alta #1, Alta #2, Média #1, Baixa #1 ]

### Drones

Dois drones simulados:

Drone	Capacidade	Alcance
drone-1	10 kg	30 u.
drone-2	8 kg	25 u.

### Regras:

Drone pega sempre o próximo pedido da fila

Se peso > capacidade → rejeitado

Se distância > alcance → rejeitado

Cada drone processa 1 pedido por vez

## Métricas

Endpoint:

```bash
GET /metricas
```

###Resposta exemplo:

```bash
{
  "entregasRealizadas": 3,
  "tempoMedioEntregaMinutos": 14.67
}
```

###Inclui:

Total de entregas concluídas ✅

Tempo médio de entrega

---

## 6. Frontend

Localizado em public/ — permite uso direto via navegador.

### Funcionalidades:

 Formulário para criar pedidos unitários

 Campo para criar pedidos em lote (JSON)

 Mapa com base, pedidos e drones

 Painel de métricas e log de ações

Acesse:
 http://localhost:3000

 7. Estrutura de Pastas

```bash
Teste_Pratico_DTI/
├── public/              # Frontend
├── src/
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   ├── services/
│   └── utils/
├── tests/               # Testes unitários (Jest)
├── package.json
└── README.md
```

---

## 8. Diferenciais Implementados

✅ Fila de pedidos com prioridade real
✅ Simulação automática de entregas
✅ Métricas em tempo real
✅ Frontend amigável
✅ Testes unitários com Jest
✅ Código modular e organizado

