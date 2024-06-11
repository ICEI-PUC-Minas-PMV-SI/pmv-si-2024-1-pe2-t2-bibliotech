# Relatórios Analíticos

Relatórios analíticos são ferramentas fundamentais que coletam, analisam e interpretam dados para apoiar a tomada de decisões informadas. Eles identificam tendências, avaliam desempenho, otimizam processos e suportam estratégias de negócios. Além disso, ajudam no monitoramento e controle de operações, comunicação com stakeholders, previsão e planejamento, identificação de problemas e garantem compliance. Em essência, transformam dados brutos em insights valiosos, capacitando as organizações a operar de forma mais eficiente e competitiva.

## Tabela de frequência de livros catalogados por bibliotecário

![processo-catalogacao](assets/Processo%20de%20catalogação%20e%20organização%20dos%20livros.png)

Por meio da tabela de frequência, é possível analisar a quantidade de livros catalogados por bibliotecário. Dessa forma, temos uma forma de identificar quais funcionários estão desempenhando bem suas funções de catalogação e quais podem necessitar de suporte ou treinamento.

### Comando SQL-DML (SELECT)

```sql
SELECT  
 b.nome as 'Bibliotecário', 
 COUNT(*) AS 'Livros Catalogados' 
FROM LIVRO as l 
JOIN BIBLIOTECARIO as b 
ON b.id_bibliotecario = l.id_bibliotecario 
GROUP BY b.nome 
```

## Consulta com a contagem de empréstimos feitas por cada Bibliotecário

![processo-emprestimo](assets/Processo%20de%20empréstimo%20dos%20livros.png)

Por meio do gráfico de pizza, é possível analisar a quantidade de empréstimos realizados por cada bibliotecário. Essas informações são valiosas para entender o desempenho individual e identificar oportunidades de treinamento ou reconhecimento.

### Comando SQL-DML (SELECT)

```sql
SELECT
 b.nome AS ‘Bibliotecário’,
 COUNT(e.id_emprestimo) AS ‘Empréstimos Realizados’
FROM EMPRESTIMO AS e
JOIN Bibliotecario AS b
ON b.id_bibliotecario = e.id_bibliotecario
GROUP BY b.nome
```

## Relatório para análise dos materiais devolvidos

![processo-devolucao](assets/Processo%20de%20devolução%20dos%20livros.png)

Por meio do histograma é possível analisar a relação dos livros emprestados com a quantidade de livros devolvidos. Com essas informações têm-se um maior controle dos materiais disponíveis na biblioteca.

Com as informações do histograma é possível elaborar uma estratégia para otimizar a quantidade de livros disponíveis na biblioteca.

### Comando SQL-DML (SELECT)

```sql
SELECT Id_Livro 
FROM Emprestimo 
WHERE devolvido = false; 
```

# Indicadores de Desempenho

Com uma visão mais estratégica, foram identificados, a partir dos relatórios analíticos, indicadores chave de processo (KPIs – Key Process Indicator) que permitam um acompanhamento integrado dos vários processos eleitos.

| Indicador                        | Objetivo                                                                        | Descrição                                                                                              | Fórmula de cálculo                                          | Fontes de dados                   | Perspectiva         |
|----------------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|-------------------------------------------------------------|----------------------------------|---------------------|
| Taxa de entrega de material      | Avaliar a quantidade de livros que estão sendo devolvidos para obter melhor controle sobre os materiais da biblioteca | Mede a porcentagem de livros devolvidos em relação aos livros emprestados                              | (quantidade de livros devolvidos / quantidade de livros emprestados) * 100 | Tabela de devolução e de empréstimo | Processos internos  |
| Taxa de utilização do acervo     | Avaliar a proporção de utilização do acervo                                     | Mede a porcentagem de livros emprestados em relação ao total disponível no acervo                       | (número de livros emprestados / total de livros no acervo) * 100             | Tabela de devolução e de empréstimo | Processos internos  |
| Eficiência de catalogação por bibliotecário | Avaliar a eficiência e precisão de cada bibliotecário no processo de catalogação de livros, com o intuito de identificar áreas de melhoria e promover treinamento específico, se necessário | Esse indicador mede o número de livros catalogados por cada bibliotecário. É útil para identificar quais funcionários estão desempenhando bem suas funções de catalogação e quais podem necessitar de suporte | número de livros catalogados / número de dias trabalhados | Tabela de livros catalogados por bibliotecário | Processos internos  |
| Taxa de crescimento de novos clientes | Avaliar o crescimento percentual da base de clientes da biblioteca em um período específico | Esse indicador mede a porcentagem de aumento no número de novos clientes registrados em comparação com o período anterior | (número de novos clientes registrados em um período / número de usuários registrados em um período anterior) * 100 | Tabela de registros de clientes | Processos internos  |
| Taxa de atraso na devolução      | Avaliar a frequência com que os livros são devolvidos após o prazo estipulado para identificar problemas relacionados ao cumprimento dos prazos pelos usuários | O indicador mede a porcentagem de livros devolvidos após a data de vencimento em relação ao total de livros devolvidos | (quantidade de livros devolvidos com atraso / quantidade total de livros devolvidos) * 100 | Tabela de devolução e de empréstimo | Processos internos  |

