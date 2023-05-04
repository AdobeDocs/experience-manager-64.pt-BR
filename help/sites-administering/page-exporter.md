---
title: O exportador de página
seo-title: The Page Exporter
description: Saiba como usar o Exportador de página de AEM.
seo-description: Learn how to use the AEM Page Exporter.
uuid: 2ca2b8f1-c723-4e6b-8c3d-f5886cd0d3f1
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 6ab07b5b-ee37-4029-95da-be2031779107
exl-id: a5cb3b7b-d40f-4d86-8473-fb584f1d486c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 1%

---

# O exportador de página{#the-page-exporter}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

AEM permite exportar uma página como uma página da Web completa, incluindo imagens, arquivos .js e .css.

Após configurar a exportação, basta solicitar uma página no navegador, substituindo `html` com `export.zip` no URL e você obtém um download de arquivo zip contendo a página renderizada no formato html e os ativos referenciados. Todos os caminhos na página, por exemplo, caminhos para imagens, são reescritos para apontar para os arquivos incluídos no arquivo zip ou para os recursos no servidor.

## Exportar uma página {#exporting-a-page}

As etapas a seguir descrevem como exportar uma página e assumir que existe um modelo de configuração de exportação para o seu site. Um modelo de configuração define como uma página é exportada e é específica do site. Para criar um template de configuração, consulte [Criando uma Configuração de Exportador de Página para seu Site](#creating-a-page-exporter-configuration-for-your-site) seção.

Para exportar uma página:

1. No seu navegador, abra a página . Por exemplo:
1. `http://localhost:4502/content/geometrixx/en/products/triangle.html`
1. Abra a caixa de diálogo de propriedades da página e selecione o **Avançado** e expanda a **Exportar** conjunto de campos.

1. Clique no ícone de lente de aumento e selecione um template de configuração. Selecione o **geometrixx** , já que é o padrão para o site do Geometrixx. Clique em **OK**.

1. Clique em **OK** para fechar a caixa de diálogo de propriedades da página.
1. Solicite a página substituindo `html` com `export.zip` no URL.

1. Baixe o `<page-name>.export.zip` para seu sistema de arquivos.

1. No sistema de arquivos, descompacte o arquivo :

   * o arquivo html da página ( `<page-name>.html`) está disponível abaixo `<unzip-dir>/<page-path>`
   * outros recursos (arquivos .js, arquivos .css, imagens, ...) estão localizados de acordo com as configurações no modelo de exportação. Neste exemplo, alguns recursos estão abaixo `<unzip-dir>/etc`, alguns abaixo `<unzip-dir>/<page-path>`.

1. Abra o arquivo html da página ( `<unzip-dir>/<page-path>.html`) no navegador para verificar a renderização.

## Criando uma Configuração de Exportador de Página para seu Site {#creating-a-page-exporter-configuration-for-your-site}

O exportador de páginas é baseado na estrutura Content Sync . As configurações disponíveis na caixa de diálogo de propriedades da página são modelos de configuração. Eles definem todas as dependências necessárias para uma página. Quando uma exportação de página é acionada, o modelo de configuração é usado e o caminho da página e o caminho do design são aplicados dinamicamente à configuração. O arquivo zip é criado usando a funcionalidade de Sincronização de conteúdo padrão.

AEM incorpora alguns modelos, incluindo:

* Um padrão em `/etc/contentsync/templates/default`. Este modelo:

   * É o modelo de fallback quando nenhum modelo de configuração é encontrado no repositório.
   * Pode servir como base para um novo modelo de configuração.

* Uma dedicada à **Geometrixx** site, em `/etc/contentsync/templates/geometrixx`. Esse template pode ser usado como exemplo para criar um novo.

Para criar um modelo de configuração de exportador de página:

1. Em **CRXDE Lite**, crie um nó abaixo `/etc/contentsync/templates`:

   * Nome: por exemplo `mysite`. O nome aparece na caixa de diálogo de propriedades da página ao escolher o modelo de exportador de página.
   * Tipo: `nt:unstructured`

1. Abaixo do nó do modelo, chamado aqui `mysite`, crie uma estrutura de nó usando os nós de configuração descritos abaixo.

### Nós de configuração do exportador de página {#page-exporter-configuration-nodes}

O template de configuração consiste em uma estrutura de nó. Cada nó tem uma `type` que define uma ação específica no processo de criação do arquivo zip. Para obter mais detalhes sobre a propriedade type , consulte a seção Visão geral dos tipos de configuração na página Estrutura de sincronização de conteúdo .

Os nós a seguir podem ser usados para criar um template de configuração de exportação:

**nó de página** O nó da página é usado para copiar o html da página para o arquivo zip. Ela tem as seguintes características:

* É um nó obrigatório.
* Está localizado abaixo `/etc/contentsync/templates/<sitename>`.
* Seu nome é `page`.
* Seu tipo de nó é `nt:unstructured`

O `page` O nó tem as seguintes propriedades:

* A `type` propriedade definida com o valor `pages`.

* Não tem um `path` como o caminho da página atual é copiado dinamicamente para a configuração.

* As outras propriedades são descritas na seção Visão geral dos tipos de configuração da estrutura de Sincronização de conteúdo.

**reescrever nó** O nó rewrite define como os links são regravados na página exportada. Os links reescritos podem apontar para os arquivos incluídos no arquivo zip ou para os recursos no servidor.

Consulte a página Sincronização de conteúdo para obter uma descrição completa do `rewrite` nó .

**nó de design** O nó de design é usado para copiar o design usado para a página exportada. Ela tem as seguintes características:

* É opcional.
* Está localizado abaixo `/etc/contentsync/templates/<sitename>`.
* Seu nome é `design`.
* Seu tipo de nó é `nt:unstructured`.

O `design` O nó tem as seguintes propriedades:

* A `type` propriedade definida como valor `copy`.

* Não tem um `path` como o caminho da página atual é copiado dinamicamente para a configuração.

**nó genérico** Um nó genérico é usado para copiar recursos como arquivos clientlibs.js ou .css para o arquivo zip. Ela tem as seguintes características:

* É opcional.
* Está localizado abaixo `/etc/contentsync/templates/<sitename>`.
* Não tem um nome específico.
* Seu tipo de nó é `nt:unstructured`.
* Possui um `type` propriedade e qualquer `type` propriedades relacionadas, conforme definido na seção Visão geral dos tipos de configuração da estrutura de Sincronização de conteúdo .

Por exemplo, o nó de configuração a seguir copia os arquivos geometrixx clientlibs.js para o arquivo zip:

```xml
"geometrixx.clientlibs.js": {
    "extension": "js",
    "type": "clientlib",
    "path": "/etc/designs/geometrixx/clientlibs",
    "jcr:primaryType": "nt:unstructured"
}
```

O **Geometrixx** o modelo de configuração de exportação de página mostra como uma exportação de página pode ser configurada. Para exibir a estrutura do nó do modelo em seu navegador como formato json, solicite o seguinte URL:

`http://localhost:4502/etc/contentsync/templates/geometrixx.-1.json`

**Implementar uma configuração personalizada**

Como você pode ter notado na estrutura do nó, a variável **Geometrixx** o modelo de configuração de exportação de página tem um `logo` nó com um `type` propriedade definida como `image`. Este é um tipo de configuração especial que foi criado para copiar o logotipo da imagem para o arquivo zip. Para atender a alguns requisitos específicos, talvez seja necessário implementar um `type` propriedade: para fazer isso, consulte a seção Implementação de um manipulador de atualização personalizado na página Sincronização de conteúdo .

## Exportar uma página de forma programática {#programmatically-exporting-a-page}

Para exportar uma página de forma programática, você pode usar o [PageExporter](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) Serviço OSGI. Este serviço permite:

* Exportar uma página e gravar na resposta do servlet HTTP.
* Exporte uma página e salve o arquivo zip em um local específico.

O servlet vinculado ao `export` e o `zip` A extensão usa o serviço PageExporter.

## Resolução de problemas {#troubleshooting}

Se você tiver um problema com o download do arquivo zip, poderá excluir o `/var/contentsync` no repositório e envie a solicitação de exportação novamente.
