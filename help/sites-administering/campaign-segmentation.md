---
title: Configuração da segmentação
seo-title: Configuração da segmentação
description: Saiba como configurar a segmentação para AEM Campanha.
seo-description: Saiba como configurar a segmentação para AEM Campanha.
uuid: f22e41b6-d9d9-4f18-9925-2d4aebc167b3
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 49c9c9ab-632a-40f7-8c30-d6a8c0f1b420
translation-type: tm+mt
source-git-commit: be46329cfe5c6fee28f616f2257e215df402e94d
workflow-type: tm+mt
source-wordcount: '1106'
ht-degree: 2%

---


# Configuração da segmentação{#configuring-segmentation}

>[!NOTE]
>
>Este documento aborda a configuração da segmentação, conforme usada com o Contexto do cliente. Para configurar segmentos com o ContextHub usando a interface de usuário de toque, consulte [Configuração da segmentação com o ContextHub](/help/sites-administering/segmentation.md).

A segmentação é uma consideração importante ao criar uma campanha. Consulte o glossário [de](/help/sites-authoring/segmentation-overview.md) segmentação para obter informações sobre como a segmentação funciona e os termos principais.

Dependendo das informações que você já coletou sobre os visitantes do site e as metas que deseja atingir, será necessário definir os segmentos e as estratégias necessárias para o conteúdo direcionado.

Esses segmentos são então usados para fornecer um visitante com conteúdo direcionado especificamente. Esse conteúdo é mantido na seção [Campanha](/help/sites-authoring/personalization.md) do site. As páginas do teaser definidas aqui podem ser incluídas como parágrafos do teaser em qualquer página e definem para qual segmento de visitante o conteúdo especializado se aplica.

AEM permite que você crie e atualize facilmente segmentos, teasers e campanhas. Também permite verificar os resultados de suas definições.

O Editor **de** segmentos permite que você defina facilmente um segmento:

![segmenteditor-1](assets/segmenteditor-1.png)

Você pode **Editar** cada segmento para especificar um **Título**, **Descrição** e fator **de Aumento** . Usando o sidekick, você pode adicionar container **AND** e **OR** para definir a lógica **do** segmento e, em seguida, adicionar as Características **do** segmento necessárias para definir os critérios de seleção.

## Fator de aumento {#boost-factor}

Cada segmento tem um parâmetro **Boost** que é utilizado como fator de ponderação; um número mais alto indica que o segmento será selecionado de preferência a um segmento com um número menor.

* Minimum value: `0`
* Maximum value: `1000000`

## Lógica do segmento {#segment-logic}

Os container lógicos a seguir estão disponíveis prontamente e permitem construir a lógica de sua seleção de segmento. Eles podem ser arrastados do sidekick para o editor:

<table> 
 <tbody> 
  <tr> 
   <td> Contêiner AND<br /> </td> 
   <td> O operador AND booleano.<br /> </td> 
  </tr> 
  <tr> 
   <td> Contêiner OR<br /> </td> 
   <td> O operador OR booleano.</td> 
  </tr> 
 </tbody> 
</table>

## Características do segmento {#segment-traits}

Os seguintes traços de segmento estão disponíveis prontamente; eles podem ser arrastados do sidekick para o editor:

<table> 
 <tbody> 
  <tr> 
   <td> Intervalo de IP<br /> </td> 
   <td>Define um intervalo de endereços IP que o visitante pode ter.<br /> </td> 
  </tr> 
  <tr> 
   <td> Visita à página<br /> </td> 
   <td>Com que frequência a página foi solicitada. <br /> </td> 
  </tr> 
  <tr> 
   <td> Propriedade da página<br /> </td> 
   <td>Qualquer propriedade da página visitada.<br /> </td> 
  </tr> 
  <tr> 
   <td> Palavras-chave de referência<br /> </td> 
   <td>Palavras-chave para corresponder às informações do site de referência. <br /> </td> 
  </tr> 
  <tr> 
   <td> Script</td> 
   <td>expressão do JavaScript a ser avaliada.<br /> </td> 
  </tr> 
  <tr> 
   <td> Referência do segmento <br /> </td> 
   <td>Referência a outra definição de segmento.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nuvem de tags<br /> </td> 
   <td>Tags a serem correspondidas com as das páginas visitadas.<br /> </td> 
  </tr> 
  <tr> 
   <td> Idade do usuário<br /> </td> 
   <td>Como retirado do perfil do usuário.<br /> </td> 
  </tr> 
  <tr> 
   <td> Propriedade do usuário<br /> </td> 
   <td>Quaisquer outras informações disponíveis no perfil do usuário. </td> 
  </tr> 
 </tbody> 
</table>

