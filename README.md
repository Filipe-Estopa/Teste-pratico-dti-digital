Teste Prático DTI – Simulador de Entregas com Drones
 1. Descrição do Projeto

Este projeto simula a operação de drones urbanos para entrega de pedidos, conforme proposto no Desafio Técnico da DTI.
Foi desenvolvido utilizando Node.js + Express no backend e um frontend visual simples para testar.

Principais funcionalidades:

 Criação de pedidos com coordenadas, peso e prioridade

 Fila de entregas por prioridade (alta → média → baixa)

 Alocação automática de pedidos em drones disponíveis

 Cálculo de tempo de entrega com base em distância

 Métricas de desempenho (tempo médio e total de entregas)

 Frontend completo e testes unitários com Jest

 2. Tecnologias Utilizadas

Backend: Node.js, Express

Frontend: HTML + JS simples (sem frameworks)

Testes: Jest

Simulação: Fila com prioridade e loop de processamento a cada 2 segundos

 3. Como executar o projeto
 Pré-requisitos:

Node.js
 (v16 ou superior)

npm (geralmente vem junto com Node)

 Instalação:
npm install

 Executar o servidor:
npm run dev


Abra no navegador:
 http://localhost:3000

A interface frontend aparecerá, permitindo criar pedidos, ver drones, métricas e logs visualmente.

 4. Executar Testes Unitários

O projeto possui testes unitários com Jest para regras principais:

 calcTempoEntrega → cálculo de distância/tempo

 filaPrioridade → ordenação correta da fila de pedidos

 droneCapacidade → rejeição de pedidos acima da capacidade do drone

Para rodar os testes:

npm test


Saída esperada 

 PASS  tests/calcTempo.test.js
 PASS  tests/filaPrioridade.test.js
 PASS  tests/droneCapacidade.test.js

Test Suites: 3 passed, 3 total
Tests:       5 passed, 5 total

 5. Regras de Negócio e Cálculos
 Coordenadas e Distância

Cada pedido é criado com coordenadas (x, y) no plano cartesiano.

A base dos drones está em (0, 0).

A distância é calculada com fórmula de Pitágoras:

Dist
a
ˆ
ncia
=
𝑥
2
+
𝑦
2
Dist
a
ˆ
ncia=
x
2
+y
2
	​


Exemplo:
Pedido em (3,4) → Distância = √(3² + 4²) = 5 unidades

⏱️ Tempo de Entrega

O tempo estimado de entrega é igual à distância, arredondado para cima (Math.ceil).

O tempo é usado para métricas, mas a simulação roda acelerada (500ms por entrega).

📦 Fila de Pedidos

Os pedidos entram em uma fila priorizada:

Alta prioridade = 1

Média = 2

Baixa = 3

A fila é ordenada por prioridade e depois por ordem de chegada (FIFO).

Exemplo de ordem:

[ Alta #1, Alta #2, Média #1, Baixa #1 ]

🚁 Drones

Dois drones simulados:

drone-1: capacidade 10 kg, alcance 30 unidades

drone-2: capacidade 8 kg, alcance 25 unidades

Regras:

Um drone pega sempre o próximo pedido disponível na fila.

Se o peso do pedido for maior que a capacidade, ele é rejeitado.

Se a distância for maior que o alcance, ele também é rejeitado.

Cada drone pode processar apenas um pedido por vez.

📊 Métricas

Total de entregas concluídas ✅

Tempo médio de entrega (baseado nas distâncias simuladas)

Endpoint:

GET /metricas


Exemplo de resposta:

{
  "entregasRealizadas": 3,
  "tempoMedioEntregaMinutos": 14.67
}

🌐 6. Frontend

O projeto inclui um frontend simples em public/ para evitar uso de Postman:

📍 Formulário para criar pedidos unitários

📋 Campo para criar pedidos em lote (JSON)

🗺️ Mapa com base, pedidos e drones

📊 Painel de métricas e log de ações

Basta acessar:
👉 http://localhost:3000

🧱 7. Estrutura de Pastas
Teste_Pratico_DTI/
├── public/              # Frontend
├── src/
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   ├── services/
│   └── utils/
├── tests/               # Testes unitários Jest
├── package.json
└── README.md

🏆 8. Diferenciais Implementados

✅ Fila de pedidos com prioridade real

✅ Simulação automática de entregas (sem necessidade de disparo manual)

✅ Métricas em tempo real

✅ Frontend amigável

✅ Testes unitários com Jest

✅ Código modular e organizado

📌 9. Possíveis Extensões Futuras

🔋 Simulação real de bateria e recarga de drones

📦 Agrupamento de pedidos para otimizar viagens (bin packing)

🛰️ Visualização animada dos drones no mapa

🧠 Algoritmos mais complexos de alocação
