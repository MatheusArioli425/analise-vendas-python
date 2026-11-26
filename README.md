# Análise exploratória de vendas em Python · Loja Horizonte

Limpeza e análise de 3.000 pedidos de um e-commerce fictício com **pandas** e **matplotlib**, em um notebook Jupyter.

> Os dados são fictícios, gerados para estudo. É a mesma base usada nos projetos interativos do meu portfólio.

## Problema

A base de pedidos misturava vendas canceladas com vendas reais e tinha valores muito acima do normal. Do jeito que estava, o faturamento e o ticket médio saíam errados.

## O que eu fiz

1. **Conferi a qualidade dos dados:** tipos, nulos, IDs duplicados e distribuição de status.
2. **Separei os pedidos válidos:** tirei os 174 cancelados, que não geram receita.
3. **Tratei os valores fora do padrão** pelo intervalo interquartil (IQR). Os 217 pedidos acima do limite são compras reais, então foram marcados, e não apagados: entram no faturamento, mas ficam fora das médias.
4. **Juntei as 4 tabelas** (pedidos, clientes, itens e produtos) com `merge`.
5. **Analisei** receita por mês (com crescimento mês a mês), por categoria, ticket médio por segmento e canal (`pivot_table`) e taxa de cancelamento por canal.

## Resultados

- **2.826 pedidos válidos** de 3.000.
- **Eletrônicos traz 51% da receita**, mesmo com menos pedidos que Moda.
- **Novembro e dezembro concentram 29% da receita do ano.** Novembro cresceu 77% sobre outubro.
- **Clientes Premium têm o maior ticket médio** em todos os canais.
- **O Marketplace cancela 7,0% dos pedidos**, contra 5,2% do Site.

![Receita por mês](graficos/receita_mensal.png)

![Receita por categoria](graficos/receita_categoria.png)

## Como rodar

Você precisa do Python 3.10 ou mais novo.

```bash
pip install -r requirements.txt
jupyter notebook analise_vendas.ipynb
```

O notebook já está salvo com os resultados. Dá para ler direto aqui no GitHub sem instalar nada.

## Estrutura

```
analise_vendas.ipynb   o notebook com a análise completa
dados/                 pedidos, clientes, itens e produtos em CSV
graficos/              gráficos gerados pelo notebook
requirements.txt       bibliotecas usadas
```

---
Feito por **Matheus Arioli** · Analista de Dados
