# Vocabulário de Banco de Dados

## Sistema Gerenciador de Banco de Dados (SGBD)
É o sistema que controla tudo no banco de dados. Ele gerencia os dados, garante que estejam corretos, cuida da segurança, dos acessos e faz com que as consultas funcionem direito.

**Exemplo prático:**  
Quando uso o MySQL Workbench pra criar uma tabela ou consultar dados com `SELECT`, quem processa isso é o SGBD MySQL.

---

## Restrições em Banco de Dados
São regras que a gente define nas tabelas pra garantir que os dados sigam uma lógica. Por exemplo: `NOT NULL` obriga a preencher, `PRIMARY KEY` identifica cada linha, `FOREIGN KEY` liga uma tabela com outra. Isso evita erro e bagunça nos dados.

**Exemplo prático:**

CREATE TABLE cliente ( 
  id INT PRIMARY KEY, 
  nome VARCHAR(100) NOT NULL, 
  email VARCHAR(100) UNIQUE 
); 

## Modelo Relacional
É o modelo mais usado hoje. Nele os dados ficam organizados em tabelas com linhas e colunas. Cada linha é um registro (ou tupla) e cada coluna é um atributo.

Exemplo prático:
A tabela cliente tem colunas como id, nome, telefone. Cada linha representa um cliente.

## Modelagem Conceitual
É a primeira etapa do planejamento do banco. Aqui a gente pensa nas entidades do mundo real (como cliente, carro, contrato) e nos relacionamentos entre elas, sem pensar ainda nas tabelas ou código.

Exemplo prático:
No DER (Diagrama Entidade-Relacionamento), represento a entidade Cliente, a entidade Veículo e o relacionamento Aluga, com suas cardinalidades.

## Modelagem Lógica
Depois de entender o mundo real na modelagem conceitual, a gente transforma isso em tabelas com colunas, chaves e relacionamentos.

Exemplo prático:
O relacionamento Cliente aluga Veículo vira uma tabela chamada contrato_aluguel com colunas id_cliente e id_veiculo como chaves estrangeiras.

## Modelagem Física
Agora sim vira código real. A gente usa SQL pra criar as tabelas e definir os detalhes, como tipos de dados, chaves e restrições.

Exemplo prático:

CREATE TABLE veiculo ( 
  id INT PRIMARY KEY, 
  placa VARCHAR(10) NOT NULL, 
  data_manutencao DATE 
); 

## Linguagem SQL
É a linguagem usada pra conversar com o banco. Com ela são cradas tabelas, inserção de dados, consultas, atualizações e deleções.

## Data Definition Language (DDL)
São os comandos SQL que servem pra criar ou alterar a estrutura do banco.

SELECT nome FROM cliente WHERE uf_cnh = 'RS'; 


Exemplo prático:

CREATE TABLE escritorio ( 
  id INT PRIMARY KEY, 
  nome VARCHAR(100) 
); 


## Data Manipulation Language (DML)
São os comandos que manipulam os dados dentro das tabelas.

## Exemplo prático:

INSERT INTO escritorio (nome) VALUES ('Escritório Central'); 
UPDATE cliente SET nome = 'João Vítor' WHERE id = 1; 
DELETE FROM veiculo WHERE placa = 'IXT0003'; 

Boas Práticas em Modelagem de Banco de Dados
Aqui é onde entra o cuidado: dar nomes claros pras tabelas e colunas, evitar repetir informações (normalizar), usar chaves corretamente e deixar tudo bem organizado.

Exemplo prático:
Ao invés de colocar a cidade dentro da tabela cliente, crio uma tabela cidade separada e relaciono com o cliente por id_cidade. Isso evita repetir “Santa Maria” mil vezes.
