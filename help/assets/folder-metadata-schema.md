---
title: Esquema de metadados de pasta
description: Este artigo descreve como criar um esquema de metadados para pastas de ativos em [!DNL Experience Manager] Ativos
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: 286a4f26-c0ad-4691-80d8-d17ba1a2dfe0
discoiquuid: 92eacea5-7511-48ce-8a72-ff4552ebb07d
feature: Metadata
role: User,Admin
exl-id: 1bc72dac-41f7-4593-aaea-d48ebd94b43e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1112'
ht-degree: 8%

---

# Esquema de metadados de pasta {#folder-metadata-schema}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Este artigo descreve como criar um esquema de metadados para pastas de ativos em [!DNL Experience Manager] Ativos.

Os Ativos Adobe Experience Manager permitem criar esquemas de metadados para pastas de ativos, que definem o layout e os metadados exibidos nas páginas de propriedades da pasta.

>[!NOTE]
>
>Essa funcionalidade exige [!DNL Experience Manager] 6.4 com pelo menos o Service Pack 2 implantado. Para [!DNL Experience Manager] 6.4 detalhes do service pack, veja estes [notas de versão](/help/release-notes/sp-release-notes.md).

## Adicionar um formulário de esquema de metadados de pasta {#add-a-folder-metadata-schema-form}

Use o editor do Forms do Esquema de metadados da pasta para criar e editar esquemas de metadados para pastas.

1. Toque/clique no botão [!DNL Experience Manager] logotipo e acesse **[!UICONTROL Ferramentas]** > **[!UICONTROL Ativos]**> **[!UICONTROL Esquemas de metadados da pasta]**.
1. Na página Forms do Esquema de metadados da pasta, toque/clique **[!UICONTROL Criar]**.
1. Especifique um nome para o formulário e toque/clique em **[!UICONTROL Criar]**. O novo formulário de esquema é listado na página Forms do esquema.

## Editar formulários de esquema de metadados de pastas {#edit-folder-metadata-schema-forms}

É possível editar um formulário de esquema de metadados recém-adicionado ou existente, incluindo o seguinte:

* Guias
* Itens de formulário nas guias.

Você pode mapear/configurar esses itens de formulário em um campo dentro de um nó de metadados no repositório CRX. É possível adicionar novas guias ou itens de formulário ao formulário de esquema de metadados.

1. Na página Schema Forms , selecione o formulário criado e toque/clique no link **[!UICONTROL Editar]** ícone na barra de ferramentas.
1. Na página Editor de esquema de metadados da pasta , toque/clique no **[!UICONTROL +]** ícone para adicionar uma guia ao formulário. Para renomear a guia , toque/clique no nome padrão e especifique o novo nome em **[!UICONTROL Configurações]**.

   ![custom_tab](assets/custom_tab.png)

   Para adicionar mais guias, toque/clique no botão **[!UICONTROL +]** ícone . Toque/clique **[!UICONTROL X]** para excluir uma guia.

1. Na guia ativa , adicione um ou mais componentes do **[!UICONTROL Criar formulário]** guia .

   ![adicionar_componentes](assets/adding_components.png)

   Se você criar várias guias, toque/clique em uma determinada guia para adicionar componentes.

1. Para configurar um componente, selecione-o e modifique suas propriedades no **[!UICONTROL Configurações]** guia .

   Se necessário, exclua um componente do **[!UICONTROL Configurações]** guia .

   ![configure_properties](assets/configure_properties.png)

1. Toque/clique **[!UICONTROL Salvar]** na barra de ferramentas para salvar as alterações.

### Componentes para criar formulários {#components-to-build-forms}

O **[!UICONTROL Criar formulário]** lista itens de formulário que você usa no formulário de esquema de metadados da pasta. O **[!UICONTROL Configurações]** A guia exibe os atributos para cada item selecionado na variável **[!UICONTROL Criar formulário]** guia . Esta é uma lista com os itens de formulário disponíveis no **[!UICONTROL Criar formulário]** guia :

| Nome do componente | Descrição |
|---|---|
| [!UICONTROL Cabeçalho da seção] | Adicione um cabeçalho de seção para obter uma lista de componentes comuns. |
| [!UICONTROL Texto em linha única] | Adicione uma propriedade de texto de linha única. Ele é armazenado como uma string. |
| [!UICONTROL Texto multivalor] | Adicione uma propriedade de texto de vários valores. Ele é armazenado como uma matriz de sequência de caracteres. |
| [!UICONTROL Número] | Adicione um componente de número. |
| [!UICONTROL Data] | Adicione um componente de data. |
| [!UICONTROL Lista suspensa] | Adicione uma lista suspensa. |
| [!UICONTROL Tags padrão] | Adicionar uma tag. |
| [!UICONTROL Campo oculto] | Adicione um campo oculto. Ele é enviado como um parâmetro POST quando o ativo é salvo. |

### Edição de itens de formulário {#editing-form-items}

Para editar as propriedades dos itens de formulário, toque/clique no componente e edite todas ou um subconjunto das seguintes propriedades na **[!UICONTROL Configurações]** guia .

