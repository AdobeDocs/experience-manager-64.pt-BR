---
title: Práticas recomendadas de integração de AEM e Creative Cloud
description: Práticas recomendadas para integrar uma implantação AEM com a Adobe Creative Cloud, a fim de simplificar os workflows de transferência de ativos e atingir a máxima eficiência
contentOwner: AG
translation-type: tm+mt
source-git-commit: ddfcb74451f41cea911700a64abceaaf47e7af49
workflow-type: tm+mt
source-wordcount: '3566'
ht-degree: 16%

---


# Práticas recomendadas de integração de AEM e Creative Cloud {#aem-and-creative-cloud-integration-best-practices}

<!-- TBD: Reconcile with 6.5 article that's ahead of this article now in terms of content streamlining and structuring.
-->

O Adobe Experience Manager Assets é uma solução de gerenciamento de ativos digitais (DAM) que pode se integrar à Adobe Creative Cloud para ajudar os usuários do DAM a trabalharem em conjunto com as equipes criativas, simplificando a colaboração no processo de criação de conteúdo.

A Adobe Creative Cloud fornece às equipes criativas um ecossistema de soluções e serviços para ajudá-las a criar ativos digitais. Inclui aplicativos para desktop e dispositivos móveis, serviços em nuvem, como armazenamento com sincronização de desktop ou experiência na Web, bem como mercados como o Adobe Stock.

Leia para saber quais integrações escolher entre desktop e DAM de nível corporativo com base no caso de uso e quais são as práticas recomendadas associadas para os workflows de conexão.

