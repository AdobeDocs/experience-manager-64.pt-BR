---
title: Configurando SSL para WebSphere Application Server
seo-title: Configuring SSL for WebSphere Application Server
description: Saiba como configurar o SSL para o WebSphere Application Server.
seo-description: Learn how to configure SSL for WebSphere Application Server.
uuid: f939a806-346e-41e0-b2c0-6d0ba83f8f6f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 7c0efcb3-5b07-4090-9119-b7318c8b7980
exl-id: 653daaa4-9e35-40eb-a61e-274109f5f0d2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1263'
ht-degree: 1%

---

# Configurando SSL para WebSphere Application Server {#configuring-ssl-for-websphere-application-server}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Esta seção inclui as seguintes etapas para configurar o SSL com seu IBM WebSphere Application Server.

## Criando uma conta de usuário local no WebSphere {#creating-a-local-user-account-on-websphere}

Para habilitar o SSL, o WebSphere precisa de acesso a uma conta de usuário no registro de usuário do SO local que tenha permissão para administrar o sistema:

* (Windows) Crie um novo usuário do Windows que faça parte do grupo Administradores e tenha o privilégio de agir como parte do sistema operacional. (Consulte [Criar um usuário do Windows para WebSphere](configuring-ssl-websphere-application-server.md#create-a-windows-user-for-websphere).)
* (Linux, UNIX) O usuário pode ser um usuário raiz ou outro usuário que tenha privilégios de raiz. Ao habilitar o SSL no WebSphere, use a identificação do servidor e a senha desse usuário.

### Criar um usuário Linux ou UNIX para WebSphere {#create-a-linux-or-unix-user-for-websphere}

1. Faça logon como o usuário raiz.
1. Crie um usuário inserindo o seguinte comando em um prompt de comando:

   * (Linux e Sun Solaris) `useradd`
   * (IBM AIX) `mkuser`

1. Defina a senha do novo usuário inserindo `passwd` no prompt de comando.
1. (Linux e Solaris) Crie um arquivo de senha de sombra inserindo `pwconv` (sem parâmetros) no prompt de comando.

   >[!NOTE]
   >
   >(Linux e Solaris) Para que o registro de segurança do SO local do WebSphere Application Server funcione, é necessário que exista um arquivo de senha de sombra. O arquivo de senha de sombra geralmente é nomeado **/etc/shadow*** e se baseia no arquivo /etc/passwd. Se o arquivo de senha de sombra não existir, ocorrerá um erro após habilitar a segurança global e configurar o registro do usuário como SO local.*

1. Abra o arquivo de grupo do diretório /etc em um editor de texto.
1. Adicione o usuário que você criou na etapa 2 à `root` grupo.
1. Salve e feche o arquivo.
1. (UNIX com SSL habilitado) Inicie e pare o WebSphere como o usuário raiz.

### Criar um usuário do Windows para WebSphere {#create-a-windows-user-for-websphere}

1. Faça logon no Windows usando uma conta de usuário do administrador.
1. Selecionar **Iniciar > Painel de controle > Ferramentas administrativas > Gerenciamento do computador > Usuários e grupos locais**.
1. Clique com o botão direito do mouse em Usuários e selecione **Novo usuário**.
1. Digite um nome de usuário e senha nas caixas apropriadas e digite quaisquer outras informações necessárias nas caixas restantes.
1. Desmarcar **O Usuário Deve Alterar A Senha No Próximo Logon**, clique em **Criar** e, em seguida, clique em **Fechar**.
1. Clique em **Usuários**, clique com o botão direito do mouse no usuário que acabou de criar e selecione **Propriedades**.
1. Clique no botão **Membro de** e clique em **Adicionar**.
1. Na caixa Inserir os nomes de objetos a serem selecionados, digite `Administrators`, clique em Verificar nomes para garantir que o nome do grupo esteja correto.
1. Clique em **OK** e, em seguida, clique em **OK** novamente.
1. Selecionar **Iniciar > Painel de controle > Ferramentas administrativas > Política de segurança local > Políticas locais**.
1. Clique em Atribuição de direitos de usuário, clique com o botão direito do mouse em Agir como parte do sistema operacional e selecione Propriedades.
1. Clique em **Adicionar usuário ou grupo**.
1. Na caixa Inserir os nomes dos objetos a serem selecionados, digite o nome do usuário criado na etapa 4 e clique em **Verificar nomes** para garantir que o nome esteja correto, e clique em **OK**.
1. Clique em **OK** para fechar a caixa de diálogo Agir como parte das propriedades do sistema operacional.

### Configurar o WebSphere para usar o usuário recém-criado como Administrador {#configure-websphere-to-use-the-newly-created-user-as-administrator}

1. Certifique-se de que o WebSphere esteja em execução.
1. No Console Administrativo do WebSphere, selecione **Segurança > Segurança global**.
1. Em Segurança administrativa, selecione **Funções administrativas de usuário**.
1. Clique em Adicionar e faça o seguinte:

   1. Tipo **&amp;ast;** na caixa de pesquisa e clique em pesquisar.
   1. Clique em **Administrador** em funções.
   1. Adicione o usuário recém-criado à função Mapeado para e mapeie-o para Administrador.

1. Clique em **OK** e salve as alterações.
1. Reinicie o perfil do WebSphere.

## Habilitar segurança administrativa {#enable-administrative-security}

1. No Console Administrativo do WebSphere, selecione **Segurança > Segurança global**.
1. Clique em **Assistente de configuração de segurança**.
1. Garantir **Habilitar Segurança de Aplicativo** a caixa de seleção está ativada. Clique em **Avançar**.
1. Selecionar **Repositórios federados** e clique em **Próximo**.
1. Especifique as credenciais que deseja definir e clique em **Próximo**.
1. Clique em **Concluir**.
1. Reinicie o perfil do WebSphere.

   O WebSphere começará a usar o armazenamento de chaves padrão e o armazenamento de confiança.

## Habilitar SSL (chave personalizada e truststore) {#enable-ssl-custom-key-and-truststore}

Truststores e keystores podem ser criados usando o utilitário ikeyman ou o console de administração. Para que o keyman funcione corretamente, certifique-se de que o caminho de instalação do WebSphere não contenha parênteses.

1. No Console Administrativo do WebSphere, selecione **Segurança > Certificado SSL e gerenciamento de chaves**.
1. Clique em **Armazenamento de chaves e certificados** em Itens relacionados.
1. No **Uso do repositório de chaves** , certifique-se de **Armazenamento de chaves SSL** está selecionada. Clique em **Novo**.
1. Digite um nome lógico e uma descrição.
1. Especifique o caminho onde deseja criar o armazenamento de chaves. Se você já criou um armazenamento de chaves por meio do keyman, especifique o caminho para o arquivo do armazenamento de chaves.
1. Especifique e confirme a senha.
1. Escolha o tipo de armazenamento de chaves e clique em **Aplicar**.
1. Salve a configuração principal.
1. Clique em **Certificado pessoal**.
1. Se você adicionou um armazenamento de chaves já criado usando o keyman, seu certificado será exibido. Caso contrário, é necessário adicionar um novo certificado autoassinado executando as seguintes etapas:

   1. Selecionar **Criar > Certificado autoassinado**.
   1. Especifique os valores apropriados no formulário de certificado. Certifique-se de manter o Alias e o nome comum como nome de domínio totalmente qualificado da máquina.
   1. Clique em **Aplicar**.

1. Repita as etapas de 2 a 10 para criar um truststore.

## Aplicar armazenamento de chaves e confiabilidade personalizados ao servidor {#apply-custom-keystore-and-truststore-to-the-server}

1. No Console Administrativo do WebSphere, selecione **Segurança > Certificado SSL e gerenciamento de chaves**.
1. Clique em **Gerenciar a configuração de segurança do ponto de extremidade**. O mapa de topologia local é aberto.
1. Em Entrada, selecione filho direto de nós.
1. Em Itens relacionados, selecione **Configurações de SSL**.
1. Selecionar **NodeDeafultSSLSetting**.
1. Nas listas suspensas nome do armazenamento confiável e nome do armazenamento de chaves , selecione o armazenamento confiável personalizado e o armazenamento de chaves que você criou.
1. Clique em **Aplicar**.
1. Salve a configuração principal.
1. Reinicie o perfil do WebSphere.

   Seu perfil agora é executado em configurações SSL personalizadas e seu certificado.

## Ativação do suporte para nativos de formulários AEM {#enabling-support-for-aem-forms-natives}

1. No Console Administrativo do WebSphere, selecione **Segurança > Segurança global**.
1. Na seção Autenticação , expanda **Segurança RMI/IIOP** e clique em **Comunicações de entrada CSIv2**.
1. Certifique-se de que **Suporte a SSL** está selecionada na lista suspensa Transporte .
1. Reinicie o perfil do WebSphere.

## Configuração do WebSphere para converter URLs que começam com https {#configuring-websphere-to-convert-urls-that-begins-with-https}

Para converter um URL que comece com https, adicione um certificado de assinante para esse URL ao servidor WebSphere.

**Criar um certificado de assinante para um site habilitado para https**

1. Certifique-se de que o WebSphere esteja em execução.
1. No Console Administrativo do WebSphere, navegue até Certificados do Assinante e clique em Segurança > Certificado SSL e Gerenciamento de Chave > Repositórios e Certificados de Chave > NodeDefaultTrustStore > Certificados do Assinante.
1. Clique em Recuperar da porta e execute estas tarefas:

   * Na caixa Host , digite o URL. Por exemplo, digite `www.paypal.com`.
   * Na caixa Porta, digite `443`. Essa porta é a porta SSL padrão.
   * Na caixa Alias, digite um alias.

1. Clique em Recuperar informações do assinante e verifique se as informações foram recuperadas.
1. Clique em Aplicar e em Salvar.

A conversão de HTML para PDF do site cujo certificado foi adicionado agora funcionará pelo serviço Gerar PDF.

>[!NOTE]
>
>Para um aplicativo se conectar a sites SSL de dentro do WebSphere, é necessário um certificado de Assinante. Ele é usado pelo Java Secure Socket Extensions (JSSE) para validar certificados que o lado remoto da conexão enviou durante um handshake SSL.

## Configuração de portas dinâmicas {#configuring-dynamic-ports}

O IBM WebSphere não permite várias chamadas para ORB.init() quando o Global Security está ativado. Você pode ler sobre a restrição permanente em https://www-01.ibm.com/support/docview.wss?uid=swg1PK58704.

Execute as seguintes etapas para definir a porta como dinâmica e resolver o problema:

1. No Console Administrativo do WebSphere, selecione **Servidores** > **Tipos de servidor** > **Servidor de aplicativos WebSphere**.
1. Na seção Preferências , selecione o servidor.
1. No **Configuração** guia , em **Comunicações** seção, expandir **Portas** e clique em **Detalhes**.
1. Clique nos seguintes nomes de porta, altere a variável **número da porta** para 0 e clique em **OK**.

   * `ORB_LISTENER_ADDRESS`
   * `SAS_SSL_SERVERAUTH_LISTENER_ADDRESS`
   * `CSIV2_SSL_SERVERAUTH_LISTENER_ADDRESS`
   * `CSIV2_SSL_MUTUALAUTH_LISTENER_ADDRESS`

## Configurar o arquivo sling.properties {#configure-the-sling-properties-file}

1. Abrir [aem-forms_root]\crx-repository\launchpad\sling.properties para edição.
1. Localize a variável `sling.bootdelegation.ibm` e adicionar `com.ibm.websphere.ssl.*`ao seu campo de valor. O campo atualizado tem a seguinte aparência:

   ```as3
   sling.bootdelegation.ibm=com.ibm.xml.*, com.ibm.websphere.ssl.*
   ```

1. Salve o arquivo e reinicie o servidor.
