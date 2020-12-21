---
title: Configurar o cache de formulários adaptáveis
seo-title: Configurar o cache de formulários adaptáveis
description: 'O cache de formulários adaptáveis foi projetado especificamente para formulários e documentos adaptáveis. Armazena em cache formulários adaptáveis e documentos adaptáveis com o objetivo de reduzir o tempo necessário para renderizar um formulário ou documento adaptável no cliente. '
seo-description: 'O cache de formulários adaptáveis foi projetado especificamente para formulários e documentos adaptáveis. Armazena em cache formulários adaptáveis e documentos adaptáveis com o objetivo de reduzir o tempo necessário para renderizar um formulário ou documento adaptável no cliente. '
uuid: 3bd4e405-1eab-4e02-95cd-eb6ac25d18e3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: dd18f7b5-882d-4e81-ab3d-85f1e5d74992
translation-type: tm+mt
source-git-commit: 49b7cff2c1583ee1eb929434f27c1989558e197f
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 1%

---


# Configurar o cache de formulários adaptáveis {#configure-adaptive-forms-cache}

Um cache é um mecanismo para reduzir os tempos de acesso aos dados, reduzir a latência e melhorar as velocidades de entrada/saída (E/S). O cache de formulários adaptáveis armazena somente o conteúdo HTML e a estrutura JSON de um formulário adaptável sem salvar os dados pré-preenchidos. Ajuda a reduzir o tempo necessário para renderizar um formulário ou documento adaptável no cliente. Ele foi projetado especificamente para formulários adaptáveis e também suporta documentos adaptáveis.

>[!NOTE]
>
>Ao usar o cache de formulários adaptáveis, use o AEM Dispatcher para armazenar em cache as bibliotecas clientes (CSS e JavaScript) de um formulário ou documento adaptável.

>[!NOTE]
>
>Ao desenvolver componentes personalizados, no servidor usado para desenvolvimento, mantenha o cache de formulários adaptáveis desativado.

## Configurar o cache {#configure-the-cache}

Execute as seguintes etapas para configurar o cache de formulários adaptáveis:

1. Vá para AEM gerenciador de configuração do console da Web em `https://[server]:[port]/system/console/configMgr`.
1. Clique em **Configuração de Canais Web de Formulário Adaptável e Comunicação Interativa** para editar os valores de configuração.
1. Na caixa de diálogo editar valores de configuração, especifique o número máximo de formulários ou documentos que uma instância do servidor AEM Forms pode armazenar em cache no campo **Número de adaptáveis Forms**. O valor padrão é 100.

   >[!NOTE]
   >
   >Para desativar o cache, defina o valor no campo Número de adaptáveis Forms como **0**. O cache é redefinido e todos os formulários e documentos são removidos do cache quando você desativa ou altera a configuração do cache.

   ![Caixa de diálogo Configuração para formulários adaptáveis cache HTML](assets/cache-configuration-edit.png)

1. Clique em **Salvar** para salvar a configuração.

