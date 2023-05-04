---
title: Compartilhar pastas do Experience Manager Assets com o Creative Cloud
description: Configuração e práticas recomendadas para permitir que os usuários do Adobe Experience Manager Assets troquem pastas de ativos com usuários do Adobe Creative Cloud.
contentOwner: AG
feature: Collaboration
role: User,Admin
exl-id: 7e2adfcc-410d-4574-8f7e-39aceecfdd4b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 0%

---

# [!DNL Experience Manager] para [!DNL Creative Cloud] práticas recomendadas de compartilhamento de pastas {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>O recurso Experience Manager to Creative Cloud Folder Sharing está obsoleto. O Adobe recomenda utilizar recursos mais recentes, como [Adobe Asset Link](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) ou [Aplicativo de desktop do Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html). Saiba mais em [Práticas recomendadas de integração de Experience Manager e Creative Cloud](/help/assets/aem-cc-integration-best-practices.md).

O Adobe Experience Manager pode ser configurado para permitir que os usuários do Experience Manager Assets compartilhem pastas com usuários do Creative Cloud, de modo que eles estejam disponíveis como pastas compartilhadas no serviço Ativos do Creative Cloud. O recurso pode ser usado para trocar arquivos entre equipes criativas e usuários da Experience Manager Assets, especialmente quando os usuários criativos não têm acesso à instância do Experience Manager Assets (eles não estão na rede corporativa).

Esse tipo de integração pode ser usado em ambos os casos de uso, especialmente ao trabalhar com usuários que não têm acesso direto ao Experience Manager Assets:

* Compartilhamento de um conjunto de ativos específicos do Experience Manager Assets com usuários de Creative Cloud Files (por exemplo, um resumo criativo e um conjunto de ativos aprovados para o trabalho de design de uma nova atividade de marketing)
* Recebendo novos arquivos de usuários do Creative Cloud.

>[!NOTE]
>
>Antes de ler este documento, você pode revisar o [Práticas recomendadas de integração de Experience Manager e Creative Cloud](aem-cc-integration-best-practices.md) para obter uma visão geral de nível superior do tópico.

## Visão geral {#overview}

O compartilhamento de pastas do Experience Manager para o Creative Cloud depende do compartilhamento de pastas e arquivos no lado do servidor entre as contas do Experience Manager Assets e do Creative Cloud. Os profissionais criativos, que usam o aplicativo Creative Cloud para desktop em seus desktops, podem também disponibilizar as pastas compartilhadas diretamente em seus discos usando a tecnologia Adobe CreativeSync.

O diagrama a seguir fornece uma visão geral da integração.

![chlimage_1-406](assets/chlimage_1-406.png)

A integração inclui os seguintes elementos:

