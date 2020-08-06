---
title: Suporte a novas localidades para localização de formulários adaptáveis
seo-title: Suporte a novas localidades para localização de formulários adaptáveis
description: A AEM Forms permite adicionar novas localidades para localizar formulários adaptativos. Por padrão, as localidades compatíveis são inglês, francês, alemão e japonês.
seo-description: A AEM Forms permite adicionar novas localidades para localizar formulários adaptativos. Por padrão, as localidades compatíveis são inglês, francês, alemão e japonês.
uuid: d4cee51b-c555-4544-9ae9-4aa8d38b2b17
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: e78f539a-109c-444c-8e52-be2260c3509f
translation-type: tm+mt
source-git-commit: c5a78d6c2b8a55cad6266e86e9b990cafc038431
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 0%

---


# Suporte a novas localidades para localização de formulários adaptáveis {#supporting-new-locales-for-adaptive-forms-localization}

## Sobre dicionários de localidades {#about-locale-dictionaries}

A localização de formulários adaptáveis depende de dois tipos de dicionários de localidade:

**Dicionário** específico do formulário Contém strings usadas em formulários adaptáveis. Por exemplo, rótulos, nomes de campos, mensagens de erro, descrições de ajuda e assim por diante. Ele é gerenciado como um conjunto de arquivos XLIFF para cada localidade e você pode acessá-lo em https://`<host>`:`<port>`/libs/cq/i18n/translator.html.

**Dicionários** globais Existem dois dicionários globais, gerenciados como objetos JSON, na biblioteca AEM cliente. Esses dicionários contêm mensagens de erro padrão, nomes de mês, símbolos de moeda, padrões de data e hora e assim por diante. Você pode encontrar esses dicionários no CRXDe Lite em /libs/fd/xfaforms/clientlibs/I18N. Esses locais contêm pastas separadas para cada localidade. Como os dicionários globais geralmente não são atualizados com frequência, a manutenção de arquivos JavaScript separados para cada localidade permite que os navegadores os armazenem em cache e reduzam o uso da largura de banda da rede ao acessar formulários adaptáveis diferentes no mesmo servidor.

### Como funciona a localização do formulário adaptável {#how-localization-of-adaptive-form-works}

Quando um formulário adaptável é renderizado, ele identifica a localidade solicitada, observando os seguintes parâmetros na ordem especificada:

* Parâmetro de solicitação `afAcceptLang`

   Para substituir a localidade do navegador dos usuários, é possível passar o parâmetro de `afAcceptLang` solicitação para forçar a localidade. Por exemplo, o URL a seguir forçará a renderização do formulário na localidade japonesa:

   `https://[*server*]:[*port*]/<*contextPath*>/<*formFolder*>/<*formName*>.html?wcmmode=disabled&afAcceptLang=ja`

* A localidade do navegador definida para o usuário, que é especificada na solicitação usando o `Accept-Language` cabeçalho.

* Configuração de idioma do usuário especificado em AEM.

Depois que a localidade é identificada, os formulários adaptativos escolhem o dicionário específico do formulário. Se o dicionário específico do formulário para a localidade solicitada não for encontrado, ele usará o dicionário inglês (en).

Se uma biblioteca do cliente para a localidade solicitada não existir, ela verificará se há uma biblioteca do cliente para o código de idioma presente na localidade. Por exemplo, se a localidade solicitada for `en_ZA` (inglês sul-africano) e a biblioteca do cliente para `en_ZA` não existir, o formulário adaptável usará a biblioteca do cliente para o idioma `en` (inglês), se existir. No entanto, se nenhum deles existir, o formulário adaptativo usará o dicionário para a `en` localidade.

## Adicionar suporte de localização para localidades não suportadas {#add-localization-support-for-non-supported-locales}

