---
title: 'Introdução à criação de formulários adaptáveis '
seo-title: 'Introdução à criação de formulários adaptáveis '
description: O AEM Forms oferece uma interface fácil de usar, mas eficiente, para a criação de formulários adaptáveis. Ele fornece vários componentes e ferramentas que podem ser usadas para criar formulários.
seo-description: O AEM Forms oferece uma interface fácil de usar, mas eficiente, para a criação de formulários adaptáveis. Ele fornece vários componentes e ferramentas que podem ser usadas para criar formulários.
uuid: 07ff8e79-daf7-4608-9171-91854619cc0b
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction, author
discoiquuid: c7a1d13e-cb61-4082-8ae7-7f5eee9e0a51
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '3078'
ht-degree: 3%

---


# Introdução à criação de formulários adaptáveis {#introduction-to-authoring-adaptive-forms}

## Visão geral {#overview}

Formulários adaptáveis permitem criar formulários envolventes, responsivos, dinâmicos e adaptáveis. O AEM Forms oferece uma interface de usuário intuitiva e componentes prontos para uso para criar e trabalhar com formulários adaptáveis. É possível optar por criar um formulário adaptável com base em um modelo de formulário ou esquema ou sem um modelo de formulário. É importante escolher cuidadosamente o modelo de formulário que atende não apenas às suas necessidades, mas estende os investimentos e ativos existentes em infraestrutura. Você pode escolher entre as seguintes opções para criar um formulário adaptável:

* **Uso de um modelo de dados de formulário**
   [A ](/help/forms/using/data-integration.md) integração de dados permite integrar entidades e serviços de diferentes fontes de dados em um modelo de dados de formulário que pode ser usado para criar formulários adaptáveis. Escolha o modelo de dados de formulário se o formulário adaptável que você está criando envolver a busca e gravação de dados de e para várias fontes de dados.

* **Usando um**
modelo de formulário XDP: é um modelo de formulário ideal se você tiver investimentos em formulários baseados em XFA ou XDP. Ele fornece uma maneira direta de converter formulários baseados em XFA em formulários adaptáveis. Quaisquer regras XFA existentes são retidas nos formulários adaptáveis associados. Os formulários adaptáveis resultantes são compatíveis com construções XFA, como validações, eventos, propriedades e padrões.

* **O uso de uma Definição de esquema XML (XSD) ou de um esquema JSON**
SchemaXML e JSON representa a estrutura na qual os dados são produzidos ou consumidos pelo sistema de back-end em sua organização. É possível associar o esquema a um formulário adaptável e usar seus elementos para adicionar conteúdo dinâmico ao formulário adaptável. Os elementos do esquema estarão disponíveis para uso na guia Objetos do modelo de dados do navegador Conteúdo ao criar formulários adaptáveis.

* **Uso de um modelo de formulário nenhum ou sem**

Os formulários adaptáveis criados com essa opção não usam nenhum modelo de formulário. O XML de dados gerado desses formulários tem uma estrutura simples com campos e valores correspondentes.

Para obter mais informações sobre como criar um formulário adaptável, consulte [Criação de um formulário adaptável](/help/forms/using/creating-adaptive-form.md).

## Interface do usuário de criação de formulário adaptável {#adaptive-form-authoring-ui}

A interface otimizada para toque para a criação de formulários adaptáveis é intuitiva e oferece:

* Funcionalidade de arrastar e soltar
* Componentes de formulário padrão
* Repositório integrado de ativos

Ao criar um novo formulário adaptável ou editar um formulário existente, você usa os seguintes elementos da interface do usuário:

