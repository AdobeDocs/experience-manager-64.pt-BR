---
title: Recurso de blog
seo-title: Blog Feature
description: Informações comunitárias em formato de diário
seo-description: Community information in a journaling format
uuid: 01f1a547-d22b-4da6-a69c-ab420e5a9e19
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: d5519211-8a04-4699-97bc-e162ec0f3781
exl-id: 12ae8b4c-73c5-4ec9-beea-b682b55ebdfd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1632'
ht-degree: 5%

---

# Recurso de blog {#blog-feature}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Introdução {#introduction}

O recurso de blog do AEM Communities se transformou de uma atividade de criação em uma verdadeira atividade da comunidade que ocorre no ambiente de publicação.

O recurso de blog suporta o fornecimento de informações da comunidade em formato de diário. As entradas do blog são feitas no ambiente de publicação por membros autorizados (usuários registrados, conectados).

O recurso de blog fornece:

* Criação de artigos e comentários do lado da publicação
* Edição de rich text
* Imagens embutidas (com suporte para arrastar e soltar)
* Conteúdo de rede social integrado ([Suporte para oEmbed](blog-developer-basics.md#allowing-rich-media))
* Modo de rascunho
* Publicação agendada
* Compor em nome (a [membro privilegiado](users.md#privileged-members-group) pode criar conteúdo em nome de um membro da comunidade diferente)
* [Moderação em contexto e em massa](moderate-ugc.md) de artigos e comentários do blog

Esta seção da documentação descreve

* Adicionar o recurso de blog a um site AEM
* Configurações para componentes do blog

>[!NOTE]
>
>Os componentes `Journal`e `Journal Sidebar` são intituladas `Blog` e `Blog Sidebar`.
>
>O recurso de blog encontrado no AEM 6.0 e em versões anteriores foi removido. Ele era baseado em um modelo e permitia apenas que os autores criassem conteúdo no ambiente de criação.

## Adicionar componentes de blog a uma página {#adding-blog-components-to-a-page}

Se desejar adicionar um blog a uma página no modo de criação, use o navegador de componentes para localizar

* `Communities / Blog`
* `Communities / Blog Sidebar`

E arraste-os para o lugar em uma página onde o blog deve aparecer.

Para obter as informações necessárias, visite [Noções básicas sobre componentes do Communities](basics.md).

Quando a variável [bibliotecas obrigatórias do lado do cliente](blog-developer-basics.md#essentials-for-client-side) são incluídos, é assim que a variável `Blog`componente será exibido:

![chlimage_1-147](assets/chlimage_1-147.png)

E como a `Blog Sidebar` aparecerá:

![chlimage_1-148](assets/chlimage_1-148.png)

### Configuração do Blog {#configuring-blog}

Selecione o `Blog` para acessar e selecionar o `Configure` ícone que abre a caixa de diálogo de edição.

![ícone configurar](assets/chlimage_1-149.png) ![Configurações do blog](assets/Blog-configure.png)

#### Guia Configurações {#settings-tab}

Em **[!UICONTROL Configurações]** , especifique os recursos básicos do blog:

* **[!UICONTROL Permitir miniatura de anexo]**
Se marcada, uma miniatura da imagem anexada é criada.

* **[!UICONTROL Tamanho máximo da miniatura do anexo]**
Tamanho máximo (em pixels) da imagem de miniatura do anexo. O valor padrão é 800 x 800.

* **[!UICONTROL Tamanho mínimo da imagem para miniatura]**
Tamanho mínimo (em bytes) da imagem para gerar miniatura de imagens em linha. O valor padrão é 100000 bytes (100 kb).

* **[!UICONTROL Tamanho máximo da miniatura]**
Tamanho máximo (em pixels) da imagem em miniatura para imagem em linha. O valor padrão é 800 x 800.

* **[!UICONTROL Permitir Membros Privados]**
Se marcada, somente os membros com privilégios poderão criar conteúdo.

* **[!UICONTROL Membros com privilégios permitidos]**
Adicione os membros privilegiados com permissão para criar conteúdo.

* **[!UICONTROL Bloquear conteúdo gerado pelo usuário no modo de edição do autor]**
Se estiver ativado, bloqueia o Conteúdo gerado pelo usuário durante a edição no Modo de autor.

* **[!UICONTROL Título do diário]**
O título do blog a ser exibido na página.
   >Nota:
   >O Título do diário é usado para criar automaticamente o URL para o blog. No máximo 50 caracteres (com 5 caracteres adicionais para exclusividade) são usados no título do diário que você especificar aqui para criar o URL do blog.

* **[!UICONTROL Descrição do diário]**
A descrição do blog.

* **[!UICONTROL Tópicos por página]**

   Define o número de entradas/comentários do blog exibidos por página. O padrão é 10.

* **[!UICONTROL Moderada]**

   Se marcada, a postagem de entradas e comentários do blog deve ser aprovada antes de serem exibidos em um site de publicação. O padrão está desmarcado.

* **[!UICONTROL Fechado]**

   Se marcada, o blog é fechado para novas entradas e comentários do blog. O padrão está desmarcado.

* **[!UICONTROL Editor de rich text]**

   Se marcada, entradas de blog e comentários podem ser inseridos com marcação. O padrão está marcado.

* **[!UICONTROL Permitir marcação]**

   Se marcada, permitir que membros adicionem rótulos de tag à publicação (consulte **[!UICONTROL Campo de tag]** ). O padrão está desmarcado.

* **[!UICONTROL Permitir carregamento de arquivos]**

   Se marcada, permita que anexos de arquivo sejam adicionados a uma entrada ou comentário do blog. O padrão está desmarcado.

* **[!UICONTROL Tamanho máximo do arquivo]**

   Relevante apenas se `Allow File Uploads` está marcada. Este campo limitará o tamanho (em bytes) de um arquivo carregado. O padrão é 104857600 (10 Mb).

* **[!UICONTROL Tipos de arquivos permitidos]**

   Relevante apenas se `Allow File Uploads` está marcada. Uma lista separada por vírgulas de extensões de arquivo com o separador &quot;ponto&quot;. Por exemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se qualquer tipo de arquivo for especificado, os não especificados não poderão ser carregados. O padrão é nenhum especificado, de modo que todos os tipos de arquivo são permitidos.

* **[!UICONTROL Tamanho máximo do arquivo de imagem a ser anexado]**

   Relevante somente se Permitir uploads de arquivo estiver marcado. Número máximo de bytes que um arquivo de imagem carregado pode ter. O padrão é 2097152 (2 Mb).

* **[!UICONTROL Permitir respostas]**

   Se marcada, permita respostas para comentários publicados na entrada do blog. O padrão está desmarcado.

* **[!UICONTROL Permitir que usuários excluam comentários e tópicos]**

   Se marcada, permita que os membros excluam os comentários e entradas de blog que publicaram. O padrão está desmarcado.

* **[!UICONTROL Permitir monitoramento]**

   Se marcada, inclua o seguinte recurso para artigos do blog, que permite que os membros sejam [notificado](notifications.md) de novos posts. O padrão está desmarcado.

* **[!UICONTROL Permitir assinaturas de email]**

   Se marcada, permita que os membros sejam notificados sobre novas postagens por email ([assinatura](subscriptions.md)). Exige `Allow Following` a verificar e [email configurado](email.md). O padrão está desmarcado.

* **[!UICONTROL Permitir votação]**

   Se marcada, inclua o recurso Votação com uma entrada de blog. O padrão está desmarcado.

* **[!UICONTROL Exibir selos]**

   Se marcada, exibir ganhado e atribuído [emblemas](implementing-scoring.md) com a entrada de um membro no blog. O padrão está desmarcado.

* **[!UICONTROL Ativar conteúdo em destaque]**

   se marcada, a ideia poderá ser identificada como [conteúdo em destaque](featured.md). O padrão está desmarcado.

#### Guia Moderação do usuário {#user-moderation-tab}

Em **[!UICONTROL Moderação do usuário]** , especifique as configurações de moderação:

* **[!UICONTROL Negar postagens]**

   Se marcada, os moderadores de membros confiáveis poderão negar publicações e impedir que a publicação apareça no fórum público. O padrão está desmarcado.

* **[!UICONTROL Fechar/Reabrir tópicos]**

   Se marcada, os moderadores de membros confiáveis podem fechar um tópico para outras edições e comentários, e também podem reabrir um tópico. O padrão está desmarcado.

* **[!UICONTROL Sinalizar postagens]**

   Se marcada, permita que os membros sinalizem os tópicos ou comentários de outras pessoas como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Sinalizar lista de motivo]**

   Se marcada, permita que os membros escolham, em uma lista suspensa, o motivo para marcar um tópico ou comentário como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Motivo personalizado de sinalização]**

   Se marcada, permita que os membros insiram seu próprio motivo para marcar um tópico ou comentário como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Limite de moderação]**

   Insira o número de vezes que um tópico ou comentário deve ser sinalizado pelos membros antes que os moderadores sejam notificados. O padrão é 1 ( uma vez).

* **[!UICONTROL Limite de sinalização]**

   Insira o número de vezes que um tópico ou comentário deve ser sinalizado antes de ser oculto da exibição pública. Se definido como -1, o tópico ou comentário sinalizado nunca será oculto da exibição pública. Caso contrário, esse número deve ser maior ou igual ao Limite de moderação. O padrão é 5.

#### Guia Campo de tag {#tag-field-tab}

Em **[!UICONTROL Campo de tag]** , especifique as tags que podem ser aplicadas se **[!UICONTROL Permitir marcação]** é verificada no **[!UICONTROL Configurações]** guia :

* **[!UICONTROL Namespaces permitidos]**

   Relevante se `Allow Tagging` é verificada sob o **[!UICONTROL Configurações]** guia . As tags que podem ser aplicadas são limitadas àquelas dentro das categorias de namespace verificadas. A lista de namespaces inclui &quot;Tags padrão&quot; (o namespace padrão) e &quot;Incluir todas as tags&quot;. O padrão não está marcado, o que significa que todos os namespaces são permitidos.

* **[!UICONTROL Limite sugerido]**

   Insira o número de tags a serem exibidas como sugestão para o membro postando no fórum. Um valor de -1 significa que não há limites. O padrão é 0.

### Configuração da barra lateral do blog {#configuring-blog-sidebar}

Quando você clicar duas vezes no botão `Blog Sidebar` , uma caixa de diálogo de edição é aberta.

Em **[!UICONTROL Configurações da barra lateral do diário]** , especifique o formato de data para arquivos e o tipo de entradas a serem exibidas na barra lateral:

![chlimage_1-151](assets/chlimage_1-151.png)

* **[!UICONTROL Formato de data]**

   O formato usado para exibir arquivos de entradas de blog. O formato usa espaços reservados de acordo com a convenção do Java.

   * aaaa: ano inteiro, como &#39;2015&#39;
   * yy: ano curto, como &quot;15&quot;
   * MMMMM: mês inteiro, como junho
   * MMM: mês curto, como junho
   * MM: número do mês, como 06

   O padrão é &quot;yyyy MMMM&quot;, que exibiria, por exemplo, &quot;2015 June&quot;

* **[!UICONTROL Visualizar tipo]**

   O Título e o tipo de entradas de blog a serem exibidas na barra lateral. A escolha é entre

   * Autores
   * Categorias
   * Arquivos

* **[!UICONTROL Caminho de componentes do diário]**

   *(Opcional)* O local do recurso de blog do qual os artigos de blog devem ser listados. Se deixado em branco, usará o componente de resourceType `social/journal/components/hbs/journal` que aparece na mesma página.

   * Por exemplo, `/content/sites/engage/en/blog/jcr:content/content/primary/blog`

* **[!UICONTROL Limite sugerido]**

   O número de artigos do blog a serem exibidos. Um valor de -1 significa que não há limite. O padrão é -1.

## Experiência de visitante do site {#site-visitor-experience}

No ambiente de publicação, o recurso de blog exibirá o artigo de blog mais recente, seguido de artigos de blog mais antigos em ordem decrescente de criação. As barras laterais do blog permitem que os visitantes do site apliquem filtros para limitar a seleção dos artigos do blog exibidos.

O artigo do blog é seguido por um link para postar ou exibir comentários.

Quando um artigo de blog é selecionado, o artigo do blog e os comentários são exibidos (se ativados).

Outras capacidades dependem se o visitante do site é um moderador, administrador, membro da comunidade, membro privilegiado ou anônimo.

### Como trabalhar com artigos {#working-with-articles}

Ao criar um novo artigo de blog, há a opção de

1. Publicar imediatamente
1. Publicar um rascunho
1. Publicar em uma data e hora programadas

Os artigos do blog aparecerão sob a guia apropriada (Publicado, Rascunhos ou Programado) para os membros capazes de criar na publicação.

#### Moderadores e administradores {#moderators-and-administrators}

Quando o usuário conectado tem privilégios de moderador ou administrador, ele pode executar [tarefas de moderação](moderate-ugc.md) (como permitido pela configuração do componente) em todos os artigos e comentários do blog publicados em um blog.

![chlimage_1-152](assets/chlimage_1-152.png)

### Membros {#members}

Quando o usuário conectado é um membro da comunidade ou [membro privilegiado](users.md#privileged-members-group) (dependendo da configuração), eles podem selecionar `New Article` para criar e publicar um novo artigo no blog.

Especificamente, podem:

* Criar um novo artigo de blog
* Publicar um novo artigo no blog em nome de outro membro
* Publicar um comentário em um artigo do blog
* Editar seu próprio artigo ou comentário no blog
* Excluir seu próprio artigo ou comentário do blog
* Sinalizar artigos ou comentários de outros blogues

![chlimage_1-153](assets/chlimage_1-153.png) ![chlimage_1-154](assets/chlimage_1-154.png)

### Anônimo {#anonymous}

Os visitantes do site que não estiverem conectados podem ler somente artigos e comentários postados do blog, traduzi-los se houver suporte, mas não podem adicionar um artigo ou comentário do blog nem sinalizar artigos ou comentários de outras pessoas.

![chlimage_1-155](assets/chlimage_1-155.png)

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas no [Blog Essentials](blog-developer-basics.md) página para desenvolvedores.

Para obter moderação de entradas e comentários do blog, consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

Para marcar entradas e comentários do blog, consulte [Marcação de conteúdo gerado pelo usuário](tag-ugc.md).

Para obter a tradução de entradas e comentários do blog, consulte [Tradução de conteúdo gerado pelo usuário](translate-ugc.md).
