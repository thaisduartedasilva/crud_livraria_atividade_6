# crud_livraria

RF1: Cadastrar Livro: o sistema deve permitir cadastrar livros informando titulo, autor e ano de publicação;
RF2: Listar Livros: o sistema deve apresentar todos os livros cadastrados;
RF3: Editar Livros: o sistema deve permitir a alteração de informações de livros já cadastrados;
RF4: Excluir Livros: o sistema deve permitir a exclusão de informações de livros já cadastrados;

(1/2) RNF1: Validação dos Campos: O sistema não deve permitir o cadastro de livros com titulo, autor ou ano vazios.

# Prepared Statement

A pasta de cadastro foi alterada para incorporar o Prepared Statement, colocando "?" no lugar de colocar diretamente "$titulo, $autor e $ano", também foi adicionado "bind_param()" que coloca os valores das variáveis nos lugares reservados, e o "execute()" para executar a consulta. 

O "ssi" significa:
- s: string ($titulo)
- s: string ($autor)
- i: inteiro ($ano)

Desse modo os dados o usuário ficam separados do comando SQL, o que torna o código mais seguro contra SQL Injection.   