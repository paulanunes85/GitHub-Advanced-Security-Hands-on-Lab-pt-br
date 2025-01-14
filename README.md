<h1 align="center">GitHub Advanced Security Laboratório Hands-On</h1>
<h5 align="center">Revisão para Português Brasil @paulanunes85 - 2025</h5>

# Sobre
Este repositório contém uma versão simples do aplicativo 'Reading Time' em .NET 6 (apenas projetos web e de teste unitário). Ele está configurado para ser usado como o 'aplicativo de exemplo' para o laboratório prático do GitHub Advanced Security na Build 2024.

## O que é GitHub Advanced Security?

O GitHub Advanced Security (GHAS) é uma solução de teste de segurança de aplicativos voltada para desenvolvedores, que traz as capacidades de segurança de classe mundial do GitHub para repositórios públicos e privados. A maioria dos recursos do GitHub Advanced Security são gratuitos para repositórios públicos, mas requerem uma licença para repositórios privados. Com apenas alguns cliques, você pode começar a usar. Desde o início, você se beneficiará de capacidades de detecção e remediação altamente curadas, criadas por alguns dos melhores engenheiros de segurança do mundo, para garantir que seu código e cadeia de suprimentos de software sejam o mais seguros possível. É totalmente automatizado, então, uma vez habilitado, você não precisa se lembrar de executar testes do GHAS ou esperar por uma revisão de segurança antes de fazer o merge.

## Instruções do Laboratório

- Você encontrará as instruções do laboratório na pasta do laboratório. [lab folder](./lab/build2024-ghas-hol.md)

## Pré-requisitos

- **Pré-requisitos:** Para usar o GitHub Copilot, você deve ter uma assinatura ativa do GitHub Copilot Business ou Enterprise. Inscreva-se para Copilot Free para VS Code apenas para fim de treinamento [Copilot for free para VS Code](https://learn.microsoft.com/en-us/visualstudio/ide/copilot-free-plan?view=vs-2022).
- **Já possuir acesso ou Habilitar GitHub Advanced Security:** [Habilitando a segurança avançada do GitHub](https://resources.github.com/pt-br/learn/pathways/security/essentials/enabling-github-advanced-security/)
- **Ter acesso a uma organização GitHub com licença do GitHub Advanced Security**
- **Conhecimento de GitHub Actions e Workflows:** É importante ter um entendimento básico de GitHub Actions e workflows para aproveitar ao máximo o laboratório

## IA Responsável

A Microsoft está comprometida em ajudar nossos clientes a usar nossos produtos de IA de forma responsável, compartilhando nossos aprendizados e construindo parcerias baseadas em confiança por meio de ferramentas como Notas de Transparência e Avaliações de Impacto. Muitos desses recursos podem ser encontrados em https://aka.ms/RAI. A abordagem da Microsoft para IA responsável é baseada em nossos princípios de IA de justiça, confiabilidade e segurança, privacidade e segurança, inclusão, transparência e responsabilidade.

Modelos de linguagem natural, imagem e fala em larga escala - como os usados neste exemplo - podem potencialmente se comportar de maneiras injustas, não confiáveis ou ofensivas, causando danos. Consulte a [nota de transparência do serviço Azure OpenAI](https://learn.microsoft.com/legal/cognitive-services/openai/transparency-note?tabs=text) para se informar sobre riscos e limitações.

A abordagem recomendada para mitigar esses riscos é incluir um sistema de segurança em sua arquitetura que possa detectar e prevenir comportamentos prejudiciais. O [Azure AI Content Safety](https://learn.microsoft.com/azure/ai-services/content-safety/overview) fornece uma camada independente de proteção, capaz de detectar conteúdo prejudicial gerado por usuários e IA em aplicativos e serviços. O Azure AI Content Safety inclui APIs de texto e imagem que permitem detectar material prejudicial. Também temos um Content Safety Studio interativo que permite visualizar, explorar e testar códigos de exemplo para detectar conteúdo prejudicial em diferentes modalidades. A seguinte [documentação de início rápido](https://learn.microsoft.com/azure/ai-services/content-safety/quickstart-text?tabs=visual-studio%2Clinux&pivots=programming-language-rest) orienta você a fazer solicitações ao serviço.

Outro aspecto a ser considerado é o desempenho geral do aplicativo. Com aplicativos multimodais e multimodelos, consideramos desempenho como o sistema funcionando conforme você e seus usuários esperam, incluindo não gerar saídas prejudiciais. É importante avaliar o desempenho do seu aplicativo geral usando [avaliadores de Desempenho e Qualidade e de Risco e Segurança.](https://learn.microsoft.com/en-us/azure/ai-studio/concepts/evaluation-metrics-built-in?tabs=warning) Você também tem a capacidade de criar e avaliar com [avaliadores personalizados.](https://learn.microsoft.com/en-us/azure/ai-studio/how-to/develop/evaluate-sdk#custom-evaluators)

Você pode avaliar seu aplicativo de IA em seu ambiente de desenvolvimento usando o [SDK de Avaliação do Azure AI.](https://microsoft.github.io/promptflow/index.html) Dado um conjunto de dados de teste ou um alvo, as gerações do seu aplicativo de IA generativa são medidas quantitativamente com avaliadores integrados ou avaliadores personalizados de sua escolha. Para começar a usar o SDK de fluxo de prompt para avaliar seu sistema, você pode seguir o [guia de início rápido.](https://learn.microsoft.com/azure/ai-studio/how-to/develop/flow-evaluate-sdk) Depois de executar uma execução de avaliação, você pode [visualizar os resultados no Azure AI Studio.](https://learn.microsoft.com/azure/ai-studio/how-to/evaluate-flow-results)

## Avisos Legais
 
A Microsoft e quaisquer colaboradores concedem a você uma licença para a documentação da Microsoft e outros conteúdos neste repositório sob a [Creative Commons Attribution 4.0 International Public License](https://creativecommons.org/licenses/by/4.0/legalcode),
veja [LICENSE](LICENSE) e concedem a você uma licença para qualquer código no repositório sob a  [MIT License](https://opensource.org/licenses/MIT), consulte
[LICENSE-CODE](LICENSE-CODE)
 
Microsoft, Windows, Microsoft Azure e/ou outros produtos e serviços da Microsoft referenciados na documentação podem ser marcas registradas ou marcas registradas da Microsoft nos Estados Unidos e/ou em outros países. As licenças para este projeto não concedem a você direitos de uso de quaisquer nomes, logotipos ou marcas registradas da Microsoft. As diretrizes gerais de marcas registradas da Microsoft podem ser encontradas em http://go.microsoft.com/fwlink/?LinkID=254653.
 
As informações de privacidade podem ser encontradas em https://privacy.microsoft.com/en-us/
 
A Microsoft e quaisquer colaboradores reservam todos os outros direitos, sejam sob seus respectivos direitos autorais, patentes, ou marcas registradas, seja por implicação, estoppel ou de outra forma.
