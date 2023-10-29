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

1. π <sub>Pnome</sub> ( FUNCIONARIO ⋈ <sub>Cpf = Fcpf</sub> DEPENDENTE )
1. AUX ← π<sub>Cpf_gerente</sub> ( FUNCIONARIO ⋈ <sub>Cpf_supervisor = Cpf_gerente</sub> DEPARTAMENTO )<br>RESULT ← π<sub>Pnome</sub> ( FUNCIONARIO ⋈ <sub>Cpf = Cpf_gerente</sub> AUX )
