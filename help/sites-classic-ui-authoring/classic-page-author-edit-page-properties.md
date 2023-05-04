---
title: Editar as propriedades da página
seo-title: Editing Page Properties
description: As propriedades de uma página podem variar dependendo da natureza da página. Por exemplo, algumas páginas podem estar conectadas a uma Live Copy, enquanto outras não estão, e as informações da Live Copy estarão disponíveis conforme apropriado.
seo-description: Properties of a page can vary depending on the nature of the page. For example some pages might be connected to a live copy while others are not and the live copy information will be available as appropriate.
uuid: 63d37d1b-52da-489d-b02b-e8b3d17571d1
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 23768c73-ac64-4727-8313-160c8c131b05
exl-id: 6969dc5e-f7fa-495e-8ddf-8123ca2bc9a6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 34%

---

# Editar as propriedades da página{#editing-page-properties}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Você pode definir as propriedades desejadas para uma página. Isso pode variar dependendo da natureza da página. Por exemplo, algumas páginas podem estar conectadas a uma Live Copy, enquanto outras não estão, e as informações da Live Copy estarão disponíveis conforme apropriado.

## Propriedades da página {#page-properties}

As propriedades são distribuídas por várias guias:

### Básico {#basic}

* **Título**

   O título da página é exibido em vários locais. Por exemplo, a variável **Sites** e a **Sites** exibições de cartão/lista.

   Este campo é obrigatório.

* **Tags**

   Aqui você pode adicionar ou remover as tags da página, atualizando a lista na caixa de seleção:

   * Após selecionar uma tag, ela é listada abaixo da caixa de seleção. Você pode remover uma tag dessa lista usando o ícone “x”.
   * Uma tag totalmente nova pode ser inserida digitando o nome em uma caixa de seleção vazia.

      A nova tag será realmente criada ao apertar a tecla enter. A nova tag será então exibida em uma caixa, com uma pequena estrela à direita, indicando que é uma nova tag.

   * Com a funcionalidade de menu suspenso, é possível selecionar tags existentes.
   * Um x é exibido ao passar o mouse sobre uma entrada de tag na caixa de seleção; isso pode ser usado para remover a tag desta página.

* **Ocultar na navegação**

   Uma opção de alternância para indicar se a página é exibida ou oculta na navegação da página.

* **Título da página**

   Um título a ser usado na página.

* **Titulo da navegação**

   Você pode especificar um título separado para usar na navegação (por exemplo, se desejar algo mais conciso). Se estiver vazio, a variável **Título** será usada.

* **Legenda**

   Um subtítulo para usar na página.

* **Descrição**

   Sua descrição da página, finalidade ou qualquer outro detalhe que desejar adicionar.

* **Em tempo**

   A data e a hora em que a página publicada será ativada. Quando publicada, esta página será mantida inativa até o tempo especificado.

   Deixe esses campos vazios para as páginas que deseja publicar imediatamente (o cenário normal).

* **Tempo desligado**

   A hora em que a página publicada será desativada.

   Deixe novamente esses campos vazios para as páginas que deseja publicar imediatamente.

* **URL personalizada**

   Permite inserir uma URL personalizada para esta página. Isso permite que você tenha um URL mais curto e mais expressivo.

   Por exemplo, se o URL personalizado estiver definido como w `elcome`para a página identificada pelo caminho / `v1.0/startpage`para o site h `ttp://example.com,` então h `ttp://example.com/welcome`seria a URL personalizada de h `ttp://example.com/content/v1.0/startpage`

   >[!CAUTION]
   >
   >URLs personalizadas:
   >
   >* deve ser exclusiva, dessa forma, é necessário tomar cuidado para que o valor não seja utilizado por outra página.
   >* não são compatíveis com padrões regex.


* **Redirecionar URL do Vanity**

   Indica se você deseja que a página use a URL personalizada.

### Avançado  {#advanced}

* **Idioma**

   O idioma da página.

* **Redirecionar**

   Indique a página para a qual essa página deve ser redirecionada automaticamente.

* **Design**

   Indique o [projeto](/help/sites-developing/designer.md) para ser usado nesta página.

* **Alias**

   Especifique um alias para ser usado com esta página.

* **Ativar grupo de usuários fechado**

   Ativa (ou desativa) o uso de [grupos de usuários fechados](/help/sites-administering/cug.md) (CUGs).

* **Página de logon**

   A página a ser usada para logon.

* **Grupos aceitos**

   Grupos elegíveis para logon no CUG.

* **Território**

   Nome do território para o CUG.

* **Exportar configuração**

   Especifique uma configuração de exportação.

### Miniatura  {#thumbnail}

* **Miniatura da página**

   Mostra a imagem de miniatura da página. É possível:

   * **Gerar pré-visualização**

      Gere uma pré-visualização da página para usar como miniatura.

   * **Fazer upload de imagem**

      Carregue uma imagem para usar como miniatura.

### Cloud Services {#cloud-services}

* **Cloud Services**

   Defina as propriedades para [serviços em nuvem](/help/sites-developing/extending-cloud-config.md).

### Personalização {#personalization}

* **Personalização**

   Selecione uma [Marca para especificar um escopo de direcionamento](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md).

### Permissões   {#permissions}

* **Permissões** (interface otimizada para toque)

   Visualize o [permissões efetivas e adicionar novas permissões](/help/sites-administering/user-group-ac-admin.md).

### Blueprint {#blueprint}

* **Blueprint**

   Defina as propriedades para uma página do Blueprint no [gerenciamento de vários sites](/help/sites-administering/msm.md). Controla as circunstâncias sob as quais as modificações serão propagadas no Live Copy.

### Live Copy  {#live-copy}

* **Live Copy**

   Defina as propriedades para uma página de Live Copy em [gerenciamento de vários sites](/help/sites-administering/msm.md). Controla as circunstâncias sob as quais as modificações serão propagadas do Blueprint.

### Estrutura do site  {#site-structure}

* Forneça links para páginas que oferecem funcionalidade em todo o site, como a **Página de inscrição**, a **Página offline**, entre outras.

## Editar as propriedades da página {#editing-page-properties-2}

### Editar as propriedades da página para uma página específica {#editing-page-properties-for-a-specific-page}

As Propriedades da página definem as várias propriedades da página, como títulos, quando aparecem no site e outros.

1. Abra a página que deseja editar.

1. No sidekick, abra o **Página** e selecione **Propriedades da Página...**

   Isso abre uma caixa de diálogo com várias guias.

1. Faça as alterações necessárias e clique em **OK** para salvar.