**[!UICONTROL Rótulo do campo]**: O nome da propriedade de metadados exibida na página de propriedades da pasta.

**[!UICONTROL Mapear para propriedade]**: Essa propriedade especifica o caminho relativo do nó da pasta no repositório CRX, onde é salva. Começa com &quot;**./**&quot;, que indica que o caminho está sob o nó da pasta.

A seguir estão os valores válidos para essa propriedade:

* `./jcr:content/metadata/dc:title`: Armazena o valor no nó de metadados da pasta como a propriedade `dc:title`.

* `./jcr:created`: Exibe a propriedade JCR no nó da pasta. Se você configurar essas propriedades no CRXDE, o Adobe recomenda marcá-las como Desativar edição, pois elas estão protegidas. Caso contrário, o erro &#39; `Asset(s) failed to modify`&#39; ocorre ao salvar as propriedades do ativo.

Para garantir que o componente seja exibido corretamente no formulário de esquema de metadados, não inclua um espaço no caminho da propriedade.

**[!UICONTROL Caminho JSON]**: Use-o para especificar o caminho do arquivo JSON, onde você especifica pares de valores chave para opções.

**[!UICONTROL Espaço reservado]**: Use essa propriedade para especificar o texto de espaço reservado relevante em relação à propriedade de metadados.

**[!UICONTROL Opções]**: Use essa propriedade para especificar opções em uma lista.

**[!UICONTROL Descrição]**: Use essa propriedade para adicionar uma breve descrição para o componente de metadados.

**[!UICONTROL Classe]**: Classe de objeto à qual a propriedade está associada.

## Excluir formulários de esquema de metadados da pasta {#delete-folder-metadata-schema-forms}

É possível excluir formulários de esquema de metadados de pastas da página Forms do Esquema de Metadados da Pasta. Para excluir um formulário, selecione-o e toque/clique no ícone Excluir na barra de ferramentas.

![delete_form](assets/delete_form.png)

## Atribuir um esquema de metadados de pasta {#assign-a-folder-metadata-schema}

Você pode atribuir um esquema de metadados de pasta a uma pasta na página Forms do Esquema de Metadados da Pasta ou ao criar uma pasta.

Se um esquema de metadados for configurado para uma pasta, o caminho para o formulário de esquema será armazenado no `folderMetadataSchema` propriedade do nó da pasta em .*/jcr:content*.

### Atribuir a um schema a partir da página Esquema de metadados da pasta {#assign-to-a-schema-from-the-folder-metadata-schema-page}

1. Toque/clique no botão [!DNL Experience Manager] logotipo e acesse **[!UICONTROL Ferramentas]** > **[!UICONTROL Ativos]** > **[!UICONTROL Esquemas de metadados da pasta]**.
1. Na página Forms do Esquema de metadados da pasta , selecione o formulário de esquema que deseja aplicar a uma pasta.
1. Na barra de ferramentas, toque/clique **[!UICONTROL Aplicar às pastas]**.

1. Selecione a pasta na qual aplicar o esquema e clique/toque em **[!UICONTROL Aplicar]**. Se um esquema de metadados já estiver aplicado na pasta, uma mensagem de aviso informará que você está prestes a substituir o esquema de metadados existente. Toque/clique **[!UICONTROL Substituir]**.
1. Abra as propriedades dos metadados da pasta na qual você aplicou o esquema de metadados.

   ![folder_properties](assets/folder_properties.png)

   Para exibir os campos de metadados da pasta, toque/clique na guia **[!UICONTROL Metadados da pasta]**.

   ![folder_metadata_properties](assets/folder_metadata_properties.png)

### Atribuir um schema ao criar uma pasta {#assign-a-schema-when-creating-a-folder}

Você pode atribuir um esquema de metadados de pasta ao criar uma pasta. Se pelo menos um esquema de metadados de pasta existir no sistema, uma lista extra será exibida no **[!UICONTROL Criar pasta]** caixa de diálogo. Você pode selecionar o schema desejado. Por padrão, nenhum esquema é selecionado.

1. No [!DNL Assets] interface do usuário, toque/clique **[!UICONTROL Criar]** na barra de ferramentas.
1. Especifique um título e nome para a pasta.
1. Na lista Esquema de metadados da pasta, selecione o esquema desejado. Em seguida, toque/clique em **[!UICONTROL Criar]**.

   ![select_schema](assets/select_schema.png)

1. Abra as propriedades dos metadados da pasta na qual você aplicou o esquema de metadados.
1. Para exibir os campos de metadados da pasta, toque/clique na guia **[!UICONTROL Metadados da pasta]**.

## Usar o esquema de metadados da pasta {#use-the-folder-metadata-schema}

Abra as propriedades de uma pasta configurada com um esquema de metadados de pasta. Uma guia **[!UICONTROL Metadados da pasta]** é exibida na página Propriedades da pasta. Para exibir o formulário de esquema de metadados da pasta, selecione essa guia.

Insira valores de metadados nos vários campos e toque/clique **[!UICONTROL Salvar]** para armazenar os valores. Os valores especificados são armazenados no nó folder no repositório CRX.

![folder_metadata_properties-1](assets/folder_metadata_properties-1.png)
