---
title: Disponibilizar fontes
seo-title: Make fonts available
description: Verifique se as fontes usadas em um formulário estão disponíveis para uso no servidor de aplicativos J2EE que hospeda formulários AEM.
seo-description: Ensure that the fonts used within a form are available for use on the J2EE application server hosting AEM forms.
uuid: 6588b4b6-f866-4253-91c8-3aa174340e8c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9f58a6c4-3190-49d4-800c-4a55dca7c296
exl-id: 33d63ec9-b100-48b4-b84d-a9de82c24f86
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 3%

---

# Disponibilizar fontes {#make-fonts-available}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Verifique se as fontes usadas em um formulário estão disponíveis para uso no servidor de aplicativos J2EE que hospeda formulários AEM. Por exemplo, considere o seguinte cenário. Um designer de formulário adiciona uma fonte ao diretório de fontes que o Designer usa e cria um formulário que usa essa fonte em um computador separado. Para que o serviço de Saída use a fonte, coloque-a no diretório de fontes do Cliente. Se o diretório de fontes do cliente não existir, crie um diretório no servidor de aplicativos J2EE que hospeda formulários AEM.

Para obter informações sobre configurações de fonte adicionais, consulte [Definir configurações gerais do AEM forms](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).

**Especifique o local do diretório de fontes do cliente**

1. No console de administração, clique em Configurações > Configurações dos sistemas principais > Configurações.
1. Na caixa Local do diretório Fontes do sistema , digite o caminho para o diretório Fontes do cliente . Vários diretórios podem ser adicionados, separados por ponto e vírgula **;**
1. Clique em OK.
1. Reinicie o sistema no qual o AEM forms está instalado.

>[!NOTE]
>
>As fontes são selecionadas do cache de fontes do sistema Windows e é necessário reiniciar o sistema para atualizar o cache. Depois de especificar o diretório de fontes do cliente, reinicie o sistema no qual AEM formulários está instalado.
