## Resultado

Clique [AQUI](../media/bd-2023-2-bcc-resumo.pdf) para ver as notas.

#### Avaliação em 04/10/2023
1. Conforme enunciado da questão, a definição de banco de dados ser tal que "englobe o conteúdo das seis definições apresentadas". Nesse sentido, a definição deve mencionar: (1) conjunto de dados; (2) dados relacionados entre si; (3) dados operacionais (reflete a dinâmica de algum domínio); (4) dados armazenados (os dados são retidos/guardados, pois possuem valor); (5) dados usados (há audiência, o que inclui o uso de sistemas/aplicações).
2. Apresentar exemplos de metadados, em vez de classificação de metadados. Os exemplos devem ser contextualizados, evitando respostas curtas que dão margem a abstração e ambiguidade (dado ou metadado?). Por exemplo: 'título de um livro', em vez de 'título'.

#### Avaliação em 11/10/2023
1. A independência de dados denota a habilidade de modificar a definição de um esquema em um nível de abstração, sem afetar a definição do esquema em um nível de abstração mais alto. Duas relações são consideradas iguais se: possuem as mesmas _tuplas_, independente da ordem (sequência) das mesmas.
2. Número total de valores do atributo A1 em r, incluindo valor nulo - número de tuplas; valores distintos que o atributo A1 pode ter - domínio de atributo; subconjunto do produto cartesiano dos domínios dos atributos - relação; conjunto de tuplas de R -	relação; conjunto de relações - banco de dados; dom(A1) × dom(A2) × ... × dom(Am)	- domínio da relação; identifica cada tupla da relação - chave primária/chave candidata; conjunto de esquemas de relação - esquema de banco de dados; R(A1, A2, ...,Am)	- esquema de relação; lista ordenada de valores: <v1, v2, ..., vm> - tupla.

#### Avaliação em 18/10/2023

- Quantas cópias do livro intitulado “Tribo Perdida” existem na unidade da biblioteca cujo nome é “Central”? -> LIVRO_COPIAS (Cod_livro) REFERENCES LIVRO (Cod_livro); LIVRO_COPIAS (Cod_unidade) REFERENCES UNIDADE_BIBLIOTECA (Cod_unidade)
- Recupere o nome de todos os usuários que não possuem livros emprestados em seu nome. -> LIVRO_EMPRESTIMOS (Nr_cartao) REFERENCES USUARIO (Nr_cartao)
- Para cada livro que é emprestado da unidade da biblioteca cujo nome é “Central” e cuja data de devolução é hoje, recupere o título do livro, o nome e o endereço do usuário que pegou o livro emprestado. -> LIVRO_EMPRESTIMOS (Cod_unidade) REFERENCES UNIDADE_BIBLIOTECA (Cod_unidade); LIVRO_EMPRESTIMOS (Cod_livro) REFERENCES LIVRO (Cod_livro); LIVRO_EMPRESTIMOS (Nr_cartao) REFERENCES USUARIO (Nr_cartao)
- Para cada unidade da biblioteca, recupere o nome da unidade e o número total de livros emprestados pela unidade. -> LIVRO_EMPRESTIMOS (Cod_unidade) REFERENCES UNIDADE_BIBLIOTECA (Cod_unidade)
- Recupere o nome, endereço e número de livros emprestados para todos os usuários que possuem mais de cinco livros emprestados. -> 
LIVRO_EMPRESTIMOS (Nr_cartao) REFERENCES USUARIO (Nr_cartao)
- Para cada livro cujo autor (ou coautor) é “Stephen King”, recupere o título e o número de cópias pertencentes à unidade da biblioteca cujo nome é “Central”. -> LIVRO_AUTOR (Cod_livro) REFERENCES LIVRO (Cod_livro); LIVRO_COPIAS (Cod_unidade) REFERENCES UNIDADE_BIBLIOTECA (Cod_unidade); LIVRO_COPIAS (Cod_livro) REFERENCES LIVRO (Cod_livro)

#### Avaliação em 25/10/2023

