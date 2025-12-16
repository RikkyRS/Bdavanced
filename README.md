Nivel 1 - Básico (CRUD e SELECT simples)
1. Criar uma tabela chamada clientes com os campos:
    ID (inteiro, chave primária)
    Nome (texto)
    Email (texto)
    Idade (inteiro)
    //CREATE TABLE clientes (
  id INTEGER PRIMARY KEY,
  nome TEXT,
  email TEXT,
  idade INTEGER
    );
2. Inserir registros
    Insira pelo menos 5 clientes diferentes na tabela.
    // INSERT INTO clientes (nome, email, idade) VALUES
3. Selecionar tudo
    Liste todos os clientes cadastrados.
    // select * from clientes;
4. Selecionar com filtro 
    Liste apenas os clientes com idade acima de 25.
    // select * from clientes where idade > 25;
5. Atualizar dados.
    Atualize o email de um cliente especifico.
    // update clientes set email = 'hotta_rodrigues@gmail.com' where id = 1;
6. Deletar registro
    Delete o cliente que tem o id = 3.
    // delete from clientes where id = 3;
Nível 2 - Intermediário(JOIN,ORDER,BY,GROUP)
7. Criar duas tabelas relacionadas.
    Crie uma tabela pedidos com:
    /CREATE TABLE clientes (
         id INTEGER PRIMARY KEY,
        nome TEXT,
        email TEXT,
        idade INTEGER
    );
    // CREATE TABLE pedidos (
        id INTEGER PRIMARY KEY,
        cliente_id INTEGER NOT NULL,
        valor DECIMAL(10,2),
        data_pedido DATE,
    FOREIGN KEY (cliente_id) REFERENCES clientes(id)
    );
8. Inserir pedidos 
    Insira pelo menos 7 pedidos, misturando pedidos de clientes diferentes.
    // INSERT INTO pedidos (cliente_id, valor, data_pedido) VALUES 
    (1, 150.50, '2025-01-10'),
    (2, 89.90, '2025-01-11'),
    (3, 300.00, '2025-01-12'),
    (1, 45.00, '2025-01-13'),
    (2, 120.75, '2025-01-14'),
    (3, 210.30, '2025-01-15'),
    (1, 99.99, '2025-01-16');
9. JOIN básico
    liste o nome do cliente e o valor do pedido.
    SELECT 
        clientes.nome,
        pedidos.valor,
    FROM pedidos 
    JOIN clientes ON pedidos.cliente_id = clientes.id;
10. Soma por cliente 
    mostre quanto cada cliente já gastou no total.
    SELECT
        clientes.nome,
        IFNULL(SUM(pedidos.valor), 0) AS total_gasto
    FROM clientes
    LEFT JOIN pedidos ON pedidos.cliente_id = clientes.id
    GROUP BY clientes.nome;
11. Ordenar resultado 
    Liste todos os pedidos do maior valor para o menor.
    SELECT
        clientes.nome,
        pedidos.valor,
        pedidos.data_pedido
    FROM pedidos
    JOIN clientes ON pedidos.cliente_id = clientes.id
    ORDER BY pedidos.valor DESC;

12. Filtrar por data
    liste os pedidos feitos no mês atual.
    SELECT
        clientes.nome,
        pedidos.valor,
        pedidos.data_pedido
    FROM pedidos
    JOIN clientes ON pedidos.cliente_id = clientes.id
    WHERE strftime('%Y-%m', pedidos.data_pedido) = strftime('%Y-%m', 'now');
