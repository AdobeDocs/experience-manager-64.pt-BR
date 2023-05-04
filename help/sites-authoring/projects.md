---
title: Projetos
seo-title: Projects
description: Projetos permitem agrupar recursos em uma única entidade, cujo ambiente comum e compartilhado facilita o gerenciamento dos projetos
seo-description: Projects let you group resources into one entity whose common, shared environment makes it easy to manage your projects
uuid: c279fa04-05ef-4a4c-9295-2194879a6271
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: projects
content-type: reference
discoiquuid: 42b224e5-1256-44b6-9b46-4cd6de5927fb
exl-id: 70a70f56-1d33-4d8a-984a-a3e6f8deedeb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1410'
ht-degree: 33%

---

# Projetos{#projects}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Projetos permitem agrupar recursos em uma única entidade. Um ambiente comum e compartilhado facilita o gerenciamento dos projetos. Os tipos de recursos que você pode associar a um projeto são referidos em AEM como Mosaicos. Blocos podem incluir informações do projeto e da equipe, ativos, workflows e outros tipos de informações, conforme descrito detalhadamente em [Blocos de projeto.](#project-tiles)

>[!CAUTION]
>
>Para que os usuários em projetos vejam outros usuários/grupos ao usar a funcionalidade Projetos, como criar projetos, criar tarefas/fluxos de trabalho, ver e gerenciar a equipe, esses usuários precisam ter acesso de leitura no **/home/users** e **/home/groups**. A maneira mais fácil de implementar isso é dar **projects-users** acesso de leitura de grupo para **/home/users** e **/home/groups**.

Como usuário, você pode fazer o seguinte:

* Criar projetos
* Associar pastas de conteúdo e ativos a um projeto
* Excluir projetos
* Remover links de conteúdo do projeto

Consulte os seguintes tópicos adicionais:

* [Gerenciamento de projetos](/help/sites-authoring/touch-ui-managing-projects.md)
* [Trabalhar com tarefas](/help/sites-authoring/task-content.md)
* [Trabalhar com fluxos de trabalho de projeto](/help/sites-authoring/projects-with-workflows.md)
* [Integração do Creative Project e do PIM](/help/sites-authoring/managing-product-information.md)

## Console Projetos {#projects-console}

O console Projetos é onde você acessa e gerencia seus projetos no AEM.

![chlimage_1-169](assets/chlimage_1-169.png)

* Selecionar **Linha do tempo** e, em seguida, um projeto para visualizar sua linha do tempo.
* Clicar/tocar **Selecionar** para entrar no modo de seleção.
* Clique em **Criar** para adicionar projetos.
* **Alternar projetos ativos** permite alternar entre todos os projetos e apenas aqueles que estão ativos.
* **Exibir Exibição de Estatísticas** permite ver estatísticas do projeto relacionadas às conclusões da tarefa.

## Mosaicos do projeto {#project-tiles}

Com Projetos, você associa diferentes tipos de informações aos seus projetos. Eles são chamados de **Mosaicos**. Cada um dos blocos e que tipo de informação eles contêm são descritos nesta seção.

Você pode ter os seguintes blocos associados ao seu projeto. Cada uma é descrita nas seções a seguir:

* Ativos e coleções de ativos
* Experiências
* Links
* Informações do projeto
* Equipe
* Landing Pages
* Emails
* Fluxos de trabalhos
* Lançamentos
* Tarefas

### Ativos {#assets}

No **Ativos** bloco , é possível coletar todos os ativos usados para um projeto específico.

![chlimage_1-170](assets/chlimage_1-170.png)

Você faz upload de ativos diretamente no bloco. Além disso, é possível criar Conjuntos de imagens, Conjuntos de rotação ou Conjuntos de mídia mista, se você tiver o complemento Dynamic Media.

![chlimage_1-171](assets/chlimage_1-171.png)

### Coleções de ativos {#asset-collections}

Semelhante a ativos, você pode adicionar [coleções de ativos](/help/assets/managing-collections-touch-ui.md) diretamente ao seu projeto. Você define coleções em Ativos.

![chlimage_1-172](assets/chlimage_1-172.png)

Adicione uma coleção ao clicar em **Adicionar coleção** e selecionar a coleção apropriada na lista.

### Experiências {#experiences}

O **Experiências** bloco permite adicionar um aplicativo móvel, site ou publicação ao projeto.

![chlimage_1-173](assets/chlimage_1-173.png)

Os ícones indicam que tipo de experiência é representada: site, aplicativo móvel ou publicação. Adicione experiências ao clicar no sinal + ou em **Adicionar experiência** e selecionar o tipo de experiência.

