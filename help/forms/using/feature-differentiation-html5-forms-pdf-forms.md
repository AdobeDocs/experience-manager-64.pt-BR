---
title: Diferenciação de recursos entre formulários HTML5 e PDF forms
seo-title: Feature differentiation between HTML5 forms and PDF forms
description: Recurso suportado em HTML5 forms e PDF forms
seo-description: Feature supported in HTML5 forms and PDF forms
uuid: b0a96da5-31d3-4f99-b100-91ad51736ffb
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 273096d0-b0e1-4519-8af6-11b3414cc172
feature: Mobile Forms
exl-id: 2b82e68c-ec11-417d-a8e2-769da9b35140
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 4%

---

# Diferenciação de recursos entre formulários HTML5 e PDF forms {#feature-differentiation-between-html-forms-and-pdf-forms}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

A tabela a seguir especifica o suporte de recursos fornecido para formulários HTML5 e PDF forms:

<table> 
 <tbody>
  <tr>
   <th>Destaque</th> 
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
   <td><strong>Assinaturas digitais</strong> não são compatíveis, mas um novo <strong>Assinatura do Scribble</strong> é adicionado para assinaturas do tipo papel. É possível assinar o formulário usando a <strong>Assinatura do Scribble</strong> campo. A assinatura é salva no formulário como uma imagem. Você pode salvar informações de localização geográfica na variável <strong>Assinatura do Scribble</strong> campo.</td> 
   <td>Campo de assinatura disponível para <strong>Assinaturas digitais</strong>.</td> 
  </tr>
  <tr>
   <td>Mesclagem de dados</td> 
   <td>Compatível</td> 
   <td>Compatível</td> 
  </tr>
  <tr>
   <td>Imagens</td> 
   <td>O esquema de URI de dados é usado para exibir imagens. Todas as versões modernas dos navegadores suportam esse esquema, mas há diferenças no intervalo de formatos de imagem suportados por cada navegador.<br /> </td> 
   <td>Os formatos .gif, .png, .jpeg, .bmp e .tiff são compatíveis.</td> 
  </tr>
  <tr>
   <td>Paginação<br /> </td> 
   <td><p>Um formulário HTML5 é dividido em painéis e caixas para dar a ele uma aparência semelhante a PDF forms. O tamanho da página é calculado dinamicamente. Se todo o conteúdo de uma página em um formulário HTML5 for excluído ou marcado como oculto, a página em branco ficará oculta e um espaço vazio (espaço em branco) não será exibido entre as páginas acima e abaixo da página em branco.</p> <p>Se os scripts ou união de dados adicionarem conteúdo a uma página, o comprimento da página será expandido para acomodar o conteúdo recém-adicionado. Nenhuma nova página é adicionada ao formulário para acomodar o conteúdo recém-adicionado. </p> <p><strong>Observação:</strong> Quando todo o conteúdo de uma página em um formulário HTML5 é excluído ou marcado como oculto, a página em branco (espaço em branco) permanece visível entre a primeira e a segunda página, mas não entre quaisquer outras páginas.</p> </td> 
   <td>A paginação no PDF depende do conteúdo de dados mesclado ou do conteúdo do usuário e a contagem de páginas é aumentada/reduzida com base nela.</td> 
  </tr>
  <tr>
   <td>Cabeçalhos/Rodapés </td> 
   <td>Compatível. <br /> <br /> Como os formulários móveis do HTML5 não são compatíveis com quebras de página, os cabeçalhos e rodapés são exibidos apenas uma vez. No entanto, é possível configurá-los no layout para serem exibidos em vários lugares na visualização de formulários móveis.<br /> </td> 
   <td>Compatível.</td> 
  </tr>
  <tr>
   <td>Widgets personalizados</td> 
   <td>É possível personalizar widgets para aprimorar a experiência do usuário em dispositivos móveis.<br /> </td> 
   <td>Todos os widgets estão bloqueados e nenhum widget personalizado pode ser conectado.<br /> </td> 
  </tr>
  <tr>
   <td>API de script XFA</td> 
   <td>Suporta as construções de script XFA mais usadas. Para obter a lista de detalhes de construções compatíveis, consulte <a href="/help/forms/using/scripting-support.md">suporte a scripts</a>.</td> 
   <td>Suporta todas as construções de script XFA.</td> 
  </tr>
  <tr>
   <td>APIs de script Acrobat </td> 
   <td>Os formulários HTML5 são compatíveis com as APIs mais usadas. Para obter detalhes, consulte <a href="/help/forms/using/scripting-support.md">suporte a scripts</a>.</td> 
   <td>Se o arquivo PDF for aberto no Acrobat ou Reader, ele também oferecerá suporte a todas as APIs de script fornecidas pelo Acrobat.</td> 
  </tr>
  <tr>
   <td>Suporte para idiomas da direita para a esquerda </td> 
   <td>Compatível</td> 
   <td>Compatível</td> 
  </tr>
 </tbody>
</table>

Siga as práticas recomendadas para ativar um modelo de formulário para representações do HTML5 e garantir que o comportamento e a aparência dos formulários do HTML5 e do PDF baseado em XFA sejam consistentes. Para obter uma lista detalhada das práticas recomendadas, consulte [Práticas recomendadas para projetar um formulário HTML5.](/help/forms/using/best-practices-for-html5-forms.md)
