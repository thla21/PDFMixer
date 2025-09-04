## PDFMixer

Script simples em Python para mesclar arquivos PDF de uma pasta em um único arquivo final, preservando a ordem alfanumérica dos nomes dos arquivos.

### Visão geral
- **Entrada**: todos os PDFs dentro da pasta `Arquivos/`.
- **Saída**: um PDF consolidado chamado `arquivo_final.pdf` na raiz do projeto.
- **Ordenação**: os arquivos são ordenados com `sort()` (ordem alfanumérica). Ex.: `01. PDF.pdf`, `02. Arquivo.pdf`, `03. Ultimo Arquivo.pdf`.

## Pré-requisitos
- **Python**: >= 3.12
- **Dependências**: `PyPDF2`

As dependências estão declaradas em `pyproject.toml`.

## Instalação

### Usando uv (recomendado)
Se você utiliza o gerenciador `uv`:

```bash
uv sync
```

### Usando pip
Se preferir `pip` tradicional:

```bash
pip install -r <(echo "PyPDF2>=3.0.1")
# ou
pip install PyPDF2>=3.0.1
```

No Windows PowerShell, uma alternativa é editar o arquivo `pyproject.toml` (já pronto) e simplesmente:

```powershell
pip install PyPDF2>=3.0.1
```

## Estrutura do projeto

```
PDFMixer/
├─ Arquivos/
│  ├─ 01. PDF.pdf
│  ├─ 02. Arquivo.pdf
│  └─ 03. Ultimo Arquivo.pdf
├─ main.py
├─ pyproject.toml
└─ README.md
```

## Como usar
1. Coloque todos os PDFs que deseja mesclar dentro da pasta `Arquivos/`.
2. Garanta que os nomes dos arquivos estejam na ordem desejada (alfanumérica). Se precisar, prefixe com números, como `01`, `02`, `03`.
3. Execute o script:

```powershell
python .\main.py
```

4. O arquivo `arquivo_final.pdf` será gerado na raiz do projeto.

## Detalhes de ordenação
- O script lê os nomes em `Arquivos/` e aplica `lista_arquivos.sort()`.
- Apenas arquivos que contenham `.pdf` no nome são anexados.

## Personalizações
- **Nome do diretório de entrada**: altere a linha que usa `os.listdir("Arquivos")` e os caminhos de `append` em `main.py`.
- **Nome do arquivo final**: altere `merger.write("arquivo_final.pdf")` em `main.py`.
- **Filtro de arquivos**: ajuste o `if ".pdf" in arquivo:` para algo mais estrito (ex.: `arquivo.lower().endswith(".pdf")`).

## Problemas comuns
- "Nenhum arquivo gerado": verifique se há PDFs na pasta `Arquivos/` e se você executou o comando no diretório correto do projeto.
- "Permissão negada" ao escrever o arquivo final: feche qualquer visualizador que esteja aberto com `arquivo_final.pdf` e execute novamente.
- PDFs corrompidos ou protegidos podem falhar ao serem mesclados.

## Licença
Este projeto é fornecido "como está". Adapte e utilize conforme necessário.


