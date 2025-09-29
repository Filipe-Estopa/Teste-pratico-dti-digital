#  Teste Prático DTI — Simulador de Entregas com Drones

Este projeto implementa um **sistema de entregas por drones**, com **fila de pedidos por prioridade**, cálculo de tempo de entrega, controle de capacidade dos drones, métricas de desempenho e uma **interface web simples** para interação sem precisar usar Postman.

---

## 📂 Estrutura do Projeto

Teste_Pratico_DTI/
├── src/
│ ├── controllers/
│ ├── models/
│ ├── routes/
│ ├── services/
│ ├── utils/
│ │ └── calcTempo.js
│ └── app.js
├── public/ # Frontend (interface visual)
│ └── index.html
├── tests/ # Testes unitários
│ ├── calcTempo.test.js
│ ├── droneCapacidade.test.js
│ └── filaPrioridade.test.js
├── jest.config.js
├── package.json
└── README.md

yaml
Copiar código

---

## 🛠️ Requisitos

- **Node.js** ≥ 16  
- **npm** ≥ 8

---

## ⚡ Instalação

1. Clone o repositório ou extraia o ZIP  
2. No terminal, acesse a pasta raiz do projeto:

   ```bash
   cd Teste_Pratico_DTI
Instale as dependências:

bash
Copiar código
npm install
 Executar o Servidor
bash
Copiar código
npm run dev
Por padrão, o servidor inicia em:
 http://localhost:3000

 Interface Web (Frontend)
Basta abrir no navegador:

 http://localhost:3000

A interface permite:

Criar múltiplos pedidos de uma vez

Atribuir prioridade a cada entrega

Visualizar fila e entregas realizadas

Ver métricas em tempo real (tempo médio, total de entregas, drones ativos)

 Endpoints Principais (API REST)
 Criar Pedido
POST /api/pedidos

json
Copiar código
{
  "id": "pedido-1",
  "peso": 5,
  "prioridade": 2,
  "destino": { "x": 3, "y": 4 }
}
 Listar Pedidos
GET /api/pedidos

 Métricas
GET /api/metricas

Retorna dados como tempo médio de entrega, total de entregas e pedidos pendentes.

 Cálculos Importantes
 Tempo de entrega
Calculado pela distância Euclidiana do ponto de origem (0,0) até o destino:

<img width="488" height="46" alt="image" src="https://github.com/user-attachments/assets/96769478-1648-4aaf-b380-e3ca24c00df6" />


Exemplo: destino (3,4) → distância = 5 → tempo = 5 min

 Bateria
Cada drone tem uma capacidade máxima e autonomia (em minutos).
Antes de cada entrega:

Se peso do pedido > capacidade do drone → rejeita

Se tempoEntrega > autonomia do drone → rejeita

 Número de viagens
Cada drone só faz 1 entrega por vez.
Após concluir, ele é marcado como disponível e pega o próximo pedido da fila de prioridade.

 Testes Unitários
O projeto utiliza Jest com suporte a ES Modules.

 Configuração especial (Windows)
No package.json:

json
Copiar código
"scripts": {
  "test": "set NODE_OPTIONS=--experimental-vm-modules && jest"
}
 Rodar os testes
bash
Copiar código
npm test
Os testes cobrem:

calcTempoEntrega (cálculo de tempo por coordenadas)

Regras de capacidade dos drones

Ordenação por prioridade na fila de pedidos

 Tecnologias Utilizadas
Node.js + Express — Backend

HTML/CSS/JS — Frontend simples

Jest — Testes unitários

ES Modules — Import/export modernos

 Possíveis Melhorias Futuras
Controle mais elaborado de bateria e recarga

Múltiplas bases de operação

Interface mais avançada com mapas reais

Dockerfile para deploy rápido
