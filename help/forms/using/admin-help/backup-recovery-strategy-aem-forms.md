---
title: Estratégia de backup e recuperação para formulários AEM
seo-title: Estratégia de backup e recuperação para formulários AEM
description: Saiba como implementar uma estratégia para fazer backup dos dados e garantir que eles permaneçam sincronizados com os dados dos formulários AEM.
seo-description: Saiba como implementar uma estratégia para fazer backup dos dados e garantir que eles permaneçam sincronizados com os dados dos formulários AEM.
uuid: 98fc3115-76e5-4e58-aa30-3601866a441f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f192a8a3-1116-4d32-9b57-b53d532c0dbf
translation-type: tm+mt
source-git-commit: a3e7cd30ba6933e6f36734d3b431db41365b6e20
workflow-type: tm+mt
source-wordcount: '1520'
ht-degree: 0%

---


# Estratégia de backup e recuperação para formulários AEM{#backup-and-recovery-strategy-for-aem-forms}

Se a implementação de formulários AEM armazenar dados personalizados adicionais em um banco de dados diferente, você será responsável pela implementação de uma estratégia para fazer backup desses dados e garantir que eles permaneçam sincronizados com os dados de formulários AEM. Além disso, o aplicativo deve ser projetado de modo que seja robusto o suficiente para lidar com um cenário em que os bancos de dados adicionais fiquem fora de sincronia. É altamente recomendável que qualquer operação de banco de dados executada seja feita no contexto de uma transação para ajudar a manter um estado consistente.

Depois de identificar como os formulários AEM são usados, determine quais arquivos devem ser submetidos a backup, com que frequência e a janela de backup a ser disponibilizada.

>[!NOTE]
>
>Assim como em qualquer outro aspecto da implementação de formulários AEM, sua estratégia de backup e recuperação deve ser desenvolvida e testada em um ambiente de desenvolvimento ou armazenamento temporário antes de ser usada na produção para garantir que toda a solução esteja funcionando como esperado, sem perda de dados.

A Adobe Experience Manager (AEM) é parte integrante dos formulários AEM. Portanto, é necessário fazer backup AEM também sincronizado com AEM backup de formulários, como a Solução de Gerenciamento de Correspondência e serviços, como o gerenciador de formulários, com base em dados armazenados AEM parte dos formulários AEM.Para evitar perda de dados, é necessário fazer backup dos dados específicos dos formulários AEM para garantir que GDS e AEM (repositório) estejam correlacionados com referências de banco de dados.Os diretórios de banco de dados, GDS, AEM e Raiz do Armazenamento de Conteúdo devem ser restaurados em um computador com o mesmo nome DNS do original.

## Tipos de backups {#types-of-backups}

A estratégia de backup de formulários AEM envolve dois tipos de backups:

**Imagem do sistema:** um backup completo do sistema que você pode usar para restaurar o conteúdo do computador se o disco rígido ou o computador inteiro parar de funcionar. Um backup de imagem do sistema é necessário somente antes da implantação de produção de formulários AEM. Políticas corporativas internas ditam a frequência com que os backups de imagem do sistema são necessários.

**AEM dados específicos dos formulários:os dados** do aplicativo existem no banco de dados, no Armazenamento Global do Documento (GDS) e AEM repositório, e devem ser copiados em backup em tempo real. GDS é um diretório usado para armazenar arquivos de longa duração usados em um processo. Esses arquivos podem incluir PDFs, políticas ou modelos de formulário.

>[!NOTE]
>
>Se o Content Services (obsoleto) estiver instalado, faça backup também do diretório raiz do Armazenamento de conteúdo. Consulte [Diretório raiz do Armazenamento de conteúdo (somente Serviços de conteúdo)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-directory-content-services-only).

O banco de dados é usado para armazenar artefatos de formulário, configurações de serviço, estado do processo e referências de banco de dados a arquivos GDS. Se você ativou o armazenamento do documento no banco de dados, os dados e documentos persistentes no GDS também são armazenados no banco de dados. O backup e a recuperação do banco de dados podem ser feitos com os seguintes métodos:

