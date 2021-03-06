---
title: Digital Rights Management em [!DNL Adobe Experience Manager Assets].
description: Saiba como gerenciar estados de expiração de ativos e informações para ativos licenciados em [!DNL Experience Manager].
contentOwner: AG
feature: DRM,Gerenciamento de ativos
role: User,Admin
exl-id: 3eea4983-9dd5-4d69-ad93-3cd37a656d22
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '1433'
ht-degree: 6%

---

# Digital Rights Management por ativos {#digital-rights-management-in-assets}

Os ativos digitais geralmente são associados a uma licença que especifica os termos e a duração do uso. Como [!DNL Adobe Experience Manager Assets] é totalmente integrado à plataforma [!DNL Experience Manager], você pode gerenciar com eficiência as informações de expiração de ativos e os estados de ativos. Você também pode associar informações de licenciamento a ativos.

## Expiração do ativo {#asset-expiration}

A expiração de ativos é uma maneira eficaz de aplicar requisitos de licença para ativos. Ela garante que o ativo publicado não seja publicado quando expira, o que evita a possibilidade de qualquer violação de licença. Um usuário sem permissões de administrador não pode editar, copiar, mover, publicar e baixar um ativo expirado.

Você pode visualizar o status de expiração de um ativo no console [!DNL Assets] nas exibições de cartão e lista.

![expirado_flag_card](assets/expired_flag_card.png)

*Figura: Na exibição de cartão, um sinalizador no cartão indica ativo expirado.*

![lista_sinalizador_expirado](assets/expired_flag_list.png)

*Figura: Na exibição em lista, a   coluna Status exibe o   Expiredbanner.*

Você pode visualizar o status de expiração de um ativo na [!UICONTROL Linha do tempo] no painel esquerdo.

![chlimage_1-144](assets/chlimage_1-144.png)

>[!NOTE]
>
>A data de expiração de um ativo é exibida de forma diferente para usuários em fusos horários diferentes.

Você também pode visualizar o status de expiração dos ativos no painel **[!UICONTROL Referências]**. Ele gerencia status de expiração de ativos e relacionamentos entre ativos compostos e subativos, coleções e projetos referenciados.

1. Navegue até o ativo para o qual você deseja exibir as páginas da Web de referência e os ativos compostos.
1. Selecione o ativo e clique no logotipo [!DNL Experience Manager].

   ![chlimage_1-145](assets/chlimage_1-145.png)

1. Escolha **[!UICONTROL Referências]** no menu.

   ![chlimage_1-146](assets/chlimage_1-146.png)

   Para ativos expirados, o painel Referências exibe o status de expiração **[!UICONTROL Ativo expirado]** na parte superior.

   ![chlimage_1-147](assets/chlimage_1-147.png)

   Se o ativo tiver expirado os subativos, o painel Referências exibirá o status **[!UICONTROL Ativo tiver subativos expirados]**.

   ![chlimage_1-148](assets/chlimage_1-148.png)

### Pesquisar ativos expirados {#search-expired-assets}

Você pode pesquisar ativos expirados, incluindo subativos expirados no painel Pesquisar .

1. No console [!DNL Assets], clique em **[!UICONTROL Pesquisar]** na barra de ferramentas para exibir a caixa Omnisearch.

   ![chlimage_1-149](assets/chlimage_1-149.png)

1. Com o cursor na caixa Omnisearch, pressione a tecla Enter para exibir a página de resultados da pesquisa.

   ![chlimage_1-150](assets/chlimage_1-150.png)

1. Clique no logotipo [!DNL Experience Manager] para exibir o painel de pesquisa.

   ![chlimage_1-151](assets/chlimage_1-151.png)

1. Clique na opção **[!UICONTROL Status de expiração]** para expandi-la.

   ![chlimage_1-152](assets/chlimage_1-152.png)

1. Escolha **[!UICONTROL Expirado]**. Os ativos expirados são exibidos nos resultados da pesquisa.

   ![chlimage_1-153](assets/chlimage_1-153.png)

Ao escolher a opção **[!UICONTROL Expirado]**, o console [!DNL Assets] exibe somente os ativos e subativos expirados referenciados por ativos compostos. Os ativos compostos que fazem referência a subativos expirados não são exibidos imediatamente após a expiração dos subativos. Em vez disso, elas são exibidas depois que [!DNL Experience Manager] detecta que fazem referência a subativos expirados na próxima vez que o programador for executado.

