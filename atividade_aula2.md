# Entrega Somativa 1

Aluno: Marcio Vinicius de Souza da Rocha

---

Identifique um problema para ser resolvido.

Utilizar uma das técnicas de análise de problemas e identificação de causa raiz, discutidas durante a aula.

## Problema

Após a alteração do João das Couves em uma determinada tela de software, **Cadastro Usuário**, apresentou erros durante os testes dessa alteração ao abrir outra tela do sistema, **Cadastro de Contrato**, impossibilitando a usabilidade da tela de **Cadastro de Contrato**. Esta apresenta a mensagem: *"A classe de Contratos não está registrada.".*

## Técnica utilizada

### 5 Porquês

#### 1 - Por que a tela de **Cadastro de Contrato** está inutilizada?

O erro reportado ao abrir a classe diz respeito à um software de autenticação externo, em que todas as classes que são instanciadas devem possuir o registro neste software, caso contráiro não é possível instânciar a(s) determinada(s) classe(s). Normalmente esta mensagem é apresentada na ausência do registro dessa classe no software externo.

#### 2 - Por que existe falha no registro desta classe?

Após verificação das classes utilizadas pela tela de **Cadastro de Contrato** chega-se à conslusão que todas possuem o registro do nome da classe no sitema de autenticação. Portanto deve-se atentar às importações dessas classes neste sistema. Ao checar estas importações percebe-se que a classe de Contratos não está importada no sistema de autenticação, apenas existe o registro nominal da mesma.

#### 3 - Por que a classe de Contrato não está importada no sistema de autenticação?

Ao verificar os LOGs é possível constatar que em versões anteriores existe o registro normal e funcionamento completo do sistema. Mas houve uma alteração não documentada na tela de **Cadastro de Contrato** por um desenvolvedor e este cometeu um erro e acabou removendo a classe errada.

#### 4 - Por que o desenvolvedor cometeu o erro?

Após identificar os registros de alterações do desenvolvedor é possível identificar que o mesmo utilizou uma ferramenta de versionamento de código de maneira errada ao tentar corrigir um outro erro que este cometeu tentando restaurar uma versão mais antiga de um arquivo com nome semelhante ao que contém a classe de Contratos.

#### 5 - Por que os arquivos contém nomes semelhantes?

Após analisar as documentações dos arquivos semelhantes é possível constatar que o desenvolvedor estava trabalhando em uma demanda de atualização do sistema, migrando a maneira de instanciação das classes para uma maneira mais nova. Neste cenário o desenvolvedor criou uma classe nova para substituir a classe antiga de contratos. Com isso acabou deixando as utilizações do sistema no "modo antigo" ao invés de atualizar as utilizações da mesma.

#### Sugestão de solução

Realizar alteração dos testes unitários, de integração e de utilização para a nova classe. Assim caso ocorra problemas semelhantes é possível corrigi-los mais rapidamente.
