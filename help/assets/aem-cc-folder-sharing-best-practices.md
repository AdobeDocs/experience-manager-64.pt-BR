---
title: Compartilhar pastas do AEM Assets com o Creative Cloud
description: Configuração e práticas recomendadas para permitir que os usuários do Adobe Experience Manager Assets troquem pastas de ativos com usuários do Adobe Creative Cloud.
contentOwner: AG
feature: Collaboration
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 0%

---


# AEM as práticas recomendadas de compartilhamento de pastas do Creative Cloud {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>O recurso de Compartilhamento de pastas do AEM para o Creative Cloud está obsoleto. O Adobe recomenda utilizar recursos mais recentes, como [Adobe Asset Link](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) ou [AEM aplicativo de desktop](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html). Saiba mais em [AEM e práticas recomendadas de integração do Creative Cloud](/help/assets/aem-cc-integration-best-practices.md).

O Adobe Experience Manager (AEM) pode ser configurado para permitir que os usuários do AEM Assets compartilhem pastas com usuários do Creative Cloud, de modo que eles estejam disponíveis como pastas compartilhadas no serviço Creative Cloud Assets. O recurso pode ser usado para trocar arquivos entre equipes criativas e usuários da AEM Assets, especialmente quando os usuários criativos não têm acesso à instância do AEM Assets (eles não estão na rede corporativa).

Esse tipo de integração pode ser usado em ambos os casos de uso, especialmente ao trabalhar com usuários que não têm acesso direto ao AEM Assets:

* Compartilhamento de um conjunto de ativos específicos do AEM Assets com usuários de Creative Cloud Files (por exemplo, um resumo criativo e um conjunto de ativos aprovados para o trabalho de design de uma nova atividade de marketing)
* Recebendo novos arquivos de usuários do Creative Cloud.

>[!NOTE]
>
>Antes de ler este documento, você pode revisar as [AEM e as práticas recomendadas de integração do Creative Cloud](aem-cc-integration-best-practices.md) para obter uma visão geral de nível superior do tópico.

## Visão geral {#overview}

O AEM para o compartilhamento de pastas do Creative Cloud depende do compartilhamento de pastas e arquivos no lado do servidor entre as contas do AEM Assets e do Creative Cloud. Os profissionais criativos, que usam o aplicativo Creative Cloud para desktop em seus desktops, podem também disponibilizar as pastas compartilhadas diretamente em seus discos usando a tecnologia Adobe CreativeSync.

O diagrama a seguir fornece uma visão geral da integração.

![chlimage_1-406](assets/chlimage_1-406.png)

A integração inclui os seguintes elementos:

* **AEM Assets** Server implantado na rede corporativa (serviços gerenciados ou no local): O compartilhamento de pastas é iniciado aqui.
* **Serviço** principal de ativos Adobe Marketing Cloud: Atua como um intermediário entre os serviços de armazenamento de AEM e Creative Cloud. O administrador da empresa que usa a integração precisa estabelecer uma relação de confiança entre a organização do Marketing Cloud e a instância do AEM Assets. Eles também [definem uma lista de Creative Cloud colaboradores aprovados](https://experienceleague.adobe.com/docs/core-services/interface/assets/t-admin-add-cc-user.html?lang=en#assets), que os usuários do AEM Assets também podem compartilhar pastas para obter segurança adicional.
* **Serviços Web do Creative Cloud Assets**  (interface do usuário da Web de arquivos de armazenamento e Creative Cloud): É aqui que usuários específicos do Creative Cloud, com os quais uma pasta do AEM Assets foi compartilhada, poderiam aceitar o convite e ver a pasta em seu armazenamento de conta do Creative Cloud.
* **Aplicativo** de desktop Creative Cloud: (Opcional) Permite acesso direto a pastas compartilhadas/arquivos da área de trabalho do usuário criativo por meio da sincronização com o armazenamento do Creative Cloud Assets.

## Características e limitações {#characteristics-and-limitations}

* **Propagação unidirecional de alterações:** as alterações de arquivo são propagadas em uma única direção - do sistema (Ativos AEM ou Creative Cloud), onde o ativo foi criado originalmente (carregado). A integração não oferece uma sincronização bidirecional totalmente automatizada entre os dois sistemas.

* **Versões:**

   * AEM cria apenas versões de um ativo em atualizações se o arquivo tiver sido originado em AEM e for atualizado lá.
   * O Creative Cloud Assets fornece seu próprio [recurso de controle de versão](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html) que é direcionado para atualizações do Work in Progress (basicamente, armazena atualizações por até 10 dias)

* **Limitações de espaço:** Tamanhos e volumes de arquivos trocados são limitados pela cotação específica do  [Creative Cloud Assets ](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) para usuários criativos (depende do nível de assinatura) e por uma limitação de tamanho máximo de arquivos de 5 GB. O espaço é também limitado pela cota de ativos que a organização tem no serviço principal do Adobe Marketing Cloud Assets.

* **Requisitos de espaço:** os arquivos em pastas compartilhadas também precisam ser armazenados fisicamente no AEM e, em seguida, na conta do Creative Cloud, com uma cópia em cache no serviço principal do Marketing Cloud Assets.
* **Rede e largura de banda:** Os arquivos em pastas compartilhadas e todas as atualizações precisam ser transportados pela rede entre os sistemas. Você deve garantir que somente os arquivos e atualizações relevantes sejam compartilhados.
* **Tipo** de pasta: O compartilhamento de uma pasta do Assets do tipo  `sling:OrderedFolder` não é suportado. Se quiser compartilhar uma pasta, ao criá-la no AEM Assets, não selecione a opção Solicitado.

## Práticas recomendadas {#best-practices}

As práticas recomendadas para o uso do AEM para o compartilhamento de pastas do Creative Cloud incluem:

* **Considerações de volume:** o Compartilhamento de pastas AEM/Creative Cloud deve ser usado para compartilhar um número menor de arquivos, por exemplo, relevantes para uma campanha ou atividade específica. Para compartilhar conjuntos maiores de ativos, como todos os ativos aprovados na organização, use outros métodos de distribuição (por exemplo, AEM Assets Brand Portal) ou AEM aplicativo de desktop.
* **Evite compartilhar hierarquias profundas:** o compartilhamento funciona de forma recursiva e não permite o compartilhamento seletivo. Normalmente, somente pastas sem subpastas ou com uma hierarquia muito superficial, como 1 nível de subpasta, devem ser consideradas para compartilhamento.
* **Pastas separadas para compartilhamento unidirecional:** pastas separadas devem ser usadas para compartilhar ativos finais do AEM Assets em arquivos Creative Cloud e para compartilhar ativos prontos para criação de volta dos arquivos Creative Cloud para o AEM Assets. Juntamente com uma boa convenção de nomenclatura para essas pastas, ela cria um ambiente de trabalho mais fácil de entender para os usuários do AEM Assets e do Creative Cloud.
* **Evite o WIP na pasta compartilhada:** a pasta compartilhada não deve ser usada para o Trabalho em Andamento - use uma pasta separada em Arquivos de Creative Cloud para realizar um trabalho que exija alterações frequentes no arquivo.
* **Inicie um novo trabalho fora da pasta compartilhada:** novos designs (arquivos criativos) devem ser iniciados na pasta WIP separada em Arquivos do Creative Cloud e, quando estiverem prontos para serem compartilhados com usuários do AEM Assets, eles devem ser movidos ou salvos na pasta compartilhada.
* **Simplifique a estrutura de compartilhamento:** para uma configuração operacional mais gerenciável, pense em simplificar a estrutura de compartilhamento. Em vez de compartilhar com todos os usuários criativos, as pastas do AEM Assets devem ser compartilhadas somente com representantes da equipe, como um diretor criativo ou gerente de equipe. O gerente do lado criativo receberia ativos finais, decidiria sobre atribuições de trabalho e deixaria os designers trabalharem em suas próprias contas de Creative Cloud em ativos WIP. Eles podem usar os recursos de colaboração do Creative Cloud para coordenar o trabalho e, por fim, selecionar e colocar ativos prontos para compartilhar com a AEM Assets em sua pasta compartilhada pronta para criação.

O diagrama a seguir ilustra um exemplo de configuração para criar novos designs com base em ativos finais existentes do AEM Assets.

![chlimage_1-407](assets/chlimage_1-407.png)