* **O modo de** backup de instantâneos indica que o sistema de formulários AEM está no modo de backup indefinidamente ou por um número especificado de minutos, após o qual o modo de backup não está mais ativado. Para entrar ou sair do modo de backup de snapshot, você pode usar uma das seguintes opções. Após um cenário de recuperação, o modo de backup de snapshot não deve ser ativado.

   * Use a página Configurações de backup no Console de administração. Para entrar no modo de instantâneo, marque a caixa de seleção Operar no modo de backup seguro. Desmarque a caixa de seleção para sair do modo de instantâneo.
   * Use o script LCBackupMode (consulte [Fazer backup do banco de dados, do GDS e dos diretórios raiz do Armazenamento de conteúdo](/help/forms/using/admin-help/backing-aem-forms-data.md#back-up-the-database-gds-aem-repository-and-content-storage-root-directories)). Para sair do modo de backup de snapshot, no argumento de script, defina o parâmetro `continuousCoverage` como `false` ou use a opção `leaveContinuousCoverage`.
   * Use a API de backup/recuperação fornecida. <!-- Fix broken link(see AEM forms API Reference section on AEM Forms Help and Tutorials page).-->

* **O modo de** backup em andamento indica que o sistema está sempre no modo de backup, com uma nova sessão de modo de backup sendo iniciada assim que a sessão anterior for lançada. Nenhum tempo limite está associado ao modo de backup em andamento. Quando o script ou as APIs LCBackupMode são chamados para sair do modo de backup em andamento, uma nova sessão do modo de backup em andamento é iniciada. Esse modo é útil para suportar backups contínuos, mas ainda permite que documentos antigos e desnecessários sejam limpos do diretório GDS. O modo de backup em andamento não é suportado pela página Backup e Recuperação. Após um cenário de recuperação, o modo de backup continuado é ativado. Você pode sair do modo de backup contínuo (modo de backup em andamento) usando o script LCBackupMode com a opção `leaveContinuousCoverage`.

>[!NOTE]
>
>Deixar o modo de backup em andamento faz com que uma nova sessão do modo de backup seja iniciada imediatamente. Para desativar completamente o modo de backup em andamento, use a opção `leaveContinuousCoverage` no script, que substitui a sessão de backup em andamento existente. Quando estiver no modo de backup de snapshot, você poderá sair do modo de backup como costuma sair.

Para evitar a perda de dados, o backup dos dados específicos dos formulários AEM deve ser feito de forma a garantir que os documentos do diretório raiz do Armazenamento de conteúdo e GDS estejam correlacionados com as referências do banco de dados.

>[!NOTE]
>
>Quando o GDS for armazenado no sistema de arquivos e não no banco de dados, execute o backup do banco de dados antes do backup GDS.

## Considerações especiais para backup e recuperação {#special-considerations-for-backup-and-recovery}

Use as seguintes diretrizes se precisar recuperar formulários AEM em outro ambiente devido às seguintes alterações:

* Alteração no endereço IP, nome do host ou porta do servidor de formulários AEM
* Alteração nas letras da unidade ou no caminho do diretório
* Alterar para um host, porta ou nome de banco de dados diferente

Normalmente, esses cenários de recuperação são causados por falha de hardware do servidor que hospeda o servidor de aplicativos, o servidor de banco de dados ou o servidor de formulários. Além das configurações específicas para formulários AEM descritas nesta seção, você também deve fazer as alterações necessárias para outras partes da implantação de formulários AEM, como balanceadores de carga e firewalls, se o nome do host ou endereço IP de um servidor de formulários AEM for alterado.

### O que não pode ser alterado {#what-cannot-be-changed}

Embora seja possível alterar o servidor de banco de dados e muitos outros parâmetros, não é possível alterar o tipo de servidor de aplicativos ou de banco de dados ao recuperar formulários AEM de um backup. Por exemplo, se você estiver recuperando um backup de formulários AEM, não poderá alterar o servidor de aplicativos de JBoss para WebLogic ou banco de dados de Oracle para DB2. Além disso, os formulários AEM recuperados devem usar os mesmos caminhos do sistema de arquivos, como o diretório de fontes.

### Reiniciando após uma recuperação {#restarting-after-a-recovery}

Antes de reiniciar o servidor de formulários após uma recuperação, faça o seguinte:

1. Start o sistema no modo de manutenção.
1. Faça o seguinte para garantir que o Gerenciador de formulários seja sincronizado com formulários AEM no modo de manutenção:

   1. Acesse https://&lt;*server*>:&lt;*port*>/lc/fm e faça logon usando as credenciais de administrador/senha.
   1. Clique no nome do usuário (neste caso, Super Administrador) no canto superior direito.
   1. Clique em **Opções de administração**.
   1. Clique em **Start** para sincronizar ativos do repositório.

1. Em um ambiente clusterizado, o nó primário (com relação ao AEM) deve estar ativo antes dos nós secundários.
1. Certifique-se de que nenhum processo seja iniciado de fontes internas ou externas, como iniciadores de processos da Web, SOAP ou EJB, até que a operação normal do sistema seja validada.

Se o banco de dados dos formulários principais AEM for movido ou alterado, consulte os Guias de instalação relevantes ao servidor de aplicativos para obter informações sobre a atualização das informações de conexão do banco de dados das fontes de dados dos formulários AEM IDP_DS e EDC_DS.

### Alteração do nome do host ou endereço IP dos formulários AEM {#changing-the-aem-forms-hostname-or-ip-address}

Em um cluster, se você usar o cache TCP em vez de UDP, precisará atualizar a configuração do localizador de cache. Consulte &quot;Configuração dos localizadores de cache (cache usando apenas TCP)&quot; no guia de configuração relevante para o servidor de aplicativos.

### Alteração dos caminhos do sistema de arquivos do nó de formulários AEM {#changing-the-aem-forms-node-file-system-paths}

Se você alterar os caminhos do sistema de arquivos para um nó independente, deverá atualizar as referências apropriadas nas preferências, outras configurações do sistema, aplicativos personalizados e aplicativos de formulários AEM implantados. Por outro lado, para um cluster, todos os nós devem usar a mesma configuração de caminho do sistema de arquivos. Você deve definir o diretório raiz GDS (Global Documento Armazenamento) e garantir que ele aponte para uma cópia do GDS recuperado que esteja em sincronia com o banco de dados recuperado. A configuração do caminho GDS é importante porque o GDS pode conter dados destinados a persistir nas reinicializações do servidor de aplicativos.

Em um ambiente clusterizado, a configuração do caminho do sistema de arquivos do repositório deve ser a mesma para todos os nós do cluster antes do backup e após a recuperação.

Use o script `LCSetGDS`na pasta `[*aem-forms root]*\sdk\misc\Foundation\SetGDSCommandline` para definir o caminho GDS depois de alterar os caminhos do sistema de arquivos. Consulte o arquivo `ReadMe.txt` na mesma pasta para obter detalhes. Se o caminho do diretório GDS antigo não puder ser usado, o script `LCSetGDS` deverá ser usado para definir o novo caminho para o GDS antes que você start formulários AEM.

>[!NOTE]
>
>Essa circunstância é a única sob a qual você deve usar esse script para alterar a localização do GDS. Para alterar o local do GDS enquanto AEM formulários estiver em execução, use o Console de administração. (Consulte [Configurar definições gerais AEM formulários](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings)*.) *

Depois de definir o caminho GDS, start o servidor de formulários no modo de manutenção e use o console de administração para atualizar os caminhos do sistema de arquivos restantes para o novo nó. Depois de verificar se todas as configurações necessárias foram atualizadas, reinicie e teste os formulários AEM.