Se você modificar a data de expiração de um ativo publicado para uma data anterior ao ciclo do programador atual, a programação ainda detectará esse ativo como um ativo expirado na próxima vez que ele for executado e refletirá seu status de acordo.

Além disso, se um erro ou falha impedir que o programador detecte ativos expirados no ciclo atual, o programador reexamina esses ativos no próximo ciclo e detecta seu status expirado.

Para permitir que o console [!DNL Assets] exiba os ativos compostos de referência junto com os subativos expirados, configure um fluxo de trabalho **[!UICONTROL Notificação de expiração do Adobe CQ DAM]** no [!DNL Experience Manager] Configuration Manager.

1. Abra o [!DNL Experience Manager] Configuration Manager.
1. Escolha **[!UICONTROL Notificação de expiração do Adobe CQ DAM]**. Por padrão, **[!UICONTROL Scheduler baseado em tempo]** é selecionado, o que agende uma tarefa para verificar em um horário específico se um ativo expirou em subativos. Após a conclusão do trabalho, os ativos que expiraram os subativos e os ativos referenciados são exibidos como expirados nos resultados da pesquisa.

   ![chlimage_1-154](assets/chlimage_1-154.png)

1. Para executar o trabalho periodicamente, desmarque o campo **[!UICONTROL Regra do agendador com base na hora]** e modifique o tempo em segundos no campo **[!UICONTROL Agendador periódico]**. Por exemplo, a expressão de exemplo &#39;0 0 0 &amp;ast; &amp;ast; ?&#39; aciona o trabalho às 00 horas.
1. Selecione **[!UICONTROL enviar email]** para receber emails quando um ativo expirar.

   >[!NOTE]
   >
   >Somente o criador de ativos (a pessoa que faz upload de um ativo específico para [!DNL Assets]) recebe um email quando o ativo expira. Consulte [como configurar a notificação por email](/help/sites-administering/notification.md) para obter detalhes adicionais sobre como configurar as notificações por email no nível [!DNL Experience Manager] geral.

1. No campo **[!UICONTROL Notificação prévia em segundos]** , especifique o tempo em segundos antes do tempo em que um ativo expira, quando você deseja receber uma notificação sobre a expiração. Se você for um administrador ou o criador do ativo, você receberá uma mensagem antes da expiração do ativo notificando que o ativo está prestes a expirar após o tempo especificado.

   Depois que o ativo expirar, você receberá outra notificação que confirma a expiração. Além disso, os ativos expirados são desativados.

1. Clique em **[!UICONTROL Salvar]**.

## Estados do ativo {#asset-states}

O console [!DNL Assets] pode exibir vários estados para ativos. Dependendo do estado atual de um ativo específico, sua exibição de cartão exibe um rótulo que descreve seu estado, por exemplo, Expirado, Publicado, Aprovado, Rejeitado e assim por diante.

1. Na interface do usuário [!DNL Assets], selecione um ativo.

   ![chlimage_1-155](assets/chlimage_1-155.png)

1. Clique em **[!UICONTROL Publicar]** na barra de ferramentas. Se não vir **Publicar** na barra de ferramentas, clique em **[!UICONTROL Mais]** na barra de ferramentas e localize a opção **[!UICONTROL Publicar]**.

   ![chlimage_1-156](assets/chlimage_1-156.png)

1. Escolha **[!UICONTROL Publish]** no menu e feche a caixa de diálogo de confirmação.
1. Sair do modo de seleção. O status da publicação do ativo é exibido na parte inferior da miniatura do ativo na exibição de cartão. Na exibição de lista, a coluna Publicado exibe o horário em que o ativo foi publicado.

   ![chlimage_1-157](assets/chlimage_1-157.png)

1. Para exibir a página Detalhes do ativo, na interface [!DNL Assets], selecione um ativo e clique em **[!UICONTROL Propriedades]**.

   ![chlimage_1-158](assets/chlimage_1-158.png)

1. Na guia Advanced , defina uma data de expiração para o ativo a partir do campo **[!UICONTROL Expires]**.

   ![definir data e hora de expiração do ativo no campo Expira](assets/chlimage_1-159.png)

   *Figura:   Guia Avançado em   Propriedade do ativo para definir a expiração do ativo.*

