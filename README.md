# Importação de Notas de Corretagem

Este projeto foi desenvolvido para automatizar a importação de dados de notas de corretagem da **Clear Corretora** em formato PDF para planilhas Excel. O objetivo é facilitar o controle de investimentos, permitindo o cálculo de preço médio e auxiliando na organização para declaração de Imposto de Renda.

O código foi inspirado no vídeo ["Como importar notas de corretagem em PDF para planilha Excel usando Python"](https://www.youtube.com/watch?v=nY3RkLmuH1w) e permite processar múltiplas notas de uma só vez.

## Funcionalidades

- **Leitura de PDF**: Extrai informações de texto de arquivos PDF de notas de corretagem.
- **Processamento de Ordens**: Identifica e estrutura dados de operações (compra/venda), ativos, quantidades, preços e valores.
- **Mapeamento de Tickers**: Converte descrições de ativos (ex: "PETZ", "SANEPAR") para seus respectivos códigos de negociação na B3 (ex: "PETZ3", "SAPR4").
- **Exportação para Excel**:
  - `ordens.xlsx`: Lista detalhada de todas as ordens extraídas, nota por nota.
  - `resumo_ordens.xlsx`: Tabela consolidada agrupada por ativo e operação, com totais de quantidade e valor, e cálculo de preço médio.

## Pré-requisitos

Certifique-se de ter o [Python](https://www.python.org/) instalado em sua máquina.

As seguintes bibliotecas Python são utilizadas:
- [Pandas](https://pandas.pydata.org/): Para manipulação e análise de dados.
- [PyPDF2](https://pypi.org/project/PyPDF2/): Para leitura de arquivos PDF.
- [openpyxl](https://pypi.org/project/openpyxl/): Para criação e edição de arquivos Excel (.xlsx).

## Instalação

1. Clone este repositório:
   ```bash
   git clone https://github.com/rogeriopradoj/importacao-notas-corretagem.git
   cd importacao-notas-corretagem
   ```

2. Instale as dependências necessárias:
   ```bash
   pip install -r requirements.txt
   ```

## Como Usar

1. Crie uma pasta chamada `notas` dentro do diretório do projeto.
2. Coloque os arquivos PDF das suas notas de corretagem dentro desta pasta `notas`.
3. Execute o script principal:
   ```bash
   python import_nota.py
   ```
4. Após a execução, dois arquivos Excel serão gerados na raiz do projeto:
   - `ordens.xlsx`
   - `resumo_ordens.xlsx`

## Estrutura do Projeto

- `import_nota.py`: Script principal que orquestra a leitura dos PDFs, processamento e exportação para Excel.
- `fileprocessor.py`: Contém a lógica de extração de texto do PDF e identificação dos campos das ordens (Ticker, Operação, Quantidade, Preço, etc.).
- `order.py`: Define a classe `Order`, representando uma ordem de compra ou venda individual.
- `trading_note.py`: Define a classe `TradingNote`, representando uma nota de corretagem contendo múltiplas ordens.
- `requirements.txt`: Lista de dependências do projeto.
- `notas/`: Diretório onde devem ser colocados os arquivos PDF (criado pelo usuário).

## Nota

Este script foi configurado especificamente para o layout de notas de corretagem da **Clear Corretora**. Notas de outras corretoras podem ter layouts diferentes e exigir adaptações na lógica de extração de texto (`fileprocessor.py`).

## Créditos

Projeto original e tutorial por [Arthur Silveira Neto](https://www.linkedin.com/in/arthur-silveira-neto-8a0110b/).
Vídeo tutorial: [YouTube](https://www.youtube.com/watch?v=nY3RkLmuH1w)
