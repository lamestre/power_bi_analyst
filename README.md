# Dasafio de Projeto 2

##  Criando um Dashboard corporativo com integração com MySql e Azure

___
#

## Procedimentos para Carga dos Dados:

1.	Criada uma instância **MySQL** na **Azure**.
	- "desafio-projeto-bi.mysql.database.azure.com"

2.	Criado um Banco de dados nesta instância do MySQL
	- **azure_company**

3.	Criadas as Tabelas e Constraints conforme script disponível no github

4.  Feito alguns ajustes no script para contornar erros que surgiram ao tratar algumas Constraints.

5.	Realizado o pvoamento das Tabelas conforme script disponível no github

6.  Feito ajuste no insert da tabela employee, para fazer a insersao por ordem hierarquica descrescente de gerencia, para evitar o erro na Constraint fk_employee.

7.	Feita a integração do **Power BI** com **MySQL** no **Azure**

8.  Foi necessario baixar e instalar o **Conector MySql** e o **Certificado SSL**.

9.	Realizadas consultas nas tabelas para verificar se no BD havia algum problema ou inconsistencia. 


## Procedimentos para Transformação dos Dados:

1.	Retiradas as Colunas referentes aos relacionamentos (MetaDados).

2.	Ajustados os Titulos das Colunas para nomes intuitivos e de facil entendimento.

3.	Ajustados os Tipos de Dados das Colunas.
	- Colunas Ssn, Super_ssn, Dno, Dnumber, Mgr_ssn, Essn, Pnumber, Dnum e Pno foram alteradas para Tipo Texto, para evitar q o PowerBI aplicasse funçoes matematicas a estes dados.
	- Coluna Salary foi alterada para Numero Decimal Fixo.

4. 	Feita a conferencia nas Tabelas em busca de alguma possivel inconsistencia:
	- Encontrado um valor NULL na Coluna employee.Super_ssn, que se trata de um empregado sem chefia imediata, provavelmente o presidente da empresa.

5.	Aplicadas estas alterações preliminares.

6.	Na tabela Employee, foi subDividida a Coluna Endereço, em 4 Colunas:
	- End_rua
	- End_numero
	- End_cidade
	- End_estado

7.	Feito os ajustes nescessarios nas novas colunas.

8.	Mescladas as Tabelas Employee e Departament, atraves dos campos Dept_codigo de cada uma, em uma nova Tabela: Empregado

9.	Excluidas da nova tabela, as colunas Dept_codigo, Mat_gerente, Data_inicio_gestao e Dept_data_criacao.

10.	Mescladas as Coluna Primeiro_nome e Sobrenome da tabela Empregado, para a nova Coluna Nome, contendo o nome e sobrenome dos colaboradores.

11.	Excluidas da Tabela Empregado, as colunas com as partes separadas dos nomes dos Colaboradores.

12. Mesclada pelo PowerQuery, a Tabela Empregado com ela mesma, atraves dos campos Chefia_imediata e Mat_empregado, para trazer para cada colaborador o Nome do seu Chefe Imediato, e assim eliminar a coluna com a respectiva matricula.

13.	Mescladas as Tabelas Departament e Dept_locations, numa nova tabela: Departamento.
	- Utilizado o recurso de Mesclar Consultas ao inves do Acrescentar Consultas, por que o segundo junta as linhas de tabelas semelhantes, ou seja, com a mesma estrutura de colunas. Neste caso não se aplica pois são tabelas diferentes e o que queremos é acrecentar uma coluna da segunda tabela a primeira.

14.	Duplicada a Tabela Empregado para criar a tabela de Colaboradores_gerente.

15.	Feita a agregação da tabela de Colaboradores_gerente, pela coluna Chefe_imediato, apresentando a nova coluna Subordinados com o total de colaboradores que responde a cada gerente.

16.	Aplicados os ajustes a Base do PowerBI.

17. Implementado o Relatorio de Caracterização da Base de Dados com os visuais exemplificados no modulo anterior.


## Relatório de Caracterização da Base de Dados de Teste Company
Este projeto foi originado pela integração de uma Base de Dados do MySql no Azure, com o PowerBI. 

O objetivo consiste em realizar um pequena caracterização dos dados. 

Os valores são originados de uma base de testes.

