---
title: 'Diferenciação de recursos entre formulários e PDF forms HTML5 '
seo-title: 'Diferenciação de recursos entre formulários e PDF forms HTML5 '
description: Recurso compatível com formulários e PDF forms HTML5
seo-description: Recurso compatível com formulários e PDF forms HTML5
uuid: b0a96da5-31d3-4f99-b100-91ad51736ffb
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 273096d0-b0e1-4519-8af6-11b3414cc172
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 3%

---


# Diferenciação de recursos entre formulários HTML5 e PDF forms {#feature-differentiation-between-html-forms-and-pdf-forms}

A tabela a seguir especifica o suporte ao recurso fornecido para formulários e PDF forms HTML5:

<table> 
 <tbody>
  <tr>
   <th>Recurso</th> 
   <th>Formulários HTML5</th> 
   <th>PDF</th> 
  </tr>
  <tr>
   <td>Códigos de barras<br /> </td> 
   <td>Não disponível no nível da interface do usuário. </td> 
   <td>Compatível</td> 
  </tr>
  <tr>
   <td>Campo de assinatura<br /> </td> 
   <td><strong>As </strong> assinaturas digitais não são suportadas, mas um novo campo de  <strong>assinatura </strong> Scribbleé adicionado para assinaturas como em papel. É possível escrever sua assinatura no formulário usando o campo <strong>Assinatura de script</strong>. A assinatura é salva no formulário como uma imagem. Você pode salvar informações de localização geográfica no campo <strong>Assinatura de script</strong>.</td> 
   <td>Campo de assinatura disponível para <strong>Assinaturas Digitais</strong>.</td> 
  </tr>
  <tr>
   <td>Mesclagem de dados</td> 
   <td>Compatível</td> 
   <td>Compatível</td> 
  </tr>
  <tr>
   <td>Imagens</td> 
   <td>O esquema de URI de dados é usado para exibir imagens. Todas as versões modernas dos navegadores suportam esse esquema, mas há diferenças no intervalo de formatos de imagem que cada navegador suporta.<br /> </td> 
   <td>Os formatos .gif, .png, .jpeg, .bmp e .tiff são suportados.</td> 
  </tr>
  <tr>
   <td>Paginação<br /> </td> 
   <td><p>Um formulário HTML5 é dividido em painéis e caixas para dar uma aparência semelhante aos PDF forms. O tamanho da página é calculado dinamicamente. Se todo o conteúdo de uma página em um formulário HTML5 for excluído ou marcado como oculto, a página em branco ficará oculta e um espaço vazio (espaço em branco) não será exibido entre as páginas acima e abaixo da página em branco.</p> <p>Se os scripts ou mesclagens de dados adicionarem conteúdo a uma página, o tamanho da página será expandido para acomodar o conteúdo recém-adicionado. Nenhuma nova página é adicionada ao formulário para acomodar o conteúdo recém-adicionado. </p> <p><strong>Observação: </strong> quando todo o conteúdo de uma página em um formulário HTML5 é excluído ou marcado como oculto, a página em branco (espaço em branco) permanece visível entre a 1ª e a 2ª página, mas não entre quaisquer outras páginas.</p> </td> 
   <td>A paginação no PDF depende da união do conteúdo de dados ou do conteúdo do usuário e a contagem de páginas é aumentada/reduzida com base nele.</td> 
  </tr>
  <tr>
   <td>Cabeçalhos/rodapés </td> 
   <td>Compatível. <br /> <br /> Como os formulários móveis HTML5 não suportam quebras de página, os cabeçalhos e os rodapés são exibidos apenas uma vez. No entanto, é possível configurá-los no layout para serem exibidos em vários locais na pré-visualização de formulários móveis.<br /> </td> 
   <td>Compatível.</td> 
  </tr>
  <tr>
   <td>Widgets personalizados</td> 
   <td>É possível personalizar widgets para aprimorar a experiência do usuário em dispositivos móveis.<br /> </td> 
   <td>Todos os widgets estão bloqueados e nenhum widget personalizado pode ser conectado.<br /> </td> 
  </tr>
  <tr>
   <td>API de script XFA</td> 
   <td>Suporta as construções de script XFA mais usadas. Para obter detalhes sobre a lista de construções compatíveis, consulte <a href="/help/forms/using/scripting-support.md">suporte a scripts</a>.</td> 
   <td>Suporta todas as construções de script XFA.</td> 
  </tr>
  <tr>
   <td>APIs de script Acrobat </td> 
   <td>Os formulários HTML5 são compatíveis com as APIs mais usadas. Para obter detalhes, consulte <a href="/help/forms/using/scripting-support.md">suporte a scripts</a>.</td> 
   <td>Se o arquivo PDF for aberto no Acrobat ou Reader, ele também oferecerá suporte a todas as APIs de script fornecidas pela Acrobat.</td> 
  </tr>
  <tr>
   <td>Suporte para idiomas da direita para a esquerda </td> 
   <td>Compatível</td> 
   <td>Compatível</td> 
  </tr>
 </tbody>
</table>

Siga as práticas recomendadas para ativar um modelo de formulário para execuções HTML5 e garantir que o comportamento e a aparência dos formulários HTML5 e PDF com base em XFA sejam consistentes. Para obter lista detalhada das práticas recomendadas, consulte [Práticas recomendadas para criar um formulário HTML5.](/help/forms/using/best-practices-for-html5-forms.md)

