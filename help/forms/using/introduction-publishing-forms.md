---
title: Introdução à publicação de formulários em um portal
seo-title: Introduction to publishing forms on a portal
description: O AEM Forms fornece componentes que você pode usar para criar o portal de formulários. Este artigo apresenta você aos componentes disponíveis do portal de formulários.
seo-description: AEM Forms provides with components that you can use to build your forms portal. This articles introduces you to the available forms portal components.
uuid: 96aa4fe2-a111-4675-a33c-7dee8b82cbc2
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 44871fe1-ddc9-492c-8784-5df3ca392f9b
exl-id: a91e23e8-339d-4090-9872-2e066ab66590
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1091'
ht-degree: 0%

---

# Introdução à publicação de formulários em um portal {#introduction-to-publishing-forms-on-a-portal}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Visão geral dos componentes do portal do AEM Forms {#aem-forms-portal-components-overview}

Em um cenário típico de implantação de portal centrado em formulários, o desenvolvimento de formulários e o desenvolvimento de portal são duas atividades disjuntas. Embora os designers de formulários criem e armazenem formulários em um repositório, os desenvolvedores da Web criam uma aplicação Web para listar formulários e lidar com o envio de formulários. Os Forms são copiados para a camada da Web, pois não há comunicação entre o repositório de formulários e o aplicativo da Web.

Tais cenários muitas vezes resultam em problemas de gerenciamento e atrasos de produção. Por exemplo, se houver uma versão mais recente de um formulário disponível no repositório, será necessário substituir o formulário na camada da Web, modificar a aplicação Web e reimplantar o formulário no site público. A reimplantação do aplicativo da Web pode causar algum tempo de inatividade do servidor. Normalmente, o tempo de inatividade do servidor é uma atividade planejada e, portanto, as alterações não podem ser enviadas para o site público instantaneamente.

O AEM Forms fornece componentes de portal que reduzem os custos gerais de gerenciamento e os atrasos de produção. Os componentes fazem com que os desenvolvedores da Web criem e personalizem um portal de formulários em sites criados usando o Adobe Experience Manager (AEM).

![Portal AEM Forms](assets/aem-forms-portal.png)

Os componentes do portal de formulário permitem adicionar a seguinte funcionalidade:

* Liste formulários em layouts personalizados. Estão prontos para uso, Exibição de lista, Exibição de cartão e Layouts de exibição de painel. Você pode criar seus próprios layouts personalizados.
* Permite que você exiba metadados personalizados, bem como ações personalizadas, ao listá-los.
* Formulários de lista publicados pela interface do usuário do AEM Forms na instância de publicação em que os componentes do Forms Portal estão sendo usados.
* Permitir que usuários finais renderizem formulários no formato HTML e PDF.
* Use o perfil de HTML personalizado para renderizar formulários.
* Ative a pesquisa de formulários com base em vários critérios, como propriedades de formulário, metadados e tags.
* Enviar dados de formulário para um servlet.
* Use o CSS personalizado para personalizar a aparência do portal.
* Criar links para formulários.
* Lista rascunhos e envios relacionados ao Formulário adaptativo criado pelo usuário final.

## Componentes disponíveis do portal do AEM Forms {#available-aem-forms-portal-components}

O AEM Forms fornece os seguintes componentes de portal prontos para uso, agrupados em **Serviços de documento** e **Predicados dos serviços de documento** grupos de componentes:

### Pesquisar &amp; Lister {#search-amp-lister}

O componente Pesquisar e listar permite listar formulários do repositório de formulários na página do portal e fornece opções de configuração para listar formulários com base em critérios especificados. Também permite especificar critérios de pesquisa para permitir que os usuários do portal pesquisem na lista de formulários.

### Rascunhos e envios {#drafts-amp-submissions}

Enquanto o componente Pesquisar e listar exibe formulários que são tornados públicos pelo autor do Forms, o componente Rascunhos e envios exibe formulários que são salvos como rascunho para preencher formulários posteriores e enviados. Esse componente fornece experiência personalizada para qualquer usuário conectado.

### Link {#link}

O componente Link permite criar um link para um formulário em qualquer lugar na página. Considere um cenário em que você está oferecendo um programa de treinamento e deseja que seus usuários enviem um formulário para se registrar no treinamento. Em seu site, você postou os detalhes do programa. Abaixo dos detalhes, você deseja fornecer um link para o formulário de registro. O componente Link pode ajudar você a criar esse link.

## Fluxo de trabalho do Forms Portal {#forms-portal-workflow}

