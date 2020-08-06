---
title: Compartilhar pastas do AEM Assets com o Creative Cloud
description: Configuração e práticas recomendadas para permitir que usuários do Adobe Experience Manager Assets troquem pastas de ativos com usuários do Adobe Creative Cloud.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 501a6c470113d249646f4424a19ee215a82b032d
workflow-type: tm+mt
source-wordcount: '1057'
ht-degree: 0%

---


# Práticas recomendadas de compartilhamento de pastas de AEM para Creative Cloud {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>O recurso AEM para compartilhamento de pasta do Creative Cloud está obsoleto. A Adobe recomenda usar recursos mais recentes, como o [Adobe Asset Link](https://helpx.adobe.com/br/enterprise/using/adobe-asset-link.html) ou [AEM aplicativo](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html)para desktop. Saiba mais sobre as práticas [recomendadas de integração de](/help/assets/aem-cc-integration-best-practices.md)AEM e Creative Cloud.

O Adobe Experience Manager (AEM) pode ser configurado para permitir que os usuários do AEM Assets compartilhem pastas com usuários do Creative Cloud, de modo que eles estejam disponíveis como pastas compartilhadas no serviço Creative Cloud Assets. O recurso pode ser usado para trocar arquivos entre equipes de criação e usuários do AEM Assets, especialmente quando os usuários criativos não têm acesso à instância do AEM Assets (eles não estão na rede corporativa).

Esse tipo de integração pode ser usado em ambos os casos de uso, especialmente ao trabalhar com usuários que não têm acesso direto ao AEM Assets:

* Compartilhamento de um conjunto de ativos específicos da AEM Assets com usuários de Creative Cloud Files (por exemplo, um resumo criativo e um conjunto de ativos aprovados para o trabalho de design de uma nova atividade de marketing)
* Recebendo novos arquivos de usuários do Creative Cloud.

>[!NOTE]
>
>Antes de ler este documento, você pode analisar as práticas [recomendadas gerais de integração de](aem-cc-integration-best-practices.md) AEM e Creative Cloud para obter uma visão geral de nível superior do tópico.

## Visão geral {#overview}

O compartilhamento de pastas AEM para o Creative Cloud depende do compartilhamento de pastas e arquivos no servidor entre as contas AEM Assets e Creative Cloud. Os profissionais criativos, que usam o aplicativo desktop Creative Cloud em seus desktops, podem disponibilizar as pastas compartilhadas diretamente em seus discos usando a tecnologia Adobe CreativeSync.

O diagrama a seguir fornece uma visão geral da integração.

![chlimage_1-406](assets/chlimage_1-406.png)

A integração inclui os seguintes elementos:

