---
title: Renderização e entrega
seo-title: Rendering and Delivery
description: Renderização e entrega
seo-description: null
uuid: 1253b6a5-6bf3-42b1-be3a-efa23b6ddb51
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
discoiquuid: 672d5b1e-6b2f-4afe-ab04-c398e5ef45d5
exl-id: d826375d-0ce6-49fc-b264-bac39882983d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 7%

---

# Renderização e entrega{#rendering-and-delivery}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>A Adobe recomenda usar o Editor de SPA para projetos que exigem renderização do lado do cliente com base em estrutura de aplicativo de página única (por exemplo, React). [Saiba mais](/help/sites-developing/spa-overview.md).

AEM conteúdo pode ser facilmente renderizado via [Servlets Padrão Sling](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) para renderizar [JSON](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html#default-json-rendering) e outros formatos.

Essas renderizações prontas para uso normalmente caminham pelo repositório e retornam o conteúdo como está.

AEM, por meio do Sling, também oferece suporte ao desenvolvimento e implantação de renderizadores de sling personalizados para assumir o controle total do esquema renderizado e do conteúdo.

Os renderizadores padrão dos serviços de conteúdo preenchem a lacuna entre os padrões de sling predefinidos e o desenvolvimento personalizado, permitindo a personalização e o controle de muitos aspectos do conteúdo renderizado sem desenvolvimento.

O diagrama a seguir mostra a renderização dos serviços de conteúdo.

![chlimage_1-15](assets/chlimage_1-15.png)

## Solicitar JSON {#requesting-json}

Use **&lt;resource.caas span=&quot;&quot; id=&quot;1&quot; translate=&quot;no&quot; />.[&lt;export-config span=&quot;&quot; id=&quot;0&quot; translate=&quot;no&quot; />.][&lt;export-config span=&quot;&quot; id=&quot;0&quot; translate=&quot;no&quot; />.json** para solicitar JSON.]

<table>
 <tbody>
  <tr>
   <td>RECURSO</td>
   <td>um recurso de entidade em /content/entities<br /> ou <br /> um recurso de conteúdo em /content</td>
  </tr>
  <tr>
   <td>EXPORT-CONFIG</td>
   <td><p><strong>OPCIONAL</strong><br /> </p> <p>uma configuração de exportação encontrada em /apps/mobileapps/caas/exportConfig/EXPORT-CONFIG<br /> <br /> Se omitida, a configuração de exportação padrão será aplicada </p> </td>
  </tr>
  <tr>
   <td>DEPTH-INT</td>
   <td><strong>OPCIONAL</strong><br /> <br /> recursão de profundidade para renderização de filhos como usado na renderização do Sling</td>
  </tr>
 </tbody>
</table>

## Criação de configurações de exportação {#creating-export-configs}

As configurações de exportação podem ser criadas para personalizar a renderização JSON.

Você pode criar um nó de configuração em */apps/mobileapps/caas/exportConfig.*

| Nome do nó | Nome da configuração (para seletor de renderização) |
|---|---|
| jcr:primaryType | nt:unstructured |

A tabela a seguir mostra as propriedades das Configurações de exportação:

<table>
 <tbody>
  <tr>
   <td><strong>Nome</strong></td>
   <td><strong>Tipo</strong></td>
   <td><strong>Padrão (se, não definido)</strong></td>
   <td><strong>Valor</strong></td>
   <td><strong>Descrição</strong></td>
  </tr>
  <tr>
   <td>includeComponents</td>
   <td>String[]</td>
   <td>incluir tudo</td>
   <td>sling:resourceType</td>
   <td>excluir detalhes de nós com sling:resourceType especificado da exportação JSON</td>
  </tr>
  <tr>
   <td>excludeComponents</td>
   <td>String[]</td>
   <td>excluir nada</td>
   <td>sling:resourceType</td>
   <td>incluir detalhes somente para nós com sling:resourceType especificado na exportação JSON</td>
  </tr>
  <tr>
   <td>excludePropertyPrefixes</td>
   <td>String[]</td>
   <td>excluir nada</td>
   <td>Prefixos de propriedade</td>
   <td>excluir propriedades que começam com prefixos especificados da exportação JSON</td>
  </tr>
  <tr>
   <td>excludeProperties</td>
   <td>String[]</td>
   <td>excluir nada</td>
   <td>Nomes de propriedades</td>
   <td>excluir propriedades especificadas da exportação JSON</td>
  </tr>
  <tr>
   <td>includeProperties</td>
   <td>String[]</td>
   <td>incluir tudo</td>
   <td>Nomes de propriedades</td>
   <td><p>if excludePropertyPrefixes<br /> isso inclui propriedades especificadas apesar de corresponder ao prefixo que está sendo excluído,</p> <p>else (exclude properties ignoradas) inclui apenas essas propriedades</p> </td>
  </tr>
  <tr>
   <td>includeChildren</td>
   <td>String[]</td>
   <td>incluir tudo</td>
   <td>nomes filhos</td>
   <td>excluir filhos especificados da exportação JSON</td>
  </tr>
  <tr>
   <td>excludeChildren</td>
   <td>String[]<br /> <br /> </td>
   <td>excluir nada</td>
   <td>nomes filhos</td>
   <td>incluir somente filhos especificados da exportação JSON, excluir outros</td>
  </tr>
  <tr>
   <td>renameProperties</td>
   <td>String[]<br /> <br /> </td>
   <td>renomear nada</td>
   <td>&lt;actual_property_name&gt;,&lt;replacement_property_name&gt;</td>
   <td>renomear propriedades usando substituições</td>
  </tr>
 </tbody>
</table>

### Substituições de exportação do tipo de recurso {#resource-type-export-overrides}

Crie um nó de configuração em */apps/mobileapps/caas/exportConfig.*

| name | resourceTypeOverrides |
|---|---|
| jcr:primaryType | nt:unstructured |

A tabela a seguir mostra as propriedades:

<table>
 <tbody>
  <tr>
   <td><strong>Nome</strong></td>
   <td><strong>Tipo</strong></td>
   <td><strong>Padrão (se, não definido)</strong></td>
   <td><strong>Valor</strong></td>
   <td><strong>Descrição</strong></td>
  </tr>
  <tr>
   <td>&lt;SELECTOR_TO_INC&gt;</td>
   <td>String[] </td>
   <td>-</td>
   <td>sling:resourceType</td>
   <td>Para os seguintes tipos de recursos do sling, não retorne a exportação padrão do CaaS json.<br /> Retorne uma exportação json do cliente renderizando o recurso como;<br /> &lt;resource&gt;.&lt;selector_to_inc&gt;.json </td>
  </tr>
 </tbody>
</table>

### Configurações de exportação dos serviços de conteúdo existentes {#existing-content-services-export-configs}

Os Serviços de conteúdo incluem duas configurações de exportação:

* padrão (nenhuma configuração especificada)
* página (para renderizar páginas do site)

#### Configuração de exportação padrão {#default-export-configuration}

A configuração de exportação padrão dos Serviços de conteúdo será aplicada se uma configuração for especificada no URI solicitado.

&lt;resource>.caas[.&lt;depth-int>].json

<table>
 <tbody>
  <tr>
   <td><strong>Nome</strong></td>
   <td><strong>Valor</strong></td>
  </tr>
  <tr>
   <td>excludeProperties</td>
   <td> </td>
  </tr>
  <tr>
   <td>excludePropertyPrefixes</td>
   <td>jcr:,sling:,cq:,oak:,pge-</td>
  </tr>
  <tr>
   <td>includeProperties</td>
   <td>jcr:text,text<br /> jcr:title,title<br /> jcr:description,descrição<br /> jcr:lastModified,lastModified<br /> cq:tags,tags<br /> cq:lastModified,lastModified</td>
  </tr>
  <tr>
   <td>includeComponents</td>
   <td> </td>
  </tr>
  <tr>
   <td>excludeComponents</td>
   <td> </td>
  </tr>
  <tr>
   <td>includeChildren</td>
   <td> </td>
  </tr>
  <tr>
   <td>excludeChildren</td>
   <td> </td>
  </tr>
  <tr>
   <td>Substituições JSON do Sling</td>
   <td>fundação/componentes/imagem<br /> wcm/foundation/components/image<br /> mobileapps/caas/components/data/contentReference<br /> mobileapps/caas/components/data/assetlist</td>
  </tr>
 </tbody>
</table>

#### Configuração de exportação de página {#page-export-configuration}

Essa configuração estende o padrão para incluir o agrupamento de filhos em um nó filho.

&lt;site_page>.caas.page[.&lt;depth-int>].json

### Recursos adicionais {#additional-resources}

Consulte os recursos abaixo para saber mais sobre tópicos adicionais nos Serviços de conteúdo:

* [Desenvolvimento de modelos](/help/mobile/administer-mobile-apps.md)
* [Criação de serviços de conteúdo](/help/mobile/develop-content-as-a-service.md)
* [Administração dos serviços de conteúdo](/help/mobile/developing-content-services.md)