É possível combinar essas características usando os operadores booleanos OU e E (consulte [Criação de um novo segmento](#creating-a-new-segment)) para definir o cenário exato para a seleção desse segmento.

Quando a declaração inteira for avaliada como true, esse segmento será resolvido. No evento de vários segmentos serem aplicáveis, o fator de **[aumento](/help/sites-administering/campaign-segmentation.md#boost-factor)**também é usado.

>[!CAUTION]
>
>O editor de segmentos não verifica se há referências circulares. Por exemplo, o segmento A faz referência a outro segmento B, que por sua vez faz referência ao segmento A. É necessário garantir que seus segmentos não contenham nenhuma referência circular.

>[!NOTE]
>
>As propriedades com o sufixo **_i18n** são definidas por um script que faz parte da clientlib da interface do usuário da personalização. Todas as clientlibs relacionadas à interface do usuário são carregadas somente no autor, pois a interface do usuário não é necessária na publicação.
>
>Portanto, ao criar um segmento com essas propriedades, normalmente é necessário confiar em **browserFamily** , por exemplo, em vez de **browserFamily_i18n**.

## Creating a New Segment {#creating-a-new-segment}

Para definir seu novo segmento:

1. No trilho, escolha **Ferramentas > Operações > Configuração**.
1. Clique na página **Segmentação** no painel esquerdo e navegue até o local desejado.
1. Crie uma [nova página](/help/sites-authoring/managing-pages.md) usando o modelo **Segmento** .
1. Abra a nova página para ver o editor de segmentos:

   ![screen_shot_2012-02-02at101726am](assets/screen_shot_2012-02-02at101726am.png)

1. Use o sidekick ou o menu de contexto (normalmente, clique com o botão direito do mouse e selecione **Novo...** para abrir a janela Inserir novo componente) para encontrar a característica do segmento que você precisa. Em seguida, arraste-o para o Editor **de** segmentos que aparecerá no container **AND** padrão.
1. Duplo-clique na nova característica para editar os parâmetros específicos; por exemplo, a posição do mouse:

   ![screen_shot_2012-02-02at103135am-1](assets/screen_shot_2012-02-02at103135am-1.png)

1. Click **OK** to save your definition:
1. Você pode **Editar** a definição do segmento para dar a ele um **Título**, **Descrição** e **[Fator de aumento](/help/sites-administering/campaign-segmentation.md#boost-factor)**:

   ![screen_shot_2012-02-02at103547am](assets/screen_shot_2012-02-02at103547am.png)

1. Adicione mais características, se necessário. Você pode formular expressões booleanas usando os componentes **AND Container** e **OR Container** encontrados em **Segment Logic**. Com o editor de segmentos, é possível excluir características ou container desnecessários ou arrastá-los para novas posições dentro da declaração.

## Uso de Container E e OU {#using-and-and-or-containers}

É possível construir segmentos complexos em AEM. Ele ajuda a conhecer alguns pontos básicos:

* O nível superior da definição é sempre o container AND criado inicialmente; isso não pode ser alterado, mas não afeta o restante da definição do segmento.
* Certifique-se de que o aninhamento do seu container faça sentido. Os container podem ser exibidos como colchetes de sua expressão booleana.

O exemplo a seguir é usado para selecionar visitantes que sejam:

Masculino e entre os 16 e os 65 anos

OU

Feminino e entre os 16 e os 62 anos

Como o operador principal é OU, é necessário start com um Container **OU**. Dentro disso você tem 2 declarações AND, para cada uma delas você precisa de um Container **AND**, no qual você pode adicionar as características individuais.

![screen_shot_2012-02-02at105145am-1](assets/screen_shot_2012-02-02at105145am-1.png)

## Teste da aplicação de um segmento {#testing-the-application-of-a-segment}

Depois que o segmento é definido, os resultados potenciais podem ser testados com a ajuda do Contexto **[do](/help/sites-administering/client-context.md)**cliente:

1. Selecione o segmento a ser testado.
1. Pressione **[Ctrl-Alt-C](/help/sites-authoring/keyboard-shortcuts.md)**para abrir o Contexto**[ do](/help/sites-administering/client-context.md)**cliente, que mostra os dados que foram coletados. Para fins de teste, é possível **Editar** determinados valores ou **Carregar** outro perfil para ver o impacto.

1. Dependendo das características definidas, os dados disponíveis para a página atual podem ou não corresponder à definição do segmento. O status da correspondência é mostrado abaixo da definição.

Por exemplo, uma definição de segmento simples pode se basear na idade e no sexo do usuário. Carregar um perfil específico mostra que o segmento foi resolvido com êxito:

![screen_shot_2012-02-02at105926am-1](assets/screen_shot_2012-02-02at105926am-1.png)

Ou não:

![screen_shot_2012-02-02at110019am-1](assets/screen_shot_2012-02-02at110019am-1.png)

>[!NOTE]
>
>Todas as características são resolvidas imediatamente, embora a maioria só seja alterada no recarregamento da página. As alterações na posição do mouse são imediatamente visíveis, portanto úteis para fins de teste.

Esses testes também podem ser executados em páginas de conteúdo e em combinação com componentes do **Teaser** .

Passar o mouse sobre um parágrafo do teaser mostrará os segmentos aplicados, se eles resolvem no momento e, portanto, por que a instância do teaser atual foi selecionada:

![chlimage_1-408](assets/chlimage_1-408.png)

## Usando seu segmento {#using-your-segment}

Os segmentos são usados atualmente no [Campanha](/help/sites-authoring/personalization.md). Eles são usados para direcionar o conteúdo real visualizado por audiências específicas do público alvo. Consulte [Entendendo segmentos](/help/sites-authoring/segmentation-overview.md) para obter mais informações.