1. RESULT ← π <sub>Pnome</sub> ( FUNCIONARIO ⋈ <sub>Cpf = Fcpf</sub> DEPENDENTE )
1. AUX ← π <sub>Cpf_gerente</sub> ( FUNCIONARIO ⋈ <sub>Cpf_supervisor = Cpf_gerente</sub> DEPARTAMENTO )<br>RESULT ← π<sub>Pnome</sub> ( FUNCIONARIO ⋈ <sub>Cpf = Cpf_gerente</sub> AUX )
1. RESULT ← π <sub>T1.Fcpf</sub> ( ρ <sub>T1</sub> (TRABALHA_EM) ⋈ <sub>T1.Fcpf = T2.Fcpf</sub> &#8743; <sub>T1.Pnr &#8800; T2.Pnr</sub> ρ <sub>T2</sub> (TRABALHA_EM) )

#### Avaliação em 01/11/2023

1. RESULT ← π <sub>FUN.Pnome, SUP.Pnome</sub> ( ρ FUN (FUNCIONARIO) ⋈ <sub>FUN.Cpf_supervisor = SUP.CPF</sub> ρ SUP (FUNCIONARIO) )
1. JOAO_CPF ← π <sub>Cpf</sub> ( σ <sub>Pnome="Joao" &#8743; Unome="Silva"</sub> (FUNCIONARIO) )<br>
JOAO_DEPENDENTES ← π <sub>Nome_dependente</sub> ( JOAO_CPF ⋈ <sub>JOAO_CPF.Cpf = DEPENDENTE.Fcpf</sub> DEPENDENTE )<br>
~~JOAO_DEPENDENTES ← σ <sub>Fcpf = JOAO_CPF</sub> ( DEPENDENTE )~~<br>
TODOS_DEPENDENTES ← π <sub>Pnome, Nome_dependente</sub> ( FUNCIONARIO ⋈ <sub>FUNCIONARIO.Cpf = DEPENDENTE.Fcpf</sub> DEPENDENTE )<br>
RESULT ← TODOS_DEPENDENTES &#247; JOAO_DEPENDENTES<br>
<sup>Não considera funcionários homônimos e dependentes homônimos.</sup>
1. PROJETOS_FUNC (Cpf, Qtde_projetos) ← Fcpf ℑ CONTA Fcpf ( TRABALHA_EM )<br>
PROJETOS_FUNC_DOIS ← σ <sub>Qtde_projetos=2</sub> ( PROJETOS_FUNC )<br>
RESULT ← π <sub>Pnome</sub> ( PROJETOS_FUNC_DOIS ⋈ <sub>PROJETOS_FUNC_DOIS.Cpf = FUNCIONARIO.Cpf</sub> FUNCIONARIO )

#### Avaliação em 08/11/2023

1. CERVEJA_PIPOCA ← π <sub>Cerveja</sub> ( σ <sub>Bar="Pipoca"</sub> ( VENDE ) )<br>
RESULT ← π <sub>Pessoa</sub> ( CERVEJA_PIPOCA ⋈ <sub>CERVEJA_PIPOCA.Cerveja = GOSTA.Cerveja</sub> GOSTA )
1. CERVEJA_PIPOCA ← π <sub>Cerveja</sub> ( σ <sub>Bar="Pipoca"</sub> ( VENDE ) )<br>
PESSOA_PIPOCA ← π <sub>Pessoa</sub> ( CERVEJA_PIPOCA ⋈ <sub>CERVEJA_PIPOCA.Cerveja = GOSTA.Cerveja</sub> GOSTA )<br>
RESULT ← π <sub>Pessoa</sub> ( GOSTA )  &#8213; PESSOA_PIPOCA
1. CERVEJA_PIPOCA ← π <sub>Cerveja</sub> ( σ <sub>Bar="Pipoca"</sub> ( VENDE ) )<br>
CERVEJA_NAO_PIPOCA ← π <sub>Cerveja</sub> ( VENDE ) &#8213; CERVEJA_PIPOCA<br>
PESSOA_NAO_PIPOCA ← π <sub>Pessoa</sub> ( CERVEJA_NAO_PIPOCA ⋈ <sub>CERVEJA_NAO_PIPOCA.Cerveja = GOSTA.Cerveja</sub> GOSTA )<br>
RESULT ← π <sub>Pessoa</sub> ( GOSTA )  &#8213; PESSOA_NAO_PIPOCA

#### Avaliação em 29/11/2023

1. SELECT P.CodProd, P.Nome, SUM(VI.QtdeVenda), SUM(VI.QtdeVenda * P.Preco)<br>
FROM PRODUTO AS P<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;JOIN VENDA_ITEM AS VI ON P.CodProd = VI.CodProd<br>
GROUP BY P.CodProd, P.Nome
1. SELECT P.CodProd, P.Nome<br>
FROM PRODUTO AS P<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;JOIN VENDA_ITEM AS VI ON P.CodProd = VI.CodProd<br>
GROUP BY P.CodProd, P.Nome<br>
HAVING SUM(VI.QtdeVenda * P.Preco) > 10000
1. SELECT C.CPF, C.Nome, SUM(VI.QtdeVenda), SUM(VI.QtdeVenda * P.Preco)<br>
FROM CLIENTE AS C<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;JOIN VENDA AS V	ON C.CPF = V.CPF<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;JOIN VENDA_ITEM AS VI ON V.NumNF = VI.NumNF<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;JOIN PRODUTO AS P ON VI.CodProd = P.CodProd<br>
GROUP BY C.CPF, C.Nome

#### Avaliação em 06/12/2023

Script para o BD<br>
CREATE TABLE FABRICA ( Unidade varchar(30), Produto varchar(30));<br>
INSERT INTO FABRICA VALUES ('Central', 'Bola');<br>
INSERT INTO FABRICA VALUES ('Central', 'Mouse');<br>
INSERT INTO FABRICA VALUES ('Central', 'Teclado');<br>
INSERT INTO FABRICA VALUES ('Central', 'Monitor');<br>
INSERT INTO FABRICA VALUES ('Central', 'Guardanapo');<br>
INSERT INTO FABRICA VALUES ('Praia', 'Bola');<br>
INSERT INTO FABRICA VALUES ('Praia', 'Cadeira');<br>
INSERT INTO FABRICA VALUES ('Praia', 'Mouse');<br>
INSERT INTO FABRICA VALUES ('Interior', 'Carro');<br>
INSERT INTO FABRICA VALUES ('Interior', 'Computador');<br>
CREATE TABLE USA ( Cliente varchar(30), Produto varchar(30));<br>
INSERT INTO USA VALUES ('Lia', 'Bola');<br>
INSERT INTO USA VALUES ('Lia', 'Cadeira');<br>
INSERT INTO USA VALUES ('Maria', 'Computador');<br>
INSERT INTO USA VALUES ('Maria', 'Carro');<br>
INSERT INTO USA VALUES ('Pedro', 'Teclado');<br>
INSERT INTO USA VALUES ('Pedro', 'Monitor');<br>
INSERT INTO USA VALUES ('Pedro', 'Mouse');<br>
INSERT INTO USA VALUES ('Ricardo', 'Guardanapo');<br>

1. SELECT DISTINCT Cliente FROM USA<br>
WHERE Produto IN (<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SELECT Produto FROM FABRICA WHERE Unidade = 'Central'<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;EXCEPT<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SELECT Produto FROM FABRICA WHERE Unidade != 'Central' )
1. SELECT Cliente FROM USA<br>
EXCEPT<br>
SELECT Cliente<br> 
FROM USA NATURAL JOIN FABRICA<br>
WHERE Unidade = 'Central'
1. SELECT DISTINCT Cliente FROM USA<br>
WHERE Cliente NOT IN (<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SELECT Cliente<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;FROM USA<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHERE Produto NOT IN (<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SELECT Produto FROM FABRICA<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHERE Unidade = 'Central' ) )

#### Avaliação em 13/12/2023

1. SELECT DISTINCT X.NOME FROM PACIENTE V JOIN MEDICO W JOIN MEDICAMENTO X JOIN CONSULTA Y JOIN PRESCRICAO Z ON V.CPF = Y.CPF AND W.CRM = Y.CRM AND Z.CPF = Y.CPF AND Z.DATAHORA = Y.DATAHORA AND Z.CODIGO = X.CODIGO WHERE V.NOME = W.NOME GROUP BY Y.CPF, Y.CRM, X.CODIGO, X.NOMEHAVING COUNT(*) > 1
1. Pode ter valores repetidos nas tuplas de QUESTAO. Pode ter valor nulo em algumas das tuplas de QUESTAO. 
1. A ordenação das tuplas de uma relação é indiferente, visto que uma relação é definida como um conjunto de tuplas. Uma tupla é uma lista ordenada de valores, então há uma posição relativa pré-definida para cada valor de atributo na tupla (por exemplo, o valor “13/02/2000”, pertinente ao atributo “data de nascimento”, é o terceiro valor na lista de valores de uma tupla).



