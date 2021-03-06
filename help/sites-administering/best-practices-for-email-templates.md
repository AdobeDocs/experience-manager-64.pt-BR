---
title: Práticas recomendadas para modelos de e-mail
description: Encontre as práticas recomendadas sobre o design de e-mail que resulta em um template de campanha de e-mail bem desenvolvido no Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices, integration
translation-type: tm+mt
source-git-commit: 425f1e6288cfafc3053877a43fa0a20fd5d2f3ac
workflow-type: tm+mt
source-wordcount: '1053'
ht-degree: 1%

---


# Práticas recomendadas para modelos de e-mail{#best-practices-for-email-templates}

Este documento descreve algumas das práticas recomendadas para o design de e-mail, resultando em um template de campanha de e-mail bem desenvolvido.

A campanha de demonstração disponível no AEM segue todas essas práticas recomendadas. Como as práticas recomendadas são implementadas na campanha de demonstração são descritas para cada prática recomendada.

Use essas práticas recomendadas ao criar seu próprio boletim informativo.

>[!NOTE]
>
>Todo o conteúdo da campanha deve ser criado em uma página `master` do tipo `cq/personalization/components/ambitpage`. Por exemplo, se você estiver planejando uma estrutura de campanha, é algo como:
>
>* `/content/campaigns/teasers/en/campaign-promotion-global`
>
>
Verifique se ele está em uma página principal:
>
>* `/content/campaigns/teasers/master/en/campaign-promotion-global`


>[!NOTE]
>
>Ao criar um modelo de email para Adobe Campaign, você deve incluir a propriedade **acMapping** com o valor **mapRecipient** no nó **jcr:content** do modelo, ou você não poderá selecionar o modelo Adobe Campaign em **Propriedades da página** AEM (o campo está desativado).

## Modelo/componente de página {#template-page-component}

***/libs/mcm/campanha/components/campanha_newsletterpage***

<table> 
 <tbody> 
  <tr> 
   <td><strong>Práticas recomendadas</strong></td> 
   <td><strong>Implementação</strong></td> 
  </tr> 
  <tr> 
   <td><p>Especifique o tipo de documento para garantir uma renderização consistente.</p> <p>Adicionar DOCTYPE no início (HTML ou XHTML)</p> </td> 
   <td><p>É configurável alterando o design da propriedade <i>cq:doctype</i> em<i>"/etc/designs/default/jcr:content/campanha_newsletterpage"</i></p> <p>O padrão é "XHTML":</p> <p>&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "https://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"&gt;</p> <p>Pode ser alterado para "HTML_5":</p> <p>&lt;!DOCTYPE HTML&gt;</p> </td> 
  </tr> 
  <tr> 
   <td><p>Especifique a definição de caractere para garantir a renderização correta de caracteres especiais.</p> <p>Adicionar declaração CHARSET (ex: iso-8859-15, UTF-8) a &lt;head&gt;</p> </td> 
   <td><p>Está definido como UTF-8.</p> <p>&lt;meta http-equiv="content-type" content="text/html; charset=UTF-8"&gt;</p> </td> 
  </tr> 
  <tr> 
   <td><p>Codifique toda a estrutura usando o elemento &lt;table&gt;element. Para layouts mais complicados, você deve aninhar tabelas para criar estruturas complexas.</p> <p>E-mail deve ficar bom mesmo sem css.</p> </td> 
   <td><p>Tabelas são usadas em todo o modelo para estruturar conteúdo. Atualmente, usando no máximo quatro tabelas aninhadas (1 tabela base + máx. 3 níveis de aninhamento)</p> <p>&lt;div&gt; as tags são usadas somente no modo de autor para garantir a edição adequada do componente.</p> </td> 
  </tr> 
  <tr> 
   <td>Use atributos de elemento (como preenchimento de célula, valor e largura) para definir dimensões de tabela. Isso força uma estrutura de modelo de caixa.</td> 
   <td><p>Todas as tabelas contêm os atributos necessários, como <i>border</i>, <i>cellpadding</i>, <i>cellspacing</i> e <i>width</i>.</p> <p>Para harmonizar o posicionamento do elemento dentro das tabelas, todas as células da tabela têm o atributo <i>valign="top"</i> sendo definido.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Se possível, considere a acessibilidade móvel. Use query de mídia para aumentar os tamanhos de texto em telas pequenas, fornecer áreas de ocorrência de tamanho mínimo para links.</p> <p>Faça com que um email responda se o design permitir.</p> </td> 
   <td>No que diz respeito aos estilos CSS usados para ilustrar o design de demonstração, os query de mídia estão sendo usados para oferta de uma versão compatível com dispositivos móveis.</td> 
  </tr> 
  <tr> 
   <td>O CSS em linha é melhor do que colocar todo o CSS no início.</td> 
   <td><p>Para demonstrar melhor a estrutura HTML subjacente e facilitar a possibilidade de personalizar a estrutura do boletim informativo, apenas algumas definições de CSS foram incorporadas.</p> <p>Os estilos básicos e as variações de modelo foram extraídos para um bloco de estilos no &lt;head&gt; da página. No envio final do boletim informativo, essas definições de CSS devem ser incorporadas no HTML. Está planejado um mecanismo automático de infiltração, mas atualmente não está disponível.</p> </td> 
  </tr> 
  <tr> 
   <td>Mantenha seu CSS simples. Evite declarações de estilo composto, código abreviado, propriedades de layout CSS, seletores complexos e pseudo-elementos.</td> 
   <td>No que diz respeito aos estilos CSS usados para ilustrar o design de demonstração, as recomendações do CSS estão sendo seguidas.</td> 
  </tr> 
  <tr> 
   <td>Os emails devem ter largura máxima de 600 a 800 pixels. Isso fará com que eles se comportem melhor dentro do tamanho do painel de pré-visualização fornecido por muitos clientes.</td> 
   <td>A <i>width</i> da tabela de conteúdo está limitada a 600px no design de demonstração.</td> 
  </tr> 
 </tbody> 