![chlimage_1-174](assets/chlimage_1-174.png)

Selecione o caminho para as miniaturas e, se aplicável, altere a miniatura da experiência. As experiências são agrupadas no bloco **Experiências.**

### Links {#links}

O bloco Links permite associar links externos ao projeto.

![chlimage_1-175](assets/chlimage_1-175.png)

Você pode nomear o link com um nome fácil de reconhecer, além de alterar a miniatura.

![chlimage_1-176](assets/chlimage_1-176.png)

### Informações do projeto {#project-info}

O bloco Informações do projeto fornece informações gerais sobre o projeto, incluindo uma descrição, o status do projeto (inativo ou ativo), uma data de vencimento e membros. Além disso, é possível adicionar uma miniatura de projeto, exibida na página principal Projetos .

![chlimage_1-177](assets/chlimage_1-177.png)

Os membros da equipe podem ser atribuídos a esse bloco e excluídos dele (ou ter suas funções alteradas), bem como do bloco Equipe.

![chlimage_1-178](assets/chlimage_1-178.png)

### Tarefa de tradução {#translation-job}

O bloco Tarefa de tradução é onde você inicia uma tradução e também vê o status de suas traduções. Para configurar sua tradução, consulte [Criação de projetos de tradução](/help/assets/translation-projects.md).

![chlimage_1-179](assets/chlimage_1-179.png)

Clique nas reticências na parte inferior do cartão **Tarefa de tradução** para ver os ativos no fluxo de tarefa de tradução. A lista de tarefas de tradução também exibe entradas para metadados e tags de ativos. Essas entradas indicam que metadados e tags de ativos também são traduzidos.

![chlimage_1-180](assets/chlimage_1-180.png)

### Equipe {#team}

Neste bloco, você pode especificar os membros da equipe do projeto. Ao editar, você pode inserir o nome do membro da equipe e atribuir a função de usuário.

![chlimage_1-181](assets/chlimage_1-181.png)