O portal do Forms permite listar formulários do repositório de formulários na página do portal. Também permite especificar critérios de pesquisa para permitir que os usuários do portal pesquisem na lista de formulários. Você também pode usar o componente Rascunhos e envios para exibir formulários salvos como rascunho para preencher formulários posteriores e enviados. É necessário executar um determinado conjunto de operações antes que essas funcionalidades fiquem disponíveis em uma página do Sites. Execute as etapas na sequência listada para disponibilizar os componentes e as respectivas funcionalidades em uma página de sites:

1. **Ativar componentes do Forms Portal**: Pronto para uso, os componentes do portal de formulários não estão disponíveis para uso. [Ativar os componentes AEM sidekick](/help/forms/using/enabling-forms-portal-components.md) para uma página do AEM Sites.
1. **Listar formulários em uma página (criar página de portal de formulários):** Você pode listar formulários em páginas do AEM Sites e em páginas do Site que não sejam AEM. A lista contém formulários disponíveis na instância de publicação. Um usuário pode abrir formulários e começar a preenchê-los. Sempre que um usuário abre um formulário, uma nova instância do formulário é criada:

   1. **Listar formulários em uma página do AEM Sites**: Adicione o **[Pesquisar &amp; Lister](/help/forms/using/creating-form-portal-page.md)** para a página e configure o **[Painel de Lista](/help/forms/using/creating-form-portal-page.md#p-list-pane-p)** nela, para listar formulários em uma página. Adicione e configure o **[Painel de pesquisa](/help/forms/using/creating-form-portal-page.md#search-pane)** para o **Pesquisar &amp; Lister** também para adicionar a funcionalidade de pesquisa à página. A página com o componente do portal de formulários é conhecida como [página do portal de formulários](/help/forms/using/creating-form-portal-page.md).
   1. **Listar formulários em uma página que não seja do AEM Sites:** Use o [APIs de pesquisa do portal de formulários](/help/forms/using/listing-forms-webpage-using-apis.md) para consultar, recuperar e listar formulários em páginas que não sejam do AEM Sites.

1. **Listar rascunho e formulários enviados em uma página de portal de formulários**: Adicione e configure o componente Rascunhos e envios para a página do portal de formulários. O componente lista todos os formulários que estão no estado de rascunho e os formulários que já foram enviados.

   Para permitir que um formulário adaptável enviado apareça na guia envios, defina a variável **Enviar ação** para **[Ação de envio do portal do Forms](https://helpx.adobe.com/in/experience-manager/6-4/forms/using/configuring-submit-actions.html).** Como alternativa, ative a opção Envio do portal do Forms . Sempre que um usuário envia o formulário, ele é adicionado à guia envios.

1. **Configure o armazenamento para os dados de rascunho e formulários enviados:** Por padrão, os dados de rascunho e envios são armazenados no repositório AEM. Em um ambiente de produção, é recomendável não armazenar dados de rascunho ou de formulário enviado em AEM repositório. [Configurar o componente de portal de formulários para salvar dados em um local seguro](/help/forms/using/draft-submission-component.md#customizing-the-storage).
1. **(Opcional) Personalização dos componentes do portal de formulários:**  [Personalizar os modelos de página do portal de formulários](/help/forms/using/customizing-templates-forms-portal-components.md) para fornecer uma aparência distinta aos componentes.
1. **(Opcional) Adicione metadados personalizados a formulários:** [Adicionar metadados personalizados a formulários](/help/forms/using/customizing-templates-forms-portal-components.md) para melhorar a experiência de listagem e pesquisa.
1. **Publicar a página do portal de formulários:** A página do portal de formulários está pronta. Publique a página.

## Artigos relacionados {#related-articles}

* [Ativar componentes do portal de formulários](/help/forms/using/enabling-forms-portal-components.md)
* [Criar página do portal de formulários](/help/forms/using/creating-form-portal-page.md)
* [Listar formulários em uma página da Web usando APIs](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Usar componente Rascunhos e Envios](/help/forms/using/draft-submission-component.md)
* [Personalizar o armazenamento de rascunhos e formulários enviados](/help/forms/using/draft-submission-component.md#customizing-the-storage)
* [Amostra para integrar o componente de rascunhos e envios ao banco de dados](https://helpx.adobe.com/in/experience-manager/6-4/forms/using/integrate-draft-submission-database.html)

* [Personalização de modelos para componentes do portal de formulários](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Introdução à publicação de formulários em um portal](/help/forms/using/introduction-publishing-forms.md)
