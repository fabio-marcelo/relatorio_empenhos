# Gerador de Relatórios de Empenho

Este projeto contém um script em R automatizado para processar planilhas de empenhos (formato CSV) e gerar automaticamente relatórios individuais em formato PDF, agrupados por fornecedor e ata.

O sistema foi projetado para ser autossuficiente: ele instala automaticamente as bibliotecas necessárias e configura o motor de geração de PDF (LaTeX/TinyTeX) caso não estejam presentes no seu computador.

## Pré-requisitos

1. **R e RStudio**: Certifique-se de ter o [R](https://cran.r-project.org/) e o [RStudio](https://posit.co/download/rstudio-desktop/) instalados na sua máquina.

2. **Permissões**: O script precisa de permissão de escrita na pasta onde está localizado para criar a subpasta `Relatorios_PDF`.

## Como usar

1. **Prepare seus dados**:
   * O arquivo deve estar no formato `.csv` (separado por ponto e vírgula `;`).
   * O script espera que os dados comecem na linha 10 (cabeçalho real).

2. **Execute o script**:
   * Abra o arquivo `gerador.R` no RStudio.
   * Clique no botão **"Source"** (ou pressione `Ctrl + Shift + S`).

3. **Selecione o arquivo**:
   * Uma janela de seleção de arquivos abrirá automaticamente.
   * Localize e selecione sua planilha de empenhos.
   * *Nota: Se a janela não aparecer, verifique sua barra de tarefas, ela pode estar minimizada.*

4. **Aguarde o processamento**:
   * O script verificará as dependências (pacotes e LaTeX).
   * Se o `TinyTeX` não estiver instalado, o script fará o download e a instalação automaticamente (isso pode levar alguns minutos na primeira vez).
   * Os relatórios serão salvos dentro da pasta `Relatorios_PDF` que será criada automaticamente no diretório do projeto.

## Estrutura do Script (`gerador.R`)

* **Autossuficiência**: O script gerencia a instalação de pacotes (`dplyr`, `knitr`, `tinytex`, etc.) e do motor LaTeX.
* **Tratamento de Dados**: Filtra entradas vazias, define códigos de UASG baseados na sigla do Pregão e limpa formatações.
* **Geração de PDF**: Utiliza `kableExtra` para formatar tabelas e `tinytex` para compilar o código LaTeX puro em um arquivo PDF profissional.

## Solução de Problemas

* **Erro no LaTeX**: Caso o script falhe ao compilar o PDF, certifique-se de que não há caracteres inválidos no nome do arquivo ou na planilha.
* **Pasta não encontrada**: Certifique-se de que o RStudio está configurado para o diretório de trabalho correto (`Session > Set Working Directory > To Source File Location`).

---
*Desenvolvido para automação administrativa.*


