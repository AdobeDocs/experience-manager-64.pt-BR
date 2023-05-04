---
title: Exportar para CSV
seo-title: Export to CSV
description: Exportar informações sobre suas páginas para um arquivo CSV em seu sistema local
seo-description: Export information about your pages to a CSV file on your local system
uuid: aa03adac-bbfb-4566-a153-25fe6f6843dd
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: d4473758-674a-42d6-923a-b536f7f9c1f7
exl-id: 52eb9c2f-ce29-4622-8726-802ac40246d4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 51%

---

# Exportar para CSV  {#export-to-csv}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

**Criar exportação de arquivos CSV** O permite exportar informações sobre suas páginas para um arquivo CSV em seu sistema local.

* O arquivo baixado é chamado de `export.csv`
* Os conteúdos dependem das propriedades que você selecionar.
* É possível definir o caminho junto com o detalhamento da exportação.

>[!NOTE]
>
>O recurso para download e o destino padrão do seu navegador são usados.

O assistente Criar exportação de arquivos CSV permite selecionar:

* Propriedades a serem exportadas

   * Metadados

      * Modificado
      * Publicado
   * Analytics

      * Exibições da página
      * Visitantes únicos
      * Tempo na página


* Profundidade

   * Caminho pai
   * Apenas secundários diretos
   * Níveis adicionais de secundários
   * Níveis

O arquivo `export.csv` resultante pode ser aberto no Excel ou qualquer outro aplicativo compatível.

![chlimage_1-58](assets/chlimage_1-58.png)

A criação **Exportação de CSV** está disponível ao navegar pelo **Sites** console (na exibição de Lista): é uma opção do **Criar** menu suspenso:

![screen_shot_2018-03-21at154719](assets/screen_shot_2018-03-21at154719.png)

Para criar uma exportação de arquivos CSV:

1. Abra o console **Sites** e navegue até o local desejado, se necessário.
1. Na barra de ferramentas, selecione **Criar** then **Exportação de CSV** para abrir o assistente:

   ![screen_shot_2018-03-21at154758](assets/screen_shot_2018-03-21at154758.png)

1. Selecione as propriedades desejadas para exportar.
1. Selecione **Criar**.
