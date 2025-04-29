# Banco de Dados
*Exercício realizado em sala sobre Banco de Dados (Módulo 2 - 29/04/2025)* <br>
---
CREATE TABLE alunos ( <br>
  id SERIAL PRIMARY KEY, <br>
  nome TEXT NOT NULL, <br>
  turma TEXT NOT NULL, <br>
  curso TEXT NOT NULL, <br>
  data_nascimento DATE <br>
); <br>

<br>

CREATE TABLE cursos ( <br>
  id SERIAL PRIMARY KEY, <br>
  nome TEXT NOT NULL, <br>
  duracao_anos INT <br>
); <br>

<br>

CREATE TABLE matriculas ( <br>
  id SERIAL PRIMARY KEY, <br>
  aluno_id INT REFERENCES alunos(id) ON DELETE CASCADE, <br>
  curso_id INT REFERENCES cursos(id) ON DELETE CASCADE, <br>
  data_matricula DATE DEFAULT CURRENT_DATE <br>
); <br>

<br>

INSERT INTO alunos (nome, turma, curso, data_nascimento) <br>
VALUES ('Ana Lima', '1A', 'Engenharia Civil', '2002-05-10'), <br>
('Bruno Souza', '1B', 'Administração', '2003-08-15'), <br>
('Carla Ferreira', '1A', 'Engenharia Química', '2003-04-16'), <br>
('Daniel Lopes', '1C', 'Ciência da Computação', '2004-11-23'), <br>
('Eduarda Martins', '1B', 'Engenharia Civil', '2002-07-02'), <br>
('Felipe Andrade', '1C', 'Administração', '2003-01-29'), <br>
('Gabriela Nunes', '1A', 'Engenharia Química', '2002-12-11'), <br>
('Henrique Silva', '1B', 'Ciência da Computação', '2004-03-05'), <br>
('Isabela Rocha', '1C', 'Administração', '2003-09-20'), <br>
('João Pedro Alves', '1A', 'Engenharia Civil', '2002-06-17'); <br>

<br>

INSERT INTO cursos (nome, duracao_anos) <br>
VALUES ('Engenharia Civil', 5), <br>
('Administração', 4), <br>
('Engenharia Química', 2), <br>
('Ciência da Computação', 2); <br>

<br>

INSERT INTO matriculas (aluno_id, curso_id) <br>
VALUES (1, 1), <br>
       (2, 2), <br>
       (3, 3), <br>
       (4, 4), <br>
       (5, 1), <br>
       (6, 2), <br>
       (7, 3), <br>
       (8, 4), <br>
       (9, 2), <br>
       (10, 1); <br>

<br>

SELECT a.nome AS aluno, c.nome AS curso <br>
FROM matriculas m <br>
JOIN alunos a ON m.aluno_id = a.id <br>
JOIN cursos c ON m.curso_id = c.id; <br>
