---
title: Visão geral do serviço de saída
seo-title: Overview of output service
description: O Output permite unir dados de formulário XML a um design de formulário criado no Designer para criar um fluxo de saída de documento em vários formatos.
seo-description: Output lets you merge XML form data with a form design created in Designer to create a document output stream in various formats.
uuid: 7890b0a6-bae5-4ad5-ae41-503b988ba3da
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 5a96f5ea-6fe3-44b1-b314-14097b9e9c01
exl-id: 00ca8bdf-77be-4f4c-a3d3-d61d13eeba7e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 2%

---

# Visão geral do serviço de saída {#overview-of-output-service}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O Output permite unir dados de formulário XML a um design de formulário criado no Designer para criar um fluxo de saída de documento em vários formatos. O fluxo de saída pode ser enviado para uma impressora de rede, uma impressora local ou um arquivo de disco

Você pode usar a página Saída no console de administração para administrar o serviço Saída. As configurações definidas são usadas em tempo de execução quando as configurações equivalentes não foram especificadas por meio da API de formulários AEM. A configuração feita por meio do SDK dos formulários AEM substitui as configurações definidas por meio do console de administração.

Para obter mais informações sobre o serviço Saída, consulte [Referência de serviços](https://www.adobe.com/go/learn_aemforms_services_61).

Nas Páginas de saída no console de administração, é possível executar várias tarefas:

* Especifique conjuntos de caracteres para internacionalização. (Consulte [Alterar o conjunto de caracteres](/help/forms/using/admin-help/change-character-set.md#change-the-character-set).)
* Especifique caminhos absolutos e relativos para URLs, URIs, XCIs e locais de arquivos. (Consulte [Especificar locais de arquivo para saída](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).)
* Configure os tamanhos e as políticas do cache. (Consulte [Especificação do modo de cache](/help/forms/using/admin-help/configuring-caching-output.md#specifying-the-cache-mode) e [Definição das configurações de cache](/help/forms/using/admin-help/configuring-caching-output.md#configuring-cache-settings).)
* Disponibilizar fontes no servidor de aplicativos. (Consulte [Disponibilizar fontes](/help/forms/using/admin-help/make-fonts-available.md#make-fonts-available).)
* Especifique as fontes a serem incorporadas. (Consulte [Especificar fontes a serem incorporadas](/help/forms/using/admin-help/specify-fonts-embed.md#specify-fonts-to-embed).)
* Especifique as opções de configuração XCI. (Consulte [Especificar opções de configuração XCI](/help/forms/using/admin-help/specify-xci-configuration-options.md#specify-xci-configuration-options).)
* Especifique as configurações de segurança. (Consulte [Especificar configurações de segurança](/help/forms/using/admin-help/specify-security-settings.md#specify-security-settings).)

Depois de alterar as configurações, clique em Salvar para aplicá-las à Saída. Não é necessário reiniciar o servidor para que as alterações tenham efeito, mas talvez seja necessário reiniciar o serviço de saída ao definir as configurações de cache.
