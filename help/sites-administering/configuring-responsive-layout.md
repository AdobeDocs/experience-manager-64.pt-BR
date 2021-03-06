---
title: Configuração do Container de layout e do modo de layout
seo-title: Configuração do Container de layout e do modo de layout
description: Saiba como configurar o Container de layout e o Modo de layout.
seo-description: Saiba como configurar o Container de layout e o Modo de layout.
uuid: 952b7c86-76ab-4699-8530-8638e46bb50f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 10940000-808a-48ae-8e46-61eccef71eab
legacypath: /content/docs/en/aem/6-2/administer/operations/page-authoring/configuring-responsive-layouting
translation-type: tm+mt
source-git-commit: 3097133c42e1d9c291706516a0dbc2aa2d15ef50
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 9%

---


# Configuração do Container de layout e do modo de layout{#configuring-layout-container-and-layout-mode}

[Layout responsivo é um mecanismo para realizar um design](/help/sites-authoring/responsive-layout.md)  da Web  [ ](https://en.wikipedia.org/wiki/Responsive_web_design)responsivo. Isso permite que o usuário crie páginas da Web com um layout e dimensões dependentes dos dispositivos que seus usuários usam.

>[!NOTE]
>
>Isso pode ser comparado aos mecanismos da Web [Mobile](/help/sites-developing/mobile-web.md), que usam o design da Web adaptável (principalmente para a interface clássica).

O AEM permite um layout responsivo para suas páginas usando uma combinação de mecanismos:

* Componente [**Contêiner de layout**](/help/sites-authoring/responsive-layout.md#adding-a-layout-container-and-its-content-edit-mode)

   Este componente fornece um sistema de parágrafo que usa grades, para que você possa adicionar e posicionar componentes dentro de uma grade responsiva . Ele pode ser usado como o parsys padrão para sua página e/ou disponibilizado aos autores no navegador de componentes.

   * O componente padrão **Container de layout** é definido em:

      /libs/wcm/fundação/componentes/responsivegrid

   * É possível definir container de layout:

      * Como um componente que o usuário pode adicionar a uma página.
      * Como o parsys padrão para a página.
      * Ambos.

         Você pode ter o container de layout como padrão para a página, ao mesmo tempo em que permite que o usuário adicione outros container de layout dentro desta página; por exemplo, para obter o controle de coluna.

* **[Modo](/help/sites-authoring/responsive-layout.md#defining-layouts-layout-mode)**
de layoutDepois que o container de layout é posicionado na página, você pode usar a variável 
**Modo de** layout para posicionar o conteúdo na grade responsiva.

* [**Emulador**](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate)
Permite criar e editar sites responsivos que reorganizam o layout de acordo com o tamanho do dispositivo ou da janela, redimensionando componentes interativamente. O usuário pode observar como o conteúdo será renderizado utilizando o Emulador.

>[!CAUTION]
>
>Embora o componente **Container de layout** esteja disponível na interface clássica, sua funcionalidade total só está disponível na interface habilitada para toque.

Com estes mecanismos de grade responsivos você pode:

* Use pontos de interrupção (que indicam o agrupamento de dispositivos) para definir um comportamento de conteúdo diferente com base no layout do dispositivo.
* Ocultar componentes com base no grupo de dispositivos (definir em qual ponto de interrupção um componente ficará oculto).
* Usar o alinhamento com a grade (colocar componentes na grade, redimensionar como necessário, definir quando devem ser recolhidos/refluir para ficarem lado a lado ou acima/abaixo).
* Executar o controle da coluna.

>[!NOTE]
>
>Em uma instalação predefinida, o layout responsivo foi configurado para o [site de referência We.Retail](/help/sites-developing/we-retail.md). Você ainda deve [ativar o componente Container Layout](#enable-the-layout-container-component-for-page) para outras páginas.

## Configuração do emulador responsivo {#configuring-the-responsive-emulator}

Essas tarefas permitem que você veja o **Emulador** responsivo em seu site.

### Registre seus componentes de página para emulação {#register-your-page-components-for-emulation}

Para permitir que o emulador suporte suas páginas, você deve registrar os componentes da página. Consulte [Registrando componentes da página para Simulação](/help/sites-developing/responsive.md#registering-page-components-for-simulation).

### Especificar os grupos de dispositivos {#specify-the-device-groups}

Para especificar os grupos de dispositivos que aparecem na lista Dispositivos do emulador, consulte [Especificação dos grupos de dispositivos](/help/sites-developing/responsive.md#specifying-the-device-groups).

### Vincule seu site aos grupos de dispositivos especificados {#link-your-site-to-the-specified-device-groups}

Para incluir o emulador, é necessário vincular seu site aos grupos de dispositivos. Consulte [Adicionar a Lista Dispositivos](/help/sites-developing/responsive.md#adding-the-devices-list) (para a interface otimizada para toque e clássica).

## Ativar o modo de layout para seu site {#activate-layout-mode-for-your-site}

Esses procedimentos são usados para habilitar o modo **Layout** no seu site.

### Configurar os pontos de interrupção {#configure-the-breakpoints}

[Pontos de interrupção](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate):

* São usados em design responsivo.
* Pode ser definido:

   * No modelo de página, de onde as configurações serão copiadas para quaisquer páginas criadas com esse modelo.
   * No nó da página, de onde as configurações serão herdadas por qualquer página secundária.

* Defina um título e uma largura:

   * O título descreve o agrupamento genérico de dispositivos, com a orientação, se necessário; por exemplo, telefone, tablet, paisagem com tablete.
   * A largura define a largura máxima em pixels para esse agrupamento de dispositivos genérico. Por exemplo, se o telefone do ponto de interrupção tiver uma largura de 768, a largura máxima do layout usado para um dispositivo telefônico.

* São visíveis como marcadores na parte superior do editor de página quando você está usando o emulador.
* São herdados da hierarquia do nó pai e podem ser substituídos à vontade.
* Existe um ponto de interrupção padrão (out-of-the-box) que cobre tudo o que está acima do último ponto de interrupção *configurado*.

Eles podem ser definidos usando CRXDE Lite ou XML.

>[!NOTE]
>
>Se você estiver configurando um novo projeto:
>
>* é necessário adicionar pontos de interrupção aos modelos.
>
>
Se você estiver migrando um projeto existente (com conteúdo existente), é necessário:
>
>* adicionar pontos de interrupção aos modelos
>* adicionar os mesmos pontos de interrupção às páginas existentes\
   >  Como a herança está em operação, você pode limitar isso à página raiz do seu conteúdo.

>



#### Configurando pontos de interrupção usando CRXDE Lite {#configuring-breakpoints-using-crxde-lite}

1. Usando o CRXDE Lite (ou equivalente), navegue até:

   * Sua definição de modelo.
   * O nó `jcr:content` da sua página.

1. Em `jcr:content` crie o nó:

   * Nome: `cq:responsive`
   * Tipo: `nt:unstructured`

1. Sob isso, crie o nó:

   * Nome: `breakpoints`
   * Tipo: `nt:unstructured`

1. No nó pontos de interrupção, é possível criar qualquer número de pontos de interrupção. Cada definição é um único nó com as seguintes propriedades:

   * Nome: `<descriptive name>`
   * Tipo: `nt:unstructured`
   * Título: `String` * `<descriptive title seen in Emulator>`*
   * Largura: `Decimal` * `<value of breakpoint>`*

#### Configurando pontos de interrupção usando XML {#configuring-breakpoints-using-xml}

Os pontos de interrupção estão localizados na seção `<jcr:content>` de `.context.html` na pasta de modelo (ou conteúdo) apropriada.

Uma definição de exemplo:

```xml
<cq:responsive jcr:primaryType="nt:unstructured">
  <breakpoints jcr:primaryType="nt:unstructured">
    <phone jcr:primaryType="nt:unstructured" title="{String}Phone" width="{Decimal}768"/>
    <tablet jcr:primaryType="nt:unstructured" title="{String}Tablet" width="{Decimal}1200"/>
  </breakpoints>
</cq:responsive>
```

### Adicionar um provedor de informações responsivo {#add-a-responsive-information-provider}

>[!NOTE]
>
>Isso só é necessário se o componente de página não for baseado no componente de página de base.

Copie a seguinte estrutura de nó `cq:infoProviders` no componente de página pai:

`/libs/foundation/components/page/cq:infoProviders/responsive`

## Ativar o redimensionamento do componente para a página {#enable-component-resizing-for-the-page}

Esses procedimentos são necessários para que você possa redimensionar os componentes no modo **Layout**.

### Definir Container de layout como principal parsys {#set-layout-container-as-main-parsys}

Para definir o principal parsys de sua página como um container de layout, é necessário definir o parsys como:

`wcm/foundation/components/responsivegrid`

Em qualquer uma das situações:

* Componente da página
* Modelo de página (para uso futuro)

Os dois exemplos a seguir ilustram a definição:

* **HTL:**

   ```xml
   <sly data-sly-resource="${'par' @ resourceType='wcm/foundation/components/responsivegrid'}/>
   ```

* **JSP:**

   ```
   <cq:include path="par" resourceType="wcm/foundation/components/responsivegrid" />
   ```

### Inclua o CSS responsivo {#include-the-responsive-css}

#### CSS para pontos de interrupção usando LESS {#css-for-breakpoints-using-less}

AEM usa MENOS para gerar partes do CSS necessário, que precisam ser incluídas para seus projetos.

Você também precisará criar uma [biblioteca do cliente](https://docs.adobe.com/content/docs/en/aem/6-0/develop/the-basics/clientlibs.html) para fornecer configurações e chamadas de função adicionais. A seguinte extração MENOS é um exemplo do mínimo que você precisa adicionar ao seu projeto:

```java
@import (once) "/libs/wcm/foundation/clientlibs/grid/grid_base.less";

/* maximum amount of grid cells to be provided */
@max_col: 12;

/* default breakpoint */
.aem-Grid {
  .generate-grid(default, @max_col);
}

/* phone breakpoint */
@media (max-width: 768px) {
  .aem-Grid {
    .generate-grid(phone, @max_col);
  }
}

/* tablet breakpoint */
@media (min-width: 769px) and (max-width: 1200px) {
  .aem-Grid {
    .generate-grid(tablet, @max_col);
  }
}
```

A definição da grade base pode ser encontrada em:

`/libs/wcm/foundation/clientlibs/grid/grid_base.less`

#### Considerações sobre estilo {#styling-considerations}

Os componentes mantidos em um container responsivo serão redimensionados (juntamente com seus respectivos elementos HTML DOM) de acordo com o tamanho da grade responsiva. Portanto, nessas circunstâncias, é recomendável evitar (ou atualizar) definições de elementos DOM de largura fixa (contidos).

Por exemplo:

* Antes:

   * `width=100px`

* Depois:

   * `max-width=100px`

#### Redimensionamento e conformidade adaptável de imagem {#resizing-and-adaptive-image-compliance}

Qualquer redimensionamento de um componente na grade acionará os seguintes ouvintes, conforme apropriado:

* `beforeedit`
* `beforechildedit`
* `afteredit`

* `afterchildedit`

Para redimensionar e atualizar corretamente o conteúdo de uma imagem adaptável incluída em uma grade responsiva, é necessário adicionar um `afterEdit` definido como `REFRESH_PAGE` listener no arquivo `EditConfig` de cada componente contido.

Por exemplo:

`<cq:listeners jcr:primaryType="cq:EditListenersConfig" afteredit="REFRESH_PAGE" />`

O mecanismo de imagem adaptativa é disponibilizado por meio de um script que controla a seleção da imagem correta para o tamanho atual da janela. Ele é ativado depois que o DOM está pronto ou ao receber um evento dedicado. Atualmente, a página deve ser atualizada para refletir adequadamente o resultado da ação do usuário.

>[!CAUTION]
>
>Os clientlibs personalizados da folha de estilos devem ser carregados como parte do cabeçalho para que funcionem corretamente no autor e na publicação.

## Ative o componente de Container de layout para a página {#enable-the-layout-container-component-for-page}

Essas tarefas permitem que os autores arrastem instâncias do componente **Container de layout** para a página.

### Ative o componente de Container de layout para edição de página {#enable-the-layout-container-component-for-page-editing}

Para permitir que os autores adicionem outras grades responsivas às páginas de conteúdo, é necessário ativar o componente de Container de layout para sua página. Você pode fazer isso usando:

* **Ambiente de criação**

   Use o [Modo de design](/help/sites-authoring/default-components-designmode.md) para ativar o componente **Container de camada** para uma página.

* **Definição do componente**

   Use `allowedComponent` ou uma inclusão estática ao definir o componente.

### Configurar a grade do Container de layout {#configure-the-grid-of-the-layout-container}

Você pode configurar o número de colunas disponíveis para cada instância específica do container de layout:

1. **Ambiente de criação**

   Você pode configurar o número de colunas disponíveis para cada instância específica do container de layout.

   Para fazer isso, use o [Modo de design](/help/sites-authoring/default-components-designmode.md) e abra a caixa de diálogo de design para o container necessário. Aqui você pode especificar quantas colunas estarão disponíveis para posicionamento e dimensionamento. O padrão é 12.

1. **XML**

   As definições para a grade responsiva são especificadas em:

   `etc/design/<*your-project-name*>/.content.xml`

   Os seguintes parâmetros podem ser definidos:

   * Número de colunas disponíveis:

      * `columns="{String}8"`
   * Componentes que podem ser adicionados ao componente atual:

      * `components="[/libs/wcm/foundation/components/responsivegrid, ...`


