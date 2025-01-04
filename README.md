# 📊 Análise de Vendas de Cosméticos  

Este projeto simula um sistema de análise de vendas de cosméticos, contendo dados de produtos, marcas, cidades, tipo de venda (online ou loja física) e faturamento. A análise é realizada por meio de uma planilha Excel, scripts SQL e gráficos interativos desenvolvidos no Power BI.  

## 📁 Estrutura do Projeto  

- **planilha_vendas_cosmeticos_atualizada.xlsx**  
  Arquivo contendo os dados simulados de vendas organizados por ano.  

- **README_SQL_Vendas_Cosmeticos.md**  
  Documento com scripts SQL para criar a tabela, popular os dados e executar consultas analíticas.  

- **Gráfico Power BI**  
  Dashboard interativo criado no Power BI para visualizar tendências de vendas, desempenho por cidade, e outros insights.  

---

## 🔢 Dados da Planilha  

A planilha foi gerada com os seguintes atributos:  

- **Produto**: Nome do produto cosmético vendido (ex.: Shampoo Dove, Creme Nívea).  
- **Marca**: Marca do produto (ex.: Natura, Dove, Maybelline).  
- **Ano**: Ano da venda (2022, 2023 ou 2024).  
- **Cidade**: Cidade brasileira onde ocorreu a venda.  
- **Quantidade Vendida**: Quantidade de unidades vendidas.  
- **Preço Unitário (R$)**: Preço por unidade do produto.  
- **Tipo de Venda**: Tipo da venda (Online ou Loja Física).  
- **Faturamento Total (R$)**: Valor total gerado (calculado como `Quantidade Vendida * Preço Unitário`).  

---

## 🛠️ Tecnologias Utilizadas  

1. **Python**: Para geração automática da planilha de dados com os códigos abaixo:  
   ```python
   import pandas as pd
   import random

   # Dados simulados
   anos = [2022, 2023, 2024]
   categorias = ["Cremes", "Perfumes", "Shampoos", "Condicionadores", "Sabonetes", "Óleos", "Maquiagem", "Hidratantes"]
   marcas = ["Natura", "O Boticário", "Dove", "Vichy", "Maybelline"]
   cidades = ["São Paulo", "Rio de Janeiro", "Belo Horizonte", "Brasília", "Salvador"]

   # Geração de dados
   produtos = []
   for ano in anos:
       for _ in range(100): # 100 produtos por ano
           produto = {
               "Produto": random.choice(categorias) + " " + str(random.randint(1, 100)),
               "Marca": random.choice(marcas),
               "Ano": ano,
               "Cidade": random.choice(cidades),
               "Quantidade Vendida": random.randint(10, 500),
               "Preço Unitário (R$)": round(random.uniform(10.0, 200.0), 2),
               "Tipo de Venda": random.choice(["Online", "Loja Física"])
           }
           produto["Faturamento Total (R$)"] = produto["Quantidade Vendida"] * produto["Preço Unitário (R$)"]
           produtos.append(produto)

   # Criando DataFrame
   df = pd.DataFrame(produtos)
   df.to_excel("planilha_vendas_cosmeticos_atualizada.xlsx", index=False)

2. SQL: Para análise de dados com as seguintes consultas:

Total de faturamento por ano:

SELECT Ano, SUM(FaturamentoTotal) AS TotalFaturamento
FROM VendasCosmeticos
GROUP BY Ano
ORDER BY Ano;

Produtos mais vendidos em 2024:

SELECT Produto, SUM(QuantidadeVendida) AS TotalVendas
FROM VendasCosmeticos
WHERE Ano = 2024
GROUP BY Produto
ORDER BY TotalVendas DESC
LIMIT 10;



3. Power BI: Para criar um dashboard interativo que apresenta:

Total de vendas por ano.

Análise de faturamento por cidade.

Comparação entre vendas online e em loja física.

Gráficos de barras, mapas interativos e filtros dinâmicos.

https://app.powerbi.com/groups/me/reports/9ae911df-c520-4ecd-bda4-90d6af320474/ff416e81d3d44a277f5d?experience=power-bi



---

🔍 Como Usar

1. Clone este repositório:

git clone https://github.com/seu-usuario/nome-do-repositorio.git


2. Abra a planilha no Excel ou importe para um banco de dados.


3. Utilize os scripts SQL no arquivo README_SQL_Vendas_Cosmeticos.md para explorar os dados.


4. Abra o arquivo Power BI para explorar os gráficos interativos.




---

📊 Dashboard Power BI

Aqui está uma prévia do dashboard criado no Power BI:

Gráfico 1: Faturmaento e quantidade de produtos vendidos, total de vendas por tipo de venda (Online vs. Loja Física), Produtos e marcas mais vendidas e cidades dos comrpadores.




Se precisar do arquivo .pbix do Power BI, por favor, entre em contato.


---

📝 Licença

Este projeto está sob a licença MIT. Consulte o arquivo LICENSE para mais detalhes.


---

Desenvolvido por Eduardo Aragão Chaves.

Se precisar, posso ajudar a criar o arquivo ou adaptá-lo.
