# Voxus-Task-

Instruçôes para rodar :

Vai baixar a pasta primeiroProjetoVoxus.rar (pode ser que essa pasta vá zipada duas vezes)
Após isso, vá até o eclipse  
Em file > import 
Dentro de import, abra a pasta General (geralmente a primeira)  depois escolha a opção Existing Projects into Workspace. Após clicar aperte em Next. 
Na pagina que vai abrir deixe em select root directory : vá em browser e selecione a pasta do projeto  (descompactada)
Ele vai localizar o projeto e dentro da aba projects vai aparecer > primeirProjetoVoxus e o local a onde o arquivo está. Após isso aperte em finish.

Na aba Project explore do lado esquerdo ira aparecer o projeto. 
Ele pode estar dando erro caso o jre não seja o 1.8.0_144
Na pasta do projeto, vamos clicar com o botão direito e ir em propriedades, e do lado esquerdo selecionar Java Build Path. na janela que abrir vamos ate libraries. Veremos que o jre esta com um X vamos clicar em cima dela e apertar o botão a direta edit. Na janela que abrir, você vai selecionar o Workspace Default JRE (numero do seu JRE) após isso vamos clicar em Finish. 

Após isso vamos instalar o servidor Tomcat 8.0.47 . Baixe o arquivo zip do tomcat que esta no github 
Vamos no botão File > New > Other..(geralmente o ultimo da lista). Após isso vai abrir uma janela no campo de busca vamos digitar Server. Clique na opção server. Vai aparecer outra janela no campo de busca digite tomcat e encontre a versão Tomcat v8.0 Server. Selecione essa opção e aperte em Next. Na janela que vai abrir, vamos em browser e iremos selecionar a pasta  a onde esta o tomcat. Após isso vamos clicar em next e vai aparecer uma tela dos projetos que podem ser configurados, um deles vai ser o primeiroPorjetoVoxus. Selecione ele e clique em add. Após isso pode clicar em finish. 

Agora na pasta Project Explore selecione o projeto  primeiroPorjetoVoxus clique com o botão direito e vai em Run As > run on server. Após isso verifique se aparece o nome Tomcat v8.0 server at localhost. Após isso aperte em finish. A pagina principal vai estar aparecendo com dois menus de navegação dentro de Task tem o menu Listagem task andamento e listagem das task encerradas 

Obrigado pela atenção qualquer duvida me chamem no email Raulalves1@gmail.com

Agora para conseguirmos colocar o banco de dados iremos ter que criar as tabelas dentro do banco e configurar o  Banco de dados  e estou usando o workBench do mySql.

Os comandos para criar as tabelas foram : 

CREATE SCHEMA IF NOT EXISTS ` bd_task ` DEFAULT CHARACTER SET utf8 ;
USE ` bd_task ` ;

-- -----------------------------------------------------
-- Table `task`.`Usuario`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `bd_task`.`Usuario` (
  `codigoUsuario` INT NOT NULL AUTO_INCREMENT,
  `nomeUsuario` VARCHAR(45) NOT NULL,
  `setor` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`codigoUsuario`),
  UNIQUE INDEX `nomeUsuario_UNIQUE` (`nomeUsuario` ASC))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table ` bd_task `.`task`
-- -----------------------------------------------------

