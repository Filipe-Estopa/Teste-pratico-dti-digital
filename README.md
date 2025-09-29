# 🚁 Teste Prático DTI — Simulador de Entregas com Drones

```plaintext
Teste_Pratico_DTI/
├── src/
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   ├── services/
│   ├── utils/
│   │   └── calcTempo.js
│   └── app.js
├── public/              # Frontend (interface visual)
│   └── index.html
├── tests/               # Testes unitários
│   ├── calcTempo.test.js
│   ├── droneCapacidade.test.js
│   └── filaPrioridade.test.js
├── jest.config.js
├── package.json
└── README.md
🛠️ Requisitos
plaintext
Copiar código
- Node.js ≥ 16
- npm ≥ 8
⚡ Instalação
bash
Copiar código
cd Teste_Pratico_DTI
npm install
▶️ Executar o Servidor
bash
Copiar código
npm run dev
plaintext
Copiar código
Servidor: http://localhost:3000
🌐 Interface Web (Frontend)
plaintext
Copiar código
- Criar múltiplos pedidos de uma vez
- Atribuir prioridade a cada entrega
- Visualizar fila e entregas realizadas
- Ver métricas em tempo real (tempo médio, total de entregas, drones ativos)
📡 Endpoints Principais (API REST)
http
Copiar código
POST /api/pedidos
json
Copiar código
{
  "id": "pedido-1",
  "peso": 5,
  "prioridade": 2,
  "destino": { "x": 3, "y": 4 }
}
http
Copiar código
GET /api/pedidos
GET /api/metricas
🧮 Cálculos Importantes
plaintext
Copiar código
Tempo de entrega = ceil( sqrt(x² + y²) )

Exemplo: destino (3,4)
distância = 5
tempoEntrega = 5 minutos
plaintext
Copiar código
Bateria:
- Se peso do pedido > capacidade do drone → rejeita
- Se tempoEntrega > autonomia do drone → rejeita
plaintext
Copiar código
Número de viagens:
- Cada drone faz 1 entrega por vez.
- Após concluir, ele pega o próximo pedido da fila de prioridade.
🧪 Testes Unitários
json
Copiar código
"scripts": {
  "test": "set NODE_OPTIONS=--experimental-vm-modules && jest"
}
bash
Copiar código
npm test
plaintext
Copiar código
Testes cobrem:
- calcTempoEntrega (cálculo de tempo)
- Regras de capacidade dos drones
- Ordenação por prioridade da fila
📝 Tecnologias Utilizadas
plaintext
Copiar código
- Node.js + Express — Backend
- HTML/CSS/JS — Frontend simples
- Jest — Testes unitários
- ES Modules — Import/export modernos
🧠 Possíveis Melhorias Futuras
plaintext
Copiar código
- Controle mais elaborado de bateria e recarga
- Múltiplas bases de operação
- Interface mais avançada com mapas reais
- Dockerfile para deploy rápido
