# Conferência de Entrada — Espelho de Palete

Aplicativo web (arquivo único, sem backend) para conferência de entrada de mercadorias:

- Importa a NF em PDF e extrai os itens automaticamente.
- Cruza cada SKU com um cadastro de "caixas por palete" (armazenado no navegador do usuário).
- Explode a quantidade da NF em linhas de palete (paletes cheios + resto, sempre do mesmo SKU).
- Permite cadastrar/atualizar o padrão de caixas por palete direto na tela.
- Exporta o espelho de conferência em `.xlsx`, já formatado (A4 paisagem, margens estreitas, cabeçalho azul com quebra automática), pronto para impressão.

## Como usar

1. Abra o arquivo `conferencia_nl.html` em qualquer navegador (Chrome, Edge, etc). Não precisa de instalação nem servidor.
2. Aba **Importar NF**: envie o PDF da nota, clique em "Processar NF", confira o espelho gerado e exporte o `.xlsx`.
3. Aba **Cadastro de SKUs**: consulte, edite ou adicione SKUs e seus padrões de caixas por palete.

## Publicando no GitHub Pages (opcional)

Como é um único arquivo HTML, dá para publicar direto:

1. Suba `conferencia_nl.html` para um repositório.
2. Em *Settings → Pages*, aponte para a branch/pasta onde o arquivo está.
3. Acesse a URL gerada — o app roda inteiramente no navegador de quem acessa.

## Observações técnicas

- Feito em HTML + JavaScript puro (sem build, sem dependências instaladas localmente).
- Bibliotecas usadas via CDN: `pdf.js` (leitura do PDF) e `ExcelJS` (geração do `.xlsx` formatado).
- A interpretação dos itens da NF usa a API da Anthropic (Claude) para estruturar o texto extraído do PDF em JSON — isso acontece no próprio navegador, a cada importação.
- O cadastro de SKUs fica salvo localmente (por usuário/navegador), não em um banco compartilhado. Se quiser um cadastro compartilhado entre várias pessoas, isso pode ser adaptado depois.
