---
title: Compartilhar pastas do AEM Assets com a Creative Cloud
description: Configuração e práticas recomendadas para permitir que usuários do Adobe Experience Manager Assets troquem pastas de ativos com usuários da Adobe Creative Cloud.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 501a6c470113d249646f4424a19ee215a82b032d
workflow-type: tm+mt
source-wordcount: '1057'
ht-degree: 0%

---


# Práticas recomendadas de compartilhamento de pastas do AEM para a Creative Cloud {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>O recurso Compartilhamento de pastas do AEM para a Creative Cloud está obsoleto. A Adobe recomenda usar recursos mais recentes, como o [Adobe Asset Link](https://helpx.adobe.com/br/enterprise/using/adobe-asset-link.html) ou o aplicativo [de desktop](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html)AEM. Saiba mais sobre as práticas [recomendadas de integração do](/help/assets/aem-cc-integration-best-practices.md)AEM e da Creative Cloud.

O Adobe Experience Manager (AEM) pode ser configurado para permitir que os usuários do AEM Assets compartilhem pastas com usuários da Creative Cloud, de modo que eles estejam disponíveis como pastas compartilhadas no serviço Creative Cloud Assets. O recurso pode ser usado para trocar arquivos entre equipes de criação e usuários de AEM Assets, especialmente quando os usuários criativos não têm acesso à instância de AEM Assets (eles não estão na rede corporativa).

Esse tipo de integração pode ser usado em ambos os casos de uso, especialmente ao trabalhar com usuários que não têm acesso direto aos AEM Assets:

* Compartilhamento de um conjunto de ativos específicos de AEM Assets com usuários da Creative Cloud Files (por exemplo, um resumo criativo e um conjunto de ativos aprovados para o trabalho de design de uma nova atividade de marketing)
* Recebendo novos arquivos de usuários da Creative Cloud.

>[!NOTE]
>
>Antes de ler este documento, você pode consultar as práticas [recomendadas gerais de integração do](aem-cc-integration-best-practices.md) AEM e da Creative Cloud para obter uma visão geral de nível superior do tópico.

## Visão geral {#overview}

O compartilhamento de pastas do AEM para a Creative Cloud depende do compartilhamento de pastas e arquivos no servidor entre contas do AEM Assets e da Creative Cloud. Os profissionais da Creative Cloud, que usam o aplicativo de desktop da Creative Cloud em seus desktops, podem disponibilizar as pastas compartilhadas diretamente em seus discos usando a tecnologia Adobe CreativeSync.

O diagrama a seguir fornece uma visão geral da integração.

![chlimage_1-406](assets/chlimage_1-406.png)

A integração inclui os seguintes elementos:

