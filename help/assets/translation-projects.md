---
title: Criação de projetos de tradução
description: Saiba como criar projetos de tradução no AEM.
contentOwner: AG
feature: Translation
role: Architect,Admin
exl-id: 1b931fef-eed0-4758-993d-cdf8d478fb6f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1975'
ht-degree: 23%

---

# Criação de projetos de tradução {#creating-translation-projects}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Para criar uma cópia de idioma, acione um dos seguintes fluxos de trabalho de cópia de idioma disponíveis no painel Referências na interface do usuário do Assets:

**Criar e traduzir**

Nesse fluxo de trabalho, os ativos a serem traduzidos são copiados para a raiz do idioma no qual você deseja traduzir. Além disso, dependendo das opções escolhidas, um projeto de tradução é criado para os ativos no console Projetos . Dependendo das configurações, o projeto de tradução pode ser iniciado manualmente ou pode ser executado automaticamente assim que o projeto de tradução for criado.

**Atualizar cópias de idioma**

Execute esse fluxo de trabalho para traduzir um grupo adicional de ativos e incluí-lo em uma cópia de idioma para uma localidade específica. Nesse caso, os ativos traduzidos são adicionados à pasta de destino que já contém os ativos traduzidos anteriormente.

>[!NOTE]
>
>Os binários de ativos são traduzidos somente se o provedor de serviços de tradução suportar a tradução de binários.

>[!NOTE]
>
>Se você iniciar um fluxo de trabalho de tradução para ativos complexos, como arquivos PDF e InDesign, seus subativos ou representações (se houver) não serão enviados para tradução.

## Criar e traduzir workflow {#create-and-translate-workflow}

Você usa o fluxo de trabalho Criar e traduzir para gerar cópias de idioma para um idioma específico pela primeira vez. O fluxo de trabalho fornece as seguintes opções:

* Criar somente estrutura
* Criar um novo projeto de tradução
* Adicionar ao projeto de tradução existente

### Criar somente estrutura {#create-structure-only}

Use a opção **Somente criar estrutura** para criar uma hierarquia de pasta de destino na raiz do idioma de destino para corresponder à hierarquia da pasta de origem na raiz do idioma de origem. Nesse caso, os ativos de origem são copiados na pasta de destino. No entanto, nenhum projeto de tradução é gerado.

1. Na interface do usuário do Assets, selecione a pasta de origem para a qual deseja criar uma estrutura na raiz do idioma de destino.
1. Abra o painel **[!UICONTROL Referências]** e clique/toque em **[!UICONTROL Cópias de idioma]**, em **[!UICONTROL Cópias]**.

   ![chlimage_1-57](assets/chlimage_1-57.png)

1. Clicar/tocar **[!UICONTROL Criar e traduzir]** na parte inferior.

   ![chlimage_1-58](assets/chlimage_1-58.png)

1. No **[!UICONTROL Idiomas de destino]** selecione o idioma para o qual deseja criar uma estrutura de pastas.

   ![chlimage_1-59](assets/chlimage_1-59.png)

1. Na lista **[!UICONTROL Projeto]**, escolha **[!UICONTROL Somente criar estrutura]**.

   ![chlimage_1-60](assets/chlimage_1-60.png)

1. Clique/toque em **[!UICONTROL Criar]**. A nova estrutura para o idioma de destino está listada em **[!UICONTROL Cópias de idioma]**.

   ![chlimage_1-61](assets/chlimage_1-61.png)

1. Clique/toque na estrutura da lista e, em seguida, clique/toque em **[!UICONTROL Receita em ativos]** para navegar até a estrutura de pastas no idioma de destino.

   ![chlimage_1-62](assets/chlimage_1-62.png)

### Criar um novo projeto de tradução {#create-a-new-translation-project}

Se você usar essa opção, os ativos a serem traduzidos serão copiados para a raiz do idioma no qual deseja traduzir. Dependendo das opções escolhidas, um projeto de tradução é criado para os ativos no console Projetos . Dependendo das configurações, o projeto de tradução pode ser iniciado manualmente ou executado automaticamente assim que o projeto de tradução for criado.

1. Na interface do usuário do Assets, selecione a pasta de origem para a qual deseja criar uma cópia de Idioma.
1. Abra o painel **[!UICONTROL Referências]** e clique/toque em **[!UICONTROL Cópias de idioma]**, em **[!UICONTROL Cópias]**.

   ![chlimage_1-63](assets/chlimage_1-63.png)

1. Clicar/tocar **[!UICONTROL Criar e traduzir]** na parte inferior.

   ![chlimage_1-64](assets/chlimage_1-64.png)

