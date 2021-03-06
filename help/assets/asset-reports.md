---
title: Relatórios sobre uso e compartilhamento de ativos digitais.
description: Relatórios sobre seus ativos em [!DNL Adobe Experience Manager Assets] que ajudam a entender o uso, a atividade e o compartilhamento dos ativos digitais.
contentOwner: AG
feature: Relatórios de ativos, Gerenciamento de ativos
role: User,Admin
exl-id: 6f03ee04-d2e2-47e6-892b-50fad3043a28
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 10%

---

# Relatórios de ativos {#asset-reports}

O relatório de ativos permite avaliar a utilidade da implantação [!DNL Adobe Experience Manager Assets]. Com [!DNL Assets], você pode gerar vários relatórios para seus ativos digitais. Os relatórios fornecem informações úteis sobre o uso do sistema, como os usuários interagem com ativos e quais ativos são baixados e compartilhados.

Use as informações nos relatórios para derivar as métricas principais de sucesso para medir a adoção de [!DNL Assets] em sua empresa e por clientes.

A estrutura de relatórios [!DNL Assets] usa tarefas [!DNL Sling] para processar de forma assíncrona solicitações de relatórios de maneira ordenada. É escalável para repositórios grandes. O processamento assíncrono de relatórios aumenta a eficiência e a velocidade com que os relatórios são gerados.

A interface de gerenciamento de relatórios é intuitiva e inclui opções e controles otimizados para acessar relatórios arquivados e visualizar status de execução de relatórios (sucesso, falha e enfileirado).

Quando um relatório é gerado, você é notificado por meio de um email (opcional) e uma notificação da caixa de entrada. Você pode exibir, baixar ou excluir um relatório da página de listagem de relatório, onde todos os relatórios gerados anteriormente são exibidos.

## Pré-requisitos {#prerequisite-for-reporting}

Para gerar relatórios, verifique se:

* Ative o serviço [!UICONTROL Day CQ DAM Event Recorder] de **[!UICONTROL Ferramentas]** > **[!UICONTROL Operações]** > **[!UICONTROL Console da Web]**.
* Selecione as atividades ou eventos sobre os quais deseja criar relatórios. Por exemplo, para gerar um relatório sobre ativos baixados, selecione [!UICONTROL Ativo baixado (BAIXADO)].

![Ativar relatórios de ativos no Console da Web](assets/reports-config-day-cq-dam-event-recorder.png)

## Gerar relatórios {#generate-reports}

[!DNL Experience Manager Assets] gera os seguintes relatórios padrão para você:

* Imagem
* Download
* Expiração
* Modificação
* Publicação
* [!DNL Brand Portal] Publicar
* Uso do disco
* Arquivos
* Compartilhamento de link

[!DNL Adobe Experience Manager] Os administradores do podem gerar e personalizar facilmente esses relatórios para sua implementação. Um administrador pode seguir estas etapas para gerar um relatório:

1. Na interface [!DNL Experience Manager], clique em **[!UICONTROL Ferramentas]** > **[!UICONTROL Ativos]** > **[!UICONTROL Relatórios]**.

   ![Página Ferramentas para navegar no relatório de ativos](assets/navigation.png)

1. Na página [!UICONTROL Relatórios de ativos], clique em **[!UICONTROL Criar]** na barra de ferramentas.
1. Na página **[!UICONTROL Criar relatório]**, escolha o relatório que deseja criar e clique em **[!UICONTROL Próximo]**.

   ![Selecionar tipo de relatório](assets/choose_report.png)

   >[!NOTE]
   >
   >Por padrão, os Fragmentos de conteúdo e os compartilhamentos de link são incluídos no ativo [!UICONTROL Relatório baixado]. Selecione a opção apropriada para criar um relatório de compartilhamentos de link ou excluir Fragmentos de conteúdo do relatório de download.

   >[!NOTE]
   >
   >O relatório [!UICONTROL Download] exibe detalhes apenas dos ativos que são selecionados individualmente e baixados ou baixados usando a Ação rápida. No entanto, não inclui os detalhes dos ativos que estavam dentro de uma pasta baixada.

