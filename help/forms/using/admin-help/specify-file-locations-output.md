---
title: Especificar locais de arquivo para saída
seo-title: Specify file locations for Output
description: Saiba como especificar locais de arquivo para Saída.
seo-description: Learn how to specify file locations for Output.
uuid: 3287274f-85b5-4811-8abb-d347a9b80947
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 460bbb31-8187-469c-8102-b310093b6c03
exl-id: 5b8f04dd-6781-4126-8bb2-5d8b7a2f19c8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 4%

---

# Especificar locais de arquivo para saída {#specify-file-locations-for-output}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Você pode especificar os locais onde o Output procura determinados tipos de arquivos necessários.

1. No console de administração, clique em Serviços > saída.
1. Em Locais, especifique as opções apropriadas.
1. Clique em Salvar.

## Configurações de localizações {#locations-settings}

**URI raiz do conteúdo:** O URI ou o local absoluto do repositório do qual os formulários são recuperados. Esse valor é combinado com o parâmetro sForm, especificado por meio da API, para construir o caminho absoluto para o formulário que é recuperado. Esse valor pode referenciar um diretório ou um local da Web acessível por meio de HTTP.

O valor padrão é uma string vazia.

**Arquivo de configuração XCI:** O local relativo ou absoluto do arquivo de configuração XCI que o serviço de saída usa para renderização. Para um valor relativo, presume-se que o arquivo XCI reside no arquivo EAR AEM formulários implantáveis.

O valor padrão é `com/adobe/formServer/PA/pa_output.xci`.

**Localização do Cache:** Especifica o local do cache do disco de saída. Quando você altera essa configuração, todas as informações de cache existentes no local atual são redefinidas e um novo cache é criado no novo local. Selecione uma das seguintes opções:

**Localização padrão:** Esta é a seleção padrão. Quando essa opção é selecionada, o cache é criado em um local que depende do servidor de aplicativos que você está usando:

* **JBoss:** `[JBoss Home]\server\[install type]\svcdata\Output\Cache`
* **WebLogic:** `[WebLogic Home]\user_projects\domains\[aem-forms domain Name]\adobe\[forms server name]\Output\Cache`
* **WebSphere:** `[IBM Home]\WebSphere\AppServer\installedApps\adobe\server1\Output\Cache`

**Diretório Temp LC:** O cache é criado em um subdiretório do diretório temporário AEM forms, que é especificado no console de administração em Configurações > Configurações do sistema principal > Configurações > Localização do diretório Temp. O subdiretório é nomeado `adobeoutput_[servername]`.

>[!NOTE]
>
>Se você estiver usando um utilitário de limpeza temporária, esteja ciente de que, ao excluir esses diretórios, a funcionalidade não será afetada, isso pode afetar significativamente o desempenho por um curto período de tempo, até que o novo cache seja criado. Para evitar esse problema, não exclua esses diretórios enquanto limpa o diretório temporário dos formulários AEM.