CREATE TABLE IF NOT EXISTS ` bd_task `.`task` (
  `codigoTask` INT NOT NULL AUTO_INCREMENT,
  `nomeTask` VARCHAR(45) NOT NULL,
  `problema` VARCHAR(45) NOT NULL,
  `descricao` VARCHAR(1000) NOT NULL,
  `prioridade` INT NOT NULL,
  `dataDeInicio` VARCHAR(8) NULL,
  `dataFim` VARCHAR(8) NULL,
  `Usuario_codigoUsuario` INT NOT NULL,
  `status_task` VARCHAR(45) NULL,
  PRIMARY KEY (`codigoTask`),
  UNIQUE INDEX `nomeTask_UNIQUE` (`nomeTask` ASC),
  INDEX `fk_table1_Usuario_idx` (`Usuario_codigoUsuario` ASC),
  CONSTRAINT `fk_table1_Usuario`
    FOREIGN KEY (`Usuario_codigoUsuario`)
    REFERENCES `task`.`Usuario` (`codigoUsuario`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;





***********************************************************


Tempo: Comecei no dia 23/11 


Parte​ ​1:​ ​CRUD: Finalizei às 17 horas do dia 27/11. Utilizei o material no link abaixo para consulta desde o início até o fim para terminar essa parte:

https://www.youtube.com/watch?v=Vb5Lk00UeI4&list=PL_GwGUsBlNycg0Ath1oYKCEPmaBkcehBD&index=3 

Parte​ ​2:​ ​Login​ ​Autenticado​ ​com​ ​o​ ​Google: Não realizado.
Tentei seguir alguns tutorias que realizavam o login , mas não encontrei nada em xhtml. Tentei seguir em outras linguagens e adaptar, mas infelizmente nao consegui. Abaixo um dos videos que assisti: 

https://www.youtube.com/watch?v=fhE2kEiop6c


Parte​ ​3:​ ​Tasks​ ​Mais​ ​Complexas
Nome da task: realizado junto a Parte 1. 

Descrição da task: Realizada junto a Parte 1.

Quantidade indefinida de anexos : Nao reãlizado. Não encontrei material relacionado aos anexos utilizando xhtml. 

Prioridade da task: Realizada junto a Parte 1.

Usuário que submeteu a task: Realizado junto a Parte 1.


Parte​ ​4:​ ​Tasks​ ​Completas: Realizada parcialmente porque não consegui realizar o sistema de login, como não consigo pegar o id do usuário que esta encerrando, o próprio usuário que vai encerrar insere o ID dele no formulário de edição. 
Levei meio período do dia 29/11.


Parte​ ​5:​ ​Suporte​ ​Robusto​ ​para​ ​Anexos​ ​+​ ​Busca: Infelizmente não consegui identificar uma forma de realizar isso dentro do xhtml, por ter pouco conhecimento na linguagem, infelizmente ficou um pouco complicado realizar esse processo. 


---------------------------
As assumptions que você fez para o desenvolvimento? 

Pensei em começar por fazer uma tela de seleção de task onde eu poderia criar, editar e excluir as tasks. 

Já iniciei juntando a Parte 1 com a Parte 3 para poupar tempo no desenvolvimento do projeto.

Na parte de listagem eu havia imaginado listar as tasks para o usuário somente pelo ID dele, para que o mesmo não pudesse alterar alguma informação de outras tasks e até mesmo diminuir a poluição da sua tela. Mas como não consegui realizar a parte de login, ficou inviável este método. (Também estava pensando em desenvolver uma parte para os Devs conseguirem listar todas as tasks de todos os usuários).

Na edição de tasks desde o início o intuito era deixar o usuário alterar tudo, exceto o ID e o nome do usuário. Isso foi concluído com sucesso :D 

Deleção de task: Na tela de listagem o usuário tem o botão de deletar onde após clicar, aparecerá as informações da task que ele quer deletar. 


Parte​ ​2:​ ​Login​ ​Autenticado​ ​com​ ​o​ ​Google
O intuito era criar duas telas de login: uma pra o usuário e a outra para os Devs logarem, para conseguirem ver as tasks e etc. 


Parte​ ​3:​ ​Tasks​ ​Mais​ ​Complexas

Nesta etapa juntei boa parte com a Parte 1, o que me facilitou bastante em relação ao tempo. A parte de anexos deixei para fazer depois, pois não sabia como iria fazer. 

Parte​ ​4:​ ​Tasks​ ​Completas

A partir deste momento pensei em criar duas telas: uma de task em andamento e a outra de task concluídas, para que não gerasse confusão no layout do sistema. 


Parte​ ​5:​ ​Suporte​ ​Robusto​ ​para​ ​Anexos​ ​+​ ​Busca:

Infelizmente não sabia nem por onde começar essa parte. Pensei em começar aquilo que parecia ser mais tranquilo de fazer, mas terminei as partes acima, e infelizmente continuei travado nessa parte. D: 

-----------------------------------------

Principais dificuldades e desafios:

Um dos maiores desafios foi a falta de conhecimento na parte web. Comecei a pesquisar bastante sobre tutorias e vídeos no youtube, achei uma playlist no youtube de um rapaz ensinando como programar em java web. Após isso entendi que estava mexendo especificamente com JSF. 

Uma das maiores dificuldades foi encontrar conteúdo sobre login, upload de arquivos e outras coisas. Infelizmente parece que fiz uma escolha errada, deveria ter buscado alguma linguagem que já teria essa facilidade de ferramenta.
