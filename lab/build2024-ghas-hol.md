# Laboratório Prático de Segurança Avançada do GitHub
O GitHub Advanced Security (GHAS) é uma solução de teste de segurança de aplicativos voltada para desenvolvedores que traz as capacidades de segurança de classe mundial do GitHub para repositórios públicos e privados. A maioria dos recursos do GitHub Advanced Security são gratuitos para repositórios públicos, mas exigem uma licença do GitHub Advanced Security para repositórios privados. São necessários apenas alguns cliques para começar. Logo de cara, você se beneficiará de capacidades de detecção e remediação altamente curadas, criadas por alguns dos melhores engenheiros de segurança do mundo para garantir que seu código e cadeia de suprimentos de software sejam o mais seguros possível. É totalmente automatizado, então, uma vez habilitado, você não precisa se lembrar de executar testes do GHAS ou esperar por uma revisão de segurança antes de fazer o merge.

Neste laboratório, você usará o GHAS como um único desenvolvedor aproveitando essas ferramentas de nível profissional que estão disponíveis gratuitamente para qualquer pessoa que use o GitHub.com ao trabalhar em seu código em público. Além disso, você usará o GitHub Codespaces como seu IDE de desenvolvimento na nuvem, então você só precisará de um navegador web moderno.

## Pré-requisitos
Para completar este laboratório, você só precisa de uma conta válida no GitHub.com e um navegador web moderno (navegadores baseados em Chromium, como Microsoft Edge ou Google Chrome, são [preferidos para acessar o GitHub Codespaces](https://docs.github.com/en/codespaces/troubleshooting/troubleshooting-github-codespaces-clients#troubleshooting-the-visual-studio-code-web-client)).

## Exercício 1
Para começar, você obterá o código de exemplo e "[fará um fork](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo)" em um novo repositório em sua conta pessoal no GitHub.com.

1. Navegue até [https://github.com](https://github.com) e faça login em sua conta pessoal.
   
2. Depois de se autenticar, navegue até [https://gh.io/build-2024-ghas-lab](https://gh.io/build-2024-ghas-lab).

3. No canto superior direito do repositório, clique no botão **Fork**.

4. Na página **Create a new fork**, verifique se você está fazendo o fork para sua *conta pessoal*--você será o Proprietário.
   
5. Remova a marca de **Copy the **`main`** branch only**.
   
6. Aceite o restante dos padrões e clique em **Create fork**.

Agora você tem uma cópia do código de exemplo e pode continuar configurando o GitHub Advanced Security (GHAS).

## Exercício 2
Agora, você configurará o GHAS em seu repositório recém-forkado.

1. Em sua cópia forkada do repositório de exemplo, clique no botão **Settings**.

2. No menu à esquerda, selecione **Code security and analysis** na seção *Security*.
   
   > Você começará com o *Dependabot*.

3. Primeiro, você precisa habilitar o **Dependency graph** clicando no botão **Enable**.
   
    > Ao clicar no botão **Enable**, você verá uma mensagem de Configurações do repositório salvas no topo da página de Configurações.

4. Clique em **Enable** ao lado dos três itens a seguir:
   1. Dependabot alerts
   2. Dependabot security updates
   3. Dependabot version updates
       
5. Clique no botão **<> Code** do repositório.

Com apenas alguns cliques, você ativou alguns recursos do GHAS. Avance para o próximo exercício para ver os resultados.

## Exercício 3
Você examinará os resultados de habilitar o Dependabot e tentará algumas coisas rápidas para tornar seu código mais seguro usando o GitHub Codespaces.

1. Na página inicial do **seu** repositório, clique no botão verde **<> Code**.

2. Selecione a aba **Codespaces**.

3. Clique em **Create codespace on main**.

4. Aguarde o início do seu codespace. Isso pode levar um ou dois minutos.

   > Examine a experiência do usuário (Visual Studio Code) **sem clicar na interface**. Na janela do Terminal, no meio da tela, você verá mensagens enquanto seu codespace termina de iniciar.

5. Examine a aba *Get Started* e/ou a aba README se elas abrirem, e feche-as quando estiver pronto.

6. Uma vez que o codespace estiver pronto, você poderá emitir comandos no prompt do terminal. O prompt do terminal será algo como **/workspaces/your-repo-name (main)**.

7. No prompt do Terminal, digite **cd src/** e pressione Enter.

8. Em seguida, digite **dotnet build** e pressione Enter. Isso deve compilar o aplicativo com sucesso. Você notou algo interessante?

9. No prompt do Terminal, digite **cd ReadingTime6.Web.Tests.Unit/** e pressione Enter.

10. Digite **dotnet test** e pressione Enter.

11. Você deve ver **13** testes passarem.

13. No Terminal, digite o seguinte comando para adicionar um pacote NuGet com uma vulnerabilidade conhecida (isso é uma linha longa de código):
   
    ``` bash
    dotnet add package Swashbuckle.AspNetCore.SwaggerUI --version 6.2.3
    ```

14. Isso deve adicionar uma nova linha ao arquivo `ReadingTime6.Web.Tests.Unit.csproj` com o pacote NuGet.

15. Na *Barra de Atividades*, clique em **Source Control**.

16. Crie uma mensagem de commit.

17. Faça o commit de suas alterações e depois faça o push de volta para o GitHub.com.

18. Retorne ao seu repositório e deixe seu codespace em execução.

19. Clique na aba **Security**, que deve ter um número **1** ao lado.

20. Clique no link **Dependabot**. Você verá que há um alerta relacionado ao novo pacote que você acabou de adicionar.

21. Clique no alerta **Server side request forgery in SwaggerUI** e examine os detalhes.
    
Você deixará isso como está por um tempo. O Dependabot sugerirá uma correção e você voltará a isso; por enquanto, continue.

## Exercício 4
Agora você vai experimentar o [Push Protection](https://docs.github.com/en/enterprise-cloud@latest/code-security/secret-scanning/push-protection-for-repositories-and-organizations). Esse recurso é ativado *automaticamente* para repositórios públicos no GitHub.com.

1. Crie um simples [Token de Acesso Pessoal do GitHub (PAT)](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) para que você tenha um segredo que tentará "push".
    1. Clique na **foto do seu perfil** no canto superior direito.

    2. Clique em **Settings**.

    3. Role até o final do menu à esquerda e navegue até **<> Developer Settings**.

    4. Clique em **Personal Access Tokens** e depois escolha **Tokens (classic)**.

    5. Clique em **Generate new token** e depois em **Generate new token (classic)**.

    6. Dê um nome ao token no campo **note**.

    7. Altere a expiração para **7 dias** e selecione o **escopo** do PAT algo relativamente inofensivo, como `repo:invite`. 

    8. Clique em **Generate Token**.

2. Copie o valor do PAT e salve-o em um arquivo de texto.

3. Quando estiver pronto, retorne ao seu codespace.

4. Execute um **pull** para garantir que você tenha o código mais recente.

5. Acesse o Explorer no seu codespace e abra o arquivo **Startup.cs** na pasta **src/ReadingTime6.Web**.

   1. Adicione o seguinte código:
   
   ``` cs
   var pat = "{coloque seu pat aqui}";
   ```

   2. ... como a última linha no construtor ...
   
   ``` cs
   public Startup(IConfiguration configuration)
   {
        Configuration = configuration;
   }
   ```

6. Salve e faça o commit da sua alteração no codespace.

7. Agora tente fazer o push.
   
   > Deve falhar com um aviso.

8. Clique em **Open Git Log**.

9. Na janela de log, encontre a URL para *aprender mais*. Siga a URL e examine a página de documentação e faça uma revisão rápida. Quando estiver pronto, retorne ao seu codespace.
    
    > **ALERTA**: para os próximos passos, preste muita atenção e leia atentamente para a melhor experiência no laboratório.

    De volta à saída, você verá uma mensagem (veja abaixo) com uma URL que você pode clicar:

    ```
    (?) Para fazer o push, remova o segredo do commit ou siga esta URL para permitir o segredo.   
    ```

10. Clique na URL e veja os detalhes. Você verá que há opções que você pode escolher para "resolver" o problema.
    
    > **Não escolha nenhuma das opções**.

11. Em vez disso, no Terminal do seu codespace, digite o seguinte:
    
    ``` bash
    git reset HEAD~1
    ```

12. Agora desfaça a alteração local. 
    
    > Você limpou as coisas. Se quiser ser realmente organizado, vá e exclua seu PAT.

13. Retorne ao seu repositório e deixe seu codespace em execução.

14. No repositório, na aba **Pull Requests**, você deve ver um *Pull Request do Dependabot*. Como mencionado anteriormente, o Dependabot encontrou uma biblioteca vulnerável e sugeriu uma correção.

15. Faça o merge do pull request. Normalmente, você executaria suas extensas suítes de testes unitários e de integração, mas para este laboratório você confiará no Dependabot.

16. Agora, acesse a aba Security e depois Dependabot e observe que você não tem problemas abertos.

Neste ponto, você usou três ótimos recursos do GHAS: Dependabot, Secret Scanning e Push Protection. Avance para o próximo exercício para usar mais recursos!

## Exercício 5
Neste exercício, você habilitará o CodeQL em seu repositório para realizar a análise de código.

1.	No seu repositório, selecione a aba **Settings**

2.	No menu à esquerda, selecione **Code security and analysis**

3. Para a opção **Code scanning**, clique no botão **Set up**.

4. Escolha a opção **Default**.

5. Na caixa de diálogo que aparece, revise as configurações e escolha **Enable CodeQL**.

    > Levará alguns minutos para o GitHub configurar a análise do CodeQL. Isso é feito via um workflow do GitHub Actions.

6.  Clique na aba **Actions**. Você deve ver um workflow **CodeQL Setup** em execução.

7.  Você pode clicar no workflow em execução para ver o status do trabalho e revisar os detalhes.

Agora você pode seguir para verificar os resultados.

## Exercício 6
Neste exercício, você examinará os resultados da análise de código.

1. Clique no botão **Security** na barra de ferramentas.

2. No menu em *Overview*, você verá um item **Code scanning**, clique nele. Haverá uma lista de resultados, com os alertas mais críticos no topo.

    > Você pode filtrar esses resultados por Pacote, Ecossistema, Manifesto ou Severidade, e classificar por prioridade, data, severidade e mais. Você pode criar diferentes visualizações e marcar os URLs para voltar a eles.

3. Você deve ver que o CodeQL encontrou **oito** vulnerabilidades. Haverá uma para C# (adicionada de propósito para o laboratório), e o restante são relacionadas a JavaScript. Você notará que quatro das oito são de alta severidade.
   
4. Examine os vários erros.
   
   > A remediação do C# será a mais fácil porque está no 'nosso' código. As outras tornam a remediação um pouco mais complexa porque precisamos de atualizações dos provedores de bibliotecas.
   
Você acabou de executar uma varredura do CodeQL usando as consultas padrão que identificaram vulnerabilidades no código do aplicativo, bem como nas bibliotecas usadas por ele.

## Exercício 7
Neste último exercício, você corrigirá o maior número possível de erros detectados pelo CodeQL.

1. Clique no botão **<> Code**.

2. Clique no menu suspenso **Switch branches** e selecione a branch **fix/ghas-found-issues**.

3. Se você clicar no link **Commits**, verá três commits que parecem corrigir os problemas de segurança.

4. Clique no botão **Pull Requests**.

5. Clique no botão verde **New pull request**.
   
    > Como você está usando um repositório forkado, o processo padrão de PR é fazer o merge de volta para o repositório de origem. Você não vai fazer isso. Você vai criar um PR usando a branch de correção local fornecida.

6. Altere o *repositório base* para **{seu usuário}/build2024ghas**. Isso mudará um pouco a interface.

7. Altere a branch *compare* para **fix/ghas-found-issues**

8. Clique no botão verde **Create pull request**.

9. Forneça uma descrição e clique no botão verde **Create pull request**.
    
    > Você verá que não deve haver conflitos, no entanto, o CodeQL está verificando o PR para ver se ele introduz algum problema.

10. Aguarde a conclusão das verificações do CodeQL. Você deve ver que nenhum novo alerta foi introduzido.

11. Faça o merge do pull request.

12. Clique na aba **Actions**. Você deve ver um workflow **CodeQL Setup** em execução.

13. Você pode clicar no workflow em execução para ver o status do trabalho e revisar os detalhes. Isso foi executado automaticamente devido à configuração do CodeQL que você fez anteriormente. Aguarde a conclusão do trabalho.

14. Clique no botão **Security** na barra de ferramentas.

15. Revise quais problemas restam. Você e o GitHub precisam trabalhar com a comunidade OSS para ajudar a relatar e, se possível, corrigir erros à medida que são encontrados.

O GitHub Advanced Security irá expor vulnerabilidades existentes e sinalizar possíveis novos problemas antes que eles sejam mesclados em seu código. Manter suas aplicações seguras é uma jornada, não um destino. Ferramentas como o GHAS são uma enorme ajuda. Mas você é o principal contribuinte para o sucesso da sua equipe e organização na construção de soluções seguras.

Obrigado por dedicar seu tempo para realizar este laboratório.