1. Na lista **[!UICONTROL Idiomas de destino]**, selecione os idiomas para os quais deseja criar uma estrutura de pastas.

   ![chlimage_1-65](assets/chlimage_1-65.png)

1. No **[!UICONTROL Projeto]** lista, selecione **[!UICONTROL Criar um novo projeto de tradução]**.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. No campo **[!UICONTROL Título do projeto]**, informe um título para o projeto.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Clicar/tocar em **[!UICONTROL Criar]**. Os ativos da pasta de origem são copiados para as pastas de destino das localidades selecionadas na etapa 4.

   ![chlimage_1-68](assets/chlimage_1-68.png)

1. Para navegar até a pasta, selecione a cópia de idioma e clique em **[!UICONTROL Receita em ativos]**.

   ![chlimage_1-69](assets/chlimage_1-69.png)

1. Navegue até o console Projetos . A pasta de tradução é copiada para o console Projetos .

   ![chlimage_1-70](assets/chlimage_1-70.png)

1. Abra a pasta para exibir o projeto de tradução.

   ![chlimage_1-71](assets/chlimage_1-71.png)

1. Clique/toque no projeto para abrir a página de detalhes.

   ![chlimage_1-72](assets/chlimage_1-72.png)

1. Para exibir o status do trabalho de tradução, clique nas reticências na parte inferior do **[!UICONTROL Tarefa de tradução]** mosaico.

   ![chlimage_1-73](assets/chlimage_1-73.png)

   Para obter mais detalhes sobre os status da tarefa, consulte [Monitorar o status de um trabalho de tradução](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job).

1. Navegue até a interface do usuário do Assets e abra a página Propriedades de cada um dos ativos traduzidos para exibir os metadados traduzidos.

   ![chlimage_1-74](assets/chlimage_1-74.png)

   >[!NOTE]
   >
   >Esse recurso está disponível para ativos e pastas. Quando um ativo é selecionado em vez de uma pasta, toda a hierarquia de pastas na raiz do idioma é copiada para criar uma cópia de idioma para o ativo.

### Adicionar ao projeto de tradução existente {#add-to-existing-translation-project}

Se você usar essa opção, o fluxo de trabalho de tradução será executado para ativos que você adicionar à pasta de origem após executar um fluxo de trabalho de tradução anterior. Somente os ativos recém-adicionados são copiados para a pasta de destino que contém ativos traduzidos anteriormente. Nenhum novo projeto de tradução é criado neste caso.

1. Na interface do usuário do Assets, navegue até a pasta de origem que contém ativos não traduzidos.
1. Selecione um ativo que deseja traduzir e abra o **[!UICONTROL painel Referência]**. A seção **[!UICONTROL Cópias de idioma]** exibe o número de cópias de tradução atualmente disponíveis.
1. Clique/toque em **[!UICONTROL Cópias de idioma]** em **[!UICONTROL Cópias]**. Uma lista de cópias de tradução disponíveis é exibida.
1. Clicar/tocar **[!UICONTROL Criar e traduzir]** na parte inferior.

   ![chlimage_1-75](assets/chlimage_1-75.png)

1. Na lista **[!UICONTROL Idiomas de destino]**, selecione os idiomas para os quais deseja criar uma estrutura de pastas.

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Na lista **[!UICONTROL Projeto]**, selecione **[!UICONTROL Adicionar ao projeto de tradução existente]** para executar o fluxo de trabalho de tradução na pasta.

   ![chlimage_1-77](assets/chlimage_1-77.png)

   >[!NOTE]
   >
   >Se você escolher a variável **[!UICONTROL Adicionar ao projeto de tradução existente]** , seu projeto de tradução será adicionado a um projeto pré-existente somente se as configurações do projeto corresponderem exatamente às configurações do projeto pré-existente. Caso contrário, um novo projeto será criado.

1. No **[!UICONTROL Projeto de tradução existente]** selecione um projeto para adicionar o ativo para tradução.

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Clique/toque em **[!UICONTROL Criar]**. Os ativos que serão traduzidos são adicionados à pasta de destino. A pasta atualizada está listada na seção **[!UICONTROL Cópias de idioma]**.

   ![chlimage_1-79](assets/chlimage_1-79.png)

1. Navegue até o console Projetos e abra o projeto de tradução existente que você adicionou.
1. Clique/toque em projeto de tradução para exibir a página de detalhes do projeto.

   ![chlimage_1-80](assets/chlimage_1-80.png)

