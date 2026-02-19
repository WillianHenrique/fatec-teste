## Guia rápido: importação de base CSV (SaaS de RH)

Se você está com erro na importação, quase sempre é por **cabeçalho fora do padrão**, **ordem de colunas incorreta** ou **dados vazios em campos obrigatórios**.

### 1) Modelo oficial obrigatório
A planilha/CSV deve seguir **exatamente** este cabeçalho e ordem:

```csv
Nome,Sexo,Data_Nascimento,Idade,Data_Admissao,Setor,Cidade,Cargo
```

> Qualquer variação (ex.: `data_nascimento`, `DataNascimento`, espaços extras, troca de ordem) pode reprovar a importação.

### 2) Regras de preenchimento recomendadas
- `Nome`: texto obrigatório.
- `Sexo`: use um padrão consistente (`M`/`F` ou `Masculino`/`Feminino`).
- `Data_Nascimento`: data válida no padrão ISO (`YYYY-MM-DD`).
- `Idade`: número inteiro compatível com a data de nascimento.
- `Data_Admissao`: data válida no padrão ISO (`YYYY-MM-DD`).
- `Setor`: texto obrigatório.
- `Cidade`: texto obrigatório.
- `Cargo`: texto obrigatório.

### 3) Exemplo de CSV válido
```csv
Nome,Sexo,Data_Nascimento,Idade,Data_Admissao,Setor,Cidade,Cargo
Maria Silva,F,1968-03-10,58,1998-07-01,Financeiro,São Paulo,Analista Sênior
João Lima,M,1970-11-22,55,2001-02-15,Operações,Campinas,Supervisor
```

### 4) Checklist de validação antes de importar
1. O cabeçalho está **idêntico** ao modelo oficial?
2. A ordem das colunas está correta?
3. Há colunas faltantes?
4. Há colunas excedentes?
5. Existem campos obrigatórios vazios?
6. Tipos de dados estão corretos (datas e números)?

### 5) Erros comuns e correção
- **Erro: "coluna não reconhecida"** → ajuste nomes para o padrão oficial.
- **Erro: "ordem inválida"** → reorganize colunas exatamente como no modelo.
- **Erro: "campo obrigatório vazio"** → preencha `Nome`, `Setor`, `Cidade`, `Cargo` e demais campos obrigatórios.
- **Erro de data** → padronize para `YYYY-MM-DD`.

### 6) Se quiser, eu valido sua base agora
Cole aqui:
- o valor de `MODULO` (ex.: `IMPORTACAO_DADOS`),
- o cabeçalho completo que você está usando,
- 5 a 10 linhas da base (sem dados sensíveis).

Com isso eu te devolvo um relatório técnico com:
- Status da Importação (`Aprovada`, `Aprovada com Alertas` ou `Rejeitada`),
- tabela comparativa (**Modelo vs Recebido**),
- inconsistências detalhadas,
- recomendações de correção.

## Front de teste (importação + cadastros)
Agora o repositório possui uma tela local em `index.html` para você testar:
- validação de importação CSV,
- cadastro manual de funcionários,
- download do CSV gerado.

### Como executar localmente
```bash
python3 -m http.server 8000
```
Abra: `http://localhost:8000/index.html`

> Se aparecer **Not Found**, acesse explicitamente `/index.html` (alguns ambientes de prévia abrem rotas diferentes).

Arquivo de base pronto para Excel/CSV:
- `dados_teste_importacao.csv`
