meu-dashboard-decibeis

Dashboard web para análise de níveis sonoros em decibéis. A página consulta uma API, exibe as leituras em um gráfico de linha ao longo do tempo e permite filtrar os dados por período.

Projeto acadêmico, feito em uma única página HTML, sem etapa de build.

Funcionalidades
Gráfico de linha com o nível de decibéis (dB) ao longo do tempo
Filtro por data e hora de início e de fim
Período inicial padrão: últimas 24 horas
Tooltip com data e hora completas no formato brasileiro
Mensagens de carregamento, de erro e de ausência de dados para o período
Layout responsivo
Tecnologias
Tecnologia	Uso
HTML5	Estrutura da página
JavaScript	Busca de dados e renderização do gráfico
Tailwind CSS (CDN)	Estilização
Chart.js (CDN)	Gráfico de linha

Não há dependências para instalar. As bibliotecas são carregadas por CDN, então é necessário acesso à internet.

Estrutura do projeto
meu-dashboard-decibeis/
├── index.html   # Página, estilos e script do dashboard
└── README.md
Como executar
Clone o repositório:
bash
   git clone https://github.com/Vinicius-jafe/meu-dashboard-decibeis.git
Entre na pasta do projeto:
bash
   cd meu-dashboard-decibeis
Abra o index.html no navegador, ou sirva a pasta localmente:
bash
   python -m http.server 8000

Depois acesse http://localhost:8000.

Também é possível usar a extensão Live Server do VS Code.

Configuração da API

O dashboard busca os dados em uma API externa. O endereço é definido pela constante API_BASE_URL, no script do arquivo index.html:

js
const API_BASE_URL = 'https://seu-servico.exemplo.com';

Altere o valor para o endereço público do seu back-end (por exemplo, um serviço hospedado no Render) ou para um endereço local, como http://localhost:3000.

Contrato esperado da API

Requisição

GET {API_BASE_URL}/api/decibeis?startDate=AAAA-MM-DDTHH:mm&endDate=AAAA-MM-DDTHH:mm

Os parâmetros startDate e endDate são opcionais e usam o formato do campo datetime-local.

Resposta

Um JSON com uma lista de leituras, cada uma contendo:

Campo	Tipo	Descrição
data	texto	Data e hora da leitura
valor	número	Nível sonoro em decibéis

Exemplo:

json
[
  { "data": "2025-06-01 14:30:00", "valor": 62.4 },
  { "data": "2025-06-01 14:31:00", "valor": 65.1 }
]

Como a página é aberta em um domínio diferente do da API, o back-end precisa permitir requisições entre origens (CORS).

Como usar
Abra a página. Ela carrega automaticamente as leituras das últimas 24 horas.
Ajuste a data e hora de início e a data e hora de fim.
Clique em Aplicar Filtro para atualizar o gráfico.

Não há atualização automática: é preciso clicar em Aplicar Filtro para buscar novos dados.

Projeto relacionado

O repositório Iotnewlaws é o serviço Flask que recebe as leituras de decibéis e as grava em um banco SQLite.

Licença

Projeto acadêmico, sem fins comerciais.