>[!NOTE]
>
>O compartilhamento de pasta AEM para Creative Cloud está obsoleto e não é mais abordado neste guia. A Adobe recomenda o uso de recursos mais recentes, como [Adobe Asset Link](https://helpx.adobe.com/br/enterprise/using/adobe-asset-link.html) ou [AEM aplicativo desktop](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html) para fornecer ao usuário criativo acesso aos ativos gerenciados na AEM.

## Necessidades de colaboração de criativos, profissionais de marketing e usuários de DAM {#collaboration-needs-of-creatives-marketers-and-dam-users}

| Requisitos | Caso de uso | Superfícies envolvidas |
|---|---|---|
| Simplifique a experiência de profissionais de criação em desktop | Simplifique o acesso a ativos de um DAM (AEM Assets) para profissionais criativos, ou, mais amplamente, para usuários de desktop que trabalham em aplicativos nativos de criação de ativos. Eles precisam de uma maneira fácil e direta de descobrir, usar (abrir), editar e salvar alterações em AEM, bem como fazer upload de novos arquivos. | Ambiente de trabalho Win ou Mac; aplicativos Creative Cloud |
| Fornecer ativos de alta qualidade e prontos para uso da Adobe Stock | Os profissionais de marketing ajudam a acelerar o processo de criação de conteúdo auxiliando na seleção de fontes e na descoberta de ativos. Profissionais criativos usam os ativos aprovados diretamente de suas ferramentas criativas. | AEM Assets; Mercado Adobe Stock; campos de metadados |
| Distribuir e compartilhar ativos por organizações | Os departamentos internos/locais e parceiros externos, distribuidores e agências usam os ativos aprovados compartilhados pela organização-mãe. A organização deseja compartilhar com segurança e facilidade os ativos criados para uma reutilização mais ampla. | Portal de marcas, Commons de compartilhamento de ativos |

## Ofertas do Adobe para dar suporte à necessidade de colaboração {#adobe-offerings-to-support-the-collaboration-need}

| Proposta de valor para as pessoas envolvidas | oferta de Adobe | Superfícies envolvidas |
|---|---|---|
| Os usuários criativos descobrem ativos de AEM, os abrem e usam, editam e carregam alterações em AEM, bem como carregam novos arquivos em AEM, sem sair dos aplicativos Creative Cloud. | [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) | Photoshop, Illustrator e InDesign |
| Os usuários empresariais simplificam a abertura e o uso de ativos, a edição e o upload de alterações em AEM e o upload de novos arquivos em AEM do ambiente para desktop. Eles usam uma integração genérica para abrir qualquer tipo de ativo no aplicativo desktop nativo, incluindo os não-Adobe. | [Aplicativo de desktop do AEM](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) | AEM aplicativo de desktop no desktop Win e Mac |
| Os profissionais de marketing e usuários comerciais descobrem, pré-visualizações, licenciam e salvam e gerenciam os ativos da Adobe Stock de dentro do AEM. Os ativos licenciados e salvos fornecem metadados Adobe Stock selecionados para melhor governança. | [Integração com Experience Manager e Adobe Stock](aem-assets-adobe-stock.md) | interface da Web AEM |

Este artigo foca principalmente nos dois primeiros aspectos das necessidades de colaboração. A distribuição e o fornecimento de ativos em escala são brevemente mencionadas como um caso de uso. Para essas necessidades, considere o Adobe Brand Portal ou o Asset Share Commons. Soluções alternativas, como [Brand Portal](https://helpx.adobe.com/br/experience-manager/brand-portal/user-guide.html), que podem ser criadas com base nos componentes [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/), [Link Share](/help/assets/link-sharing.md), usando [Experience Manager Assets](/help/assets/managing-assets-touch-ui.md) devem ser revisadas com base em requisitos específicos.

![Conexões de Creative Cloud para AEM: Decidir qual capacidade usar](assets/creative-connections-aem.png)

<!-- 
## Terms and definitions {#terms-and-definitions}

The terms used in this document may have a different meaning in other contexts. In particular, the following terms pertaining to the digital asset lifecycle are used when referring to workflows between a creative professional's desktop and DAM:

* **Work-in-progress or creative work-in-progress (WIP):** A phase in asset lifecycle where an asset undergoes multiple changes and is typically not yet ready to be shared with broader teams.
* **Creative-ready assets:** Assets that are ready to be shared with a broader team, or have been  selected / approved  by the creative team for sharing with marketing or LOB teams.
* **Asset approvals:** The approval process that runs for assets already uploaded to DAM, which typically includes brand approvals, legal approvals, and so on.
* **Final asset:** An asset that has gone through all  approvals/metadata  tagging and is ready to be used by the broader team. Such an asset is stored in DAM and made available to all (or all interested) users. It can be used in marketing channels or by creative teams to create designs.
* **Minor asset  update/change:** A quick and small change to a digital asset. It is often made in response to a retouching or minor editing request, asset review, or approval (for example, reposition, change text size, adjust saturation/brightness, color, and so on).
* **Major asset  update/change:** A change to a digital asset that requires considerable work, and sometimes must be done over a longer period of time. It typically includes multiple changes. The asset must be saved multiple times while being updated. Major asset updates typically cause the asset to enter a WIP stage.
* **DAM:** Digital asset management. In this document, it is synonymous with AEM Experience Manager Assets, unless specifically mentioned otherwise.
* **Creative user:** A creative professional, who creates digital assets using Creative Cloud apps and services. In some cases, a creative user may be a member of a creative team who may use Creative Cloud, but does not create digital assets (like a creative director or creative team manager).
* **DAM user:** A typical user of a DAM system. Depending on the organization, a DAM user can be a marketing or a non-marketing user, for example a Line-of-Business (LOB) user, librarian, sales person, and so on.
-->

### Mapeamento de casos de utilização

| Caso de uso | Aplicativo de desktop do AEM | Compartilhamento de pastas | Outras soluções |
|---|---|---|---|
| Compartilhar um número menor (1) de ativos DAM com o usuário da Creative | ✔ | Can |  |
| Compartilhe um número maior (2) de ativos DAM com o usuário da Creative | ✔ | ✘ | [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) <br> [Compartilhamento de ativos](assets-finder-editor.md) |
| Compartilhar ativos DAM com usuários que têm acesso ao DAM | ✔ | Can | [Compartilhamento de link](link-sharing.md) |
| Compartilhar ativos DAM com usuários que não têm acesso ao DAM | ✘ | ✔ | [Portal de marcas](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) <br> [Compartilhamento de ativos](assets-finder-editor.md) |
| Salvar um número/volume menor de ativos no DAM | ✔ | Can | [UI da Web Carregar](managing-assets-touch-ui.md) |
| Salvar um número maior de ativos no DAM (3) | ✔ | ✘ | [UI da Web ](managing-assets-touch-ui.md) <br> UploadScript/ferramenta personalizada |
| Migrar um grande número de ativos para o DAM | ✘ | ✘ | [Guia de migração](assets-migration-guide.md) |
| Abrir rapidamente um ativo no desktop | ✔ | ✘ |  |
| Abrir e alterar rapidamente ativos no desktop | ✔ | ✘ |  |

A legenda dos símbolos:

* ✔: solução preferencial
* Can solução aceitável
* ✘: não deve ser usado para o caso de uso

Observações adicionais:

* (1) Menor número de ativos: por exemplo, um pequeno conjunto de ativos relacionados a um projeto ou campanha
* (2) Maior número de ativos: por exemplo, todos os ativos aprovados na organização
* (3) Usar AEM recurso de pasta de upload do aplicativo para desktop

Para suportar casos de uso de distribuição de ativos, outras soluções devem ser consideradas:

* [Brand ](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html) Portalate para um complemento configurável SaaS à AEM Assets para publicar ativos.
* As soluções personalizadas são criadas com base na base de código [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/).
* AEM [link share](/help/assets/link-sharing.md) para compartilhar ativos ad hoc usando links.
* [A interface da Web da AEM Assets ](/help/assets/managing-assets-touch-ui.md) interage com áreas para terceiros protegidos pela configuração AEM Controle de acesso e com os ajustes necessários de configuração de TI/rede, dando a esses usuários externos acesso à AEM.

## Principais conceitos e casos de uso {#key-concepts-and-use-cases}

### Glossário de termos comuns {#glossary-of-common-terms}

* **Trabalho em andamento ou trabalho criativo em andamento (WIP)**: uma fase no ciclo de vida do ativo em que um ativo sofre várias alterações e normalmente ainda não está pronto para ser compartilhado com equipes maiores.
* **Ativos prontos para criação**: os ativos que prontos para serem compartilhados com uma equipe maior ou que foram selecionados/aprovados pela equipe criativa para compartilhamento com equipes de marketing ou LOB.
* **Aprovações de ativos**: o processo de aprovação que executa ativos já carregados no DAM, que normalmente inclui aprovações de marca, legais e assim por diante.
* **Ativo final**: um ativo que passou por todas as aprovações/marcações de metadados e está pronto para ser usado pela equipe maior. Esse ativo é armazenado no DAM e disponibilizado a todos os usuários (ou a todos os interessados). Ele pode ser usado em canais de marketing ou por equipes criativas para criar designs.
* **Atualização/alteração de ativos secundários:** uma pequena e rápida mudança em um ativo digital. Geralmente é feito em resposta a uma solicitação de retoque ou edição secundária, revisão de ativos ou aprovação (por exemplo, reposição, alteração do tamanho do texto, ajuste da saturação/brilho, cor e assim em diante).
* **Atualizações/alterações de ativos principais:** uma mudança em um ativo digital que requer trabalho considerável, e às vezes deve ser feita por um período mais longo. Normalmente, inclui várias alterações. O ativo deve ser salvo várias vezes durante a atualização. As atualizações de ativos principais normalmente fazem com que o ativo entre em um estágio WIP.
* **DAM:** Gerenciamento de ativos digitais. Neste documento, ele é sinônimo do AEM Experience Manager Assets, a menos que especificamente mencionado o contrário.
* **Usuário criativo**: um profissional criativo, que cria ativos digitais usando aplicativos e serviços da Creative Cloud. Em alguns casos, um usuário criativo pode ser membro de uma equipe criativa que pode usar a Creative Cloud, mas não cria ativos digitais (como um diretor criativo ou gerente de equipe criativa).
* **Usuário do DAM:** um usuário típico de um sistema DAM. Dependendo da organização, um usuário do DAM pode ser um usuário de marketing ou não, por exemplo, um usuário de Linha de Negócios (LOB), um bibliotecário, um vendedor e assim por diante.

### Considerações ao usar a integração AEM e Creative Cloud {#considerations-when-using-aem-and-creative-cloud-integration}

* Consulte [práticas recomendadas do aplicativo desktop](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/troubleshoot.html?lang=en#best-practices-to-prevent-troubles)
* Consulte [Integração Adobe Stock](aem-assets-adobe-stock.md)
* Consulte [Link do ativo do Adobe](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)

Este é um breve resumo das práticas recomendadas para integração entre Experience Manager e Creative Cloud. Leia o resto deste documento para entender os detalhes.

* **Para usuários criativos, que trabalham no Photoshop, InDesign ou Illustrator:** o do Adobe Asset Link fornece a melhor experiência do usuário, incluindo a manipulação limpa do Trabalho em andamento em ativos tirados do AEM
* **Para simplificar o acesso a ativos do desktop para qualquer formato de arquivo ou aplicativo genérico:** use o aplicativo de desktop do AEM
* **Entenda por que e quando armazenar ativos no DAM:** atualizações a serem disponibilizadas para a equipe maior em sua organização
* **Considere o volume de ativos compartilhados:** se o caso de uso for a distribuição de ativos, a governança e a segurança podem ser os aspectos mais importantes. Considere usar ferramentas criadas para fazer isso em escala, como o Brand Portal.
* **Entenda o ciclo de vida do ativo:** saiba como os ativos são manipulados em sua organização por equipes diferentes
* **Lidar com salvamentos frequentes em ativos com cuidado:** o Adobe Asset Link cuida disso para você com PS, AI, ID. Em outros aplicativos, não realize tarefas em andamento na pasta mapeada/compartilhada, a menos que precise de todas as alterações no DAM

### Acesso aos ativos Adobe Stock da AEM Assets {#access-to-adobe-stock-assets-from-aem-assets}

[A ](/help/assets/aem-assets-adobe-stock.md) integração entre AEM e Adobe Stock fornece aos usuários AEM a capacidade de pesquisar, pré-visualização, licenciar e salvar ativos da Adobe Stock em AEM. Os ativos Adobe Stock licenciados e salvos selecionaram os metadados do Stock, que podem ser usados para pesquisá-los com filtros extras.

Alguns pontos importantes sobre essa integração:

* Quando os ativos do Adobe stock são salvos em AEM, eles se tornam um AEM Assets comum, com um binário salvo no repositório AEM. Alguns metadados relacionados ao Adobe Stock são salvos para o ativo no AEM, caso contrário, o processo de ingestão terá a mesma aparência de qualquer outro arquivo. Por exemplo, se as Tags inteligentes estiverem ativas, as tags serão adicionadas a esses ativos ao salvar.
* O ativo salvo no AEM é uma cópia, não um link de volta para o Adobe Stock.

**Trabalhar com ativos salvos da Adobe Stock em AEM no Creative Cloud**. Essa integração é independente do Link do ativo do Adobe, mas o Link do ativo do Adobe reconhece esses ativos salvos do Stock dessa forma e exibe metadados adicionais e o ícone do Stock nesses ativos na interface do usuário da extensão do Link do ativo do Adobe no Photoshop, Illustrator ou InDesign. Os arquivos estão disponíveis para navegação, abertura e assim por diante - porque são ativos comuns AEM quando salvos em AEM.
Os usuários criativos que trabalham em aplicativos Creative Cloud com a extensão do Link de ativos Adobe, além de terem acesso a ativos já licenciados da Adobe Stock no AEM, também podem usar o painel Bibliotecas Creative Cloud para pesquisar, pré-visualização e licenciar ativos da Adobe Stock.
Os ativos da Adobe Stock licenciados e salvos em AEM tornam-se disponíveis para equipes mais amplas que acessam a implantação da AEM Assets, enquanto os ativos de licenciamento da Adobe Stock por meio do painel Bibliotecas Creative Cloud disponibilizam-nos somente por padrão em suas contas Creative Cloud.

<!-- 
TBD: A condensed version of the below content is better placed in the Adobe DAM article.
-->

## Sobre o armazenamento de ativos em um DAM {#about-storing-assets-in-a-dam}

Para projetar um fluxo de trabalho eficiente entre equipes de criação e marketing/linha de negócios (LOB) e escolher os melhores recursos de suporte, é importante entender quando e por que os ativos são armazenados no DAM.

### Por que os ativos são armazenados no DAM {#why-assets-are-stored-in-dam}

Armazenar ativos no DAM os torna facilmente acessíveis e acessíveis. Ela garante que os ativos possam ser aproveitados por vários usuários em toda a organização ou ecossistema, o que inclui parceiros, clientes e assim por diante.

A maioria das organizações escolhe armazenar apenas ativos relevantes para os processos de marketing/LOB a jusante (publicação em canais como canal da Web via AEM Sites ou outros canais servidos pela Adobe Experience Cloud - Marketing Cloud, Advertising Cloud e medidos pela Analytics Cloud, fornecendo a usuários/parceiros e assim por diante). Além disso, as organizações armazenam ativos que podem estar sujeitos a um processo de revisão/aprovação no DAM. Dessa forma, o DAM armazena principalmente ativos que têm grandes chances de serem aproveitados e evita armazenar ativos ociosos.

Armazenar ativos também está sujeito a considerações técnicas e de utilização de recursos. O DAM fornece serviços adicionais sobre ativos armazenados, incluindo extração de metadados, controle de versão, geração de pré-visualizações/transcodificação, gerenciamento de referências e adição de informações de controle de acesso. Esses serviços consomem mais tempo e recursos de infraestrutura.

Geralmente, armazenar todos os ativos e atualizações não é desejável. Por exemplo, se as atualizações de ativos específicos forem de baixa qualidade e consumirem recursos excessivos, os ativos podem não ser armazenados no DAM.

### Quando os ativos são armazenados no DAM {#when-assets-are-stored-in-dam}

Geralmente, as equipes criativas (e organizações) não estão interessadas em armazenar ativos em cada estágio do ciclo de vida do ativo. Por exemplo, eles evitam armazenar ativos nos seguintes casos:

* Ativos que ainda não foram finalizados ou estão sujeitos a experimentação
* Ativos que não passam no ciclo de análise da equipe interna/criativa
* Em comparação com o ativo em questão, a equipe tem melhores candidatos para representar seu trabalho para equipes externas

Normalmente, os seguintes ativos de classes são armazenados no DAM:

* Ativos que atingiram um determinado prazo de vencimento e são considerados prontos para serem partilhados
* Ativos pré-selecionados pela equipe criativa
* Formatos de ativos específicos que são utilizáveis ou solicitados pelo marketing, dependendo de um contrato ou contrato específico (por exemplo, arquivos JPG convertidos de arquivos RAW, TIFFs/imagens de originais PSD)

### Quando as atualizações de ativos são armazenadas no DAM {#when-updates-to-assets-are-stored-in-dam}

Como regra, somente as atualizações de ativos relevantes para o conjunto mais amplo de usuários do DAM devem ser armazenadas no DAM. Ela garante que os usuários (marketing e funções semelhantes) visualizem somente as versões relevantes na linha do tempo do ativo DAM.

Normalmente, as alterações estão relacionadas aos principais marcos no ciclo de vida do ativo. Por exemplo, o ativo pronto para criação inicial ou uma atualização oficial com base na solicitação/revisão fornecida pela equipe criativa deve ser armazenada e controle de versão no DAM.

A atualização da equipe criativa para revisão pela equipe de marketing após uma solicitação de alteração no ativo existente no DAM é um exemplo de uma atualização relevante. Ele deve ser armazenado e controle de versão no DAM para referência adicional ou para reverter para a versão anterior.

A seguir estão exemplos de atualizações que normalmente não são relevantes:

* Versões antecipadas de ativos carregados antes de estarem prontos para a revisão de marketing
* Alterações criativas frequentes no ativo na fase de trabalho em andamento antes que a equipe criativa decida que o ativo está pronto

### Acesso do usuário ao DAM {#user-access-to-dam}

A AEM Assets oferece suporte a dois tipos de usuários com base em seu acesso à implantação do AEM Assets. Normalmente, os usuários dentro da rede corporativa (firewall) têm acesso direto ao DAM. Outros usuários fora da rede corporativa não teriam acesso direto. O tipo de usuário determina quais integrações podem ser usadas do ponto de vista técnico.

#### Usuários criativos com acesso direto ao DAM {#creative-users-with-direct-access-to-dam}

Geralmente, equipes de criação interna ou agências/profissionais de criação integrados à rede interna têm acesso à instância do DAM, incluindo logon AEM.

Nesses casos, AEM aplicativo de desktop ajuda a facilitar o acesso aos ativos finais/aprovados e permite salvar ativos prontos para criação no DAM.

#### Usuários criativos sem acesso ao DAM {#creative-users-without-access-to-dam}

Agências externas e freelancers sem acesso direto à instância do DAM podem exigir acesso a ativos aprovados ou podem adicionar seus novos designs ao DAM.

Nesses casos, você pode aproveitar a integração AEM/Creative Cloud para melhorar o fluxo de trabalho. O pré-requisito é que os usuários criativos tenham um Adobe ID e uma conta Creative Cloud com o serviço armazenamento.

Use as seguintes estratégias para fornecer acesso aos ativos finais/aprovados:

* Para fornecer acesso a um grande número de ativos: Use [o Portal de Marcas da AEM Assets](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html), ou a implementação pelo cliente de [Compartilhamento de Ativos](assets-finder-editor.md) AEM infraestrutura de publicação

* Para fornecer acesso a alguns ativos: AEM compartilhamento de pastas com a Adobe Creative Cloud pode ser usado além do AEM Assets Brand Portal ou do Asset Share. Observe que há certas limitações relacionadas a essa integração, abordadas com mais detalhes neste artigo.

### Casos de uso {#use-cases}

Os seguintes casos de uso descrevem vários tipos de workflows entre o DAM e a área de trabalho do designer.

#### Criar novos designs usando ativos do DAM {#creating-new-designs-using-assets-from-dam}

O diagrama a seguir ilustra o ciclo de vida do ativo digital. Ela descreve como os usuários criativos e os usuários de DAM (comerciantes, usuários de LOB) aproveitam os ativos existentes e os usam para criar mais ativos e enviá-los para aprovação.

![chlimage_1-301](assets/chlimage_1-301.png)

O ciclo de vida do ativo inclui as seguintes etapas:

1. Compartilhe ativos aprovados na área de trabalho criativa: Os ativos finais do DAM são disponibilizados ao usuário criativo (no desktop)
1. Crie um novo design (ativo digital criativo): Um novo arquivo é armazenado na área de trabalho em andamento (WIP).
1. Usar ativos aprovados (colocar) em um novo design: O usuário criativo produz um novo ativo usando ativos aprovados existentes em aplicativos Creative Cloud
1. Salvando frequentemente atualizações do WIP: O usuário criativo repete rapidamente e salva o arquivo com frequência. Neste estágio, o usuário criativo pode colaborar com outras pessoas, mas as atualizações salvas frequentemente não interessam aos usuários do DAM.
1. O ativo atinge o status de criativo pronto e é salvo na pasta Creative Ready
1. Atualização do ativo: Uma atualização de ativo ou um novo arquivo está disponível para os usuários no DAM
1. O ativo é colocado em produção: Este é um processo de DAM, que, dependendo da organização, pode incluir marcação, aprovações e alteração de controles de acesso. Neste estágio, o ativo é considerado final e pode ser usado por equipes mais amplas aproveitando o DAM. Também pode ser usado por usuários criativos para criar outros ativos.

Estas são algumas recomendações gerais sobre como gerenciar ativos por meio deste processo:

* Use uma área/sistema de armazenamentos dedicados, como a pasta sincronizada Adobe Creative Cloud Assets, para os arquivos WIP: As atualizações frequentes que não são relevantes para os usuários do DAM são melhor tratadas por um sistema dedicado, e não pela AEM Assets. Os ativos WIP podem ser sincronizados com o disco local usando o aplicativo Adobe Creative Cloud desktop, salvos no armazenamento local e assim por diante.
* Use pastas/compartilhamentos separados para ativos finais e ativos que são carregados no DAM: para maior clareza, os ativos finais devem ter sua própria pasta mapeada/compartilhada (&quot;Exemplo final&quot; acima), e os ativos a serem carregados de volta para o DAM devem ter sua própria pasta (&quot;Creative Ready&quot;)

#### Alterar ativos existentes gerenciados no DAM {#changing-existing-assets-managed-in-dam}

Em alguns casos, os ativos no DAM podem exigir alterações. Os exemplos incluem:

* Solicitação de alterações em ativos da revisão e aprovação feitas no AEM Assets
* Principais atualizações dos ativos finais existentes
* Edições rápidas em um arquivo existente (especialmente antes de ser aprovado pela última vez)

Nesses casos, o aplicativo AEM desktop fornece a maneira mais fácil de executar essas operações.

![chlimage_1-302](assets/chlimage_1-302.png)

Este é o fluxo de eventos apresentado no diagrama:

<!-- TBD for formatting. 
This article will get fixed automatically when 6.5 content is ported to it.
And 6.5 content will be ported after updating it for AEM desktop app 2.0 best practices.
And it will be updated for DA2.0 best practices after 6.5 repo is available for writers to edit content in.
-->

* **1:** Compartilhe o ativo do DAM para o desktop ou abra-o diretamente no desktop no aplicativo preferido (por exemplo, Adobe Photoshop e assim por diante). O check-out é recomendado para bloquear o arquivo.
* **2:** Atualização secundária: Edite o arquivo e salve as alterações.
* Fluxo alternativo para a etapa 2

   * **R:Atualização** principal: Se o arquivo exigir um conjunto elaborado de alterações, ele deverá ser salvo intermitentemente e copiado para uma pasta/área WIP.
   * **B:** O trabalho continua no arquivo nas pastas WIP. As alterações salvas não estão sendo sincronizadas com a versão no DAM
   * **C:** Após a conclusão das atualizações, o arquivo é copiado de volta ou salvo na pasta mapeada

* **3:As atualizações** de ativos são refletidas no DAM. Verifique o ativo para desbloqueá-lo.
* **4:** O ativo é colocado em produção.

Estas são algumas recomendações gerais sobre como gerenciar ativos ao longo deste processo:

* Evite salvar diretamente um arquivo aberto de um compartilhamento de rede mapeado por AEM aplicativo de desktop, a menos que as alterações feitas no arquivo sejam pequenas.
* Copie o arquivo para uma pasta WIP separada se desejar fazer alterações adicionais, salvar intermitentemente ou colaborar com a equipe Creative.

#### Carregamento em massa para DAM {#bulk-upload-to-dam}

Você pode ter a necessidade de carregar simultaneamente um número maior de arquivos no DAM em alguns cenários, por exemplo:

* Carregar resultados de fotografias ou projetos maiores
* Fazer upload de ativos fornecidos por agências criativas
* Carregar ativos selecionados de um conjunto maior se a seleção for feita fora do DAM

Observe que essa descrição se refere ao carregamento de arquivos operacionalmente (por exemplo, toda semana, ou com cada fotografia, etc.), como uma parte normal do fluxo de trabalho do usuário do desktop. As migrações de grandes ativos não são abordadas aqui.

Você pode aproveitar os seguintes recursos se quiser fazer upload de ativos em massa:

* Para carregar pastas grandes/hierárquicas, use AEM aplicativo de desktop, que fornece um recurso [Upload de pasta](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html#bulkupload). Você também pode carregar estruturas hierárquicas de pastas. Os ativos são carregados em segundo plano e, portanto, não são vinculados a uma sessão do navegador da Web
* Se quiser carregar alguns arquivos de uma única pasta, arraste-os diretamente da área de trabalho para a interface do usuário da Web ou use a opção Criar na interface do usuário da Web do AEM Assets.

>[!NOTE]
>
>Dependendo dos requisitos de sua empresa, você também pode usar o carregador personalizado.

#### Gerenciar ativos digitais diretamente do desktop {#managing-digital-assets-directly-from-desktop}

Se você usar Compartilhamentos de arquivos de rede para gerenciar ativos digitais, o uso do compartilhamento de rede mapeado por AEM aplicativo desktop pode ser visto como um substituto conveniente. Durante a transição dos compartilhamentos de arquivos de rede, lembre-se de que AEM interface do usuário da Web fornece um conjunto avançado de recursos de Gerenciamento de ativos digitais que vão muito além do que é possível em um compartilhamento de rede (pesquisa, coleções, metadados, colaboração, pré-visualização etc.) e AEM aplicativo de desktop fornece um link útil para conectar o repositório DAM do lado do servidor ao trabalho no desktop.

Evite usar AEM aplicativo de desktop para gerenciar ativos diretamente no compartilhamento de rede da AEM Assets. Por exemplo, evite usar AEM aplicativo de desktop para mover/copiar vários arquivos. Em vez disso, use a interface do usuário da Web do AEM Assets para arrastar pastas do Finder/Explorer para o compartilhamento de rede ou use o recurso AEM Assets Folder Upload.

#### Migração de ativos {#asset-migration}

Para planejar e executar migrações de ativos do sistema existente para um novo sistema ou migração de um grande volume de ativos armazenados em servidores, consulte o [Guia de Migração](/help/assets/assets-migration-guide.md). AEM aplicativo de desktop e AEM para integrações Creative Cloud não suportam essas migrações. Devido aos grandes volumes de ativos a serem ingeridos e aos requisitos adicionais em torno do mapeamento, transformação e ingestão de metadados, as migrações devem ser tratadas usando diferentes ferramentas e abordagens.

>[!MORELIKETHIS]
>
>* [Link de ativo do Adobe](https://helpx.adobe.com/in/enterprise/using/adobe-asset-link.html)
>* [Práticas recomendadas do aplicativo para desktop AEM](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/archive/best-practices-for-v1.html)
>* [AEM Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html)
>* [Integração AEM e Adobe Stock](aem-assets-adobe-stock.md)

