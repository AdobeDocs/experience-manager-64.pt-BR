---
title: Usar páginas da Web de segurança do documento
seo-title: Using the document security webpages
description: Saiba como fazer logon, navegar e usar as páginas da Web de segurança do documento.
seo-description: Learn how you can login, navigate and use the document security web pages.
uuid: b4863343-cda5-474a-a101-a20e39b1f8c7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 2878b145-e6c0-48d3-810c-3540de13c826
feature: Document Security
exl-id: f93d496e-6bd3-462a-b57a-80085647a636
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 0%

---

# Usar páginas da Web de segurança do documento {#using-the-document-security-webpages}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Os usuários e administradores usam as páginas da Web de segurança de documentos para criar e gerenciar políticas, gerenciar documentos protegidos por políticas e monitorar eventos associados a documentos protegidos por políticas. Os administradores também usam as páginas da Web para criar conjuntos de políticas e designar coordenadores de conjuntos de políticas, configurar configurações padrão de segurança de documentos, gerenciar registros de usuários convidados e contas, além de monitorar e gerenciar eventos relacionados a servidor, política, usuário e documento.

>[!NOTE]
>
>Também é possível fazer logon na segurança do documento por meio do Acrobat e de outros aplicativos cliente usando a conta de logon do usuário. (Consulte [Configuração do acesso à segurança de documentos a partir de aplicativos clientes](using-document-security-web-pages.md#setting-up-access-to-document-security-from-client-applications).)

Para abrir as páginas da Web, você precisa de um navegador e o URL e suas informações de logon para a segurança do documento. O URL para usuários é diferente do URL para administradores.

Como a segurança dos documentos faz referência aos diretórios existentes de sua organização para obter informações sobre o usuário, as informações de logon da segurança do documento podem ser as mesmas que você usa para fazer logon na rede e em outros aplicativos. Consulte o administrador do sistema ou o administrador para obter as informações da sua conta.

Para fazer logon como administrador, é necessário ter a função de administrador atribuída a você. Você pode usar a conta de superadministrador padrão criada durante o processo de instalação.

## Fazer logon nas páginas da Web {#log-in-to-the-web-pages}

Para fazer logon nas páginas da Web usando um navegador, você precisa do URL de segurança do documento e de uma conta. O URL para usuários é diferente do URL para administradores. Os administradores também podem fazer logon nas páginas do usuário para criar políticas.

Se você tiver acesso a mais de uma instalação de segurança de documento, precisará do URL para a instância de segurança de documento que deseja acessar. Consulte o administrador se não tiver essas informações. O URL padrão das páginas de usuário é https://*[host]*:*[porta]*/edc. O número da porta pode não ser necessário em alguns casos. Peça detalhes ao administrador.

O URL padrão para administradores é https://*[host]*:*[porta]*/adminui.

Para administradores, uma conta de superadministrador padrão é criada durante a instalação. Você pode usar essa conta para fazer logon quando a segurança do documento for instalada pela primeira vez.

>[!NOTE]
>
>Você também pode acessar as páginas da Web do Acrobat e de outros aplicativos clientes. Consulte Ajuda do Acrobat ou a Ajuda das extensões do Acrobat Reader DC apropriada para obter detalhes.

1. Digite o URL no seu navegador:

   URL de segurança do documento: `https://`*[host ]*`:`*[porta]* `/edc`

   ou URL do Console de administração: `https://`*[host ]*`:`*[porta]* `/adminui`

1. Na janela de logon, digite o nome de usuário e a senha e clique em OK.
1. No Console de Administração, clique em Serviços > segurança do documento.

>[!NOTE]
>
>Ao trabalhar com as páginas da Web, evite usar os botões do navegador, como o botão Voltar, o botão Atualizar e as setas para trás e para a frente, pois essa ação pode causar problemas indesejados de captura de dados e de exibição de dados.

## Navegação das páginas da Web {#navigating-the-web-pages}

Ao fazer logon nas páginas da Web do usuário, você verá links para as páginas de usuário Políticas, Documentos e Eventos .

Ao fazer logon no console de administração e navegar até a página principal de segurança do documento, você também pode ver um ou dois links adicionais, um para a página Configuração e outro para a página Usuários convidados e locais. A página Usuários convidados e locais é exibida somente se o registro de usuário convidado estiver ativado.

Use esses links para acessar as várias páginas, onde você cria e gerencia políticas e documentos protegidos por políticas.

**Exibir uma página**

1. Clique no nome da página; como políticas de clique.

**Voltar para a página anterior**

1. Clique no link de navegação na parte superior da página para a página que você deseja voltar.

**Atualizar a listagem de dados em uma página**

1. Na página principal, clique no link da página que deseja atualizar.

>[!NOTE]
>
>Ao trabalhar com as páginas da Web, evite usar os botões do navegador, como o botão Voltar, o botão Atualizar e as setas para trás e para a frente, pois essa ação pode causar problemas indesejados de captura de dados e de exibição de dados.

## Configuração do acesso à segurança de documentos a partir de aplicativos clientes {#setting-up-access-to-document-security-from-client-applications}

Os aplicativos cliente devem ser configurados para se conectar à segurança do documento para proteger documentos, abrir documentos protegidos por política e se conectar às páginas da Web de segurança do documento. Consulte *Ajuda do Acrobat* ou *Ajuda do RightsManagementExtension* para obter informações sobre como configurar a conexão dentro do aplicativo cliente.

A segurança do documento é acessada via SSL (Secure Sockets Layer). Você deve instalar o certificado do site no armazenamento de certificados para poder acessar a segurança do documento por meio dos aplicativos clientes.

<!-- Fix broken link See Configuring SSL for information on SSL.-->

Essas instruções são específicas do Internet Explorer, mas você pode instalar o certificado usando qualquer navegador da Web compatível. Para obter mais informações, consulte a Ajuda do seu navegador.

**Instalar o certificado do servidor usando o Internet Explorer**

1. Abra o navegador da Web e digite o URL básico para a segurança do documento na caixa Endereço. Por exemplo, digite `https://[host]:[port]`. Uma caixa de diálogo Alerta de segurança é exibida.
1. Clique em Exibir certificado e, em seguida, clique em Instalar certificado e selecione os padrões para instalação. O certificado precisa ser instalado nas Autoridades de Certificação Raiz Confiáveis.
1. Feche a sessão do navegador.
1. Abra outra janela do navegador e digite o mesmo URL na caixa Endereço. Uma caixa de diálogo Alerta de segurança não deve ser exibida. Este teste confirma que o certificado está instalado corretamente.

## Saia das páginas da Web {#log-out-of-the-web-pages}

Faça logoff quando terminar de usar as páginas da Web para usar com segurança seu navegador da Web para outros fins. Dependendo de como a segurança do documento está configurada, talvez seja necessário fechar o navegador para encerrar a sessão completamente.

1. No canto superior direito da página, clique em Logout.
1. Se uma mensagem for exibida na página Logout , feche a janela do navegador para fazer logoff. Caso contrário, você poderá continuar a usar o navegador para outros fins.
