# Combustíveis: preço eficiente e marca mais barata (Literacia Financeira)

Dois blocos extra da página `/precos-combustiveis` do literaciafinanceira.pt.

## Ficheiros

- `combustiveis-extra.js`: insere os blocos "Preço eficiente" e "Que marca tem o combustível mais barato?" a seguir à fiscalidade. O CSS vai dentro do JS.
- `extra.json`: os dados dos dois blocos.
- `atualizar_extra.py`: atualiza o `extra.json`.
- `.github/workflows/atualizar-extra.yml`: corre o script todos os dias às 07:41 UTC.

## Fontes

- Preço eficiente: [relatório semanal da ERSE](https://www.erse.pt/combustiveis-e-gpl/supervisao-do-mercado/supervisao-dos-precos-de-combustiveis/) (PDF). O script abre o relatório mais recente e lê o preço eficiente, a variação semanal e a comparação com os preços de pórtico e com descontos da semana anterior.
- Preço médio por marca: API pública da [DGEG](https://precoscombustiveis.dgeg.gov.pt/), média simples dos preços afixados, marcas com 20 ou mais postos.

## Segurança do script

Se o PDF mudar de formato e os números não baterem certo entre si, o script mantém os valores da semana anterior em vez de publicar dados errados. Convém olhar para a página à segunda ou terça-feira, quando sai o relatório novo.

## Testar a leitura de um PDF

```
pip install pypdf
python3 atualizar_extra.py --pdf relatorio.pdf
```
