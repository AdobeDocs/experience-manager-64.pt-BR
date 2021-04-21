---
title: Novidades AEM Comunidades 6.4
description: A AEM Communities oferece uma estrutura para as empresas colaborarem entre seus parceiros, clientes e funcionários.
uuid: e4bf343c-59cd-48ac-bee4-85db109e4c65
contentOwner: mgulati
discoiquuid: 3e3c867f-afb0-4402-94f4-16e1a556ddee
exl-id: fcdc65c9-929d-4a87-8ff7-5e3cf5711fd9
translation-type: tm+mt
source-git-commit: 1a7ecec2f3c2618bb6d0280a8f9a66754cd8a1a3
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 0%

---

# Novidades das Comunidades AEM 6.4 {#what-s-new-in-aem-communities}

A AEM Communities oferece uma estrutura para as empresas colaborarem entre seus parceiros, clientes e funcionários. Ele confere recursos sociais à estrutura do site e ajuda as empresas a engajarem e fornecerem conhecimento aos participantes, para aprimorar o valor da marca no seu caminho.

AEM 6.4 Comunidades traz funcionalidades para aprimorar as experiências dos usuários da comunidade e facilitar as tarefas atuais de administradores, moderadores e gerentes da comunidade.

Leia mais para uma rápida introdução a novos recursos e melhorias. Além disso, consulte AEM 6.4 Comunidades [notas de versão](../release-notes/communities-release-notes.md). Para obter AEM documentação do Communities 6.4, visite [AEM 6.4 Communities User Guide](home.md).

## Gerenciando subcomunidades ou grupos da comunidade {#managing-sub-communities-or-community-groups}

O AEM Communities permite que os administradores da comunidade criem grupos e subgrupos no site de comunidades, usando modelos predefinidos, no ambiente de criação. Esses grupos servem como subcomunidades, o que pode herdar muitas configurações, como temas e estilo do site pai. No entanto, esses grupos podem diferir do site pai, por exemplo, ter um conjunto diferente de moderadores de grupo ou pode variar no nível de segurança. Esses grupos funcionam como miniccomunidades independentes e de pleno direito, que são ainda mais capacitadas pelas melhorias a seguir.

### Criar grupos de várias localidades em uma única etapa {#create-multi-locale-groups-in-single-step}

Como parte de um site da comunidade, grupos multilíngues podem ser criados em uma única operação. **[!UICONTROL O campo Idioma(s) do grupo da comunidade disponível adicional]** na página  **[!UICONTROL Modelo do grupo da]** comunidade, que está disponível ao criar um  [novo grupo da comunidade ](groups.md) em um site da comunidade, torna isso viável.

![multilingualgroup-1](assets/multilingualgroup-1.png)

Para criar esses grupos, os usuários podem simplesmente navegar até a Coleção de grupos do site de comunidades desejado no console Sites . Crie um grupo e especifique os idiomas desejados no campo **[!UICONTROL Idioma(s) adicional(ais) do grupo da comunidade disponível]** da página **[!UICONTROL Modelo de grupo da comunidade]**.

### Excluir grupos da comunidade do console de grupos {#delete-community-groups-from-groups-console}