* **Servidor** AEM Assets implantado na rede corporativa (serviços gerenciados ou no local): O compartilhamento de pastas é iniciado aqui.
* **Serviço** principal do Adobe Marketing Cloud Assets: Atua como intermediário entre os serviços de armazenamento e AEM. O administrador da empresa que usa a integração precisa estabelecer uma relação de confiança entre a organização do Marketing Cloud e a instância do AEM Assets. Eles também [definem uma lista de colaboradores](https://docs.adobe.com/content/help/en/core-services/interface/assets/t-admin-add-cc-user.html)aprovados para Creative Cloud, que os usuários da AEM Assets também podem compartilhar pastas para segurança adicional.
* **Serviços** da Web do Creative Cloud Assets (UI da Web de arquivos de armazenamento e Creative Cloud): É aqui que usuários Creative Cloud específicos, com os quais uma pasta AEM Assets foi compartilhada, poderão aceitar o convite e ver a pasta em seu armazenamento de conta Creative Cloud.
* **Aplicativo** para desktop Creative Cloud: (Opcional) Permite acesso direto a pastas/arquivos compartilhados da área de trabalho do usuário criativo por meio da sincronização com o armazenamento Creative Cloud Assets.

## Características e limitações {#characteristics-and-limitations}

* **Propagação unidirecional das alterações:** As alterações de arquivo são propagadas em uma única direção - do sistema (AEM ou Creative Cloud Assets), onde o ativo foi criado originalmente (carregado). A integração não fornece uma sincronização bidirecional totalmente automatizada entre os dois sistemas.

* **Versões:**

   * AEM cria somente versões de um ativo em atualizações se o arquivo tiver se originado em AEM e for atualizado lá.
   * O Creative Cloud Assets fornece seu próprio recurso [de](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html) controle de versão direcionado para atualizações do Work in Progress (basicamente, armazena atualizações por até 10 dias)

* **Limitações de espaço:** Os tamanhos e volumes de arquivos trocados são limitados pela cota [específica do](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) Creative Cloud Assets para usuários criativos (depende do nível de subscrição) e por uma limitação de 5 GB do tamanho máximo do arquivo. O espaço é adicionalmente limitado pela cota de ativos que a organização tem no serviço principal do Adobe Marketing Cloud Assets.

* **Requisitos de espaço:** Os arquivos em pastas compartilhadas também precisam ser armazenados fisicamente em AEM e, em seguida, na conta do Creative Cloud, com uma cópia em cache no serviço principal dos Ativos do Marketing Cloud.
* **Rede e largura de banda:** Os arquivos em pastas compartilhadas e todas as atualizações precisam ser transportados pela rede entre os sistemas. Você deve garantir que somente os arquivos e as atualizações relevantes sejam compartilhados.
* **Tipo** de pasta: Não há suporte para o compartilhamento de uma pasta Assets do tipo `sling:OrderedFolder`. Se desejar compartilhar uma pasta, ao criá-la no AEM Assets, não selecione a opção Solicitado.

## Best practices {#best-practices}

As práticas recomendadas para aproveitar o compartilhamento de pastas AEM para Creative Cloud incluem:

* **Considerações sobre volume:** O Compartilhamento de pastas AEM/Creative Cloud deve ser usado para compartilhar um número menor de arquivos, por exemplo, relevantes para uma campanha ou atividade específica. Para compartilhar conjuntos maiores de ativos, como todos os ativos aprovados na organização, use outros métodos de distribuição (por exemplo, o Portal da Marca AEM Assets) ou AEM aplicativo de desktop.
* **Evite compartilhar hierarquias profundas:** O compartilhamento funciona recursivamente e não permite o compartilhamento seletivo. Normalmente, somente pastas sem subpastas ou com uma hierarquia muito superficial, como 1 nível de subpasta, devem ser consideradas para compartilhamento.
* **Separe pastas para compartilhamento unidirecional:** Pastas separadas devem ser usadas para compartilhar ativos finais de arquivos AEM Assets para Creative Cloud e para compartilhar ativos prontos para criação de volta de arquivos Creative Cloud para AEM Assets. Junto com uma boa convenção de nomenclatura para essas pastas, ela cria um ambiente de trabalho mais fácil de entender para usuários do AEM Assets e do Creative Cloud.
* **Evite o WIP na pasta compartilhada:** A pasta compartilhada não deve ser usada para o Trabalho em andamento - use uma pasta separada em Arquivos de Creative Cloud para realizar um trabalho que exija alterações frequentes no arquivo.
* **Start do novo trabalho fora da pasta compartilhada:** Os novos designs (arquivos criativos) devem ser iniciados na pasta WIP separada em Arquivos de Creative Cloud e, quando estiverem prontos para serem compartilhados com usuários da AEM Assets, devem ser movidos ou salvos na pasta compartilhada.
* **Simplifique a estrutura de compartilhamento:** Para uma configuração operacional mais gerenciável, pense em simplificar a estrutura de compartilhamento. Em vez de compartilhar com todos os usuários criativos, as pastas do AEM Assets devem ser compartilhadas somente com os representantes da equipe, como um diretor criativo ou um gerente de equipe. O gerente do lado criativo receberia ativos finais, decidiria sobre atribuições de trabalho e deixaria os designers trabalharem em suas próprias contas de Creative Cloud nos ativos WIP. Eles podem usar os recursos de colaboração Creative Cloud para coordenar o trabalho e, por fim, selecionar e colocar ativos prontos para compartilhar de volta para a AEM Assets em sua pasta compartilhada pronta para criação.

O diagrama a seguir ilustra um exemplo de configuração para a criação de novos designs com base nos ativos finais existentes da AEM Assets.

![chlimage_1-407](assets/chlimage_1-407.png)
