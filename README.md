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

# Melhorando a Segurança do CRUD com Prepared Statements


## O que é um Prepared Statement?

Os Prepared Statements são declarações preparadas – literalmente como uma tradução do inglês para o português – que são armazenados no servidor de bancos de dados com a finalidade de executar consultas sem variação sintática, com dinamismo apenas nos parâmetros. Um Prepared Statement pode ainda ser definido dentro ou fora do contexto de um banco de dados e pode receber ou não parâmetros para sua execução. 
O maior benefício que se tem em trabalhar com os Prepared Statements é a velocidade na execução dos comandos SQL, pois, após preparada, a declaração SQL é armazenada de forma pré-compilada no servidor de bancos de dados, sendo “parcelado” somente uma vez, mesmo que executado várias vezes. Após prepararmos uma declaração, podemos executá-lo através do comando EXECUTE, seguido pelo nome dado ao Prepared Statement. 
O Prepared Statement consiste em duas etapas: preparação e execução. Na etapa de preparação, um modelo de instrução é enviado ao servidor de banco de dados. O servidor realiza uma verificação de sintaxe e inicializa os recursos internos do servidor para uso posterior.
O servidor MySQL suporta o uso de marcadores de posição anônimos com ?.
A etapa de preparação é seguida pela de execução. Durante a execução, o cliente associa os valores dos parâmetros e os envia ao servidor. O servidor executa a instrução com os valores associados, utilizando os recursos internos previamente criados.




## O que é SQL Injection?

Uma injeção SQL (SQLi) é um tipo de ataque no qual cibercriminosos tentam explorar vulnerabilidades no código de um aplicativo inserindo uma consulta SQL em campos regulares de entrada ou formulário, como um nome de usuário ou senha. A instrução SQL é então passada para o banco de dados SQL subjacente do aplicativo.
Os  ataques de injeção SQL são bem-sucedidos quando o formulário de entrada baseado na  web permite que as instruções SQL geradas pelo usuário consultem o banco de dados diretamente. Esses ataques também se proliferaram com o uso de bases de código compartilhadas, como plugins do WordPress, que  contêm uma vulnerabilidade no padrão de código subjacente. Essa vulnerabilidade é transferida para todo o aplicativo e pode afetar  centenas de milhares de sites que usam esse código compartilhado.
O dano pode ser vasto. Um invasor com bom conhecimento de SQL insere consultas em um aplicativo baseado na web sem parâmetros de validação de entrada em vigor e, em seguida, acessa facilmente os arquivos de clientes de uma empresa ou informações financeiras confidenciais.
Como prevenir a injeção de SQL (SQLi):
Higienização
Se os invasores puderem inserir uma consulta inesperada que o aplicativo aceitar, então faz sentido limitar a funcionalidade de entrada para proteger os dados. Os desenvolvedores podem empregar validação de entrada ou higienização, portanto, o aplicativo aceita apenas certas entradas em campos de formulário e rejeita aquelas que não estão em conformidade. Os usuários da Web estão familiarizados com essa prática. Um exemplo é quando eles são solicitados a criar uma senha que deve ter um determinado número de caracteres e inclui pelo menos um caractere especial.
No entanto, esta não é uma solução ideal porque é difícil planejar todas as combinações de entrada permitidas. Um número substancial de erros resultará de usuários, que podem ser funcionários ou clientes. Isso pode afetar significativamente as operações comerciais. 
Filtragem e validação
Para filtrar o SQLi e bloquear ameaças potenciais, as empresas podem instalar umfirewall de aplicativo  web (WAF).WAF Um WAF combina as entradas de um aplicativo com uma grande lista de assinaturas conhecidas para impedir consultas SQL maliciosas. A lista é atualizada e corrigida regularmente para que uma organização possa acompanhar o cenário de ameaças em evolução.
Limitação do escopo dos comandos SQL
Embora a filtragem  paraSQLi  seja necessária, o bloqueio de 100% das consultas SQL não é viável. Funcionários, parceiros ou especialistas do setor de segurança podem ter que testar o aplicativo e precisarão de permissão para fazê-lo. O WAF pode verificar a entrada com dados de protocolo de internet (IP) antes de bloquear a solicitação. 
Evite parâmetros de URL desprotegidos
Se um site não usar o Hypertext Transfer Protocol Secure (HTTPS), que aproveita a segurança da camada de soquetes seguros/camada de transporte (SSL/TLS) para criptografia, um invasor pode manipular o cookie de sessão com SQLi para obter acesso ao banco de dados. As organizações devem proteger seus URLs de sites e aplicativos web para evitar isso.

## Fonte: 
- https://www.php.net/manual/en/mysqli.quickstart.prepared-statements.php
- https://imasters.com.br/data/mysql-prepared-statement
- https://www.fortinet.com/br/resources/cyberglossary/sql-injection