* **Servidor** AEM Assets implantado na rede corporativa (serviços gerenciados ou no local): O compartilhamento de pastas é iniciado aqui.
* **Serviço** principal do Adobe Marketing Cloud Assets: Atua como intermediário entre os serviços de armazenamento do AEM e da Creative Cloud. O administrador da empresa que usa a integração precisa estabelecer uma relação de confiança entre a organização da Marketing Cloud e a instância do AEM Assets. Eles também [definem uma lista de colaboradores](https://docs.adobe.com/content/help/en/core-services/interface/assets/t-admin-add-cc-user.html)aprovados da Creative Cloud, que os usuários do AEM Assets também podem compartilhar pastas para obter segurança adicional.
* **Serviços** da Web do Creative Cloud Assets (interface do usuário da Web de arquivos do armazenamento e da Creative Cloud): É aqui que usuários específicos da Creative Cloud, com os quais uma pasta de AEM Assets foi compartilhada, poderão aceitar o convite e ver a pasta em seu armazenamento de conta da Creative Cloud.
* **Aplicativo** de desktop da Creative Cloud: (Opcional) Permite acesso direto a pastas/arquivos compartilhados da área de trabalho do usuário criativo por meio da sincronização com o armazenamento Creative Cloud Assets.

## Características e limitações {#characteristics-and-limitations}

* **Propagação unidirecional das alterações:** As alterações de arquivo são propagadas em uma única direção - do sistema (AEM ou Creative Cloud Assets), onde o ativo foi criado originalmente (carregado). A integração não fornece uma sincronização bidirecional totalmente automatizada entre os dois sistemas.

* **Versões:**

   * O AEM só cria versões de um ativo em atualizações se o arquivo tiver origem no AEM e for atualizado nele.
   * A Creative Cloud Assets fornece seu próprio recurso [de](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html) controle de versão direcionado para atualizações do Work in Progress (basicamente, armazena atualizações por até 10 dias)

* **Limitações de espaço:** Os tamanhos e volumes de arquivos trocados são limitados pela cota [específica de ativos da](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) Creative Cloud para usuários criativos (depende do nível de subscrição) e por uma limitação de 5 GB do tamanho máximo de arquivos. O espaço é adicionalmente limitado pela cota de ativos que a organização tem no serviço principal do Adobe Marketing Cloud Assets.

* **Requisitos de espaço:** Os arquivos em pastas compartilhadas também precisam ser armazenados fisicamente no AEM e, em seguida, na conta da Creative Cloud, com uma cópia em cache no serviço principal dos Ativos da Marketing Cloud.
* **Rede e largura de banda:** Os arquivos em pastas compartilhadas e todas as atualizações precisam ser transportados pela rede entre os sistemas. Você deve garantir que somente os arquivos e as atualizações relevantes sejam compartilhados.
* **Tipo** de pasta: Não há suporte para o compartilhamento de uma pasta Assets do tipo `sling:OrderedFolder`. Se desejar compartilhar uma pasta, ao criá-la no AEM Assets, não selecione a opção Solicitado.

## Best practices {#best-practices}

As práticas recomendadas para aproveitar o compartilhamento de pastas do AEM para a Creative Cloud incluem:

* **Considerações sobre volume:** O compartilhamento de pastas do AEM/Creative Cloud deve ser usado para compartilhar um número menor de arquivos, por exemplo, relevantes para uma campanha ou atividade específica. Para compartilhar conjuntos maiores de ativos, como todos os ativos aprovados na organização, use outros métodos de distribuição (por exemplo, Portal de marca do AEM Assets) ou aplicativo de desktop do AEM.
* **Evite compartilhar hierarquias profundas:** O compartilhamento funciona recursivamente e não permite o compartilhamento seletivo. Normalmente, somente pastas sem subpastas ou com uma hierarquia muito superficial, como 1 nível de subpasta, devem ser consideradas para compartilhamento.
* **Separe pastas para compartilhamento unidirecional:** Pastas separadas devem ser usadas para compartilhar ativos finais de AEM Assets para arquivos da Creative Cloud e para compartilhar ativos prontos para criação de volta de arquivos da Creative Cloud para AEM Assets. Junto com uma boa convenção de nomenclatura para essas pastas, ela cria um ambiente de trabalho mais fácil de entender para usuários do AEM Assets e da Creative Cloud.
* **Evite o WIP na pasta compartilhada:** A pasta compartilhada não deve ser usada para o Trabalho em andamento - use uma pasta separada na Creative Cloud Files para realizar um trabalho que exija alterações frequentes no arquivo.
* **Start do novo trabalho fora da pasta compartilhada:** Os novos designs (arquivos criativos) devem ser iniciados na pasta WIP separada nos Arquivos da Creative Cloud e, quando estiverem prontos para serem compartilhados com os usuários do AEM Assets, devem ser movidos ou salvos na pasta compartilhada.
* **Simplifique a estrutura de compartilhamento:** Para uma configuração operacional mais gerenciável, pense em simplificar a estrutura de compartilhamento. Em vez de compartilhar com todos os usuários criativos, as pastas do AEM Assets devem ser compartilhadas somente com representantes da equipe, como um diretor criativo ou um gerente de equipe. O gerente do lado criativo receberá ativos finais, decidirá sobre atribuições de trabalho e permitirá que os designers trabalhem em suas próprias contas da Creative Cloud em ativos WIP. Eles podem usar os recursos de colaboração da Creative Cloud para coordenar o trabalho e, por fim, selecionar e colocar ativos prontos para compartilhamento em AEM Assets em sua pasta compartilhada pronta para criação.

O diagrama a seguir ilustra um exemplo de configuração para a criação de novos designs com base nos ativos finais existentes dos AEM Assets.

![chlimage_1-407](assets/chlimage_1-407.png)
