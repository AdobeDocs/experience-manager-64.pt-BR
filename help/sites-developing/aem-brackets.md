---
title: Extensão dos colchetes AEM
seo-title: Extensão dos colchetes AEM
description: 'null'
seo-description: 'null'
uuid: 2f0dfa42-eb34-44ae-90eb-b5f321c03b79
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 8231a30a-dcb7-4156-bb45-c5a23e5b56ef
translation-type: tm+mt
source-git-commit: 8e2bd579e4c5edaaf86be36bd9d81dfffa13a573
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 0%

---


# Extensão dos colchetes AEM{#aem-brackets-extension}

## Visão geral {#overview}

A Extensão de colchetes de AEM fornece um fluxo de trabalho suave para editar AEM componentes e bibliotecas clientes, e aproveita o poder do editor de códigos [do Brackets](https://brackets.io/) , que dá acesso de dentro do editor de código a arquivos e camadas do Photoshop. A sincronização fácil oferecida pela extensão (sem necessidade de Maven ou File Vault) aumenta a eficiência do desenvolvedor e também ajuda os desenvolvedores de front-end com conhecimento AEM limitado a participar de projetos. Essa extensão também oferece suporte para a Linguagem de modelo [HTML (HTL)](https://helpx.adobe.com/experience-manager/htl/user-guide.html), que elimina a complexidade do JSP para facilitar e proteger o desenvolvimento de componentes.

![chlimage_1-53](assets/chlimage_1-53.png)

### Recursos {#features}

Os principais recursos da Extensão de colchetes de AEM são:

* Sincronização automatizada de arquivos alterados para a instância de desenvolvimento AEM.
* Sincronização bidirecional manual de arquivos e pastas.
* Sincronização completa do pacote de conteúdo do projeto.
* Conclusão do código HTL para declarações de expressões e `data-sly-*` bloqueio.

Além disso, o Brackets vem com muitos recursos úteis para desenvolvedores AEM de fontes:

* Suporte a arquivos Photoshop para extrair informações de um arquivo PSD, como camadas, medidas, cores, fontes, textos etc.
* Dicas de código do PSD, para reutilizar facilmente essas informações extraídas no código.
* Suporte a pré-processador CSS, como LESS e SCSS.
* E centenas de extensões adicionais que cobrem necessidades mais específicas.

## Instalação {#installation}

### Colchetes {#brackets}

A extensão de suportes AEM suporta os suportes versão 1.0 ou superior.

Descarregue a versão mais recente do Brackets de [churrascos.io](https://brackets.io/).

### A extensão {#the-extension}

Para instalar a extensão, siga estas instruções:

1. Abra Colchetes. No menu **Arquivo**, selecione **Extension Manager...**
1. Digite **AEM** na barra de pesquisa e procure **AEM extensão** de colchetes.

   ![chlimage_1-54](assets/chlimage_1-54.png)

1. Clique em **Instalar**.
1. Feche a caixa de diálogo e a Extension Manager após a conclusão da instalação.

## Introdução {#getting-started}

### O projeto Content-Package {#the-content-package-project}

Depois que a extensão for instalada, você poderá start o desenvolvimento de componentes AEM abrindo uma pasta de pacote de conteúdo do seu sistema de arquivos com chaves.

O projeto deve conter pelo menos:

1. uma `jcr_root` pasta (por exemplo, `myproject/jcr_root`)

1. um `filter.xml` arquivo (por exemplo, `myproject/META-INF/vault/filter.xml`); para obter mais detalhes sobre a estrutura do `filter.xml` arquivo, consulte a definição [de Filtro da](https://jackrabbit.apache.org/filevault/filter.html)Workspace.

No menu **Arquivo** de colchetes, escolha **Abrir pasta...** e selecione a `jcr_root` pasta ou a pasta do projeto pai.

>[!NOTE]
>
>Se você não tiver um projeto próprio com um pacote de conteúdo, experimente o exemplo [](https://github.com/Adobe-Marketing-Cloud/aem-sightly-sample-todomvc)HTL TodoMVC. No GitHub, clique em **Baixar ZIP**, extraia os arquivos localmente e, conforme as instruções acima, abra a `jcr_root` pasta em Colchetes. Em seguida, siga as etapas abaixo para configurar as Configurações **do** projeto e, por fim, carregue o pacote inteiro para sua instância de desenvolvimento AEM, fazendo um Pacote **de conteúdo de** exportação, conforme instruído mais adiante na seção Sincronização completa do pacote de conteúdo.
>
>Após essas etapas, você deve ser capaz de acessar o `/content/todo.html` URL na instância de desenvolvimento AEM e pode fazer modificações no código no Brackets e ver como, depois de fazer uma atualização no navegador da Web, as alterações foram sincronizadas imediatamente no servidor AEM.

### Configurações do projeto {#project-settings}

Para sincronizar o conteúdo de e para uma instância de desenvolvimento AEM, é necessário definir as Configurações do projeto. Isso pode ser feito indo para o menu **AEM** e escolhendo Configurações **do projeto...**

![chlimage_1-55](assets/chlimage_1-55.png)

As Configurações do projeto permitem definir:

1. O URL do servidor (por exemplo, `http://localhost:4502`)
1. Tolerar servidores que não tenham um certificado HTTPS válido (mantenha desmarcado, a menos que necessário)
1. O nome de usuário usado para sincronizar conteúdo (por exemplo, `admin`)
1. A senha do usuário (por exemplo, `admin`)

## Sincronizando conteúdo {#synchronizing-content}

A Extensão de colchetes de AEM fornece os seguintes tipos de sincronização de conteúdo para arquivos e pastas permitidos pelas regras de filtragem definidas em `filter.xml`:

### Sincronização Automatizada De Arquivos Alterados {#automated-synchronization-of-changed-files}

Isso só sincronizará as alterações de Colchetes para a instância AEM, mas nunca o contrário.

### Sincronização bidirecional manual {#manual-bidirectional-synchronization}

No Project Explorer, abra o menu contextual clicando com o botão direito do mouse em qualquer arquivo ou pasta e as opções **Exportar para servidor** ou **Importar do servidor** podem ser acessadas.

![chlimage_1-56](assets/chlimage_1-56.png)

>[!NOTE]
>
>Se a entrada selecionada estiver fora da `jcr_root` pasta, as entradas do menu contextual **Exportar para servidor** e **Importar do servidor** serão desativadas.

### Sincronização completa do pacote de conteúdo {#full-content-package-synchronization}

No menu **AEM** , as opções **Exportar pacote** de conteúdo ou **Importar pacote** de conteúdo permitem sincronizar o projeto inteiro com o servidor.

![chlimage_1-57](assets/chlimage_1-57.png)

### Status da sincronização {#synchronization-status}

A Extensão de colchetes AEM apresenta um ícone de notificação na barra de ferramentas à direita da janela Colchetes, que indica o status da última sincronização:

* verde - todos os arquivos foram sincronizados com êxito
* azul - uma operação de sincronização está em andamento
* amarelo - alguns arquivos não foram sincronizados
* vermelho - nenhum dos arquivos foi sincronizado

Clicar no ícone de notificação abrirá a caixa de diálogo do relatório Status de sincronização que lista de todo o status de cada arquivo sincronizado.

![chlimage_1-58](assets/chlimage_1-58.png)

>[!NOTE]
>
>Somente o conteúdo marcado como incluído pelas regras de filtragem de `filter.xml` será sincronizado, independentemente do método de sincronização usado.
>
>Além disso, `.vltignore` os arquivos são suportados para excluir o conteúdo da sincronização para e do repositório.

## Edição do código HTL {#editing-htl-code}

A Extensão de suportes de AEM também apresenta alguns recursos de autocompletar para facilitar a escrita de atributos HTL e expressões.

### Autocompletar de atributo {#attribute-auto-completion}

1. Em um atributo HTML, digite `sly`. O atributo é preenchido automaticamente para `data-sly-`.
1. Selecione o atributo HTL na lista suspensa.

### Autocompletar de Expressão {#expression-auto-completion}

Em uma expressão `${}`, os nomes de variáveis comuns são preenchidos automaticamente.

## Mais informações {#more-information}

A AEM Brackets Extension é um projeto open-source, hospedado no GitHub pela organização da [Adobe Marketing Cloud](https://github.com/Adobe-Marketing-Cloud) , sob a licença do Apache, versão 2.0:

* Repositório de código: [https://github.com/Adobe-Marketing-Cloud/aem-sightly-brackets-extension](https://github.com/Adobe-Marketing-Cloud/aem-sightly-brackets-extension)
* Licença do Apache, versão 2.0: [https://www.apache.org/licenses/LICENSE-2.0.html](https://www.apache.org/licenses/LICENSE-2.0.html)

O editor de códigos do Brackets também é um projeto de código aberto, hospedado no GitHub pela organização da [Adobe Systems Incorporated](https://github.com/adobe) :

* Repositório de código: [https://github.com/adobe/brackets](https://github.com/adobe/brackets)

Sinta-se à vontade para contribuir!