</table>

## Imagens {#images}

/libs/mcm/campanha/componentes/imagem

| **Prática recomendada** | **Implementação** |
|---|---|
| Adicionar atributos *alt* a imagens | O atributo *alt* foi definido como obrigatório para o componente de imagem. |
| Use o formato *jpg* em vez do formato *png* para imagens | As imagens sempre serão servidas como JPG pelo componente de imagem. |
| Use `<img>` elemento em vez de imagens de plano de fundo em uma tabela. | Nenhum dado de imagem de plano de fundo é usado nos modelos. |
| Adicione o atributo style=&quot;display block&quot; nas imagens. Permite exibir bem no Gmail. | Todas as imagens contêm, por padrão, o atributo *style=&quot;display block&quot;*. |

## Texto e links {#text-and-links}

/libs/mcm/campanha/componentes/cabeçalho, /libs/mcm/campanha/componentes/textimage

<table> 
 <tbody> 
  <tr> 
   <td><strong>Prática recomendada</strong></td> 
   <td><strong>Implementação</strong></td> 
  </tr> 
  <tr> 
   <td>Use html &lt;font&gt; em vez do estilo em CSS (font-family)</td> 
   <td>O RichTextEditor (por exemplo, no componente de tempo de texto) agora oferece suporte à escolha e aplicação de famílias de fontes e tamanhos de fonte a textos selecionados. Eles serão renderizados como tags &lt;font&gt;.</td> 
  </tr> 
  <tr> 
   <td>Use fontes básicas e em várias plataformas, como <i>Arial, Verdana, Georgia</i> e <i>Times New Roman</i>.</td> 
   <td><p>Depende do design de boletins informativos.</p> <p>Para o design de demonstração, a fonte "Helvetica" é usada, mas voltará para a fonte sans-serif genérica, se não estiver presente.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Genérico {#generic}

| **Prática recomendada** | **Implementação** |
|---|---|
| Use o validador W3C para corrigir o código HTML. Verifique se todas as tags abertas estão fechadas corretamente. | O código foi validado. Apenas para o Doctype de transição XHTML o atributo xmlns ausente para o elemento `<html>` está ausente. |
| Não se incomode com JavaScript ou Flash - essas tecnologias geralmente não são suportadas pelos clientes de e-mail. | Nem o JavaScript nem o Flash são usados no modelo do boletim informativo. |
| Adicione uma versão de texto simples para envio de várias partes. | Um novo widget foi criado nas propriedades da página para extrair facilmente uma versão de texto simples do conteúdo da página. Isso pode ser usado como ponto de partida para a versão final de texto simples. |

## Modelos e exemplos de newsletters da campanha {#campaign-newsletter-templates-and-examples}

AEM vem com vários modelos e componentes prontos para uso para criar newsletters de campanha. Você pode usar esses modelos e componentes para criar seus boletins personalizados.

### Modelos {#templates}

Para oferta de uma base sólida e para ampliar a variedade de possibilidades de fluxo de conteúdo, há três tipos de modelo ligeiramente diferentes disponíveis na caixa. Você pode usá-los facilmente para criar uma nova carta personalizada.

Todos têm uma seção **header**, **footer** e **body**. Abaixo da seção de corpo, cada modelo difere no **design de coluna** (1, 2 ou 3 colunas).

![chlimage_1-318](assets/chlimage_1-318.png)

### Componentes {#components}

Atualmente, há [sete componentes disponíveis para uso em templates de campanha](/help/sites-authoring/adobe-campaign-components.md). Esses componentes são baseados na linguagem de marcação de Adobe **HTL**.

| **Nome do componente** | **Caminho do componente** |
|---|---|
| Cabeçalho | /libs/mcm/campanha/componentes/cabeçalho |
| Imagem | /libs/mcm/campanha/componentes/imagem |
| Texto e personalização | /libs/mcm/campanha/componentes/personalização |
| Textimage | /libs/mcm/campanha/componentes/textimage |
| Link | /libs/mcm/campanha/componentes/referência |
| Modelo de imagem Dynamic Media Classic (antigo Scene7) | /libs/mcm/campanha/s7image |
| Referência direcionada | /libs/mcm/campanha/componentes/referência |

>[!NOTE]
>
>Esses componentes são otimizados para conteúdo de email; ou seja, eles seguem as práticas recomendadas descritas neste documento. O uso de outros componentes predefinidos normalmente violará essas regras.

Esses componentes são descritos detalhadamente em [componentes do Adobe Campaign](/help/sites-authoring/adobe-campaign-components.md).
