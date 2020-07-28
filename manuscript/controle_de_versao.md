# Sistemas de Controle de versão (Francílio Araújo)

## Introdução

O código fonte de qualquer software é sujeito a mudanças contínuas. Novas funcionalidades, correções de bugs e manutenções podem causar adição, remoção e alteração de linhas de código e adição e remoção de arquivos da base. Sistemas de controle de versão são ferramentas criadas para melhor gerenciar estas mudanças em uma base de código.

Espera-se, em geral, que um sistema de controle de versão (SCV) seja capaz de:
1. Manter um log de modificações realizadas na base;
2. Manter um log dos autores destas modificações;
3. Mover-se livremente no histórico de modificações;
4. Desfazer facilmente modificações recentes;
5. Permitir que várias pessoas possam trabalhar na mesma base;
6. Facilitar a integração do trabalho de diversas pessoas trabalhando no código.

Vários softwares com estas características foram lançados durante os anos, como CVS, Subversion, Mercurial, Bazaar e Git. Nos últimos anos o Git tem se tornado praticamente o padrão de SCV no desenvolvimento.

## Papel do SCV no deploy

São acordados, explicita ou implicitamente, os comportamentos que o software deve desempenhar no ambiente de produção. Modificações na base de código pressupõem que há uma versão em que estes comportamentos ainda não existem e que eles serão adicionados em uma versão posterior. Deste modo faz-se necessário saber em quais versões estes comportamentos estão presentes para que o deploy do software seja satisfatório.

Não apenas o código fonte goza os benefícios de um SCV. Configuração também pode ser versionada, facilitando o retorno a uma configuração que já se sabia funcionar.

É necessário conhecer bem a sua ferramenta de SCV para tirar o maior proveito da mesma. A maioria destas ferramentas foi desenvolvida para trabalhar com arquivos de texto. Pode parecer razoável usar o git para gerenciar binários, como bibliotecas, mas isto pode resultar em repositórios inchados e que demoram demais para clonar.

O repositório deve conter o máximo de recursos para o build do software. Quanto menos conhecimento houver fora do repositório, mais fácil é realizar o build em ambientes diferentes. Esta regra nunca estará acima do fator segurança. Informações sensíveis devem ficar fora do código, e por consequência fora dos repositórios de código.

## Um mesmo código, diversos ambientes

Como dito anteriormente, espera-se que um SCV possibilite com que múltiplas pessoas trabalhem na mesma base de código ao mesmo tempo. Vários desenvolvedores podem estar desenvolvendo coisas diferentes no código e ao mesmo tempo ser necessário disponibilizar uma versão para teste. A maioria dos SCV possuem suporte a branches.

No git as modificações são gravadas em commits e estes podem referenciar um commit anterior formando uma sequência histórica de modificações. Acontece que é possível criar uma sequência histórica paralela, criando assim uma ramificação na história do projeto. A estas ramificações é dado o nome de branch. Cada pessoa pode trabalhar em uma branch sem interferir no trabalho dos outros.

No contexto de deploy, pode-se usar um branch específico para deploys em ambientes de teste ou stagging e um branch para dploys em ambiente de produção. Os desenvolvedores podem trabalhar em branches separados dependendo da atividade que estiverem desempenhando. Esta liberdade dá origem a diversos modos de trabalho, gerenciando não apenas a organização humana, mas a organização de branches no repositório e até gerenciamento do deploy.

## Conclusão

## Leitura Complementar

- [A Visual Guide to Version Control](https://betterexplained.com/articles/a-visual-guide-to-version-control/)
- [Continuous Integration - Maintain a Single Source Repository](https://martinfowler.com/articles/continuousIntegration.html#MaintainASingleSourceRepository.)
- [Pro Git 2nd Edition - 3. Git Branching](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)
- [Branching Patterns](https://martinfowler.com/articles/branching-patterns.html)
- [Comparando fluxos de trabalho](https://www.atlassian.com/br/git/tutorials/comparing-workflows)
