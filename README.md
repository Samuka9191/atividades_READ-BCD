````
1. Consultar todos os produtos

Exibe todos os registros da tabela produto.

USE vendas_informatica;
SELECT * FROM produto;

2. Consultar nome, marca e estoque dos produtos

Exibe o nome, a marca e a quantidade em estoque de cada produto.

USE vendas_informatica;
SELECT nome_produto, marca, estoque
FROM produto;

3. Consultar produtos ordenados por marca

Exibe o nome, a categoria, a marca, o preço unitário e a data de cadastro, ordenando pela marca em ordem crescente.

USE vendas_informatica;
SELECT nome_produto, categoria, marca, preco_unitario, data_cadastro 
FROM produto 
ORDER BY marca ASC;

4. Consultar produtos ordenados pela data de cadastro

Exibe o nome, a categoria, a marca e a data de cadastro dos produtos, em ordem crescente de data.

USE vendas_informatica;
SELECT nome_produto, categoria, marca, data_cadastro 
FROM produto 
ORDER BY data_cadastro ASC;

5. Consultar todos os clientes

Exibe todos os registros da tabela cliente.

USE vendas_informatica;
SELECT * FROM cliente;

6. Consultar e-mail, cidade e estado dos clientes

Exibe o e-mail, a cidade e o estado de cada cliente.

USE vendas_informatica;
SELECT email, cidade, estado
FROM cliente;

7. Consultar clientes ordenados por estado

Exibe o nome, a cidade e o estado dos clientes, organizando os resultados em ordem crescente de estado.

USE vendas_informatica;
SELECT nome_cliente, cidade, estado
FROM cliente
ORDER BY estado ASC;

8. Consultar clientes ordenados pela data de cadastro

Exibe o nome, o e-mail, o estado e a data de cadastro dos clientes, em ordem crescente de data.

USE vendas_informatica;
SELECT nome_cliente, email, estado, data_cadastro
FROM cliente
ORDER BY data_cadastro ASC;

9. Consultar todas as vendas

Exibe todos os registros da tabela venda.

USE vendas_informatica;
SELECT * FROM venda;

10. Consultar vendas com informações dos clientes

Relaciona as tabelas cliente e venda para exibir o nome do cliente, a data da venda, o preço unitário da venda e a forma de pagamento.

USE vendas_informatica;
SELECT cliente.nome_cliente, venda.data_venda, venda.preco_unitario_venda, venda.forma_pagamento
FROM cliente
INNER JOIN venda
ON venda.id_cliente =cliente.id_cliente;

11. Consultar vendas com informações dos produtos

Relaciona as tabelas produto e venda para exibir o nome do produto, a data da venda, a quantidade vendida e o status da venda.

USE vendas_informatica;
SELECT produto.nome_produto, venda.data_venda, venda.quantidade, venda.status_venda
FROM produto
INNER JOIN venda
ON venda.id_produto = produto.id_produto;

12.01. Consultar vendas realizadas por PIX ou Boleto

Exibe o nome do produto, o preço unitário da venda e a forma de pagamento, filtrando as vendas realizadas por "PIX" ou "Boleto".

USE vendas_informatica;
SELECT produto.nome_produto, venda.preco_unitario_venda, venda.forma_pagamento
FROM venda
INNER JOIN produto
ON venda.id_produto = produto.id_produto
WHERE forma_pagamento IN("PIX", "Boleto");

12.02. Consultar clientes, produtos e vendas

Relaciona as tabelas cliente, produto e venda para exibir o nome do cliente, o nome do produto, a data da venda e a quantidade vendida.

USE vendas_informatica;
SELECT cliente.nome_cliente, produto.nome_produto, venda.data_venda, venda.quantidade
FROM venda
INNER JOIN cliente
ON venda.id_cliente = cliente.id_cliente
INNER JOIN produto
ON venda.id_produto = produto.id_produto;

13. Consultar descontos e formas de pagamento

Exibe o nome do produto, o percentual de desconto, a forma de pagamento e a data da venda, ordenando as vendas pela data em ordem crescente.

USE vendas_informatica;
SELECT produto.nome_produto, venda.desconto_percentual, venda.forma_pagamento, venda.data_venda
FROM venda
INNER JOIN produto
ON venda.id_produto = produto.id_produto
ORDER BY venda.data_venda ASC;

14. Consultar vendas ordenadas pelo status

Exibe o nome do produto, o nome do cliente, o desconto percentual, a forma de pagamento e o status da venda, ordenando os resultados em ordem crescente de status.

USE vendas_informatica;
SELECT produto.nome_produto, cliente.nome_cliente, venda.desconto_percentual, venda.forma_pagamento, venda.status_venda
FROM venda
INNER JOIN cliente
ON venda.id_cliente = cliente.id_cliente
INNER JOIN produto
ON venda.id_produto = produto.id_produto
ORDER BY venda.status_venda ASC;

15. Consultar informações completas das vendas

Exibe o nome e o e-mail do cliente, o nome, a marca e a categoria do produto, a forma de pagamento e o status da venda, ordenando os resultados pelo status em ordem decrescente.

USE vendas_informatica;
SELECT cliente.nome_cliente, cliente.email, produto.nome_produto, produto.marca, produto.categoria, venda.forma_pagamento, venda.status_venda
FROM venda
INNER JOIN cliente
ON venda.id_cliente = cliente.id_cliente
INNER JOIN produto
ON venda.id_produto = produto.id_produto
ORDER BY venda.status_venda DESC;


16-SELECT cliente.nome_cliente, cliente.email, produto.nome_produto, produto.marca, produto.categoria, venda.forma_pagamento, venda.status_venda
FROM cliente INNER JOIN venda ON venda.id_cliente = cliente.id_cliente
INNER JOIN produto ON venda.id_produto = produto.id_produto
WHERE venda.status_venda = 'Cancelada' OR venda.status_venda = 'Concluída'
ORDER BY (venda.preco_unitario_venda * venda.quantidade) DESC;
Principais comandos utilizados

USE: seleciona o banco de dados.
SELECT: seleciona os dados que serão exibidos.
FROM: indica a tabela consultada.
INNER JOIN: relaciona tabelas com base em uma condição.
ON: define a condição de relacionamento entre as tabelas.
WHERE: filtra os registros conforme uma condição.
IN: verifica se um valor corresponde a um dos valores informados.
ORDER BY: ordena os resultados.
ASC: ordena em ordem crescente.
DESC: ordena em ordem decrescente.
Conclusão

O projeto permitiu praticar consultas SQL utilizando as tabelas de produtos, clientes e vendas. Foram utilizados comandos para selecionar informações, aplicar filtros, ordenar resultados e relacionar tabelas, desenvolvendo conhecimentos fundamentais para a manipulação de bancos de dados relacionais.


