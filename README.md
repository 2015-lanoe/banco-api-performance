# Testes de Performance da API do Bancocom k6

Repositório: [banco-api-performance](https://github.com/2015-lanoe/banco-api-performance)

## 📌 Introdução
Este projeto contém scripts de testes de performance desenvolvidos em **JavaScript** utilizando a ferramenta **k6**.  
O objetivo é avaliar a performance e a resiliência da aplicação **Banco API**, simulando diferentes cargas de usuários, monitorando métricas em tempo real e gerando relatórios.

---

## 🛠️ Tecnologias Utilizadas
- [JavaScript](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript) → Linguagem de programação utilizada para os scripts.  
- [k6](https://k6.io/) → Ferramenta open-source para execução de testes de carga e performance. 
- [GJSON] (https://github.com/tidwall/gjson) - para extração de dados em resposta JSON.
- Variáveis de ambiente para configuração dinâmica (ex: `BASE_URL`).

---

## 📂 Estrutura do Repositório
```bash
banco-api-performance/
├── fixtures/              # Dados de entrada para os testes (ex: usuários, payloads)
├── helpers/               # Funções utilitárias reutilizáveis para interação com a API
├── tests/                 # Casos de testes organizados por módulos da API
├── config/                # Arquivo de configuração de variável de ambiente
├── utils/                 # Funções utilitárias
│── README.md              # Documentação do projeto
```

---

## 🎯 Objetivo de Cada Grupo de Arquivos
- **`fixtures/`** → Dados de entrada para os testes (ex: usuários, payloads)
- **`helpers/`** → Funções utilitárias reutilizáveis para interação com a API
- **`tests/`** → Casos de testes organizados por módulos da API
- **`utils/`** → Funções auxiliares e utilitárias que podem ser reaproveitadas em diferentes testes.  
- **`config/`** → Arquivo de configuração de variável de ambiente

---

## ⚙️ Instalação do Projeto
1. Clone o repositório:
   ```bash
   git clone https://github.com/2015-lanoe/banco-api-performance.git
   cd banco-api-performance
   ```

2. Instale o k6:  
   - **Linux/macOS**:  
     ```bash
     brew install k6
     ```  
   - **Windows (via Chocolatey)**:  
     ```bash
     choco install k6

3 - Configure as Variáveis de Ambiente:

    Altere o arquivo `config.local.json`e defina a BASE_URL a ser testada

    ```json
    {
    "baseUrl": "http://localhost:3000"
    }

    Essas variáveis erão usadas dinamicamente nos testes para montar as requisições

---

## ▶️ Execução dos Testes
Antes de executar, configure a variável de ambiente `BASE_URL`, que será utilizada como endereço base da API:  
```bash
export BASE_URL=https://sua-api.com   # Linux/macOS
set BASE_URL=https://sua-api.com      # Windows (cmd)
$env:BASE_URL="https://sua-api.com"   # Windows (PowerShell)
```

### Executando os scripts de teste
```bash
k6 run tests/login.test.js

Certifique-se de passar a variável de ambiente `BASE_URL` 
caso nao esteja usando um config.local.json 
ou uma abordagem de carregamento automático.

```bash
k6 run tests/autenticacao/login.tests.js -e
BASE_URL=http://localhost:3000
 
### 📊 Execução com relatório em tempo real
Para acompanhar os resultados em tempo real no dashboard do **k6**, utilize:
```bash
K6_WEB_DASHBOARD=true \
K6_WEB_DASHBOARD_EXPORT=html-report.html\
k6 run tests/autenticacao/login.tests.js \
-e BASE_URL=http://localhost:3000 \
```

### 💾 Exportação do relatório
Também é possível exportar o relatório em HTML:
```bash
K6_WEB_DASHBOARD=true K6_WEB_DASHBOARD_EXPORT=html-report.html k6 run 
```

O relatório será salvo no arquivo `html-report.html`.
