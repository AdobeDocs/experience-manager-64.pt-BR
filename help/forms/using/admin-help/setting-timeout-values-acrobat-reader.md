---
title: Configuração de valores de tempo limite para uso com as extensões do Acrobat Reader DC
seo-title: Setting timeout values for use with Acrobat Reader DC extensions
description: Saiba como definir valores de tempo limite para uso com extensões do Acrobat Reader DC.
seo-description: Learn how to set timeout values for use with Acrobat Reader DC extensions.
uuid: d6d072a0-0a30-417a-98b1-df8b4ff8f911
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a9aeeb89-45e9-4d5d-aa25-8145c89b64f2
exl-id: e7de9971-3eac-4248-8709-0da7dd709d1b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 3%

---

# Configuração de valores de tempo limite para uso com as extensões do Acrobat Reader DC  {#setting-timeout-values-for-use-with-acrobat-reader-dc-extensions}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Ao trabalhar em muitos arquivos PDF nas extensões do Acrobat Reader DC, verifique se os valores de tempo limite a seguir estão definidos adequadamente para evitar que as tarefas atinjam o tempo limite e falhem:

**Tempo Limite de Eliminação do Documento**

Esse valor pode ser definido no console de administração. Clique em Configurações > Configurações principais do sistema > Configurações e especifique um valor para o Tempo limite padrão de eliminação de documentos.

**O Gerenciador de usuários AEM o tempo limite dos formulários:** Esse valor pode ser definido editando o arquivo config.xml. No console de administração, clique em Configurações > Gerenciamento de usuários > Configuração > Importar e exportar arquivos de configuração e, em seguida, clique em Exportar. Abra o arquivo config.xml exportado e edite as seguintes linhas:

&lt;entry key=&quot;assertionValidityInMinutes&quot; value=&quot;600&quot;/>

&lt;entry key=&quot;SessionTimeout&quot; value=&quot;600&quot;/>

Salve e importe o arquivo config.xml de volta para o console de administração.

**Tempo limite da sessão do servidor de aplicativos:** Esse valor pode ser definido no servidor de aplicativos. Para obter mais informações, consulte a documentação fornecida com o servidor de aplicativos.
