# Modelagem_biblioteca
Modelagem de banco de dados de uma biblioteca

Este é um sistema de gerenciamento de biblioteca projetado para controlar livros, autores, empréstimos, reservas e usuários, permitindo um gerenciamento eficaz dos recursos da biblioteca. O banco de dados é estruturado para rastrear informações sobre livros, autores, gêneros literários, empréstimos, reservas e status de pagamentos, proporcionando uma solução completa para o gerenciamento de uma biblioteca.

Estrutura do Banco de Dados
O banco de dados é composto pelas seguintes tabelas principais:

1. Tabela livros
Armazena as informações sobre os livros disponíveis na biblioteca.

id (INT, PK): Identificador único do livro.
titulo (VARCHAR(100)): Título do livro.
total_exemplares (INT): Número total de exemplares disponíveis.
exemplares_disponiveis (INT): Número de exemplares disponíveis para empréstimo.
2. Tabela autores
Armazena as informações sobre os autores dos livros.

id (INT, PK): Identificador único do autor.
nome (VARCHAR(100)): Nome do autor.
3. Tabela livros_autores
Relacionamento entre livros e autores (um livro pode ter múltiplos autores, e um autor pode escrever vários livros).

id (INT, PK): Identificador único da relação.
id_livro (INT, FK): Identificador do livro (referência à tabela livros).
id_autor (INT, FK): Identificador do autor (referência à tabela autores).
4. Tabela generos
Armazena os gêneros literários disponíveis para os livros.

id (INT, PK): Identificador único do gênero.
genero (VARCHAR(100)): Nome do gênero literário.
5. Tabela livro_genero
Relacionamento entre livros e gêneros literários (um livro pode ter múltiplos gêneros).

id (INT, PK): Identificador único da relação.
id_livro (INT, FK): Identificador do livro (referência à tabela livros).
id_genero (INT, FK): Identificador do gênero (referência à tabela generos).
6. Tabela usuario
Armazena os usuários da biblioteca.

id (INT, PK): Identificador único do usuário.
nome (VARCHAR(200)): Nome do usuário.
email (VARCHAR(200)): E-mail do usuário (único).
7. Tabela status_emprestimo
Armazena os status possíveis de um empréstimo de livro.

id (INT, PK): Identificador único do status.
status (VARCHAR(100)): Nome do status (ex: "Em andamento", "Atrasado", "Concluído").
8. Tabela status_pagamento
Armazena os status do pagamento do empréstimo.

id (INT, PK): Identificador único do status de pagamento.
status (VARCHAR(100)): Nome do status de pagamento (ex: "Pagamento efetuado", "Pagamento pendente").
9. Tabela emprestimos
Armazena as informações dos empréstimos realizados pelos usuários.

id (INT, PK): Identificador único do empréstimo.
id_usuario (INT, FK): Identificador do usuário (referência à tabela usuario).
id_livro (INT, FK): Identificador do livro (referência à tabela livros).
data_emprestimo (DATE): Data de empréstimo do livro.
data_devolucao (DATE): Data de devolução do livro.
data_limite (DATE): Data limite para devolução.
id_status (INT, FK): Status do empréstimo (referência à tabela status_emprestimo).
multa (INT): Valor da multa em caso de atraso.
id_status_pagamento (INT, FK): Status do pagamento da multa (referência à tabela status_pagamento).
10. Tabela status_reserva
Armazena os status das reservas de livros.

id (INT, PK): Identificador único do status.
status (VARCHAR(100)): Nome do status da reserva (ex: "Em andamento", "Concluído", "Cancelado").
11. Tabela reserva
Armazena as informações sobre as reservas realizadas pelos usuários.

id (INT, PK): Identificador único da reserva.
id_usuario (INT, FK): Identificador do usuário (referência à tabela usuario).
id_livro (INT, FK): Identificador do livro (referência à tabela livros).
data_reserva (DATE): Data da reserva.
data_limite (DATE): Data limite para retirar o livro reservado.
id_status (INT, FK): Status da reserva (referência à tabela status_reserva).
Relacionamentos Entre Tabelas
O banco de dados possui os seguintes relacionamentos:

Livros e Autores: Muitos-para-muitos (um livro pode ter múltiplos autores e um autor pode ter escrito vários livros).
Livros e Gêneros: Muitos-para-muitos (um livro pode ter vários gêneros e um gênero pode ter vários livros).
Empréstimos e Usuários: Um-para-muitos (um usuário pode ter múltiplos empréstimos).
Empréstimos e Livros: Um-para-muitos (um livro pode ser emprestado várias vezes).
Reservas e Usuários: Um-para-muitos (um usuário pode fazer várias reservas).
Reservas e Livros: Um-para-muitos (um livro pode ser reservado várias vezes).
