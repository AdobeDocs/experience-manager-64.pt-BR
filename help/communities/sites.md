---
title: Modelos de site
seo-title: Modelos de site
description: Como acessar o console Modelos de site
seo-description: Como acessar o console Modelos de site
uuid: d2f7556e-7e43-424e-82f1-41790aeb2d98
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 202d7dba-2b34-431d-b10f-87775632807f
role: Admin
exl-id: 5049c5df-c874-4c34-a96b-7944cd0353d5
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 3%

---

# Modelos de site {#site-templates}

O console Modelos de site é muito semelhante ao console [Modelos de grupo](tools-groups.md), que está focado em funções de interesse para grupos da Comunidade.

>[!NOTE]
>
>Os consoles para a criação de [sites da comunidade](sites-console.md), [modelos de site da comunidade](sites.md), [modelos de grupo da comunidade](tools-groups.md) e [funções da comunidade](functions.md) são para uso somente no ambiente do autor.

## Console de modelos de site {#site-templates-console}

No ambiente de criação, para acessar o console de sites da comunidade

* Na navegação global: **[!UICONTROL Ferramentas > Comunidades > Modelos do site]**

Esse console exibe os modelos a partir dos quais um [site da comunidade](sites-console.md) pode ser criado e permite a criação de novos modelos de site.

![chlimage_1-18](assets/chlimage_1-18.png)

## Criar modelo de site {#create-site-template}

Para começar a criar um novo modelo de site, selecione `Create`.

Isso exibirá o painel Editor de sites , que contém três subpainéis:

### Informações básicas {#basic-info}

![chlimage_1-19](assets/chlimage_1-19.png)

No painel Informações básicas , um nome, uma descrição e se o modelo está ativado ou desativado são configurados:

* **[!UICONTROL Nome do modelo de site da comunidade]**
A ID do nome do modelo

* **[!UICONTROL Descrição do modelo do site da comunidade]**
A descrição do modelo

* **[!UICONTROL Desativado/]**
AtivadoUma opção de alternância que controla se o modelo é referenciável

### Miniatura  {#thumbnail}

![chlimage_1-20](assets/chlimage_1-20.png)

(Opcional) Selecione o ícone Fazer upload da imagem para exibir uma miniatura junto com o nome e a descrição para os criadores de sites da comunidade.

### Estrutura {#structure}

![chlimage_1-21](assets/chlimage_1-21.png)

Para adicionar funções de comunidade, arraste do lado direito para a esquerda na ordem em que os links de menu do site devem aparecer. Os estilos serão aplicados ao modelo durante a criação do site.

Por exemplo, se você deseja uma página inicial, arraste a função Página da biblioteca e solte no construtor de modelos. Isso resultará na abertura da caixa de diálogo de configuração da página. Consulte o [console de funções](functions.md) para obter informações sobre as caixas de diálogo de configuração.

Continue arrastando e soltando quaisquer outras funções da comunidade desejadas para um site da comunidade com base neste modelo.

A função de página fornece uma página vazia. A função de grupos fornece a capacidade de criar um site de grupo (subcomunidade) no site da comunidade.

>[!CAUTION]
>
>A função de grupos deve *não* ser a *primeira nem a única* função na estrutura do site.
>
>Qualquer outra função, como [page function](functions.md#page-function), deve ser incluída e listada primeiro.

![chlimage_1-22](assets/chlimage_1-22.png)

### Função Modelos de Grupo para Grupos {#group-templates-for-groups-function}

Ao incluir uma função de grupos no modelo do site, a configuração requer a especificação das opções de modelo de grupo permitidas quando um novo grupo é criado no ambiente de publicação.

>[!CAUTION]
>
>A função Grupos deve *não* ser a *primeira nem a única* função na estrutura do site.

![chlimage_1-23](assets/chlimage_1-23.png)

Ao selecionar dois ou mais modelos de grupo da comunidade, uma opção é fornecida ao administrador do grupo ao realmente criar um novo grupo na comunidade.

![chlimage_1-24](assets/chlimage_1-24.png)

## Modelo de sites de edição {#edit-site-template}

Ao visualizar modelos de site no [console Modelos de site](#site-templates-console) principal, é possível selecionar um modelo de site existente para edição.

Esse processo fornece os mesmos painéis que [criar um modelo de site](#create-site-template).
