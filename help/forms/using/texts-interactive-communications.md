---
title: Textos em Comunicações interativas
seo-title: Text in Interactive Communications
description: Criação e edição de fragmentos de documento de texto a serem usados em Comunicações interativas - o texto é um dos quatro tipos de fragmentos de documento usados para criar Comunicações interativas. As outras três são condições, listas e fragmentos de layout.
seo-description: Creating and editing text document fragments to be used in Interactive Communications
uuid: b2188d34-14f9-4c4e-bbe0-a2e763ed2958
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 7677327a-cc56-413b-b2e3-7b10d0d0319d
feature: Interactive Communication
exl-id: a689aead-7b39-4d66-8922-ae8910c5e9ef
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2269'
ht-degree: 0%

---

# Textos em Comunicações interativas {#texts-in-interactive-communications}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Criação e edição de fragmentos de documento de texto a serem usados em Comunicações interativas - o texto é um dos quatro tipos de fragmentos de documento usados para criar Comunicações interativas. As outras três são condições, listas e fragmentos de layout.

## Visão geral {#overview}

Um fragmento de documento de texto consiste em um ou mais parágrafos de texto. Um parágrafo pode ser estático ou dinâmico. Um parágrafo dinâmico pode conter propriedades e variáveis do modelo de dados de formulário. Também é possível aplicar regras e repetir em um fragmento de documento de texto. Por exemplo, o nome do cliente em uma saudação pode ser uma propriedade do Form Data Model (FDM) com seu valor disponibilizado no tempo de execução. Ao alterar esses valores, a mesma Comunicação interativa pode ser usada para preparar a Comunicação interativa para diferentes clientes usando a interface do usuário do agente.

O fragmento de documento de texto em Comunicação interativa é compatível com o seguinte tipo de dados dinâmicos:

* **Objetos do modelo de dados**: As propriedades dos dados usam uma fonte de dados back-end.
* **Conteúdo baseado em regras**: Partes de conteúdo em um texto que são exibidas ou ocultadas com base em uma regra. Uma regra também pode se basear em propriedades e variáveis do modelo de dados de formulário.
* **Variáveis**: No fragmento do documento de texto, as variáveis não são vinculadas a uma fonte de dados de backend. O agente preenche/seleciona valores em variáveis ou vincula as variáveis a fontes de dados, enquanto prepara a Comunicação interativa para enviá-la a um processo de publicação.
* **Repetir**: Você pode ter informações dinâmicas em sua Comunicação Interativa, como transações em um demonstrativo de cartão de crédito, cujo número de ocorrências pode continuar mudando a cada Comunicação Interativa gerada. Usando a repetição, você pode formatar e estruturar essas informações dinâmicas. Para obter mais informações, consulte [Condição embutida e repetição](cm-inline-condition.md).

## Criar texto {#createtext}

1. Selecionar **`[!UICONTROL Forms]`** > **[!UICONTROL Fragmentos de documento]**.
1. Selecionar **`[!UICONTROL Create]`** > **[!UICONTROL Texto]**.
1. Especifique as seguintes informações:

   * **[!UICONTROL Título]**: (Opcional) Insira o título do fragmento do documento de texto. Os títulos não precisam ser exclusivos e podem ter caracteres especiais e caracteres que não sejam do inglês. Os textos são referenciados por seus títulos (quando disponíveis), como em miniaturas e propriedades.
   * **[!UICONTROL Nome]**: O nome exclusivo do texto, em uma pasta. Não é possível existir dois fragmentos de documento (texto, condição ou lista) em qualquer estado com o mesmo nome em uma pasta. No campo Nome , é possível inserir somente caracteres, números e hifens em inglês. O campo Nome é automaticamente preenchido com base no campo Título . Os caracteres especiais, espaços, números e caracteres que não estão em inglês inseridos no campo Título são substituídos por hífens no campo Nome. Embora o valor no campo Título seja copiado automaticamente para o Nome, você pode editar o valor.
   * **[!UICONTROL Descrição]**: Digite uma descrição do texto.
   * **[!UICONTROL Modelo de dados do formulário]**: Como opção, selecione o botão de opção Modelo de dados de formulário para criar o texto com base em um modelo de dados de formulário. Quando você seleciona o botão de opção Modelo de dados de formulário , **[!UICONTROL Modelo de dados do formulário*]** é exibido. Navegue e selecione um modelo de dados de formulário. Ao criar texto e condição para uma Comunicação interativa, certifique-se de usar o mesmo modelo de dados que pretende usar na Comunicação interativa. Para obter mais informações sobre o Modelo de dados de formulário, consulte [Integração de dados](/help/forms/using/data-integration.md).
   * **[!UICONTROL Tags]**: Como opção, para criar valor de entrada de tag personalizado no campo de texto e pressione Enter. Ao salvar esse texto, as tags recém-adicionadas são criadas.

