---
title: Limpar registros do banco de dados do Gerenciador de Jobs
seo-title: Purge records from the Job Manager database
description: Dados de processos grandes podem resultar em desempenho de formulários de AEM mais baixo. É uma boa prática limpar dados do processo quando os registros não forem mais necessários.
seo-description: Large process data can result in lower AEM forms performance. It is good practice to purge process data when records are no longer necessary.
uuid: cf214498-36e9-4dcc-b4d4-e7c46f80dbab
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 69a406f2-4fa8-40bb-b671-7b0f5b6a2c4c
exl-id: be2e2a4b-5aac-4612-81b6-b4bbb3036d77
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 1%

---

# Limpar registros do banco de dados do Gerenciador de Jobs {#purge-records-from-the-job-manager-database}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Os dados de processo gerados quando um processo de longa duração é chamado podem se tornar muito grandes, resultando em menor desempenho AEM formulários e no uso de espaço em disco desnecessário. É uma boa prática limpar dados do processo quando os registros não forem mais necessários.

Você pode usar o console de administração para executar uma limpeza única de registros obsoletos ou para programar purgas automáticas regulares. Outros métodos para limpar registros obsoletos são discutidos em [Limpeza de dados do processo](/help/forms/using/admin-help/purging-process-data.md#purging-process-data).

**Acesse a página Agendador de limpeza de trabalhos**

1. No Console de administração, clique em Monitor de integridade no canto superior direito da página.
1. Clique na guia Agendador de limpeza de trabalhos .

As informações sobre quaisquer purgações programadas no momento são exibidas na caixa Informações do Programador de Expurgação da Tarefa.

>[!NOTE]
>
>Clicar em Parar Scheduler interrompe qualquer limpeza programada no futuro, mas não interrompe um trabalho de limpeza que já está em andamento.

**Programar uma limpeza única**

1. Selecione Apenas Uma Vez.
1. Na área Limpar filtros de registros concluídos , especifique o número de dias ou semanas após os quais um registro é considerado obsoleto e pronto para limpeza.

   >[!NOTE]
   >
   >Os registros relacionados a processos que não foram concluídos não são limpos, mesmo que sejam mais antigos que a idade especificada.

1. Especifique quando a limpeza ocorrerá. Marque a caixa de seleção Usar data e hora atuais ou desmarque a caixa de seleção e clique nos ícones de calendário e relógio para especificar a data e a hora em que a limpeza será realizada.

   >[!NOTE]
   >
   >Se você especificar a data e a hora de início no passado, a limpeza ocorre imediatamente ao clicar em Iniciar Scheduler.

1. Clique em Iniciar Scheduler. Todas as configurações do programador previamente agendadas são substituídas pelas novas configurações.

**Configurar uma programação de limpeza automática**

1. Selecione Receber a cada e especifique o número de dias ou semanas entre purgas.
1. Na área Limpar filtros de registros concluídos , especifique o número de dias ou semanas após os quais um registro é considerado obsoleto e pronto para limpeza. Não é possível definir o valor como `0`.

   >[!NOTE]
   >
   >Os registros relacionados a processos que não foram concluídos não são limpos, mesmo que sejam mais antigos que a idade especificada.

1. Especifique quando as purgas começarão. Marque a caixa de seleção Usar data e hora atuais ou desmarque a caixa de seleção e clique nos ícones de calendário e relógio para especificar a data e a hora em que a limpeza será realizada.

   >[!NOTE]
   >
   >Se você especificar a data e a hora de início no passado, AEM formulários calculará a data lógica de próximo início com base na data especificada. Por exemplo, se você agendar a limpeza do trabalho para ocorrer semanalmente a partir de 7 de abril, e agora será em 9 de abril, a primeira limpeza ocorrerá em 14 de abril.

1. Clique em Iniciar Scheduler. Todas as configurações do programador previamente agendadas são substituídas pelas novas configurações.
