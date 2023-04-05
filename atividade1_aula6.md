<!-- markdownlint-disable MD024 -->
# Backlog Priorizado

Aluno: Marcio Vinicius de Souza da Rocha

---

1. Construir o backlog das tarefas que serão realizadas (podem considerar outras funcionalidades necessárias)
2. Definir as ordens de prioridade para as entregas das funcionalidades solicitadas nos seugintes niveis
   1. Alta
   2. Média
   3. Baixa

## Sistema Web de Biblioteca

### Perfis de Usuários

* Alunos
* Atendentes
* Administradores

### Funcionalidades

* Consultar e resevar livros
* Adicionar comentários sobre os livros
* Consultar empréstimos em atraso
* Emprestar livros entre bibliotecas (comuniação inter-bibliotecas)

---

### Backlog

| Ordem | Prioridade | Funcionalidade |
| --- | --- | --- |
| 1 | Alta | Cadastrar usuário |
| 1 | Alta | Cadastrar Livros |
| 3 | Média | Consultar Livros |
| 4 | Média | Atualizar status do livro |
| 6 | Média | Consultar Empréstimos em atraso |
| 7 | Baixa | Comunicação inter-bibliotecas |
| 8 | Baixa | Comentários sobre os Livros |

### Tarefas

#### Cadastrar usuário

##### Alterações do Banco de Dados

* Criar Tabela **Pessoa** (Possui todos os dados referentes à uma pessoa)
* Criar Tabela de Aluno, responsável pelos dados de um perfil de aluno (possui FK da **Pessoa**)
* Criar Tabela de Atendente, responśavel pelos dados de um perfil de atendente (possui FK da **Pessoa**)
* Criar Tabela de Administrador, responsável pelos dados de um perfil de administrador (possui FK da **Pessoa**)

##### Alterações do Software

* Criar interface de **IPessoa**, com comportamento base
* Criar a interfafe **IAluno**, esta é herdeira de **IPessoa**
* Criar a interface **IAtendente**, esta é herdeira de **IPessoa**
* Criar a interface **IAdministrador**, esta é herdeira de **IPessoa**
* Criar classes que implementar as interfaces **IAluno, IAtendente e IAdministrador**
* Criar mapemanto Objeto-Relacional referente às classes
* Desenvolver formulário de cadastro de **IPessoa**
* Restringir o formulário para o perfil **IAdministrador**

#### Cadastrar Livro

##### Alterações do Banco de Dados

* Criar tabela **Biblioteca**, indicador de locaziação de qual biblioteca está armazenado o livro
* Criar tabela **Estante**
* Criar tabela **BibliotecaEstante** que irá conter o relacionamento *n-n* entre **Biblioteca** e **Estante**
* Criar tabela **Livro**, contém as informações de "metadados" do livro, possui FK da tabela de relacionamento **BibliotecaEstante**

##### Alterações do Software

* Criar interface **IBiblioteca**
* Criar interface **IEstante**
* Criar interface **BibliotecaEstante**
* Criar interface **ILivro**
* Criar as classes que implementam as interfaces **IBiblioteca, IEstante, IBibliotecaEstante, ILivro**
* Criar mapeamento Objeto-Relacional referente ás classes
* Desenvolver Formulário de Cadastro de **Bibliotecas**, **Estante**, e **Livro**
* Restrir o formulário criado para os perfis **IAtendente, IAdministrador**

#### Consultar Livros

##### Alterações do Software

* Criar tela para consulta dos livros
* Reutilizar as classes e mapeamentos previamente criados
* Permitir Selecionar Livros por ID (Alteração na DAL)
* Permitir selecionar Livros por Autor (Alteração na DAL)
* Permitir selecionar Livros por Nome (Alteração na DAL)
* Permitir selecionar Livros por Ano de publicação (Alteração na DAL)
* Permitir selecionar Livros por Editora (Alteração na DAL)

#### Atualizar stauts do Livro

##### Alterações do Software

* Por meio da tela de Consultar Livros permitir atualizar status do livro
  * **Disponível**
  * **Locado**
  * **Atrasado**
  * **Em Reforma**
* Status **Disponível** só pode ser alterados para
  * **Locado**
  * **Em Reforma**
* Status **Locado** só pode ser alterado para
  * **Disponível**
  * **Atrasado**
* Status **Atrasado** só pode ser alterado para **Disponível**
* Status **Em Reforma** só pode ser alterado para **Disponível**

#### Consultar Empréstimos em atraso

##### Alterações do Software

* Criar opção de selecionar livro pela Data de Devolução
* Criar botão na tela de consulta de livros para selecionar com datas maiores que a data atual

#### Comunicação inter-bibliotecas

##### Alterações do Software

* Criar possibilidade de consulta em outras bibliotecas
* Criar reserva de livro em outra biblioteca
  * Transferir o livro para o acervo da outra biblioteca (que será retirado o livro)
  * Marcar o livro como **Reservado** para uma entidade **IPessoa**
* Criar devolução de livro em outra biblioteca
  * Transferir o livro par ao acervo da outra biblioteca (que receberá/recebe o livro)
  * Atualizar Status do livro para **Disponível**

#### Comentários sobre os Livros

##### Alteraçõs do Banco de Dados

* Criar tabela **Comentário**, possui FK de **Livro**
* Alterar relacionamento do acervo para que diversas cópias de um livro possuam o mesmo comentário, isto não deve ser limitado à uma biblioteca

##### Alterações do Software

* Corrigir mapeamento Objeto-Relacional
* Criar interface **ICOmentario**
* Criar classe **Comentario** que implementa a interface **IComentario**