1. Toque **[!UICONTROL Próximo]**.

   A página Criar texto é exibida. Se você optou por criar um texto baseado no modelo de dados de formulário, as propriedades do modelo de dados de formulário aparecerão no painel esquerdo.

1. Digite o texto e use as seguintes opções para formatar, condicionar e inserir as propriedades e variáveis do modelo de dados de formulário no texto:

   * [Modelo de dados do formulário](#formdatamodel)
   * [Variáveis](#variables)
   * [Editor de regras](#rules)
   * [Opções de formatação](#formatting)

      * [Copiar e colar texto formatado de outros aplicativos](#paste)
      * [Realçar partes do texto](#highlight)
   * [Repetir](/help/forms/using/cm-inline-condition.md)
   * [Caracteres especiais](#special)
   * [Como pesquisar e substituir texto](#search-features)
   * [Atalhos de teclado](/help/forms/using/keyboard-shortcuts.md)


1. Toque **[!UICONTROL Salvar]**.

   O texto é criado. Agora, você pode continuar usando o texto como um elemento fundamental ao criar uma Comunicação interativa.

## Editar texto {#edittext}

É possível editar um fragmento de documento de texto existente usando as etapas a seguir. Você também pode optar por editar um fragmento de documento de texto de um editor de Comunicação interativa.

1. Selecionar **`[!UICONTROL Forms]`** > **[!UICONTROL Fragmentos de documento]**.
1. Navegue até um fragmento de documento de texto e selecione-o.
1. Toque **[!UICONTROL Editar]**.
1. Faça as alterações necessárias. Para obter mais informações sobre opções no texto, consulte [Criar texto](#createtext).
1. Toque **[!UICONTROL Salvar]** em seguida, toque em **[!UICONTROL Fechar]**.

## Personalização de um fragmento de documento de texto usando propriedades de modelo de dados de formulário {#formdatamodel}

É possível personalizar fragmentos de documento de texto inserindo as propriedades do modelo de dados de formulário. Inserindo propriedades de modelo de dados de formulário no texto, você pode buscar e preencher dados específicos do recipient da fonte de dados associada, enquanto visualiza uma Comunicação interativa. Para obter mais informações sobre o modelo de dados de formulário, consulte [Integração de dados do AEM Forms](/help/forms/using/data-integration.md).

Se você tiver especificado um modelo de dados de formulário ao criar um texto, as propriedades no modelo de dados de formulário aparecerão no painel esquerdo do editor de texto. O modelo de dados de formulário especificado deve ser o mesmo para o fragmento de documento de texto, bem como para a Comunicação interativa que o inclui.

![insertfdmelementtext](assets/insertfdmelementtext.png)

* Para inserir uma propriedade do FDM no texto, coloque o cursor onde deseja inserir a propriedade e selecione o **`[A]`** no painel esquerdo, tocando nela e toque em **`[B]`** **[!UICONTROL Adicionar Selecionado]**. Também é possível tocar duas vezes na propriedade para inseri-la na variável **`[C]`** posição do cursor. As propriedades do modelo de dados de formulário são destacadas em uma cor de fundo acastanhada.

* Para permitir que os agentes editem o valor de uma propriedade do FDM na interface do usuário do agente enquanto [Preparar e enviar comunicação interativa](/help/forms/using/prepare-send-interactive-communication.md) usando a interface do usuário do agente, toque no **`[D]`** ícone de bloqueio para essa propriedade e verifique se está em um estado desbloqueado. O estado padrão da propriedade é bloqueado e um agente não pode editar a propriedade na interface do agente.

Também é possível usar as propriedades do modelo de dados de formulário para criar regras para exibir ou ocultar partes do conteúdo. Para obter mais informações, consulte [Criar regras no texto](#rules).

## Como criar e usar variáveis em um fragmento de documento de texto {#variables}

As variáveis são marcadores de posição que podem ser vinculados ao criar uma Comunicação interativa. As variáveis podem ser vinculadas a uma propriedade de modelo de dados de formulário ou a um fragmento de texto. As variáveis também podem ser deixadas para o agente preencher.

Você pode usar variáveis em vez de propriedades de modelo de dados de formulário quando:

* Um fragmento de documento de texto deve ser usado em várias Comunicações interativas, onde o vínculo precisa ser diferente para diferentes Comunicações interativas.
* O fragmento do documento de texto não tem um modelo de dados de formulário no momento de sua criação. Você pode inserir variáveis e depois vinculá-las às propriedades do modelo de dados de formulário no momento da criação da Comunicação interativa.
* É necessário vincular e recuperar o texto de um fragmento de documento de texto. Somente esses fragmentos de documento de texto podem ser vinculados a variáveis não devem ter variáveis no .

Ao criar ou editar um fragmento de documento de texto, você pode criar e inserir variáveis. As variáveis criadas aparecem na guia Dados da interface do usuário do agente. O agente especifica os valores para as variáveis enquanto [Preparar e enviar comunicação interativa usando a interface do usuário do agente](/help/forms/using/prepare-send-interactive-communication.md).

### Criar variáveis {#create-variables}

1. No painel esquerdo, toque em **[!UICONTROL Variáveis]**.

   O painel Variáveis é exibido.

   ![variablespanel](assets/variablespane.png)

1. Toque **[!UICONTROL Criar]**.

   O painel Criar variáveis é exibido.

1. Insira as seguintes informações e toque em **[!UICONTROL Criar]**:

   * **[!UICONTROL Nome*]**: Nome da variável.
   * **[!UICONTROL Descrição]**: Opcionalmente, insira uma descrição sobre a variável.
   * **[!UICONTROL Tipo*]**: Selecione um tipo da variável: Sequência, número, booleano ou data.
   * **[!UICONTROL Permitir apenas valores específicos]**: Para variáveis String e Number, você pode garantir que o agente escolha a partir de um conjunto específico de valores para um espaço reservado na interface do agente. Para especificar o conjunto de valores, selecione essa opção e especifique valores separados por vírgula permitidos na variável **[!UICONTROL Valores]** campo.

1. Toque **[!UICONTROL Criar]**.

   A variável é criada e listada no painel Variáveis.

1. Para inserir uma variável no texto, coloque o cursor no local apropriado, selecione a variável e toque em **[!UICONTROL Adicionar Selecionado]**.

   ![variableinserted](assets/variableinserted.png)

   As variáveis são destacadas com a cor de fundo azul claro, enquanto as propriedades do modelo de dados de formulário são destacadas com uma cor acastanhada.

1. Toque **[!UICONTROL Salvar]**.

## Criar regras no texto {#rules}

Usando o editor de regras em um texto, você pode criar regras para exibir ou ocultar cadeias de texto ou partes de conteúdo com base em **condições predefinidas**. Essas condições podem ser construídas com base em:

* Cadeias de caracteres
* Números
* Expressão matemática
* Datas
* Propriedades do modelo de dados de formulário associado
* Quaisquer variáveis que você tenha criado no texto

### Criar regras no texto {#create-rules-in-text}

1. Ao criar ou editar um texto, selecione a string de texto, o parágrafo ou o conteúdo que deseja condicionar usando a regra.

   ![seletcontentapplyrule](assets/selectcontentapplyrule.png)

1. Toque **[!UICONTROL Criar regra]**.

   A caixa de diálogo Criar regra é exibida. Além da string, do número, da expressão matemática e da data, as seguintes etapas também estão disponíveis no Editor de regras para criar instruções das regras:

   * Propriedades do modelo de dados de formulário associado
   * Quaisquer variáveis que você tenha criado

   Selecione a opção apropriada a ser avaliada.

   ![editor de regras](assets/ruleeditor.png)

   ![ruleeditorfdm](assets/ruleeditorfdm.png)

   >[!NOTE]
   >
   >A propriedade Collection não é compatível com a criação de regras para condicionar e exibir texto.

1. Selecione o operador apropriado para avaliar a regra, como Is Equal To, Contains e Starts With.

   ![ruleeditorfdm-1](assets/ruleeditorfdm-1.png)

1. Insira a expressão de avaliação, o valor, a propriedade do modelo de dados ou a variável.

   ![Regra para exibir o texto selecionado se o local do recipient for US de acordo com os dados de origem do FDM](assets/ruleeditorfdm-1-1.png)

   Regra para exibir o texto selecionado se o local do recipient for US de acordo com os dados de origem do FDM

   * Ao criar ou editar uma regra, também é possível tocar em ![icon_resize](assets/icon_resize.png) (Redimensionar) para expandir a caixa de diálogo Criar regra/Editar regra . A caixa de diálogo expandida de janela cheia permite arrastar e soltar as propriedades e variáveis do modelo de dados de formulário para criar regras. Toque em Redimensionar novamente para voltar à caixa de diálogo Criar regra .
   * Também é possível criar várias condições em uma regra.
   * Você também pode criar regras sobrepostas, nas quais uma regra é aplicada a uma parte de um conteúdo que já tem uma regra aplicada.

1. Toque **[!UICONTROL Concluído]**.

   A regra é aplicada. O texto ou conteúdo ao qual a regra é aplicada é destacado em verde. Quando você passa o mouse sobre a alça esquerda do destaque, a regra aplicada é exibida.

   ![appledruletext](assets/appliedruletext.png)

   Ao clicar no identificador esquerdo da regra aplicada, você obtém as opções para editar ou remover a regra.

## Formatação de texto {#formatting}

Ao criar ou editar texto, a barra de ferramentas é alterada dependendo do tipo de edições que você escolher fazer: Parágrafo, Alinhamento ou Listagem:

Selecione o tipo de barra de ferramentas: Parágrafo, Alinhamento ou Listagem

![Barra de ferramentas de edição de fontes](do-not-localize/paragraphtoolbar-1.png)

Barra de ferramentas de edição de fontes

![Barra de ferramentas Alinhamento](assets/alignmenttoolbar.png)

Barra de ferramentas Alinhamento

![Barra de ferramentas Listagem](do-not-localize/listingtoolbar.png)

Barra de ferramentas Listagem

### Realçar/realçar partes do texto {#highlight}

Para realçar ou enfatizar partes do texto em um fragmento de documento editável, selecione o texto e toque em Realçar cor.

![textbackground aplicado-1](assets/textbackgroundcolorapplied-1.png)

Você pode tocar diretamente em uma cor básica **`[A]`** presente na paleta Cores básicas ou toque em **Selecionar** depois de usar o controle deslizante **`[B]`** para escolher a sombra apropriada da cor.

Opcionalmente, também é possível acessar a guia Avançado para selecionar a Matiz, a Luminosidade e a Saturação apropriadas **`[C]`** para criar a cor precisa e toque em Selecionar **`[D]`** para aplicar a cor para realçar o texto.

![textbackground color-2](assets/textbackgroundcolor-2.png)

### Colar texto formatado {#paste}

Para reutilizar um ou mais parágrafos de texto que existem em outro aplicativo, como nas páginas do Microsoft® Word ou HTML, copie e cole o texto no editor de texto. A formatação do texto copiado é retida no editor de texto.

Você pode copiar e colar um ou mais parágrafos de texto em um fragmento de documento de texto editável. Por exemplo, você pode ter um documento do Microsoft® Word com uma lista com marcadores de provas aceitáveis de residência como:

![pastetextmsword- 2](assets/pastetextmsword-2.png)

Você pode copiar e colar diretamente o texto do documento do Microsoft® Word em um fragmento de documento de texto editável. A formatação, como lista com marcadores, fonte e cor do texto, é mantida no fragmento do documento de texto.

![pastetexteditablemodule-1](assets/pastetexteditablemodule-1.png)

>[!NOTE]
>
>A formatação do texto colado, no entanto, tem alguns [limitações](https://helpx.adobe.com/aem-forms/kb/cm-copy-paste-text-limitations.html).

## Inserir caracteres especiais no texto {#special}

Se necessário, insira caracteres especiais no fragmento do documento. Por exemplo, é possível usar a paleta Caracteres especiais para inserir:

* Símbolos monetários como €, ¥ e £
* Símbolos matemáticos como ∑, Lei e ^
* Símbolos de pontuação como ‟ e&quot;

![specialcharacter-2](assets/specialcharacters-2.png)

O editor de texto tem suporte integrado para 210 caracteres especiais. O administrador pode [adicionar suporte para caracteres especiais mais/personalizados por personalização](/help/forms/using/custom-special-characters.md).

## Como pesquisar e substituir texto {#search-features}

Ao trabalhar com fragmentos de documento de texto contendo uma grande quantidade de texto, é necessário procurar por uma string de texto específica. Talvez também seja necessário substituir uma string específica de texto por uma string alternativa.

O recurso Localizar e substituir permite que você procure (e substitua) qualquer string de texto em um fragmento de documento de texto. O recurso também inclui uma pesquisa de expressão regular avançada.

1. Abrir um fragmento de documento de texto para [edição](#edittext).
1. Toque **[!UICONTROL Localizar e Substituir]**.

1. Insira o texto a ser pesquisado no **[!UICONTROL Localizar]** caixa de texto e o novo texto (texto de substituição) na **[!UICONTROL Substituir]** caixa de texto e toque em **[!UICONTROL Substituir]**.

1. Se o texto pesquisado for encontrado, ele será substituído pelo texto substituto.

   * Se outra instância do texto de pesquisa for encontrada, essa instância será realçada no fragmento do documento de texto. Se você tocar em **[!UICONTROL Substituir]** novamente, a instância realçada é substituída e o cursor avança, se uma terceira instância for encontrada.
   * Se outra instância não for encontrada, a caixa de diálogo Localizar e substituir exibirá uma mensagem: Fim do módulo atingido.

   Você também pode tocar em Substituir tudo para substituir todas as correspondências de uma só vez.

   Localizar e substituir também inclui uma pesquisa de expressão regular avançada. Para usar o regex em sua pesquisa, selecione **[!UICONTROL Reg ex]** em seguida, toque em **[!UICONTROL Localizar]** ou **[!UICONTROL Substituir]**.
