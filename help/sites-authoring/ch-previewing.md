---
title: Visualização de páginas usando dados do ContextHub
seo-title: Previewing Pages Using ContextHub Data
description: A barra de ferramentas do ContextHub exibe os dados dos armazenamentos do ContextHub, permite alterar esses dados e é útil para visualizar o conteúdo
seo-description: The ContextHub toolbar displays data from ContextHub stores and enables you to change store data and  is useful for previewing content
uuid: 0150555a-0a92-4692-a706-bbe59fd34d6a
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: personalization
discoiquuid: f281ef8c-0831-470c-acb7-189f20452a50
exl-id: 24f94dd5-62a4-4ac3-9a1b-a8e189da9958
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 29%

---

# Visualização de páginas usando dados do ContextHub{#previewing-pages-using-contexthub-data}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O [ContextHub](/help/sites-developing/contexthub.md) A barra de ferramentas exibe dados de armazenamentos do ContextHub e permite alterar os dados de armazenamento. A barra de ferramentas do ContextHub é útil para visualizar o conteúdo que é determinado pelos dados em um armazenamento do ContextHub.

A barra de ferramentas consiste em uma série de modos de interface que contêm um ou mais módulos de interface.

* Os modos da interface do usuário são ícones que aparecem no lado esquerdo da barra de ferramentas. Ao clicar ou tocar em um ícone, a barra de ferramentas revela os módulos de interface que ele contém.
* Os módulos de interface exibem dados de um ou mais armazenamentos do ContextHub. Alguns módulos de interface também permitem manipular os dados de armazenamento.

O ContextHub instala vários modos de interface do usuário e módulos de interface do usuário. O administrador pode ter [ContextHub configurado](/help/sites-administering/contexthub-config.md) para exibir diferentes.

![screen_shot_2018-03-23at093446](assets/screen_shot_2018-03-23at093446.png)

## Revelar a barra de ferramentas do ContextHub {#revealing-the-contexthub-toolbar}

A barra de ferramentas do ContextHub está disponível no modo de Visualização. A barra de ferramentas está disponível somente nas instâncias do autor e somente se o administrador a tiver ativado.

![screen_shot_2018-03-23at093730](assets/screen_shot_2018-03-23at093730.png)

1. Com a página aberta para edição, clique ou toque em Visualizar na barra de ferramentas.

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. Para exibir a barra de ferramentas, clique ou toque no ícone ContextHub.

   ![](do-not-localize/screen_shot_2018-03-23at093621.png)

## Recursos do módulo da interface do usuário {#ui-module-features}

Cada módulo de interface fornece um conjunto diferente de recursos, mas os seguintes tipos de recursos são comuns. Como os módulos de interface podem ser estendidos, o desenvolvedor pode implementar outros recursos, conforme necessário.

### Conteúdo da barra de ferramentas {#toolbar-content}

Os módulos de interface podem exibir dados de um ou mais armazenamentos do ContextHub na barra de ferramentas. Os módulos de interface usam um ícone e um título para se identificarem.

![screen_shot_2018-03-23at093936](assets/screen_shot_2018-03-23at093936.png)

### Conteúdo pop-up {#popup-content}

Alguns módulos de interface exibem uma sobreposição de pop-up quando clicados ou tocados. Normalmente, o pop-up contém mais informações do que o que aparece na barra de ferramentas.

![screen_shot_2018-03-23at094003](assets/screen_shot_2018-03-23at094003.png)

### Pop-up Forms {#popup-forms}

A sobreposição de pop-up de um módulo pode incluir elementos de formulário que permitem alterar os dados no armazenamento do ContextHub. Se o conteúdo da página for determinado pelos dados de armazenamento, você poderá usar o formulário e observar as alterações no conteúdo da página.

### Modo de tela inteira {#fullscreen-mode}

As sobreposições de pop-up podem incluir um ícone que você clica ou toca para expandir o conteúdo do pop-up para cobrir toda a janela ou tela do navegador.

![](do-not-localize/chlimage_1-18.png)
