# Arquivo ainda em Edição!	
    
## O que é um repositório?

Segundo o [dicio](https://www.dicio.com.br/repositorio/) um repositório é o local em que algumas coisas são guardadas, arquivadas ou colecionadas.

## O que é Git? (Repositório Local)

O Git nada mais é do que um sistema distribuido de versionamento de projetos, criado e projetado por Linus Torvalds em 2005. O sistema foi criado por ele porque o sistema de versionamento que ele usava para manter o desenvolvimento do kernel do linux começou a gerar mais problemas do que deveria, a partir disso, Linus decidiu criar o seu próprio sistema. Com o Git somos capazes de criar um histórico de alterações no nosso código, salvando pontos de restauração no tempo e conseguindo voltar para eles com facilidade. O Git também nos ajuda a controlar como funcionará o fluxo de implementação de novas funcionalidades no nosso sistema, pois oferece diversos recursos para evitar problemas que seriam causados pelo simples fato de terem várias pessoas trabalhando em um só projeto.
	
## E GitHub? (Repositório Remoto)

O GitHub além de uma rede social de programadores também é um repositório online onde você pode hospedar seus repositórios locais, além de conectá-los e sincronizá-los. Quando salvamos algum ponto de restauração na nossa máquina (chamados commits), outros programadores não tem acesso a eles pelo fato desses dados serem locais, mas quando utilizamos o GitHub estes dados passam a ter um lugar de acesso comum para serem salvos e acessados por diversos programadores.

## Comandos básicos do CMD para facilitar o trabalho (WINDOWS).
	
Primeiramente devemos deixar claro que tais comandos não servirão para o terminal do MacOs ou de um sistema Linux, já que são específicos para o CMD do Windows e cada SO tem seus próprios comandos de gerenciamento, mesmo que alguns deles sejam parecidos, ainda existirão diferença. É importante frizar que estes comando são básicos, e que existem muito mais, mas apenas estes são suficientes para começar a trabalhar com git.
	
`q` :pushpin: Voltar ao modo de digitação.

`cls` :pushpin: Limpa o CMD.

`cd NomeDoDiretório` :pushpin: Entra em um diretório especificado.

`cd ..` :pushpin: Volta um nível de diretório.

`dir` ou `tree/f` :pushpin: Mostra todos os arquivos que existem dentro do diretório que você se encontra.

`mkdir NomeDaPasta` ou `md NomeDaPasta` :pushpin: Cria uma pasta.

`rd NomeDaPasta` :pushpin: Apaga a pasta especificada.

`erase NomeDoArquivo` ou `del NomeDoArquivo` :pushpin: Apaga o arquivo especificado.

`copy > NomeDoArquivo.Extenção` ou `dir > NomeDoArquivo.Extenção` :pushpin: Cria um arquivo dentro do diretório em que você se encontra.


## Configurações iniciais.

A primeira coisa que devemos fazer após instalar o git certo para o sistema operacional que estamos usando, é fazer algumas configurações iniciais. No linux e mac podemos usar o terminal padrão para fazer essas configurações, já no windows devemos usar o GitBash, que é um terminal que vem junto com o pacote de instalação do git para windows. Essa configuração será feita apenas uma vez no seu usuário, já que o parâmetro --global define a configuração para todos os projetos do usuário atual, também é o mais recomendado. Também podemos utilizar o parâmetro --system válido para todos os usuários no sistema e todos os seus repositórios.

`git config --global user.name "Seu Nome"` :pushpin: Salvando o nome do usuário.

`git config --global user.email "seuemail@email.com"` :pushpin: Salvando o email do usuário.

`git config --global core.editor SeuEditor` :pushpin: salvando o editor do usuário.

`git branch -M main` :pushpin: Apenas a fim de informação, houve alterações em alguns nomes no Github por terem cunho racista. A branch "master" agora se chama "main", por isso para posteriormente conectar o Git ao GitHub sem criar uma nova branch "master" ao ligar o repositório remoto ao local, no Github, temos o seguinte comando: `git branch -M main`, que nos permite mudar o nome da nossa branch principal para **main**.

### Após fazer as configurações iniciais podemos visualizá-las através dos comandos:

`git config user.Parâmetro` :pushpin: user.name Irá retornar "Seu Nome" por exemplo.

`git config --list` :pushpin: Irá retornar uma lista de tudo o que está salvo.

## Começando a utilizar o git.

Primeiramente você deve estar dentro do diretório que você deseja que seja "visto" ou "varrido" pelo git, eu por exemplo estou na pasta (C:\Users\GustavoRicardo\Documents\git-projects). Logo após isso podemos começa com o comando:

`git init` :pushpin: Uma vez estando dentro da pasta onde irá ficar o seu repositório deve-se usar este comando para iniciar o git, logo após isso você receberá uma mensagem de confirmação dizendo se o git foi ou não inicializado. É importante falar que todo diretório que esteja sendo "varrido" pelo git terá dentro dele uma pasta oculta (.git/) que contém informações importantes para o funcionamento.

## Ciclo de vida dos arquivos em Git.

O Git serpada todos os arquivos que estão sendo trabalhados em **4 estados bem definidos** do chamado "Ciclo de vida" dos arquivos, sendo eles:

**Untracked: (Não marcado)**  Este é o estado de um arquivo que acabou de ser adicionado no repositório mas ainda não foi "visto" pelo Git, o mesmo ainda não reconhece esse arquivo nem nenhuma versão dele. Arquivos recém criados no repositório sempre estarão nesse estado.

**Unmodified: (Não modificado)** Depois que você adiciona um arquivo Untracked no Git ele passa a ser Unmodified, ou seja, ele existe no git mas ainda não foi modificado.

**Modified: (Modificado)** Após fazer alguma edição ou alteração num arquivo Unmodified ele passa a ser considerado Modified.

**Staged:** Depois de modificado você pode deixar esse arquivo em um estágio chamado Staged, que basicamente diz ao Git "esse arquivo está pronto para ser salvo em um ponto de restaturação(commit)".

Logo após salvar(commitar) arquivos na versão **Staged** eles voltarão a ser **Unmodified**, pois eles foram salvos mas nada foi modificado desde o último commit.
 
## Comandos De Ciclo de Vida Git

`git status` :pushpin: Irá mostrar o que foi adicionado, alterado, deletado e em qual branch você está trabalhando.

`git add NomeDoArquivo` :pushpin: Para adicionar apenas um arquivo ainda no estado Untracked ou Modified, a partir deste momento o arquivo passa do estado Untracked ou Modified para Staged. Neste ponto é muito importante ter os clicos de vida claros.

`git add -A` ou `git add .` :pushpin: Adiciona TODOS os arquivos ainda no estado Untracked ou Modified, a partir deste momento TODOS os arquivos passamdo estado Untracked ou Modified para Staged. A única diferença do `.` para o `-A` é que a segunda opção deleta arquivos que foram apagados durante o processo de manutenção.

A Partir do momento em que eu adiciono um novo arquivo eu posso salvá-lo em um ponto de restauração(commitar), pois ele ainda não foi modificado, se eu modificá-lo ele irá cair no estado **Modified.** Quando um arquivo já adicionado é editado estando **Modified**, ao utilizar o o comando `git status` o Git me mostra que eu posso commitá-lo mas sem as modificações.

## Git Commit 

Primeiramente é importante entender o que é um commit. Toda vez que você quiser salvar o seu projeto naquele estado em que ele se encontra, um ponto de restauração com o repositório naquele exato momento pode ser criado, esse ponto de restaturação se chama commit. Todo commit carrega consigo um hash (código de identificação), um resumo das alterações que foram feitas e algumas informações meta como autor do commit, data em que o commit foi feito e etc.

Agora uma dica que eu encontrei em um repositório do usuário [victorsenam](https://github.com/victorsenam)

>O ideal é que os commit sejam feitos de forma lógica e organizada, por exemplo: Você criou uma alteração no layout e vai comitar ela depois, ao invés de fazer commits separados ("Adição de div no HTML", "Alteração do CSS", "link do CSS"), faça um só commit ("Alteração no layout: "pequena descrição sobre a alteração").
Ou seja, faça commit de alterações já completas ou que possam ser completadas por alguém. Nunca separe alterações em pequenos commits de poucas mudanças. Para isso usamos o comando.

`git commit -m "DescriçãoDoCommit"` :pushpin: Faz um commit do repositório no estado atual, "-m" é um parâmetro para apontar a mensagem. Logo após este comando você receberá uma mensagem de retorno dizendo em qual branch você se encontra, quais alterações foram feitas e que mensagem foi passada, também é mostrado número identificador daquele commit (hash).

`git commit -am "DescriçãoDoCommit"` :pushpin: Recebe a mesma descrição do comando "git commit -m "DescriçãoDoCommit"" mas, pula o passo de adicionar arquivos que não são mais Untracked. Sendo assim só será necessário usar o "git add NomeDoArquivo" ou "git add -A" para arquivos Untracked.

`git log` :pushpin: Mostra um histórico de todos os commits que já foram feitas, juntamente com detalhes de cada um como o código de identificação, a mensagem que foi passada, o autor, email e a branch na qual aquele commit foi dado.

`git log --graph` :pushpin: Mais detalhes sobre a linha do tempo do repositório.

`git show IdentificadorCommit` :pushpin: Nos mostra mais detalhes sobre aquele commit específico, por exemplo o que foi modificado ou alterado e salvo pelo commit.

`git diff` :pushpin: Ele nos mostra o que foi modificado ou alterado, mas antes mesmo de commitar, assim podemos revisar o que fizemos antes de commitar algo.

`git diff --name-only` :pushpin: Mostra apenas o nome dos arquivos que foram modificados e não o que. Assim podemos revisar o que fizemos antes de commitar algo.

`git diff NomeDoArquivo` :pushpin: Mostra o que foi alterado apenas no arquivo especificado. Assim podemos revisar o que fizemos antes de commitar algo.

## Git Reset

Vamos imaginar um cenário em que após fazer uma alteração, antes de commitar você decidiu ver no git diff as alterações que foram feitas. Logo após analisar as alterações, você deseja não commitá-las e apenas voltar para o último ponto de restauração (commit) feito. Para isso utilizamos:

`git ckeckout NomeDoArquivo` :pushpin: Vai simplesmente voltar o arquivo para o estado antes de ser editado. Isso só funciona caso ele ainda não esteja no estado Staged ou seja, ele não pode ter sido adicionado, funcionará apenas no estado Modified.

`git reset HEAD` :pushpin: Tira as alterações atuais do estado Staged e deixa suas alterações no estado Modified. Isso serve para caso queira voltar um arquivo já adicionado para o último ponto de restauração pois, logo após utilizar este comando é possível utilizar o `git checkout NomeDoArquivo`.

Caso você já tenha dado um commit mas de forma errônea, com alterações que não deveriam ter sido feitas ou erros, pode usar outros parâmetros do "reset". Este "hashDoCommit" só fará sentido se for de um ou vários commit antes do que você quer apagar.

`git reset --soft hashDoCommit` :pushpin: Apaga o último commit e deixa o git com os arquivos deste commit no estado Staged, ou seja, prontos para serem commitados novamente. (Mais recomendado para trabalhos em equipe).

`git reset --mixed hashDoCommit` :pushpin: Apaga o último commit e deixa o git com os arquivos deste commit no estado Modified, ou seja, eles ainda terão de ser adicionados antes de ser commitados.

`git reset --hard hashDoCommit` :pushpin: Irá ignorar tudo que existiu e voltará para o commit que você quer, arquivos e alteração serão apagadas.

## Git Branches

Para iniciar devemos entender o que é uma branch. Quando você cria seu repositório local é criado um branch denominado main, todo commit que você dá é commitado diratamente no branch main e isso além de não ser uma prática tão boa pode causar alguns problemas. Para que isso não aconteça você cria uma branch (ramificação) que basicamente clona a main com exatamente tudo o que ela tinha naquele ponto, a partir daí você passa a trabalhar nessa branch criada e todos os seus commits serão comittados nessa ramificação. Depois de concluir as atualizações dos códigos da ramificação, você pode mesclar a ramificação com a principal. 

`git branch` :pushpin: Mostra as branches existentes e um "*" na branch que você se encontra no momento.

`git branch NomeDoBranch` :pushpin: Cria uma nova branch.
	
`git checkout NomeDoBranch` :pushpin: Entra na branch especificada.

`git branch -d NomeDoBranch` :pushpin: A opção -d é um atalho para --delete, que irá excluir o branch local, apenas se você já tiver feito push ou merge com seu branch remoto. Para deletar um branch é necessário primeiramente sair dela

`git branch -D NomeDoBranch` :pushpin: A opção -D é um atalho para --delete --force, ou seja, exclui o branch independente de seu status de push ou merge, portanto, tenha cuidado ao utilizar essa opção. Para deletar um branch é necessário primeiramente sair dela

## Como conectar o Git ao GitHub?

Como de forma ilustrativa é bem mais simples entender os passos dessa etapa, primeiramente deixarei alguns links para clarear a explicação:

[DevFuria](http://devfuria.com.br/git/tutorial-para-iniciar-com-o-git-e-o-github/)

[GitHub](https://docs.github.com/pt/github/authenticating-to-github/connecting-to-github-with-ssh)

Os comandos dados nessa etapa não precisam ser claramente entendidos por só dizerem sobre o tipo de chave que está sendo criada.

Primeiramente na nossa conta do GitHub devemos criar um repositório em branco. Apenas com o nome e a descrição.

Para conectar o GitHub a sua máquina você terá que gerar uma chave SSH. Uma chave SSH se resume em um protocolo que serve para ligar um usuário local a um servidor, neste caso o nosso servidor será o GitHub. Neste sistema existirá uma chave pública e uma chave privada, apenas a chave privada consegue abrir a chave pública. Tendo a chave pública em mãos nós a enviamos para o servidor (GitHub) e com a chave privada na nossa máquina nós conseguimos abrir a chave pública que se encontrano GitHub, resumidamente os passos serão:

`ssh-keygen -t rsa -b 4096 -C "meuemail@email.com"
Enter
Enter
Enter`

A partir desse momento, será baixada na sua máquina uma pasta nomeada **.ssh**, essa pasta normalmente se encontra dentro do caminho `C:/Users/SeuUsuário`. Esta pasta irá conter duas chaves, uma pública e uma privada. 

Depois disso é só ir no seu perfil do GitHub e seguir o caminho:  `settings > SSH and GPG keys > New SSH Key`, após fazer isso você deve colar o texto que existe dentro da sua chave pública na caixa de texto e adicioná-la. Neste momento o servidor já tem a chave pública dentro dele.

Agora, dentro do nosso Git devemos dizer a qual repositório remoto ele tem que se conectar, seguindo os comandos:

`git remote add origin UrlDoDiretorio` :pushpin: Este comando está dizendo para o nosso reposiório local que ele deve se conectar com um repositório remoto que está no link especificado. Lembrando que origin é o apelido para seu repositório remoto, pode-se ser utilizado qualquer nome, mas normalmente se utiliza origin.

A partir deste momento seu repositório local e remoto já devem estar interligados, para verificar isso basta digitar os comandos:

`git remote` :pushpin: Vai mostrar a qual repositório remoto seu repositório local está ligado.

`git remote -v` :pushpin: Tratá mais informações sobre  a qual repositório remoto seu repositório local está ligado.

### Git Pull

Sempre antes de enviar os arquivos locais para o servidor é interessante utilizar o **pull**, o que este comando faz é ir até o seu repositório remoto e baixar os conteúdos mais atualizados para o seu repositório local, para que quando você for mandar suas atualizações para o servidor não saia nada de errado nem arquivos faltando. Pull = Puxar.

`git pull origin main` :pushpin: Caso alguma alteração seja feita diretamente no seu repositório remoto (GitHub) e você queira trazê-lo para o repositório local é necessário utilizar este comando.



### Git Push

Logo após isso devemos utilizar o **push**, o que este comando faz é basicamente encontrar todos os arquivos do seu repositório local que já foram devidamente commitados e enviá-los para o seu servidor remoto. Note também que o nome é autoexplicativo já que push significa empurrar em português, logo estamos empurrando os arquivos do Git para o GitHub.

`git push -u origin main` :pushpin: Manda todo o meu repositório local para o GitHub, perceba que o -u só precisará ser utilizado na primeira vez. 

## Como clonar um repositório público para a sua máquina local?

Podemos simplesmente clonar qualquer repositório no GitHub para a sua máquina local, com apenas um comando:

`git clone LinkDoDiretorio` :pushpin: o Link SSH sempre é mais rápido que o HTTP. Após dar o comando ele fará uma pergunta (yes/no), basta digitar yes e dar Enter.

## Posteriormente estudar Fork, Pull request, Rebase e Merge.