# Consultas SQL

## Buscar livros filtrando por ISBN

```sql
SELECT *  
FROM LIVRO  
WHERE ISBN = 'exemploisbn'  
```

Essa consulta SQL recupera todas as colunas de todas as linhas da tabela LIVRO onde o valor do campo ISBN é igual a 'exemploisbn'.

- `SELECT *`: Seleciona todas as colunas da tabela LIVRO para serem retornadas como resultado da consulta;

- `FROM LIVRO`: Especifica a tabela da qual os dados serão selecionados, que é a tabela LIVRO;

- `WHERE ISBN = 'exemploisbn'`: Cláusula de restrição que filtra as linhas retornadas para aquelas em que o valor do campo ISBN é exatamente igual a 'exemploisbn'. Esta cláusula restringe o conjunto de resultados apenas aos livros que correspondem ao ISBN especificado.

## Buscar livros com empréstimos fora do prazo

```sql
SELECT *  
FROM EMPRESTIMO  
LEFT JOIN LIVRO  
WHERE EMPRESTIMO.data_devolucao_prevista < CURDATE();
```

Esta consulta SQL retorna todas as colunas de todas as linhas da tabela EMPRESTIMO, juntamente com todas as colunas correspondentes da tabela LIVRO, onde a data de devolução prevista (do empréstimo) é anterior à data atual.

- `SELECT *`: Seleciona todas as colunas das tabelas EMPRESTIMO e LIVRO para serem retornadas como resultado da consulta;

- `FROM EMPRESTIMO`: Especifica a tabela principal da qual os dados serão selecionados, que é a tabela EMPRESTIMO;

- `LEFT JOIN LIVRO`: Realiza uma junção entre as tabelas EMPRESTIMO e LIVRO. Isso significa que todas as linhas da tabela EMPRESTIMO serão incluídas no resultado. Se não houver correspondência, os valores das colunas da tabela LIVRO serão nulos para essas linhas;

- `WHERE EMPRESTIMO.data_devolucao_prevista < CURDATE()`: Esta cláusula de restrição filtra o conjunto de resultados para incluir apenas as linhas em que a data de devolução prevista (armazenada na tabela EMPRESTIMO) é anterior à data atual. CURDATE() é uma função que retorna a data atual. Portanto, esta parte da consulta retorna apenas os registros de empréstimos que estão vencidos, ou seja, a data de devolução prevista é anterior à data atual.

## Buscar cliente pelo ID

```sql
SELECT *  
FROM CLIENTE  
WHERE id_cliente = 'exemploid' 
```

Essa consulta SQL retorna todas as colunas de todas as linhas da tabela CLIENTE onde o valor do campo id_cliente é igual a 'exemploid'.

- `SELECT *`: Seleciona todas as colunas da tabela CLIENTE para serem retornadas como resultado da consulta;

- `FROM CLIENTE`: Especifica a tabela da qual os dados serão selecionados, que é a tabela CLIENTE;

- `WHERE id_cliente = 'exemploid'`: Esta é uma cláusula de restrição que filtra as linhas retornadas para aquelas em que o valor do campo id_cliente é exatamente igual a 'exemploid'. Essa cláusula restringe o conjunto de resultados apenas aos clientes que correspondem ao ID especificado.