Atualmente, a AEM Forms suporta localização de conteúdo de formulários adaptáveis em inglês (en), espanhol (es), francês (fr), italiano (it), alemão (de), japonês (ja), português-brasileiro (pt-BR, chinês - (zh-CN), chinês-Taiwan (zh-TW) e coreano (ko-KR).

Para adicionar suporte para uma nova localidade em tempo de execução de formulários adaptáveis:

1. [Adicionar uma localidade ao serviço GuideLocalizationService](/help/forms/using/supporting-new-language-localization.md#p-add-a-locale-to-the-guide-localization-service-br-p)

1. [Adicionar biblioteca de cliente XFA para uma localidade](/help/forms/using/supporting-new-language-localization.md#p-add-xfa-client-library-for-a-locale-br-p)

1. [Adicionar biblioteca de cliente de formulário adaptável para uma localidade](/help/forms/using/supporting-new-language-localization.md#p-add-adaptive-form-client-library-for-a-locale-br-p)
1. [Adicionar suporte de localidade para o dicionário](/help/forms/using/supporting-new-language-localization.md#p-add-locale-support-for-the-dictionary-br-p)
1. [Reinicie o servidor](/help/forms/using/supporting-new-language-localization.md#p-restart-the-server-p)

### Adicionar uma localidade ao serviço de Localização do Guia {#add-a-locale-to-the-guide-localization-service-br}

1. Ir para `https://[server]:[port]/system/console/configMgr`.
1. Clique para editar o componente Serviço **de Localização do** Guia.
1. Adicione a localidade que deseja adicionar à lista de localidades compatíveis.

![GuideLocalizationService](assets/configservice.png)

### Adicionar biblioteca de cliente XFA para uma localidade {#add-xfa-client-library-for-a-locale-br}

Crie um nó do tipo `cq:ClientLibraryFolder` em `etc/<folderHierarchy>`, com categoria `xfaforms.I18N.<locale>`, e adicione os seguintes arquivos à biblioteca do cliente:

* **I18N.js** definindo `xfalib.locale.Strings` para o `<locale>` conforme definido em `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N`.

* **js.txt** contendo o seguinte:

```
/libs/fd/xfaforms/clientlibs/I18N/Namespace.js
I18N.js
/etc/clientlibs/fd/xfaforms/I18N/LogMessages.js
```

### Adicionar biblioteca de cliente de formulário adaptável para uma localidade {#add-adaptive-form-client-library-for-a-locale-br}

Crie um nó do tipo `cq:ClientLibraryFolder` em `etc/<folderHierarchy>`, com categoria como `guides.I18N.<locale>` e e dependências como `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` e `guide.common`. &quot;

Adicione os seguintes arquivos à biblioteca do cliente:

* **i18n.js** definindo `guidelib.i18n`, tendo padrões de &quot;calendáriosSímbolos&quot;, `datePatterns`, `timePatterns`, `dateTimeSymbols`, `numberPatterns`, `numberSymbols`, `currencySymbols`, `typefaces` para as especificações XFA `<locale>` [](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf)conforme as especificações deEspecificação deLocale Set. Você também pode ver como ele é definido para outras localidades compatíveis em `/etc/clientlibs/fd/af/I18N/fr/javascript/i18n.js`.

* **LogMessages.js** definindo `guidelib.i18n.strings` e `guidelib.i18n.LogMessages` para o `<locale>` conforme definido em `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js`.

* **js.txt** contendo o seguinte:

```
i18n.js
LogMessages.js
```

### Adicionar suporte de localidade para o dicionário {#add-locale-support-for-the-dictionary-br}

Execute essa etapa somente se o item `<locale>` que você está adicionando não estiver entre `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja``ko-kr`, .

1. Crie um `nt:unstructured` nó `languages` em `etc`, se ainda não estiver presente.

1. Adicione uma propriedade de string com vários valores `languages` ao nó, se ainda não estiver presente.
1. Adicione os valores de localidade `<locale>` padrão `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`, se ainda não estiver presente.

1. Adicione os valores `<locale>` da `languages` propriedade de `/etc/languages`.

O `<locale>` será exibido em `https://[server]:[port]/libs/cq/i18n/translator.html`.

### Restart the server {#restart-the-server}

Reinicie o servidor AEM para que a localidade adicionada entre em vigor.

## Amostra de bibliotecas para adicionar suporte ao espanhol {#sample-libraries-for-adding-support-for-spanish}

Amostra de bibliotecas de clientes para adicionar suporte para espanhol

[Obter arquivo](assets/sample.zip)