AEM Comunidades 6.4 fornece o ícone Excluir grupo nos grupos da comunidade existentes, na coleção Grupos da comunidade no console Sites da comunidade. Isso habilita a [exclusão de grupo](groups.md#deleting-the-group) em um clique, juntamente com a exclusão de todos os itens associados (como conteúdo e associações de usuário) ao grupo.

![deletegrp](assets/deletegrp.png)

### Criar e atribuir recursos de ativação em grupos {#create-and-assign-enablement-resources-within-groups}

O conteúdo de aprendizado agora pode ser criado, gerenciado e publicado para um conjunto específico de membros da comunidade direcionados. Devido à disponibilidade de funções de catálogo e atribuição para grupos da comunidade (e não apenas para todo o site da comunidade), os gerentes de ativação podem [atribuir recursos de ativação](resource.md) e caminho de aprendizagem a um pequeno conjunto de pessoas também.

![catálogo de atribuições](assets/assignmentcatalog.png)

## Moderação do conteúdo gerado pelo usuário {#moderating-user-generated-content}

AEM 6.4 Comunidades oferecem poucas melhorias em relação à moderação, o que é fundamental para facilitar o dia a dia dos moderadores comunitários.

### Detecção automática de spam {#automatic-spam-detection}

O novo mecanismo de detecção de spam ajuda a filtrar o conteúdo indesejado e não solicitado gerado pelo usuário em sites ou grupos da comunidade. Quando ativada, essa funcionalidade pode marcar uma parte do conteúdo gerado pelo usuário como Spam ou Not Spam com base em um conjunto predefinido de palavras de spam. Os moderadores podem agir com base no conteúdo para negar ou permitir que ele apareça na instância de publicação. Essas ações de moderação podem ser executadas em linha ou por meio do console de moderação em massa.

![spamdetect-1](assets/spamdetection-1.png)

[O ](moderate-ugc.md#spam-detection) Detector de spam encontra e sinaliza uma determinada parte do conteúdo gerado pelo usuário com 90% de precisão. No entanto, essa funcionalidade não é ativada por padrão. Para habilitá-lo, os administradores da comunidade precisam navegar até configMgr no sistema/console e adicionar Processo de spam.

![spamprocess-1](assets/spamprocess-1.png)

### Novos filtros (respondidos/não atendidos) para QnA {#new-answered-unanswered-filters-for-qna}

O AEM 6.4 adiciona dois [novos filtros](moderation.md#filter-rail), chamados Respondidos e Não respondidos para perguntas de QnA, ao console de moderação em massa. Esses filtros estão disponíveis em Status no Filtro do trilho.

![status](assets/statuses.png)

Ao selecionar o status Respondido, todas as perguntas respondidas ficam visíveis para o moderador na área de conteúdo. Enquanto que, se apenas o status Não respondido for selecionado, o moderador visualizará todo o conteúdo (para todos os tipos de conteúdo) exceto as perguntas respondidas, pois a propriedade responsável pela Pergunta respondida não existe no caso de perguntas não respondidas e outro conteúdo, como tópico do fórum, artigo do blog ou comentários.

### Filtros de moderação de marcador {#bookmark-moderation-filters}

O AEM Communities fornece a capacidade de [marcar os filtros de moderação predefinidos](moderation.md#filter-rail) no console de moderação. Esses marcadores salvos podem ser revisitados posteriormente e compartilhados com outros usuários.

Os usuários precisam apenas selecionar os filtros desejados no Filtro do painel de moderação, para visualizar o UGC filtrado e marcar os filtros em seus navegadores. Esses filtros são anexados ao final da cadeia de caracteres do URL e, portanto, podem ser compartilhados, reutilizados e revisitados posteriormente.

## Gerenciando sites da comunidade {#managing-community-sites}

As Comunidades AEM 6.4 oferecem melhorias no gerenciamento de sites, o que garante que vários sites da comunidade em diferentes idiomas sejam facilmente criados, gerenciados e excluídos pelos administradores do site.

### Criar sites de comunidade com várias localidades em uma etapa {#create-multi-locale-community-sites-in-one-step}

O AEM Communities permite criar [sites de comunidade multilíngues](create-site.md) em uma única operação. Isso é possível devido à disponibilidade de vários idiomas para selecionar no campo **[!UICONTROL Community Site Base Language]** na página **[!UICONTROL Site Template]**, enquanto cria um novo site da comunidade a partir do console de sites.

![multilocalesite](assets/multilocalesite.png)

Os usuários podem selecionar pastas de configuração, marcas e muitas outras configurações ao mesmo tempo para todos esses sites.

### Excluir sites da comunidade do console de sites {#delete-community-sites-from-sites-console}

AEM Comunidades 6.4 fornece o ícone Excluir site nos sites existentes da comunidade, no console Sites da comunidade. Isso permite a [exclusão do site](create-site.md) e os itens associados em um clique.

![siteactions](assets/siteactions.png)

## Gerenciamento de perfis de usuário e UGC {#managing-ugc-and-user-profiles}

Mantendo a proteção de dados do usuário no centro da experiência das comunidades, o AEM Communities expõe [APIs prontas para uso](user-ugc-management-service.md) e [servlet de amostra](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet). Essas APIs ajudam a gerenciar em massa (exclusão em massa e exportação em massa) o conteúdo gerado pelo usuário e excluir perfis de usuário, além de serem fundamentais para lidar com as solicitações de conformidade do GDPR da UE.

## O que foi alterado {#what-s-changed}

* A verificação Captcha, ao criar um novo site da comunidade, não está mais disponível prontamente no AEM 6.4 Communities. No entanto, o site Comunidades pode ser personalizado para incluir [o componente Google reCAPTCHA](https://helpx.adobe.com/experience-manager/using/aem_recaptcha.html) para melhor segurança.
* A opção para carregar um CSS personalizado foi removida dos sites da comunidade e do tema de grupos.
* Os ícones Somente conteúdo e Pesquisa foram adicionados ao Painel de filtros na interface do usuário de moderação em massa.
* O filtro Caminho do conteúdo foi adicionado no Trilho de filtros na interface do usuário de moderação em massa.
* Os modos de alternância para o modo em massa e Saída em massa foram removidos da interface do usuário de moderação em massa. Para entrar no modo de seleção múltipla, clique no ícone Selecionar ( ![seletor](assets/selecticon.png)) em uma publicação, que aparece ao passar o mouse sobre ela (desktop) ou pressionando e segurando um dedo na publicação (móvel).