1. Clique em **[!UICONTROL Salvar]** e em **[!UICONTROL Fechar]** para exibir o console Ativo.
1. O status da publicação do ativo indica um status expirado na parte inferior da miniatura do ativo na exibição de cartão. Na exibição de lista, o status do ativo é exibido como **[!UICONTROL Expirado]**.

   ![chlimage_1-160](assets/chlimage_1-160.png)

1. No console [!DNL Assets], selecione uma pasta e crie uma tarefa de revisão na pasta.
1. Revise e aprove/rejeite os ativos na tarefa de revisão e clique em **[!UICONTROL Concluir]**.
1. Navegue até a pasta para a qual você criou a tarefa de revisão. O status dos ativos que você aprovou/rejeitou é exibido na parte inferior da exibição de cartão. Na exibição em lista, os status de aprovação e expiração são exibidos em colunas apropriadas.

   ![chlimage_1-161](assets/chlimage_1-161.png)

1. Para pesquisar ativos com base em seu status, clique em **[!UICONTROL Pesquisar]** para exibir a barra Omnisearch.

   ![chlimage_1-162](assets/chlimage_1-162.png)

1. Pressione return e clique em [!DNL Experience Manager] para exibir o painel de pesquisa.
1. No painel de pesquisa, clique em **[!UICONTROL Publicar status]** e selecione **[!UICONTROL Publicado]** para procurar ativos publicados em [!DNL Assets].

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. Clique em **[!UICONTROL Status de aprovação]** e clique na opção apropriada para procurar ativos aprovados ou rejeitados.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. Para pesquisar ativos com base no status de expiração, selecione **[!UICONTROL Status de expiração]** no painel Pesquisar e escolha a opção adequada.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Também é possível pesquisar ativos com base em uma combinação de status em vários aspectos de pesquisa. Por exemplo, você pode pesquisar ativos publicados que foram aprovados em uma tarefa de revisão e ainda não expiraram selecionando as opções apropriadas nos aspectos de pesquisa.

   ![chlimage_1-166](assets/chlimage_1-166.png)

## Digital Rights Management em [!DNL Assets] {#digital-rights-management-in-assets-1}

Esse recurso impõe a aceitação do contrato de licença antes que você possa baixar um ativo licenciado de [!DNL Adobe Experience Manager Assets].

Se você selecionar um ativo protegido e clicar em **[!UICONTROL Download]**, será redirecionado para uma página de licença para aceitar o contrato de licença. Se você não aceitar o contrato de licença, a opção **[!UICONTROL Download]** não estará disponível.

Se a seleção contiver vários ativos protegidos, selecione um ativo de cada vez, aceite o contrato de licença e continue para baixar o ativo.

Um ativo é considerado protegido se qualquer uma dessas condições for satisfeita:

* A propriedade de metadados do ativo `xmpRights:WebStatement` aponta para o caminho da página que contém o contrato de licença do ativo.
* O valor da propriedade de metadados do ativo `adobe_dam:restrictions` é um HTML bruto que especifica o contrato de licença.

>[!NOTE]
>
>O local `/etc/dam/drm/licenses` usado para armazenar licenças em versões anteriores de [!DNL Experience Manager] está obsoleto.
>
>Se você criar ou modificar páginas de licença ou as portas de versões anteriores [!DNL Experience Manager], o Adobe recomenda que você as armazene em `/apps/settings/dam/drm/licenses` ou `/conf/&ast;/settings/dam/drm/licenses`.

### Baixar ativos protegidos por DRM {#downloading-drm-assets}

1. Na exibição de cartão, selecione os ativos que deseja baixar e clique em **[!UICONTROL Download]**.
1. Na página **[!UICONTROL Gerenciamento de direitos autorais]**, selecione o ativo que deseja baixar na lista.
1. No painel [!UICONTROL Licença], escolha **[!UICONTROL Concordar]**. Uma marca de seleção aparece ao lado do ativo. Clique na opção **[!UICONTROL Download]**.

   >[!NOTE]
   >
   >A opção **[!UICONTROL Download]** só é ativada quando você opta por concordar com o contrato de licença de um ativo protegido. No entanto, se sua seleção incluir ativos protegidos e desprotegidos, somente os ativos protegidos serão listados no painel e a opção **[!UICONTROL Download]** será ativada para baixar os ativos desprotegidos. Para aceitar simultaneamente contratos de licença para vários ativos protegidos, selecione os ativos na lista e escolha **[!UICONTROL Concordar]**.

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. Na caixa de diálogo, clique em **[!UICONTROL Download]** para baixar o ativo ou suas representações.
