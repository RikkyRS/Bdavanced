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