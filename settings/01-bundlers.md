# bundler

* Agrupa/empacota arquivos e suas dependências para otimizar o carregamento da página.

## Funcionamento:

    - Geração do gráfico de dependências e

    - Empacotamento de arquivos.

* O Bundler identifica as dependências dos arquivos, cria um mapa de relacionamento e gera um único arquivo de saída para o navegador processar.

## Processo:

    - Resolução de dependências e

    - Empacotamento.

## Objetivo:

* Melhorar o carregamento da página

## Gráfico de Dependências:

* Passos:

    1. Resolução de Dependências: Gera um mapa de relacionamento de todos os arquivos servidos.

    2. Requer um arquivo de entrada (geralmente, o arquivo principal).

    3. Analisa o arquivo de entrada, para entender suas dependências.

    4. Faz uma relação das dependências e de suas subdependências.

    5. Packing: Entrega ativos estáticos - integra os vários arquivos de código em um único.
