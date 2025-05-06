# Banco-eleição
atividade 03 de banco de dados para técnico em redes de computação

CREATE DATABASE EleitoralDB;
USE EleitoralDB;

CREATE TABLE LOCALIDADE (
    id_localidade INTEGER PRIMARY KEY,
    nome_localidade VARCHAR(255),
    estado VARCHAR(255)
);

CREATE TABLE ZONA_ELEITORAL (
    id_zona INTEGER PRIMARY KEY,
    nome_zona VARCHAR(255),
    FK_LOCALIDADE_id_localidade INTEGER REFERENCES LOCALIDADE(id_localidade)
);

CREATE TABLE SECAO_ELEITORAL (
    id_secao INTEGER PRIMARY KEY,
    nome_secao VARCHAR(255),
    FK_ZONA_id_zona INTEGER REFERENCES ZONA_ELEITORAL(id_zona)
);

INSERT INTO LOCALIDADE VALUES
(1, 'Localidade A', 'Estado X'),
(2, 'Localidade B', 'Estado Y'),
(3, 'Localidade C', 'Estado Z'),
(4, 'Localidade D', 'Estado W'),
(5, 'Localidade E', 'Estado V');

INSERT INTO ZONA_ELEITORAL VALUES
(1, 'Zona 1', 1),
(2, 'Zona 2', 2),
(3, 'Zona 3', 3),
(4, 'Zona 4', 4),
(5, 'Zona 5', 5);

INSERT INTO SECAO_ELEITORAL VALUES
(1, 'Secao 1', 1),
(2, 'Secao 2', 2),
(3, 'Secao 3', 3),
(4, 'Secao 4', 4),
(5, 'Secao 5', 5);

UPDATE LOCALIDADE SET nome_localidade = 'Localidade F' WHERE id_localidade = 1;
UPDATE ZONA_ELEITORAL SET nome_zona = 'Zona 6' WHERE id_zona = 2;

DELETE FROM SECAO_ELEITORAL WHERE id_secao = 4;
DELETE FROM LOCALIDADE WHERE id_localidade = 5;

SELECT * FROM ZONA_ELEITORAL WHERE FK_LOCALIDADE_id_localidade = 1 ORDER BY nome_zona;
SELECT * FROM SECAO_ELEITORAL WHERE FK_ZONA_id_zona = 3 ORDER BY nome_secao;