* [Barra lateral](#sidebar)
* [Barra de ferramentas da página](#page-toolbar)

* [Barra de ferramentas Componente](#component-toolbar)
* [Página de formulário adaptável](#af-page)

![Interface do usuário de criação de formulário adaptável](assets/formeditor.png)

**A.** Barra lateral  **B.** Barra de ferramentas da página  **C.** Página de formulário adaptável

### Barra lateral {#sidebar}

A barra lateral permite

* Consulte o conteúdo do formulário, como painéis, componentes, campos e layout.
* Editar propriedades de componentes.
* Pesquise, visualize e use ativos no repositório do Gerenciamento de ativos digitais do AEM (DAM).
* Adicione componentes ao formulário.

   ![Barra lateral](assets/sidebar-comps-2.png)
   [Clique para ampliar](assets/sidebar-comps-2.png)

**A.** Navegador de conteúdo  **B.** Navegador de propriedades  **C.** Navegador de ativos  **D.** Componentes navegador

A barra lateral inclui os seguintes navegadores:

* **Navegador de conteúdo**

   No navegador de conteúdo, você pode ver

   * **Objetos do Formulário**

      Mostra a hierarquia de objetos do Formulário. O autor pode navegar até um componente de formulário específico tocando nesse elemento na Árvore de objetos de formulário. O autor pode pesquisar objetos e reorganizá-los a partir dessa árvore.

   * **Objetos do modelo de dados**

      Permite ver a hierarquia do modelo de formulário.

      Ela permite arrastar e soltar elementos do modelo de formulário no formulário adaptável. Os elementos adicionados são convertidos automaticamente em componentes de formulário, mantendo suas propriedades originais. É possível ver objetos de modelo de dados quando o formulário usa esquema XML, esquema JSON ou modelo XDP.

* **Navegador de propriedades**

   Permite editar as propriedades de um componente. As propriedades mudam de acordo com um componente. Para ver as propriedades do contêiner de formulário adaptável:

   Selecione um componente, toque em ![nível de campo](assets/field-level.png) > **[!UICONTROL Contêiner de formulário adaptável]** e toque em ![cmppr](assets/cmppr.png).

* **Navegador de ativos**

   Segrega diferentes tipos de conteúdo, como imagens, documentos, páginas, filmes e assim por diante.

* **Navegador de componentes**

   Inclui componentes que podem ser usados para criar um formulário adaptável. Você pode arrastar componentes do para o formulário adaptável para adicionar elementos de formulário e configurar o elemento adicionado de acordo com os requisitos. A tabela a seguir descreve os componentes listados no navegador de componentes.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Componente</strong></th> 
   <th><strong>Funcionalidade</strong></th> 
  </tr> 
  <tr> 
   <td>Bloco do Adobe Sign</td> 
   <td>Adiciona um bloco de texto com espaços reservados para os campos a serem preenchidos ao assinar usando o Adobe Sign.</td> 
  </tr> 
  <tr> 
   <td>Botão</td> 
   <td>Adiciona um botão, que pode ser configurado para executar ações, como salvar, redefinir, seguir, anterior e assim por diante.</td> 
  </tr> 
  <tr> 
   <td>Captcha</td> 
   <td>Adiciona validação CAPTCHA usando o serviço Google reCAPTCHA. Para obter detalhes, consulte <a href="/help/forms/using/captcha-adaptive-forms.md" target="_blank">Usando CAPTCHA em formulários adaptáveis</a>.</td> 
  </tr> 
  <tr> 
   <td>Gráfico</td> 
   <td>Adiciona um gráfico que pode ser usado em formulários e documentos adaptáveis para representação visual de dados bidimensionais em painéis repetitivos e linhas de tabela.</td> 
  </tr> 
  <tr> 
   <td>Caixa de seleção</td> 
   <td>Adiciona uma caixa de seleção.</td> 
  </tr> 
  <tr> 
   <td>Campo de Entrada de Data</td> 
   <td>Use o componente Campo de entrada de data em seu formulário, para permitir que os clientes preencham dia, mês e ano separadamente em três caixas. Você pode personalizar a aparência do componente e alterar o formato de data. Por exemplo, você pode permitir que seus clientes insiram datas no formato MM/DD/AAAA ou DD/MM/AAAA.</td> 
  </tr> 
  <tr> 
   <td>Seletor de data</td> 
   <td>Adiciona um campo de calendário para selecionar uma data.</td> 
  </tr> 
  <tr> 
   <td>Fragmento do documento</td> 
   <td>Permite adicionar componentes reutilizáveis de uma correspondência.</td> 
  </tr> 
  <tr> 
   <td>Grupo de fragmento de documento</td> 
   <td>Permite adicionar um grupo de fragmentos de documento relacionados que você pode usar em um modelo de carta como uma única unidade.</td> 
  </tr> 
  <tr> 
   <td>Lista suspensa</td> 
   <td>Adiciona uma lista suspensa - seleção única ou múltipla</td> 
  </tr> 
  <tr> 
   <td>E-mail</td> 
   <td><p>Adiciona um campo para capturar o endereço de email. O componente Email, por padrão, valida endereços de email usando a seguinte expressão regular.</p> <p><code>^[a-zA-Z0-9.!#$%&amp;’*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$</code></p> </td> 
  </tr> 
  <tr> 
   <td>Anexo de arquivo</td> 
   <td><p>Adiciona um botão que permite aos usuários navegar e anexar documentos de suporte a um formulário.</p> <p><strong>Observação:  </strong>O componente Anexo de arquivo oferece suporte a um conjunto predefinido de formatos de arquivo em formulários adaptáveis habilitados para o Adobe Sign. Para obter mais informações, consulte <a href="https://helpx.adobe.com/document-cloud/help/supported-file-formats-fill-sign.html">Formatos de arquivo compatíveis</a>.</p> </td> 
  </tr> 
  <tr> 
   <td>Lista de anexos de arquivo</td> 
   <td>Adiciona um campo que lista todos os anexos carregados usando o componente Anexo de arquivo.</td> 
  </tr> 
  <tr> 
   <td>Rodapé<br /> </td> 
   <td>Adiciona o cabeçalho da página que normalmente inclui o logotipo de uma corporação, o título do formulário e o resumo.<br /> </td> 
  </tr> 
  <tr> 
   <td>Cabeçalho</td> 
   <td>Adiciona o rodapé da página que normalmente inclui informações de direitos autorais e links para outras páginas. </td> 
  </tr> 
  <tr> 
   <td>Imagem</td> 
   <td>Permite inserir uma imagem.</td> 
  </tr> 
  <tr> 
   <td>Opção de Imagem</td> 
   <td>Permite que seus clientes selecionem uma imagem para fornecer informações. Você pode usar as informações para fornecer serviços personalizados aos clientes.</td> 
  </tr> 
  <tr> 
   <td>Próximo botão</td> 
   <td>Adiciona um botão para navegar até o próximo painel em um formulário.</td> 
  </tr> 
  <tr> 
   <td>Caixa numérica</td> 
   <td>Adiciona um campo para capturar valores numéricos</td> 
  </tr> 
  <tr> 
   <td>Escalonador Numérico</td> 
   <td>Use o Numeric Stepper em seu formulário para permitir que seus clientes insiram um valor numérico, que pode aumentar ou diminuir com base em uma etapa predefinida.</td> 
  </tr> 
  <tr> 
   <td>Painel</td> 
   <td><p>Adiciona um painel ou subpainel.</p> <p>Você também pode adicionar um componente de painel na barra de ferramentas do painel pai usando o botão <span class="uicontrol">Adicionar painel filho</span>. Da mesma forma, é possível adicionar uma barra de ferramentas específica do painel usando o botão <span class="uicontrol">Adicionar barra de ferramentas do painel</span>. É possível configurar a posição da barra de ferramentas do painel usando a caixa de diálogo Editar painel .</p> </td> 
  </tr> 
  <tr> 
   <td>Caixa de senha</td> 
   <td>Adiciona um campo para capturar uma senha.</td> 
  </tr> 
  <tr> 
   <td>Botão Anterior</td> 
   <td>Adiciona um botão que os usuários precisam para retornar à página ou ao painel anterior.</td> 
  </tr> 
  <tr> 
   <td>Botão de opção</td> 
   <td>Adiciona botões de opção.</td> 
  </tr> 
  <tr> 
   <td>Botão de redefinição</td> 
   <td>Adiciona um botão para redefinir campos de formulário.</td> 
  </tr> 
  <tr> 
   <td>Botão salvar</td> 
   <td>Adiciona um botão para salvar os dados do formulário.</td> 
  </tr> 
  <tr> 
   <td>Assinatura</td> 
   <td>Adiciona um campo para capturar assinaturas do rabisco.</td> 
  </tr> 
  <tr> 
   <td>Separador</td> 
   <td>Permite a segregação visual de painéis em seu formulário.</td> 
  </tr> 
  <tr> 
   <td>Etapa de assinatura</td> 
   <td>Exibe as informações fornecidas no formulário e os campos de assinatura para o usuário verificar e assinar o formulário.</td> 
  </tr> 
  <tr> 
   <td>Texto</td> 
   <td>Permite que você especifique texto estático.</td> 
  </tr> 
  <tr> 
   <td>Botão enviar</td> 
   <td>Adiciona um botão Enviar para enviar o formulário para a ação de envio configurada.</td> 
  </tr> 
  <tr> 
   <td>Etapa de resumo</td> 
   <td>Envia o formulário e exibe o texto resumido que os autores especificam após o envio do formulário. </td> 
  </tr> 
  <tr> 
   <td>Alternar</td> 
   <td>Adiciona um switch que executa uma ação de alternância ou ativação/desativação. Não é possível adicionar mais de duas opções no componente Switch. Como um switch pode ter apenas dois valores: Ligado ou desligado, não é obrigatório. Pelo menos um valor é salvo independentemente da entrada do usuário. <br /> </td> 
  </tr> 
  <tr> 
   <td>Tabela</td> 
   <td>Adiciona uma tabela que permite organizar dados em linhas e colunas. </td> 
  </tr> 
  <tr> 
   <td>Telefone</td> 
   <td><p>Adiciona um campo para capturar o número de telefone. O componente Telefone permite que os autores configurem um dos seguintes tipos de número de telefone. Cada tipo está associado a uma expressão regular padrão para validação.</p> 
    <ul> 
     <li>O Tipo Internacional é validado por <code>^[+][0-9]{0,14}$</code>.</li> 
     <li>O tipo USPhoneNumber é validado por <code>{'+1 ('999') '999-9999}</code>.</li> 
     <li>O tipo UKPhoneNumber é validado por <code>text{'+'99 999 999 9999}</code>.</li> 
     <li>Tipo Personalizado não fornece um padrão de validação padrão. Obtém o valor do último tipo de número de telefone selecionado. Você também pode especificar seu próprio padrão de validação personalizado.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Termos e condições<br /> </td> 
   <td>Adiciona um campo que os autores podem usar para especificar os termos e condições que os usuários devem revisar antes de preencher o formulário.</td> 
  </tr> 
  <tr> 
   <td>Caixa de texto </td> 
   <td><p>Adiciona uma caixa de texto na qual o usuário pode especificar as informações necessárias. </p> <p>Por padrão, o componente Caixa de texto aceita apenas texto sem formatação. Você pode ativar um componente Caixa de texto para aceitar Rich Text. Um componente de texto Rich Text habilitado fornece opções para adicionar cabeçalhos, alterar estilos de caracteres (negrito, itálico, sublinhar os caracteres), criar listas ordenadas e não ordenadas, alterar o plano de fundo do texto e a cor do texto e adicionar hiperlinks. Para ativar rich text para uma caixa de texto, habilite a opção<strong> Permitir Rich Text</strong> nas propriedades do componente.</p> </td> 
  </tr> 
  <tr> 
   <td>Título</td> 
   <td>Especifica um título para o formulário adaptável.</td> 
  </tr> 
  <tr> 
   <td>Etapa de verificação</td> 
   <td><p>Adiciona um espaço reservado para exibir o formulário preenchido para verificação por usuário.</p> <p><strong>Observação</strong>: O formulário adaptável contendo o componente Verificar não suporta usuários anônimos. Além disso, não é recomendado usar o componente Verificar em um fragmento de formulário adaptável.</p> </td> 
  </tr> 
 </tbody> 
</table>

#### Práticas recomendadas para trabalhar com componentes {#best-practices}

Algumas práticas recomendadas e pontos principais a serem lembrados ao trabalhar com componentes de formulário adaptáveis são os seguintes:

* Cada componente tem propriedades associadas que controlam sua aparência e funcionalidade. Para configurar as propriedades de um componente, toque no componente e em ![cmppr](assets/cmppr.png) para abrir as propriedades do componente no navegador Propriedades.
* Um componente é identificado com seu nome de elemento. Ao tocar em ![cmppr](assets/cmppr.png), é possível alterar o nome do componente alterando o valor do campo **[!UICONTROL Nome do elemento]** no navegador de propriedades. O campo Nome do elemento aceita somente letras, números, hifens (-) e sublinhados (_). Outros caracteres especiais não são permitidos e o nome do elemento deve começar com uma letra.

* Você pode modificar a propriedade Título de um componente de formulário adaptável em linha no editor de formulário sem abrir o navegador Propriedades , desde que o título esteja visível no formulário. Para fazer isso:

   1. Toque para selecionar um componente que tenha uma propriedade **[!UICONTROL Title]** e cuja propriedade **[!UICONTROL Ocultar título]** esteja desativada.
   1. Toque em ![aem_6_3_edit](assets/aem_6_3_edit.png) para tornar o título editável.
   1. Modifique o título e toque na tecla Return ou em qualquer lugar fora do componente para salvar as alterações. Toque na chave Esc para descartar as alterações.

* Alguns componentes de formulário adaptáveis, como Email e Telefone, incluem padrões de validação prontos para uso. No entanto, você pode especificar a validação personalizada atualizando o campo **[!UICONTROL Padrão de validação]** na opção Padrões nas propriedades do componente. Consulte descrições de componentes na tabela acima para obter mais informações sobre validações padrão.

* Campos de formulários adaptáveis, como Caixa numérica e Email podem ser configurados para incluir tipos de entrada HTML5 especializados. Quando esses campos estão em foco em dispositivos móveis e tablets, o teclado exibe um alfabeto, números e caracteres específicos na frente, normalmente usados para inserir informações nos campos. Ajuda os usuários a inserir informações rapidamente sem precisar alternar entre conjuntos de caracteres no teclado. Para permitir entrada especializada para um componente, ative a caixa de seleção **[!UICONTROL Usar número de tipo HTML]** nas propriedades do componente.

* Você pode ativar um componente Caixa de texto para aceitar Rich Text. Para ativar rich text para uma caixa de texto, ative a caixa de seleção **[!UICONTROL Permitir Rich Text]** nas propriedades do componente.

* Você pode ativar os componentes Caixa de texto, Email e Telefone para preencher automaticamente valores para campos como nome, endereço, cartão de crédito, telefone e email a partir das informações armazenadas nas configurações de preenchimento automático do navegador. Para ativar esse recurso, selecione **[!UICONTROL Ativar preenchimento automático]** nas propriedades do componente e selecione um **[!UICONTROL Atributo de preenchimento automático]**. Quando um usuário preenche um formulário adaptável, os valores são sugeridos a partir do perfil de preenchimento automático no navegador ou com base nos valores preenchidos anteriormente pelo usuário. Observe que o preenchimento automático funciona se as configurações de preenchimento automático no navegador do usuário estiverem ativadas.

* Especifique valores para itens de Botão de opção e Caixa de seleção no formato `{value}={text}` nas propriedades do componente.
* O componente File attachment, por padrão, permite que um usuário anexe apenas um arquivo. No entanto, é possível configurar as propriedades do componente para suportar vários anexos. Além disso, se um usuário anexar vários arquivos com o mesmo nome de arquivo, os anexos podem causar alguns problemas. Portanto, é recomendável associar um identificador exclusivo para cada anexo enviado no envio do formulário. Para fazer isso:

   1. No servidor do AEM Forms, navegue até **[!UICONTROL Adobe Experience Manager > Ferramentas > Operações > Console da Web]**.
   1. Localize e toque em **[!UICONTROL Adaptive Forms Configuration Service]**.
   1. Na caixa de diálogo Adaptive Forms Configuration Service , habilite **[!UICONTROL Tornar nomes de arquivo exclusivos]**. Por padrão, está desativado.

* Para permitir que os usuários anexem um PDF usando o navegador Safari, verifique se **[!UICONTROL application/pdf]** é adicionado à propriedade Tipos de arquivo suportados do componente Anexo de arquivo. Os formulários adaptáveis criados com a versão anterior do AEM Forms podem conter **[!UICONTROL .pdf]** em vez de **[!UICONTROL application/pdf]** na propriedade Tipos de arquivo suportados.

Para obter mais práticas recomendadas sobre formulários adaptáveis, consulte [Práticas recomendadas para trabalhar com formulários adaptáveis](/help/forms/using/adaptive-forms-best-practices.md).

>[!NOTE]
>
>Os componentes de formulário adaptável não suportam idiomas da direita para a esquerda (RTL). Por exemplo, hebraico.

### Barra de ferramentas da página {#page-toolbar}

A barra de ferramentas da página na parte superior fornece opções que permitem visualizar o formulário, alterar as propriedades do formulário e editar o layout do formulário. É possível visualizar o formulário ao criá-lo e fazer alterações de acordo. Na barra de ferramentas da página, você vê:

* **[!UICONTROL Alternar painel lateral do]** ![painel lateral](assets/toggle-side-panel.png): Permite mostrar ou ocultar a Barra Lateral.

* **[!UICONTROL Informações da página]** ![opções de tema](assets/theme-options.png): Permite exibir as propriedades da página, publicar/desfazer a publicação de um formulário, iniciar um fluxo de trabalho de formulário e abrir o formulário na interface clássica.

* **** ![Emulador](assets/ruler.png): Permite que você emule a aparência de seu formulário para diferentes tamanhos de exibição, como tablets e telefones.

* **[!UICONTROL Editar]**: Permite selecionar outros modos, como:  **Editar, Estilo, Desenvolvedor****e Design**.

   * **[!UICONTROL Editar]**: Permite editar as propriedades do formulário e seus componentes. Por exemplo, adicionar um componente, soltar uma imagem e especificar campos obrigatórios.
   * **[!UICONTROL Estilo]**: Permite estilizar a aparência dos componentes do formulário. Por exemplo, no modo de estilo, é possível selecionar um painel e especificar a cor do plano de fundo.
   * **[!UICONTROL Desenvolvedor]**: Permite que um desenvolvedor:

      * Descubra de quais formulários são compostos.
      * Depurar o que está acontecendo onde e quando, o que, por sua vez, ajuda a resolver problemas.
   * **[!UICONTROL Design]**: Permite ativar ou desativar componentes personalizados ou componentes prontos para uso que não estejam listados na Barra lateral.


* **[!UICONTROL Visualização]**: Permite que você visualize a aparência do formulário ao publicá-lo.

### Barra de ferramentas do componente {#component-toolbar}

![Barra de ferramentas do componente na interface de toque](assets/component-toolbar.png)

Ao selecionar um componente, você verá uma barra de ferramentas que permite trabalhar nele. Você tem opções para recortar, colar, mover e especificar as propriedades dos componentes. Suas opções são:

A.**[!UICONTROL Configurar]**: Ao tocar em **[!UICONTROL Configurar]**, as propriedades do componente ficam visíveis na barra lateral. A configuração dessas propriedades permite personalizar a experiência de captura de dados. Você pode alterar o nome do elemento do componente, especificar o texto do rótulo no campo Título do componente. O nome do elemento permite capturar valores inseridos pelos usuários usando o componente. Nas propriedades do componente, especifique o comportamento do componente e gerencie a entrada do usuário. Configure as propriedades na barra lateral para capturar os dados do usuário e usá-los para processamento adicional. As propriedades do contêiner de formulário adaptável permitem especificar as bibliotecas do cliente, os Layouts, os Temas, as configurações de Documento de registro, salvar configurações, as configurações de envio e as configurações de metadados.

B.**[!UICONTROL Copiar]**: Você pode usar a opção de copiar para copiar um componente e colá-lo em outros lugares do formulário. Quando você cola um componente, o componente colado obtém um novo nome de elemento, mas retém as propriedades do componente copiado.

C.**[!UICONTROL Recortar]**: Você pode usar a opção de recortar para mover um componente de um local para outro no formulário adaptável.

D. **[!UICONTROL Excluir]**: Permite excluir o componente do formulário.

E. **[!UICONTROL Inserir]**: Permite inserir um componente acima do componente selecionado.

F. **[!UICONTROL Colar]**: Permite colar o componente cortado ou copiado usando as opções descritas acima.

G. **[!UICONTROL Editar regras]**: Permite abrir o editor de regras. Para obter mais informações, consulte [Editor de regras](/help/forms/using/rule-editor.md).

H. **Grupo**: Permite selecionar vários componentes se você deseja cortar, copiar ou colar mais de um componente.

I. **[!UICONTROL Pai]**: Permite selecionar o pai de um componente. Por exemplo, um campo de texto está em uma subseção, que fica em uma seção. A seção encontra-se no painel raiz do guia e o contêiner de formulário adaptável é o pai de um painel raiz do guia. Para um componente, você pode ver todas as opções com a hierarquia inferior classificada.

Por exemplo, se você tocar em **[!UICONTROL Pai]** para uma caixa de texto, poderá ver:

* Subseção
* Seção
* guideRootPanel
* Contêiner de formulário adaptável

J. **Outros**: Fornece mais opções para trabalhar com o componente selecionado.

* Exibir expressão SOM
* Salvar um painel como fragmento (somente para painéis)
* Adicionar painel filho (somente para painéis)
* Adicionar barra de ferramentas do painel (somente para painéis)
* Substituir (não para painéis)

### Página de formulário adaptável {#af-page}

A página de formulário adaptável é o formulário real. É como qualquer outra página WCM modelada como o componente `cq:Page` do WCM. A imagem a seguir mostra a estrutura de conteúdo de um formulário adaptável típico.

![Estrutura de conteúdo de uma página WCM de formulário adaptável](assets/afstructure.png)

A estrutura de conteúdo normalmente contém os seguintes componentes principais:

* **[!UICONTROL guideContainer]**: A raiz de um formulário adaptável, que é marcada como  **Início de** formulário adaptável na interface do usuário de formulário adaptável. Nesse componente, você pode especificar:

   * *Layout móvel do formulário* adaptável: Define a aparência do formulário em dispositivos móveis.
   * *Página* de agradecimento: Define a página para a qual o usuário é redirecionado após enviar o formulário.
   * *Enviar ação*: Define como o formulário é processado no servidor depois que o usuário envia o formulário.
   * *Estilo*: Especifica o caminho para o arquivo CSS usado para personalizar a aparência do formulário.

* **[!UICONTROL rootPanel]**: O painel raiz de um formulário adaptável. Ele pode conter subpainéis sob o nó items . Cada painel, incluindo o painel raiz, pode ter um layout associado a ele. O layout do painel determina como o formulário é posicionado. Por exemplo, no layout Acordeão*, *seus itens são apresentados como etapas de Acordo.

* **[!UICONTROL barra de ferramentas]**: Um contêiner de formulário adaptável tem uma barra de ferramentas global associada, que é global ao formulário. Essa barra de ferramentas pode ser adicionada usando a ação **Adicionar barra de ferramentas** na barra de edição, que permite que os autores adicionem ações, como Enviar, Salvar, Redefinir e assim por diante.

* **[!UICONTROL ativos]**: Esse nó contém informações adicionais usadas para a criação de formulários. Por exemplo, detalhes do modelo de formulário, detalhes de localização e assim por diante).