É possível adicionar e excluir membros da equipe. Além disso, você pode editar a [função de usuário](#user-roles-in-a-project) atribuída ao membro da equipe.

![chlimage_1-182](assets/chlimage_1-182.png)

### Landing Pages {#landing-pages}

O **Aterrissagem** O bloco Páginas permite solicitar uma nova página de aterrissagem.

![chlimage_1-183](assets/chlimage_1-183.png)

Esse workflow é descrito em [Criar um fluxo de trabalho de página de aterrissagem](/help/sites-authoring/projects-with-workflows.md#request-landing-page-workflow).

### Emails {#emails}

O **Emails** ajuda você a gerenciar solicitações de email. Ele inicia o fluxo de trabalho Solicitar email .

![chlimage_1-184](assets/chlimage_1-184.png)

Mais informações estão descritas na seção [Fluxo de trabalho Solicitar email .](/help/sites-authoring/projects-with-workflows.md#request-email-workflow)

### Fluxos de trabalhos {#workflows}

Você pode atribuir seu projeto para seguir determinados fluxos de trabalho. Se algum workflow estiver em execução, seu status será exibido na variável **Fluxos de trabalho** em Projetos.

![chlimage_1-185](assets/chlimage_1-185.png)

Você pode atribuir seu projeto para seguir determinados fluxos de trabalho. Dependendo do projeto escolhido, você tem fluxos de trabalho diferentes disponíveis.

Estes são descritos em [Trabalhar com fluxos de trabalho de projeto.](/help/sites-authoring/projects-with-workflows.md)

### Lançamentos {#launches}

O bloco Lançamentos mostra todas as inicializações que foram solicitadas com um [Fluxo de trabalho Solicitar lançamento .](/help/sites-authoring/projects-with-workflows.md)

![chlimage_1-186](assets/chlimage_1-186.png)

### Tarefas {#tasks}

As tarefas permitem monitorar o status de qualquer tarefa relacionada ao projeto, incluindo fluxos de trabalho. As tarefas são abordadas em detalhes em [Trabalhar com tarefas](/help/sites-authoring/task-content.md).

![chlimage_1-187](assets/chlimage_1-187.png)

## Modelos de projeto {#project-templates}

O AEM acompanha três modelos diferentes prontos para uso:

* Um projeto simples - Uma amostra de referência para qualquer projeto que não se encaixe em outras categorias (uma categoria genérica). Ele inclui três funções básicas (Proprietários, Editores e Observadores) e quatro fluxos de trabalho (Aprovação de projeto, Solicitar lançamento, Solicitar página de aterrissagem e Solicitar email).
* Um projeto de mídia - Um projeto de amostra de referência para atividades de mídia. Ele inclui várias funções de projeto relacionadas a mídia (Fotógrafos, Editores, Redatores, Designers, Proprietários e Observadores). Também inclui dois fluxos de trabalho relacionados ao conteúdo de mídia - Solicitar cópia (para solicitar e revisar texto) e Sessão fotográfica do produto (para gerenciar fotos relacionadas ao produto)
* [Projeto de sessão fotográfica do produto](/help/sites-authoring/managing-product-information.md) - Uma amostra de referência para o gerenciamento de fotografias de produtos relacionados ao comércio eletrônico. Ele inclui funções para Fotógrafos, Editores, Retocadores de fotos, Proprietários, Diretores criativos, Profissionais de marketing de redes sociais, Gerentes de marketing, Revisores e Observadores.
* [Um projeto de tradução](/help/sites-administering/translation.md) - Uma amostra de referência para o gerenciamento de atividades relacionadas a tradução. Ele inclui três funções básicas (Proprietários, Editores e Observadores). Também inclui dois fluxos de trabalho que são acessados na interface de usuário de Fluxos de trabalho.

Com base no modelo selecionado, você tem opções diferentes disponíveis, principalmente em torno de funções de usuário e fluxos de trabalho.

## Funções de usuário em um projeto {#user-roles-in-a-project}

As diferentes funções de usuário são definidas em um modelo de Projeto e são usadas por dois motivos principais:

1. Permissões. As funções de usuário se encaixam em uma das três categorias listadas: Observador, Editor, Proprietário. Por exemplo, um Fotógrafo ou Redator terá os mesmos privilégios de um Editor. As permissões determinam o que um usuário pode fazer com o conteúdo em um projeto.
1. Fluxos de trabalhos. Os fluxos de trabalho determinam quem recebe tarefas em um projeto. As tarefas podem ser associadas a uma função de projeto. Por exemplo, uma tarefa pode ser atribuída a Fotógrafos para que todos os membros da equipe que tenham a função Fotógrafo recebam a tarefa.

Todos os projetos oferecem suporte às seguintes funções padrão para permitir que você administre permissões de segurança e controle:

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Função</strong></p> </td> 
   <td><p><strong>Descrição</strong></p> </td> 
   <td><p><strong>Permissões</strong></p> </td> 
   <td><p><strong>Associação de Grupo</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Observador</p> </td> 
   <td><p>Um usuário nessa função pode exibir detalhes do projeto, incluindo o status do projeto.</p> </td> 
   <td><p>Permissões somente leitura em um projeto</p> </td> 
   <td><p>grupo de usuários do fluxo de trabalho</p> </td> 
  </tr> 
  <tr> 
   <td><p>Editor</p> </td> 
   <td><p>Um usuário nessa função pode fazer upload e editar o conteúdo de um projeto.</p> <p> </p> </td> 
   <td> 
    <ul> 
     <li>Acesso de leitura e gravação em um projeto, metadados associados e ativos relacionados.</li> 
     <li>Privilégios para fazer upload de uma lista de capturas, sessão de fotos e revisar e aprovar ativos</li> 
     <li>Permissão de gravação em /etc/commerce</li> 
     <li>Ter permissão de modificação em um projeto específico</li> 
    </ul> </td> 
   <td><p>grupo de usuários do fluxo de trabalho</p> </td> 
  </tr> 
  <tr> 
   <td><p>Proprietário</p> </td> 
   <td><p>Um usuário nessa função pode iniciar um projeto. Um proprietário pode criar um projeto, iniciar o trabalho em um projeto e também mover ativos aprovados para a pasta Produção. Além disso, todas as outras tarefas no projeto também podem ser visualizadas e executadas pelo proprietário.</p> </td> 
   <td> 
    <ul> 
     <li>Permissão de gravação em /etc/commerce</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Grupo de usuários do DAM (para criar um projeto)</li> 
     <li>grupo project-administrators (para poder mover ativos)</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

Para projetos criativos, também são fornecidas funções adicionais - por exemplo, fotógrafos. Você pode usar essas funções para derivar funções personalizadas para um projeto específico.

>[!NOTE]
>
>Ao criar o projeto e adicionar usuários às várias funções, os grupos associados ao projeto são criados automaticamente para gerenciar as permissões associadas. Por exemplo, um projeto chamado Myproject teria três grupos: **Proprietários do Myproject**, **Editores do Myproject**, **Observadores do Myproject**. No entanto, se o projeto for excluído, esses grupos não serão excluídos automaticamente. Um administrador precisa excluir manualmente os grupos em **Ferramentas** > **Segurança** > **Grupos**.
