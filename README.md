# Banco de Dados
*Exercício realizado em sala sobre Banco de Dados (Módulo 2 - 29/04/2025)* <br>


CREATE TABLE alunos (
  id SERIAL PRIMARY KEY,
  nome TEXT NOT NULL,
  turma TEXT NOT NULL,
  curso TEXT NOT NULL,
  data_nascimento DATE
);

CREATE TABLE cursos (
  id SERIAL PRIMARY KEY,
  nome TEXT NOT NULL,
  duracao_anos INT
);

CREATE TABLE matriculas (
  id SERIAL PRIMARY KEY,
  aluno_id INT REFERENCES alunos(id) ON DELETE CASCADE,
  curso_id INT REFERENCES cursos(id) ON DELETE CASCADE,
  data_matricula DATE DEFAULT CURRENT_DATE
);

INSERT INTO alunos (nome, turma, curso, data_nascimento)
VALUES ('Ana Lima', '1A', 'Engenharia Civil', '2002-05-10'),
('Bruno Souza', '1B', 'Administração', '2003-08-15'),
('Carla Ferreira', '1A', 'Engenharia Química', '2003-04-16'),
('Daniel Lopes', '1C', 'Ciência da Computação', '2004-11-23'),
('Eduarda Martins', '1B', 'Engenharia Civil', '2002-07-02'),
('Felipe Andrade', '1C', 'Administração', '2003-01-29'),
('Gabriela Nunes', '1A', 'Engenharia Química', '2002-12-11'),
('Henrique Silva', '1B', 'Ciência da Computação', '2004-03-05'),
('Isabela Rocha', '1C', 'Administração', '2003-09-20'),
('João Pedro Alves', '1A', 'Engenharia Civil', '2002-06-17');

INSERT INTO cursos (nome, duracao_anos)
VALUES ('Engenharia Civil', 5),
('Administração', 4),
('Engenharia Química', 2),
('Ciência da Computação', 2);

INSERT INTO matriculas (aluno_id, curso_id)
VALUES (1, 1),
       (2, 2),
       (3, 3),
       (4, 4),
       (5, 1),
       (6, 2),
       (7, 3),
       (8, 4),
       (9, 2),
       (10, 1);

SELECT a.nome AS aluno, c.nome AS curso
FROM matriculas m
JOIN alunos a ON m.aluno_id = a.id
JOIN cursos c ON m.curso_id = c.id;
