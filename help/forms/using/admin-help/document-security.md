---
title: 'Sobre a segurança do documento '
seo-title: 'Sobre a segurança do documento '
description: Saiba como criar, armazenar e aplicar configurações de confidencialidade predefinidas e distribuir suas informações com segurança usando a segurança do documento.
seo-description: Saiba como criar, armazenar e aplicar configurações de confidencialidade predefinidas e distribuir suas informações com segurança usando a segurança do documento.
uuid: 31b0c24f-a588-44f7-a9ba-e9780e82c066
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 46847c9f-c66d-46fa-8ff5-a99d2462c099
feature: Document Security
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '2548'
ht-degree: 0%

---


# Sobre a segurança do documento {#about-document-security}

A segurança de documentos garante que somente usuários autorizados possam usar seus documentos. Usando a segurança de documentos, você pode distribuir com segurança todas as informações salvas em um formato compatível. Os formatos de arquivo compatíveis incluem:

* Arquivos Adobe PDF
* Arquivos do Microsoft® Word, Excel e PowerPoint

Para obter mais informações sobre como as políticas protegem os tipos de arquivos suportados, consulte [Informações adicionais sobre segurança de documentos](https://www.adobe.com/go/learn_aemforms_doc_security_63).

Usando a segurança de documentos, você pode criar, armazenar e aplicar facilmente configurações de confidencialidade predefinidas a seus documentos. Para evitar que as informações se espalhem além do seu alcance, você também pode monitorar e controlar como os recipients usam seus documentos depois de distribuí-los.

Você pode proteger documentos usando políticas. Uma *política* é uma coleção de informações que inclui configurações de confidencialidade e uma lista de usuários autorizados. As configurações de confidencialidade especificadas em uma política determinam como um destinatário pode usar um documento ao qual você aplica a política. Por exemplo, você pode especificar se os destinatários podem imprimir ou copiar texto, editar texto ou adicionar assinaturas e comentários a documentos protegidos.

Os usuários de segurança de documentos criam políticas por meio das páginas da Web do usuário final. Os administradores usam as páginas da Web de segurança de documentos para criar conjuntos de políticas que contêm políticas compartilhadas disponíveis para todos os usuários autorizados.

Embora as políticas sejam armazenadas na segurança do documento, você as aplica a documentos por meio do aplicativo cliente. Como aplicar políticas a documentos PDF é descrito detalhadamente em *Ajuda do Acrobat*. A aplicação de políticas usando outros aplicativos, como o Microsoft Office, está documentada na *Ajuda de extensões do Acrobat Reader DC* para o aplicativo.

Quando você aplica uma política a um documento, as configurações de confidencialidade especificadas na política protegem as informações que o documento contém. As configurações de confidencialidade também protegem quaisquer arquivos (texto, áudio ou vídeo) dentro de um documento PDF. Você pode distribuir o documento protegido por política para recipients autorizados pela política.

**Controle de acesso a documentos e auditoria**

Usar uma política para proteger um documento dá a você controle contínuo sobre esse documento, mesmo após distribuí-lo. Você pode monitorar o documento, fazer alterações na política, impedir que os usuários continuem acessando o documento e mudar a política aplicada ao documento.

Por meio da segurança do documento, é possível monitorar documentos protegidos por políticas e rastrear eventos, como quando um usuário autorizado ou não autorizado tenta abrir o documento.

**Componentes**

A segurança do documento consiste em um servidor e interface do usuário:

**Servidor:** o componente central pelo qual a segurança de documentos executa transações, como autenticação de usuário, gerenciamento em tempo real de políticas e aplicação de confidencialidade. O servidor também fornece um repositório central para políticas, registros de auditoria e outras informações relacionadas.

**Páginas da Web:** a interface em que você cria políticas, gerencia documentos protegidos por políticas e monitora eventos associados a documentos protegidos por políticas. Os administradores também podem configurar opções globais, como autenticação de usuários, auditoria e mensagens para usuários convidados, e gerenciar contas de usuários convidados.

![rm_psworkflow](assets/rm_psworkflow.png)

As etapas na ilustração são as seguintes:

1. O proprietário do documento cria políticas usando as páginas da Web. Os proprietários de documentos podem criar políticas pessoais que são acessíveis somente para eles. Os administradores e os coordenadores de conjunto de políticas podem criar políticas compartilhadas em conjuntos de políticas que são acessíveis aos usuários autorizados.
1. O proprietário do documento aplica a política e, em seguida, salva e distribui o documento. O documento pode ser distribuído por e-mail, por meio de uma pasta de rede ou em um site.
1. O recipient abre o documento no aplicativo do cliente apropriado. O recipient pode usar o documento de acordo com sua política.
1. O proprietário do documento, o coordenador do conjunto de políticas ou o administrador pode rastrear documentos e modificar o acesso a eles usando as páginas da Web.

## Sobre usuários de segurança de documentos {#about-document-security-users}

Vários tipos de usuários trabalham com a segurança do documento para realizar tarefas diferentes:

* O administrador do sistema ou outra pessoa do sistema de informações (IS) instala e configura a segurança do documento. Essa pessoa também pode ser responsável por definir configurações globais para o servidor, páginas da Web e políticas e documentos.

   Essas configurações podem incluir, por exemplo, um URL de segurança do documento básico, notificações de auditoria e privacidade, avisos de registro de usuário convidados e períodos padrão de concessão offline.

* Os administradores de segurança de documentos criam políticas e conjuntos de políticas e gerenciam documentos protegidos por políticas para usuários, conforme necessário. Eles também criam contas de usuário convidadas e monitoram sistema, documento, usuário, política, conjunto de políticas e eventos personalizados. Eles também podem ser responsáveis pela configuração do servidor global, da página da Web e das configurações de política junto com um administrador do sistema.

   Os administradores podem atribuir aos usuários as seguintes funções na área Gerenciamento de usuários do console de administração. Os usuários atribuídos a essas funções executam suas tarefas na área da interface de usuário de segurança de documentos do console de administração.

   **Superadministrador de segurança do documento**

   Os usuários com essa função têm acesso a todas as configurações de segurança de documentos no console de administração. Essas permissões estão associadas à função :

   * Gerenciar configuração
   * Gerenciar política
   * Gerenciar conjuntos de políticas
   * Gerenciar documentos
   * Gerenciar editores de documento
   * Gerenciar usuários convidados e locais
   * Exibir eventos
   * Delegar
   * Convidar usuários externos

   **Administrador de segurança do documento**

   Os usuários com essa função podem configurar o servidor de segurança de documentos usando a página Configuração na seção de segurança de documentos do console de administração. Essa permissão está associada à função Gerenciar configuração.

   >[!NOTE]
   >
   >Os usuários com essa função também devem ter a função Usuário do console de administração para poder fazer logon no console de administração e editar quaisquer configurações relacionadas à configuração.

   **Administrador do conjunto de políticas de segurança do documento**

   Os usuários com essa função podem usar a seção segurança do documento do console de administração para editar as políticas de outros usuários e para criar, editar e excluir conjuntos de políticas. Quando um administrador de conjunto de políticas cria um conjunto de políticas, ele pode atribuir um coordenador de conjunto de políticas a esse conjunto de políticas. Essas permissões estão associadas à função :

   * Gerenciar política
   * Gerenciar conjuntos de políticas
   * Gerenciar documentos
   * Gerenciar editores de documento
   * Exibir eventos
   * Delegar

   >[!NOTE]
   >
   >Os usuários com essa função também devem ter a função Usuário do console de administração para poder fazer logon no console de administração e editar quaisquer configurações relacionadas à configuração.

   **Gerenciamento de segurança de documentos usuários convidados e locais**

   Os usuários com essa função podem executar tarefas necessárias para gerenciar todos os usuários convidados e locais nas páginas da Web de segurança de documentos relevantes. Essas permissões estão associadas à função :

   * Gerenciar usuários convidados e locais
   * Convidar usuários externos
   * Acessar páginas da Web do usuário final

   >[!NOTE]
   >
   >Os usuários com essa função também devem ter a função Usuário do console de administração para poder fazer logon no console de administração e editar quaisquer configurações relacionadas à configuração.

   **Usuário do convite para segurança de documentos**

   Os usuários com essa função podem convidar usuários. Essas permissões estão associadas à função :

   * Convidar usuários externos
   * Acessar páginas da Web do usuário final

   **Usuário final de segurança do documento**

   Os usuários com essa função podem acessar as páginas da Web do usuário final de segurança do documento. Essa função também pode ser atribuída aos administradores para permitir que eles criem políticas usando as páginas do usuário final. Essa permissão está associada à função Acessar páginas da Web do usuário final.

* Os usuários da organização que têm contas de segurança de documentos válidas criam suas próprias políticas, usam políticas para proteger documentos, rastreiam e gerenciam seus documentos protegidos por políticas e monitoram eventos relacionados a seus documentos.
* Os coordenadores de conjuntos de políticas gerenciam documentos, exibem eventos e gerenciam outros coordenadores de conjuntos de políticas (com base em suas permissões). Os administradores designam os utilizadores como coordenadores de conjuntos de políticas para determinados conjuntos de políticas.
* Os usuários externos à sua organização (por exemplo, um parceiro comercial) podem usar documentos protegidos por políticas se estiverem no diretório de segurança do documento de segurança, se o administrador criar uma conta para eles ou se se registrarem na segurança do documento por meio de um processo automatizado de convite por email. Dependendo de como o administrador habilita as configurações de acesso, os usuários convidados também podem ter permissão para aplicar políticas a documentos, criar, modificar e excluir suas políticas e convidar outros usuários externos para usar seus documentos protegidos por políticas.
* Os desenvolvedores usam o SDK de formulários AEM para integrar aplicativos personalizados à segurança de documentos.

Os administradores de segurança de documentos podem criar funções personalizadas usando as seguintes permissões no Gerenciamento de usuários:

* Configuração do Gerenciador de Segurança de Documento
* Segurança de documentos Gerenciar usuários convidados e locais
* Conjuntos de políticas de gerenciamento de segurança de documentos
* Conjuntos de políticas de gerenciamento de segurança de documentos
* Eventos do Servidor de Visualização de Segurança de Documentos
* Proprietário da Política de Alteração de Segurança do Documento

## Políticas e documentos protegidos por políticas {#policies-and-policy-protected-documents}

Uma *policy* define um conjunto de configurações de confidencialidade e usuários que podem acessar um documento ao qual a política é aplicada. Uma política também permite que as permissões em um documento sejam alteradas dinamicamente. Fornece à pessoa que protege o documento permissão para alterar as configurações de confidencialidade para revogar o acesso ao documento ou para alterar a política.

A proteção de política pode ser aplicada a um documento PDF usando o Adobe Acrobat® Pro e o Acrobat Standard. A proteção de políticas pode ser aplicada a outros tipos de arquivos, como arquivos do Microsoft Word, Excel e PowerPoint, usando o aplicativo cliente com as extensões adequadas do Acrobat Reader DC instaladas.

### Como as políticas funcionam {#how-policies-work}

As políticas contêm informações sobre os usuários autorizados e as configurações de confidencialidade a serem aplicadas aos documentos. Os usuários podem ser qualquer pessoa em sua organização, bem como pessoas externas à organização que têm uma conta. Se o administrador ativar o recurso de convite do usuário, será possível adicionar novos usuários às políticas, iniciando um processo de email de convite de registro.

As configurações de confidencialidade em uma política determinam como os destinatários podem usar o documento. Por exemplo, você pode especificar se os destinatários podem imprimir ou copiar texto, fazer alterações ou adicionar assinaturas e comentários a documentos protegidos. A mesma política também pode especificar configurações de confidencialidade diferentes para usuários específicos.

>[!NOTE]
>
>As configurações de confidencialidade aplicadas por meio de uma política substituem quaisquer configurações que possam ter sido aplicadas a um documento PDF no Acrobat usando as opções de segurança de senha ou certificado. (Consulte a Ajuda do Acrobat para obter mais informações.)

Usuários e administradores criam políticas por meio das páginas da Web de segurança de documentos. Somente uma política de cada vez pode ser aplicada a um documento. É possível aplicar uma política usando um destes métodos:

* Abra o documento no Acrobat ou em outro aplicativo cliente e selecione uma política para proteger o documento.
* Envie um documento como anexo de email no Microsoft Outlook. Nesse caso, você pode selecionar uma política de uma lista de políticas ou selecionar uma política gerada automaticamente que o Acrobat crie com um conjunto padrão de configurações de confidencialidade para proteger o documento somente para os recipients da mensagem de email.

Uma política pode ser removida de um documento usando o aplicativo cliente.

![rm_psonline_policy](assets/rm_psonline_policy.png)

As etapas no diagrama são as seguintes:

1. O proprietário do documento protege o documento de um aplicativo cliente suportado com uma política que permite o uso online.
1. A segurança de documentos cria uma licença de documento e chaves de documento e criptografa a política. A licença do documento, a política criptografada e a chave do documento são retornadas ao aplicativo cliente.
1. O documento é criptografado com a chave do documento e a chave do documento é descartada. O documento agora incorpora a licença e a política. Essas tarefas são executadas no aplicativo cliente suportado.

Quando você aplica uma política a um documento, as informações que o documento contém, incluindo quaisquer arquivos contidos (texto, áudio ou vídeo) em documentos PDF, são protegidas pelas configurações de confidencialidade especificadas na política. A segurança do documento gera uma licença e informações de criptografia incorporadas ao documento. Ao distribuir o documento, a segurança do documento pode autenticar os recipients que tentarem abrir o documento e autorizar o acesso de acordo com os privilégios especificados na política.

Se o uso offline estiver ativado, os recipients também poderão usar documentos protegidos por política offline (sem uma conexão ativa de Internet ou de rede) pelo período especificado na política.

### Como os documentos protegidos por política funcionam {#how-policy-protected-documents-work}

Para abrir e usar documentos protegidos por políticas, a política deve incluir seu nome como destinatário e você deve ter uma conta de segurança de documento válida. Para documentos PDF, você precisa do Acrobat ou Adobe Reader®. Para outros tipos de arquivos, você precisa do aplicativo apropriado para o arquivo com as extensões do Acrobat Reader DC instaladas.

Ao tentar abrir um documento protegido por política, o Acrobat, o Adobe Reader ou as extensões do Acrobat Reader DC conectam-se à segurança do documento para autenticá-lo. Em seguida, você pode continuar a fazer logon. Se o uso do documento estiver sendo auditado, uma mensagem de notificação será exibida. Depois que a segurança do documento determina quais permissões de documento conceder, ele gerencia a descriptografia do documento. Você pode então usar o documento de acordo com as configurações de confidencialidade da política.

![rm_psopen_online](assets/rm_psopen_online.png)

As etapas no diagrama são as seguintes:

1. O usuário do documento abre o documento em um aplicativo cliente suportado e se autentica no servidor. O identificador de documento é enviado ao servidor de segurança do documento.
1. A segurança do documento autentica os usuários, verifica a política para autorização e cria um comprovante. O comprovante (que contém a chave do documento e as permissões) é retornado ao aplicativo cliente.
1. O documento é descriptografado com a chave do documento e a chave do documento é descartada. O documento pode então ser usado de acordo com as configurações de confidencialidade da política. Essas tarefas são executadas no aplicativo cliente suportado.

Você pode continuar usando um documento sob estas condições:

* Indefinidamente ou para o período de validade especificado na política
* Até que o administrador ou a pessoa que aplicou a política revogue o acesso ao documento ou altere a política

Também é possível usar documentos protegidos por políticas offline (sem uma conexão de Internet ou de rede) se a política permitir acesso offline. Primeiro, você deve fazer logon na segurança do documento para sincronizar o documento. Você pode então usar o documento pela duração do período de concessão offline especificado na política.

Quando o período de concessão offline terminar, você deverá sincronizar o documento com a segurança do documento novamente, entrando online e abrindo um documento protegido por política ou usando um comando no aplicativo cliente. (Consulte *Ajuda do Acrobat* ou a *Ajuda do Acrobat Reader DC Extensions* apropriada para obter detalhes.)

Se você salvar uma cópia de um documento protegido por política usando o comando de menu Salvar ou Salvar como, a política será automaticamente aplicada e aplicada ao novo documento. Eventos como tentativas de abrir o novo documento também são auditados e registrados para o documento original.

## Conjuntos de políticas {#policy-sets}

*Os* conjuntos de políticas são utilizados para agrupar um conjunto de políticas que têm um objetivo comercial comum. Esses conjuntos de políticas são então disponibilizados a um subconjunto de usuários no sistema.

Cada conjunto de políticas pode ter um ou mais coordenadores de conjunto de políticas associados. O coordenador do conjunto de políticas é um administrador ou usuário com permissões adicionais. O *coordenador do conjunto de políticas* normalmente é um especialista na organização que pode criar melhor as políticas em um conjunto de políticas específico.

Os coordenadores do conjunto de políticas podem executar estas tarefas:

* Criar novas políticas
* Editar e excluir qualquer política no conjunto de políticas
* Editar configurações do conjunto de políticas
* Adicionar e remover coordenadores de conjunto de políticas
* Exibir eventos de política e documento para qualquer política ou documento dentro do conjunto de políticas
* Revogar acesso a documentos
* Alternar políticas para o documento.

Os conjuntos de políticas são criados e excluídos nas páginas da Web da administração de segurança de documentos por administradores e coordenadores de conjuntos de políticas que têm permissão para isso.

Os conjuntos de políticas geralmente são disponibilizados a um número limitado de usuários, especificando quais usuários ou grupos em um domínio podem usar as políticas do conjunto de políticas para proteger documentos.

Quando a segurança do documento é instalada, um conjunto de políticas padrão é criado chamado *Conjunto de Políticas Global*. O administrador que instalou o software gerencia esse conjunto de políticas.