* **[!DNL Assets]server** implantado na rede corporativa (serviços gerenciados ou no local): O compartilhamento de pastas é iniciado aqui.
* **Serviço principal de ativos da Adobe Marketing Cloud**: Atua como um intermediário entre os serviços de armazenamento de Experience Manager e Creative Cloud. O administrador da empresa que usa a integração precisa estabelecer uma relação de confiança entre a organização do Marketing Cloud e a instância do Experience Manager Assets. Eles também [definir uma lista de colaboradores aprovados do Creative Cloud](https://experienceleague.adobe.com/docs/core-services/interface/assets/t-admin-add-cc-user.html#assets), que os usuários do Assets também podem compartilhar pastas para obter segurança adicional.
* **Serviços da Web do Creative Cloud Assets** (interface da Web de arquivos de armazenamento e Creative Cloud): É aqui que usuários específicos do Creative Cloud, com quem uma pasta Assets foi compartilhada, poderiam aceitar o convite e ver a pasta em seu armazenamento de conta do Creative Cloud.
* **aplicativo de desktop Creative Cloud**: (Opcional) Permite acesso direto a pastas compartilhadas/arquivos da área de trabalho do usuário criativo por meio da sincronização com o armazenamento do Creative Cloud Assets.

## Características e limitações {#characteristics-and-limitations}

* **Propagação unidirecional das alterações:** As alterações de arquivo são propagadas em uma única direção, somente no sistema (Experience Manager ou Creative Cloud Assets), onde o ativo foi criado originalmente (carregado). A integração não oferece uma sincronização bidirecional totalmente automatizada entre os dois sistemas.

* **Versões:**

   * O Experience Manager cria apenas versões de um ativo em atualizações se o arquivo tiver origem no Experience Manager e for atualizado lá.
   * O Creative Cloud Assets fornece seu próprio [recurso de controle de versão](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html) direcionado para atualizações do Work in Progress (basicamente, armazena atualizações por até 10 dias)

* **Limitações de espaço:** Os tamanhos e volumes de ficheiros trocados são limitados pela [Cota do Creative Cloud Assets](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) para usuários criativos (depende do nível de assinatura) e uma limitação de tamanho máximo de arquivo de 5 GB. O espaço é também limitado pela cota de ativos que a organização tem no serviço principal do Adobe Marketing Cloud Assets.

* **Requisitos de espaço:** Os arquivos em pastas compartilhadas também precisam ser armazenados fisicamente no Experience Manager e, em seguida, na conta do Creative Cloud, com uma cópia em cache no serviço principal do Marketing Cloud Assets.
* **Rede e largura de banda:** Os arquivos em pastas compartilhadas e todas as atualizações precisam ser transportados pela rede entre os sistemas. Você deve garantir que somente os arquivos e atualizações relevantes sejam compartilhados.
* **Tipo de pasta**: Compartilhamento de uma pasta de Ativos do tipo `sling:OrderedFolder`, não é compatível. Se quiser compartilhar uma pasta, ao criá-la no Experience Manager Assets, não selecione a opção Solicitado.

## Práticas recomendadas {#best-practices}

As práticas recomendadas para o uso do compartilhamento de pasta Experience Manager para Creative Cloud incluem:

* **Considerações sobre volume:** Experience Manager, o Creative Cloud Folder Sharing deve ser usado para compartilhar um número menor de arquivos, por exemplo, relevantes para uma campanha ou atividade específica. Para compartilhar conjuntos maiores de ativos, como todos os ativos aprovados na organização, use outros métodos de distribuição (por exemplo, Experience Manager Assets Brand Portal) ou aplicativo de desktop Experience Manager.
* **Evite compartilhar hierarquias profundas:** O compartilhamento funciona de forma recursiva e não permite o compartilhamento seletivo. Normalmente, somente pastas sem subpastas ou com uma hierarquia muito superficial, como 1 nível de subpasta, devem ser consideradas para compartilhamento.
* **Pastas separadas para compartilhamento unidirecional:** Pastas separadas devem ser usadas para compartilhar ativos finais do Experience Manager Assets em arquivos Creative Cloud e para compartilhar ativos prontos para criação de volta de arquivos Creative Cloud para [!DNL Assets]. Juntamente com uma boa convenção de nomenclatura para essas pastas, ela cria um ambiente de trabalho mais fácil de entender para os usuários do Experience Manager Assets e do Creative Cloud.
* **Evite o WIP na pasta compartilhada:** A pasta compartilhada não deve ser usada para o Trabalho em Andamento - use uma pasta separada em Arquivos do Creative Cloud para realizar um trabalho que exija alterações frequentes no arquivo.
* **Iniciar novo trabalho fora da pasta compartilhada:** Novos designs (arquivos criativos) devem ser iniciados na pasta WIP separada em Arquivos do Creative Cloud e, quando estiverem prontos para serem compartilhados com usuários do Experience Manager Assets, eles devem ser movidos ou salvos na pasta compartilhada.
* **Simplifique a estrutura de compartilhamento:** Para uma configuração operacional mais gerenciável, pense em simplificar a estrutura de compartilhamento. Em vez de compartilhar com todos os usuários criativos, as pastas do Experience Manager Assets devem ser compartilhadas somente com representantes da equipe, como um diretor criativo ou gerente de equipe. O gerente do lado criativo receberia ativos finais, decidiria sobre atribuições de trabalho e deixaria os designers trabalharem em suas próprias contas de Creative Cloud em ativos WIP. Eles podem usar os recursos de colaboração do Creative Cloud para coordenar o trabalho e, por fim, selecionar e colocar ativos prontos para compartilhar com a Experience Manager Assets em sua pasta compartilhada pronta para criação.

O diagrama a seguir ilustra um exemplo de configuração para criar novos designs com base em ativos finais existentes do Experience Manager Assets.

![chlimage_1-407](assets/chlimage_1-407.png)
