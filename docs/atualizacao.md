# TECHDEX 1.0 — Guia de Expansão e Atualização da Base

Este documento descreve o fluxo passo a passo para cadastrar novos dispositivos, atualizar especificações ou expandir o modelo semântico.

---

## 1. Como Cadastrar um Novo Dispositivo

1. Abra o arquivo `data/dispositivos.csv`.
2. Adicione uma nova linha respeitando a formatação:
   - **DeviceID**: Próximo código sequencial livre (ex: `TDX-0086`).
   - **Nome**: Nome de mercado (ex: `ESP32-P4`).
   - **Modelo**: Código de part number oficial.
   - **FabricanteID**: ID correspondente em `fabricantes.csv`.
   - **CategoriaID**: Número de 1 a 8 em `categorias.csv`.
   - **Subcategoria** e **Familia**.
   - **Descricoes**, **ImagemURL**, **DatasheetURL** e **StatusCicloVida**.
   - **DataUltimaValidacao**: Data corrente `AAAA-MM-DD`.
3. Insira as especificações na tabela fato `data/especificacoes.csv`:
   - Associe o `DeviceID` aos `AtributoID` correspondentes (1 a 15).
   - Preencha `ValorNumerico` para grandezas escalares (Clock, RAM, Flash, GPIOs, ADC, Sleep Current) e `ValorTexto` para nomes de arquitetura.
4. Mapeie os protocolos suportados na tabela ponte `data/ponte_dispositivo_protocolo.csv`.
5. Salve os arquivos em formato **UTF-8 com BOM** para preservar acentuações e caracteres técnicos.

---

## 2. Atualização no Power BI Desktop

1. Abra o arquivo `TECHDEX.pbip` ou `TECHDEX.pbix` no Power BI Desktop.
2. Na guia **Página Inicial (Home)**, clique no botão **Atualizar (Refresh)**.
3. Todas as consultas M lerão os arquivos CSV atualizados instantaneamente.
4. Os indicadores dinâmicos do cabeçalho (`TotalDispositivos`, `TotalFabricantes`) e os filtros do catálogo serão recalculados automaticamente sem necessidade de editar nenhum visual.

---

## 3. Atualização Agendada no Power BI Service

Para manter a base sincronizada em produção na nuvem:
1. Armazene os arquivos CSV em um repositório GitHub público ou em uma pasta do SharePoint / OneDrive corporativo.
2. No Power Query, utilize `Web.Contents("URL_DO_RAW_GITHUB")` ou a função nativa `SharePoint.Files`.
3. Dessa forma, a atualização no Power BI Service ocorrerá de forma 100% autônoma na nuvem, **sem necessidade de Gateway de Dados Local**.