1. Configure os detalhes do relatório, como título, descrição, miniatura e caminho da pasta no repositório CRX, onde o relatório é armazenado. Por padrão, o caminho da pasta é `/content/dam`. Você pode especificar um caminho diferente.

   ![Página para adicionar detalhes do relatório](assets/report_configuration.png)

   Escolha o intervalo de datas do seu relatório.

   Você pode optar por gerar o relatório agora ou em uma data e hora futuras.

   >[!NOTE]
   >
   >Se optar por agendar o relatório posteriormente, especifique a data e a hora nos campos Data e hora . Se você não especificar um valor, o mecanismo de relatório o tratará como um relatório que deve ser gerado instantaneamente.

   Os campos de configuração podem ser diferentes com base no tipo de relatório que você cria. Por exemplo, o relatório **[!UICONTROL Uso de disco]** fornece opções para incluir representações de ativos ao calcular o espaço em disco usado pelos ativos. Você pode optar por incluir ou excluir ativos em subpastas para o cálculo do uso do disco.

   >[!NOTE]
   >
   >O relatório **[!UICONTROL Uso de disco]** não inclui campos de intervalo de datas porque indica apenas o uso atual do espaço em disco.

   ![Página Detalhes do relatório de Uso de Disco](assets/disk_usage_configuration.png)

   Ao criar o relatório **[!UICONTROL Files]**, é possível incluir/excluir subpastas. No entanto, não é possível incluir representações de ativos para esse relatório.

   ![Página de detalhes do relatório Arquivos](assets/files_report.png)

   O relatório **[!UICONTROL Compartilhamento de links]** exibe URLs de ativos que são compartilhados com usuários externos a partir do [!DNL Assets]. Inclui IDs de email do usuário que compartilhou os ativos, IDs de email de usuários com os quais os ativos são compartilhados, data de compartilhamento e data de expiração do link. As colunas não são personalizáveis.

   O relatório **[!UICONTROL Compartilhamento de links]** não inclui opções para subpastas e representações porque apenas publica os URLs compartilhados que aparecem em `/var/dam/share`.

   ![Página de detalhes do relatório de Compartilhamento de links](assets/link_share.png)

1. Clique em **[!UICONTROL Avançar]** na barra de ferramentas.

1. Na página **[!UICONTROL Configurar colunas]**, algumas colunas são selecionadas para serem exibidas no relatório por padrão. Você pode selecionar mais colunas. Desmarque uma coluna selecionada para excluí-la do relatório.

   ![Selecionar ou desmarcar colunas de relatório](assets/configure_columns.png)

   Para exibir um nome de coluna ou caminho de propriedade personalizado, configure as propriedades do binário de ativo no nó `jcr:content` no CRX. Como alternativa, adicione-o por meio do seletor de caminho de propriedade.

   ![Selecionar ou desmarcar colunas de relatório](assets/custom_columns.png)

1. Clique em **[!UICONTROL Criar]** na barra de ferramentas. Uma mensagem notifica que a geração de relatório foi iniciada.
1. Na página [!UICONTROL Relatórios de Ativos], o status da geração de relatórios é baseado no estado atual do trabalho de relatório, por exemplo [!UICONTROL Sucesso], [!UICONTROL Falha], [!UICONTROL Em fila] ou [!UICONTROL Programado]. O mesmo status aparece na caixa de entrada de notificações.Para exibir a página do relatório, clique no link do relatório. Como alternativa, selecione o relatório e clique em **[!UICONTROL Exibir]** na barra de ferramentas.

   ![Um relatório gerado](assets/report_page.png)

   Clique em **[!UICONTROL Download]** na barra de ferramentas para baixar o relatório no formato CSV.

## Adicionar colunas personalizadas {#add-custom-columns}

Você pode adicionar colunas personalizadas aos seguintes relatórios para exibir mais dados para seus requisitos personalizados:

* Imagem
* Baixar
* Expiração
* Modificação
* Publicação
* [!DNL Brand Portal] Publicar
* Arquivos

Para adicionar colunas personalizadas a esses relatórios, siga estas etapas:

1. No [!DNL Manager interface], clique em **[!UICONTROL Ferramentas]** > **[!UICONTROL Ativos]** > **[!UICONTROL Relatórios]**.
1. Na página [!UICONTROL Relatórios de ativos], clique em **[!UICONTROL Criar]** na barra de ferramentas.

1. Na página **[!UICONTROL Criar relatório]**, escolha o relatório que deseja criar e clique em **[!UICONTROL Próximo]**.
1. Configure os detalhes do relatório, como título, descrição, miniatura, caminho da pasta e intervalo de datas, conforme aplicável.

1. Para exibir uma coluna personalizada, especifique o nome da coluna em **[!UICONTROL Colunas personalizadas]**.

   ![Especificar o nome da coluna personalizada do relatório](assets/custom_columns-1.png)

1. Adicione o caminho da propriedade no nó `jcr:content` no CRXDE usando o seletor de caminho de propriedade. Como alternativa, digite o caminho no campo do caminho da propriedade.

   ![Mapear o caminho da propriedade de caminhos em jcr:content](assets/property_picker.png)

   Como alternativa, digite o caminho no campo do caminho da propriedade.

   ![property_path](assets/property_path.png)

   Para adicionar mais colunas personalizadas, clique em **[!UICONTROL Adicionar]** e repita as etapas 5 e 6.

1. Clique em **[!UICONTROL Criar]** na barra de ferramentas. Uma mensagem notifica que a geração de relatório foi iniciada.

## Configurar o serviço de limpeza {#configure-purging-service}

Para remover relatórios que não são mais necessários, configure o serviço de Expurgação de relatórios do DAM no console da Web para limpar relatórios existentes com base em sua quantidade e idade.

1. Acesse o console da Web (gerenciador de configuração) em `https://[aem_server]:[port]/system/console/configMgr`.
1. Abra a configuração do **[!UICONTROL DAM Report Purge Service]**.
1. Especifique a frequência (intervalo de tempo) do serviço de limpeza no campo `scheduler.expression.name` . Você também pode configurar a idade e o limite de quantidade para os relatórios.
1. Salve as alterações.