1. Clique/toque nas reticências na parte inferior da **Tarefa de tradução** bloco para exibir os ativos no fluxo de trabalho de tradução. A lista de tarefas de tradução também exibe entradas para metadados e tags de ativos. Essas entradas indicam que metadados e tags de ativos também são traduzidos.

   >[!NOTE]
   >
   >Se você excluir a entrada para tags ou metadados, nenhuma tag ou metadados é traduzido para qualquer um dos ativos.

   >[!NOTE]
   >
   >Se você usar Tradução automática, os binários de ativos não serão traduzidos.

   >[!NOTE]
   >
   >Se o ativo adicionado ao trabalho de tradução incluir subativos, selecione os subativos e remova-os para que a tradução continue sem falhas.

1. Para iniciar a tradução dos ativos, clique/toque na seta na **[!UICONTROL Tarefa de tradução]** bloco e selecione **[!UICONTROL Iniciar]** na lista.

   ![chlimage_1-81](assets/chlimage_1-81.png)

   Uma mensagem notifica o início do trabalho de tradução.

   ![chlimage_1-82](assets/chlimage_1-82.png)

1. Para exibir o status do trabalho de tradução, clique/toque nas reticências na parte inferior do **[!UICONTROL Tarefa de tradução]** mosaico.

   ![chlimage_1-83](assets/chlimage_1-83.png)

   Para obter mais detalhes, consulte [Monitorar o status de um trabalho de tradução](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job).

1. Após a conclusão da tradução, o status é alterado para Pronto para revisar. Navegue até a interface do usuário do Assets e abra a página Propriedades de cada um dos ativos traduzidos para exibir os metadados traduzidos.

## Atualizar cópias de idioma {#update-language-copies}

Execute esse fluxo de trabalho para traduzir qualquer conjunto adicional de ativos e incluí-lo em uma cópia de idioma para uma localidade específica. Nesse caso, os ativos traduzidos são adicionados à pasta de destino que já contém os ativos traduzidos anteriormente. Dependendo da escolha de opções, um projeto de tradução é criado ou um projeto de tradução existente é atualizado para os novos ativos. O fluxo de trabalho Atualizar cópias de idioma inclui as seguintes opções:

* Criar um novo projeto de tradução
* Adicionar ao projeto de tradução existente

### Criar um novo projeto de tradução {#create-a-new-translation-project-1}

Se você usar essa opção, um projeto de tradução será criado para o conjunto de ativos para os quais deseja atualizar uma cópia de idioma.

1. Na interface do usuário do Assets, selecione a pasta de origem onde você adicionou um ativo.
1. Abra o painel **[!UICONTROL Referências]** e clique/toque em **[!UICONTROL Cópias de idioma]** em **[!UICONTROL Cópias]** para exibir a lista de cópias de idioma.
1. Marque a caixa de seleção ao lado de **[!UICONTROL Cópias de idioma]** e selecione a pasta de destino correspondente ao local adequado.

   ![chlimage_1-84](assets/chlimage_1-84.png)

1. Clicar/tocar **[!UICONTROL Atualizar cópias de idioma]** na parte inferior.

   ![chlimage_1-85](assets/chlimage_1-85.png)

1. No **[!UICONTROL Projeto]** listar, escolha **[!UICONTROL Criar um novo projeto de tradução]**.

   ![chlimage_1-86](assets/chlimage_1-86.png)

1. No campo **[!UICONTROL Título do projeto]**, informe um título para o projeto.

   ![chlimage_1-87](assets/chlimage_1-87.png)

1. Clique/toque em **[!UICONTROL Iniciar]**.
1. Navegue até o console Projetos . A pasta de tradução é copiada para o console Projetos .

   ![chlimage_1-88](assets/chlimage_1-88.png)

1. Abra a pasta para exibir o projeto de tradução.

   ![chlimage_1-89](assets/chlimage_1-89.png)

1. Clique/toque no projeto para abrir a página de detalhes.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Para iniciar a tradução dos ativos, clique na seta na **[!UICONTROL Tarefa de tradução]** bloco e selecione **[!UICONTROL Iniciar]** na lista.

   ![chlimage_1-91](assets/chlimage_1-91.png)

   Uma mensagem notifica o início do trabalho de tradução.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. Para exibir o status do trabalho de tradução, clique/toque nas reticências na parte inferior do **[!UICONTROL Tarefa de tradução]** mosaico.

   ![chlimage_1-93](assets/chlimage_1-93.png)

   Para obter mais detalhes sobre os status da tarefa, consulte [Monitorar o status de um trabalho de tradução](../sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job).

1. Navegue até a interface do usuário do Assets e abra a página Propriedades de cada um dos ativos traduzidos para exibir os metadados traduzidos.

### Adicionar ao projeto de tradução existente {#add-to-existing-translation-project-1}

Se você usar essa opção, o conjunto de ativos será adicionado a um projeto de tradução existente para atualizar a cópia de idioma para o local escolhido.

1. Na interface do usuário do Assets, selecione a pasta de origem na qual você adicionou uma pasta de ativos.
1. Abra o painel **[!UICONTROL Referências]** e clique/toque em **[!UICONTROL Cópias de idioma]** em **[!UICONTROL Cópias]** para exibir a lista de cópias de idioma.

   ![chlimage_1-94](assets/chlimage_1-94.png)

1. Marque a caixa de seleção ao lado de **[!UICONTROL Cópias de idioma]**, que seleciona todas as cópias de idioma. Desmarque as outras cópias, exceto a cópia de idioma (cópias) correspondente às localidades para as quais você deseja traduzir.

   ![chlimage_1-95](assets/chlimage_1-95.png)

1. Clicar/tocar **[!UICONTROL Atualizar cópias de idioma]** na parte inferior.

   ![chlimage_1-96](assets/chlimage_1-96.png)

1. No **[!UICONTROL Projeto]** listar, escolha **[!UICONTROL Adicionar ao projeto de tradução existente]**.

   ![chlimage_1-97](assets/chlimage_1-97.png)

1. No **[!UICONTROL Projeto de tradução existente]** selecione um projeto para adicionar o ativo para tradução.

   ![chlimage_1-98](assets/chlimage_1-98.png)

1. Clique/toque em **[!UICONTROL Iniciar]**.
1. Veja as etapas 9 a 14 de [Adicionar ao projeto de tradução existente](translation-projects.md#add-to-existing-translation-project) completar o resto do procedimento.

## Criação de cópias temporárias de idioma {#creating-temporary-language-copies}

Quando você executa um fluxo de trabalho de tradução para atualizar uma cópia de idioma com as versões editadas dos ativos originais, a cópia de idioma existente é preservada até que você aprove o(s) ativo(s) traduzido(s). [!DNL Experience Manager] Os ativos armazenam o(s) ativo(s) recém-traduzido(s) em um local temporário e atualizam a cópia de idioma existente após você aprovar explicitamente o(s) ativo(s). Se você rejeitar o(s) ativo(s), a cópia de idioma permanecerá inalterada.

1. Clique/toque na pasta raiz de origem, em **[!UICONTROL Cópias de idioma]**, para as quais você já criou uma cópia de idioma e clique/toque em **[!UICONTROL Revelar no Assets]** para abrir a pasta nos Assets.[!DNL Experience Manager]

   ![chlimage_1-99](assets/chlimage_1-99.png)

1. Na interface do usuário do Assets, selecione um ativo já traduzido e clique/toque no **[!UICONTROL Editar]** ícone na barra de ferramentas para abrir o ativo no modo de edição.

   ![chlimage_1-100](assets/chlimage_1-100.png)

1. Edite o ativo e salve as alterações.
1. Execute as etapas 2 a 14 do [Adicionar ao projeto de tradução existente](#add-to-existing-translation-project) procedimento para atualizar a cópia de idioma.
1. Clique/toque nas reticências na parte inferior da **[!UICONTROL Tarefa de tradução]** mosaico. Na lista de ativos na **[!UICONTROL Tarefa de tradução]** , você pode exibir claramente o local temporário onde a versão traduzida do ativo é armazenada.

   ![chlimage_1-101](assets/chlimage_1-101.png)

1. Marque a caixa de seleção ao lado de **[!UICONTROL Título]**.
1. Na barra de ferramentas, clique/toque em **[!UICONTROL Aceitar tradução]** e em **[!UICONTROL Aceitar]** na caixa de diálogo para substituir o ativo traduzido na pasta de destino pela versão traduzida do ativo editado.

   ![chlimage_1-102](assets/chlimage_1-102.png)

   >[!NOTE]
   >
   >Para permitir que o fluxo de trabalho de tradução atualize o(s) ativo(s) de destino, aceite o ativo e os metadados.

   Clicar/tocar **[!UICONTROL Rejeitar tradução]** para reter a versão traduzida originalmente do ativo na raiz da localidade de destino e rejeitar a versão editada.

   ![chlimage_1-103](assets/chlimage_1-103.png)

1. Navegue até o console Assets e abra a página Propriedades de cada um dos ativos traduzidos para exibir os metadados traduzidos.

Para obter dicas sobre como traduzir metadados para ativos com eficiência, consulte esta página arquivada sobre [5 etapas para traduzir metadados com eficiência](https://web.archive.org/web/20181217033517/https://blogs.adobe.com/experiencedelivers/experience-management/translate_aemassets_metadata/).
