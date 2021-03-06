---
title: Configure a marcação de ativos usando o Serviço de conteúdo inteligente.
description: Saiba como configurar a marcação inteligente e a marcação inteligente aprimorada no  [!DNL Adobe Experience Manager], usando o Serviço de conteúdo inteligente.
contentOwner: AG
feature: Tags inteligentes,Marcação
role: Admin
exl-id: 11c5dd92-f824-41d2-9ab2-b32bdeae01b6
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '1215'
ht-degree: 34%

---

# Configurar a marcação de ativos usando o Serviço de conteúdo inteligente {#configure-asset-tagging-using-the-smart-content-service}

Você pode integrar [!DNL Adobe Experience Manager] ao Serviço de conteúdo inteligente usando [!DNL Adobe Developer Console]. Use essa configuração para acessar o Serviço de conteúdo inteligente de dentro de [!DNL Experience Manager].

O artigo detalha as seguintes tarefas principais que são necessárias para configurar o Serviço de conteúdo inteligente. No back-end, o servidor [!DNL Experience Manager] autentica suas credenciais de serviço no gateway [!DNL Adobe Developer Console] antes de encaminhar sua solicitação ao Serviço de conteúdo inteligente.

1. [Crie uma configuração do ](#obtain-public-certificate) Serviço de conteúdo inteligente no  [!DNL Experience Manager] para gerar uma chave pública. [Obtenha um certificado público](#obtain-public-certificate) para a integração OAuth.

1. [Crie uma integração no Console do desenvolvedor](#create-adobe-i-o-integration) e faça upload da chave pública gerada.

1. [Configure sua ](#configure-smart-content-service) implantação usando a chave da API e outras credenciais do  [!DNL Adobe Developer Console].

1. [Teste a configuração](#validate-the-configuration).

1. Opcionalmente, [ative a marcação automática no upload de ativos](#enable-smart-tagging-in-the-update-asset-workflow-optional).

## Pré-requisitos {#prerequisites}

Antes de usar o Serviço de conteúdo inteligente, verifique o seguinte para criar uma integração em [!DNL Adobe Developer Console]:

* Existência de uma Adobe ID com privilégios de administrador para a organização.

* O Serviço de conteúdo inteligente está habilitado para sua organização.

Para ativar as Tags inteligentes aprimoradas, além do acima, instale também o [Experience Manager service pack](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=pt-BR) mais recente.

## Criar configuração do Serviço de conteúdo inteligente para obter o certificado público {#obtain-public-certificate}

Um certificado público permite autenticar seu perfil em [!DNL Adobe Developer Console].

1. Na interface do usuário [!DNL Experience Manager], acesse **[!UICONTROL Ferramentas]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Cloud Services herdadas]**.

1. Na página Cloud Services, clique em **[!UICONTROL Configurar agora]** em **[!UICONTROL Tags inteligentes de ativos]**.

1. Na caixa de diálogo **[!UICONTROL Criar configuração]**, especifique um título e um nome para a configuração de Tags inteligentes. Clique em **[!UICONTROL Criar]**.

1. Na caixa de diálogo **[!UICONTROL AEM Serviço de Conteúdo Inteligente]**, use os seguintes valores:

   **[!UICONTROL URL do serviço]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Servidor de autorização]**: `https://ims-na1.adobelogin.com`

   Deixe os outros campos em branco por enquanto (a ser fornecido posteriormente). Clique em **[!UICONTROL OK]**.

   ![Caixa de diálogo Serviço de conteúdo inteligente do Experience Manager para fornecer URL de serviço de conteúdo](assets/aem_scs.png)


   *Figura: Caixa de diálogo Serviço de conteúdo inteligente para fornecer URL de serviço de conteúdo*

   >[!NOTE]
   >
   >O URL fornecido como [!UICONTROL URL de serviço] não é acessível via navegador e gera um erro 404. A configuração funciona bem com o mesmo valor do parâmetro [!UICONTROL Service URL]. Para obter o status geral do serviço e o cronograma de manutenção, consulte [https://status.adobe.com](https://status.adobe.com).

1. Clique em **[!UICONTROL Baixar Certificado Público para Integração OAuth]** e baixe o arquivo de certificado público `AEM-SmartTags.crt`.

   ![Uma representação das configurações criadas para o serviço de marcação inteligente](assets/smart-tags-download-public-cert.png)


   *Figura: Configurações do serviço de marcação inteligente*

### Reconfigure quando um certificado expirar {#certrenew}

Depois que um certificado expira, ele não é mais confiável. Não é possível renovar um certificado expirado. Para adicionar um novo certificado, siga estas etapas.

1. Faça logon na implantação do [!DNL Experience Manager] como administrador. Clique em **[!UICONTROL Ferramentas]** > **[!UICONTROL Segurança]** > **[!UICONTROL Usuários]**.

1. Localize o usuário **[!UICONTROL dam-update-service]** e clique nele. Clique na guia **[!UICONTROL Armazenamento de chaves]**.

1. Exclua o armazenamento de chaves **[!UICONTROL similaritysearch]** existente com o certificado expirado. Clique em **[!UICONTROL Salvar e fechar]**.

   ![Exclua a entrada similaritysearch existente no Armazenamento de chaves para adicionar um novo certificado de segurança](assets/smarttags_delete_similaritysearch_keystore.png)

   *Figura: exclua a entrada `similaritysearch` existente no Armazenamento de chaves para adicionar um novo certificado de segurança.*

1. Navegue até **[!UICONTROL Ferramentas]** > **[!UICONTROL Serviços da nuvem]** > **[!UICONTROL Serviços da nuvem herdados]**. Clique em **[!UICONTROL Tags inteligentes de ativos]** > **[!UICONTROL Mostrar configuração]** > **[!UICONTROL Configurações disponíveis]**. Clique na configuração necessária.

1. Para baixar um certificado público, clique em **[!UICONTROL Baixar certificado público para integração OAuth]**.

1. Acesse [https://console.adobe.io](https://console.adobe.io) e navegue até os Serviços de conteúdo inteligente existentes na página **[!UICONTROL Integrações]**. Faça upload do novo certificado. Para obter mais informações, consulte as instruções em [Criar integração do Console do Desenvolvedor do Adobe](#create-adobe-i-o-integration).

## Criar integração com o Console do desenvolvedor do Adobe {#create-adobe-i-o-integration}

Para usar APIs do Serviço de conteúdo inteligente, crie uma integração no Console do desenvolvedor do Adobe para obter [!UICONTROL Chave da API] (gerada no campo [!UICONTROL ID do CLIENTE] da integração do Console do desenvolvedor do Adobe), [!UICONTROL ID DA CONTA TÉCNICA], [!UICONTROL ID DA ORGANIZAÇÃO] e [!UICONTROL CLIENT T] para [!UICONTROL Configurações do serviço de marcação inteligente de ativos] da configuração de nuvem em [!DNL Experience Manager].

1. Acesse [https://console.adobe.io](https://console.adobe.io/) em um navegador. Selecione a conta e verifique se a organização associada tem a função de administrador do sistema.

1. Crie um projeto com o nome que quiser. Clique em **[!UICONTROL Adicionar API]**.

1. Na página **[!UICONTROL Adicionar uma API]**, selecione **[!UICONTROL Experience Cloud]** e selecione **[!UICONTROL Conteúdo inteligente]**. Clique em **[!UICONTROL Avançar]**.

1. Selecione **[!UICONTROL Fazer upload da sua chave pública]**. Forneça o arquivo de certificado baixado do [!DNL Experience Manager]. Será exibida a mensagem [!UICONTROL Chave(s) pública(s) carregada(s) com êxito]. Clique em **[!UICONTROL Avançar]**.

   A página [!UICONTROL Criar uma nova credencial de conta de serviço (JWT)] exibe a chave pública da conta de serviço recém-configurada.

1. Clique em **[!UICONTROL Avançar]**.

1. Na página **[!UICONTROL Selecionar perfis de produtos]**, selecione **[!UICONTROL Serviços de conteúdo inteligente]**. Clique em **[!UICONTROL Salvar API configurada]**.

   Uma página exibe mais informações sobre a configuração. Mantenha essa página aberta para copiar e adicionar esses valores em [!UICONTROL Configurações do serviço de marcação inteligente de ativos] da configuração de nuvem em [!DNL Experience Manager] para configurar tags inteligentes.

   ![Na guia Visão geral, é possível revisar as informações da integração.](assets/integration_details.png)

   *Figura: Detalhes da integração no Console do desenvolvedor do Adobe*

## Configurar o Serviço de Conteúdo Inteligente {#configure-smart-content-service}

Para configurar a integração, use os valores dos campos [!UICONTROL TECHNICAL ACCOUNT ID], [!UICONTROL ORGANIZATION ID], [!UICONTROL CLIENT SECRET] e [!UICONTROL CLIENT ID] da integração do Console do Desenvolvedor do Adobe. Criar uma configuração de nuvem de Tags inteligentes permite a autenticação de solicitações de API da implantação [!DNL Experience Manager].

1. Em [!DNL Experience Manager], navegue até **[!UICONTROL Ferramentas > Cloud Service > Cloud Services herdados]** para abrir o console [!UICONTROL Cloud Services].

1. Em **[!UICONTROL Tags inteligentes do Assets]**, abra a configuração criada acima. Na página de configurações do serviço, clique em **[!UICONTROL Editar]**.

1. Na caixa de diálogo **[!UICONTROL Serviço de conteúdo inteligente do AEM]**, use os valores pré-preenchidos nos campos **[!UICONTROL URL do serviço]** e **[!UICONTROL Servidor de autorização]**.

1. Para os campos [!UICONTROL Chave da Api], [!UICONTROL ID da Conta Técnica], [!UICONTROL ID da Organização] e [!UICONTROL Segredo do Cliente], copie e use os seguintes valores gerados em [Integração do Console do Desenvolvedor](#create-adobe-i-o-integration).

   | [!UICONTROL Configurações do serviço de marcação inteligente de ativos] | [!DNL Adobe Developer Console] campos de integração |
   |--- |--- |
   | [!UICONTROL Chave da API] | [!UICONTROL ID DO CLIENTE] |
   | [!UICONTROL ID da conta técnica] | [!UICONTROL ID DA CONTA TÉCNICA] |
   | [!UICONTROL ID da organização] | [!UICONTROL ID DA ORGANIZAÇÃO] |
   | [!UICONTROL Client Secret] | [!UICONTROL SEGREDO DO CLIENTE] |

## Validar a configuração {#validate-the-configuration}

Após concluir a configuração, use um MBean JMX para validar a configuração. Para validar, siga estas etapas.

1. Acesse seu servidor [!DNL Experience Manager] em `https://[aem_server]:[port]`.

1. Vá para **[!UICONTROL Tools > Operations > Web Console]** para abrir o console OSGi. Clique em **[!UICONTROL Principal > JMX]**.

1. Clique em **[!UICONTROL com.day.cq.dam.similaritysearch.internal.impl]**. Ele abre **[!UICONTROL SemelhançaPesquisar Tarefas Diversas]**.

1. Clique em **[!UICONTROL validateConfig()]**. Na caixa de diálogo **[!UICONTROL Validar configurações]**, clique em **[!UICONTROL Invocar]**.

   Os resultados da validação são exibidos na mesma caixa de diálogo.

## Habilitar marcação inteligente no fluxo de trabalho Ativo de atualização DAM (opcional) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. Em [!DNL Experience Manager], vá para **[!UICONTROL Ferramentas]** > **[!UICONTROL Fluxo de trabalho]** > **[!UICONTROL Modelos]**.

1. Na página **[!UICONTROL Modelos de fluxo de trabalho]**, selecione o modelo de fluxo de trabalho **[!UICONTROL Ativo de atualização DAM]**.

1. Clique em **[!UICONTROL Editar]** na barra de ferramentas.

1. Expanda o painel lateral para exibir as etapas. Arraste a etapa **[!UICONTROL Ativo de tag inteligente]** disponível na seção Fluxo de trabalho do DAM e coloque-a após a etapa **[!UICONTROL Processar miniaturas]**.

   ![Etapa para adicionar ativo de tag inteligente após a etapa de miniatura do processo no fluxo de trabalho Ativo de atualização DAM](assets/smart-tag-in-dam-update-asset-workflow.png)

   *Figura: etapa para adicionar ativo de tag inteligente após a etapa de miniatura do processo no fluxo de trabalho Ativo de atualização DAM*

1. Abra a etapa no modo de edição. Em **[!UICONTROL Configurações avançadas]**, verifique se a opção **[!UICONTROL Avanço do manipulador]** está selecionada.

   ![Configurar o fluxo de trabalho do Ativo de atualização do DAM e adicionar etapa de tag inteligente](assets/smart-tag-step-properties-workflow1.png)


   *Figura: Configurar o fluxo de trabalho do Ativo de atualização do DAM e adicionar etapa de tag inteligente*

1. Na guia **[!UICONTROL Argumentos]**, selecione **[!UICONTROL Ignorar erros]** se desejar que o fluxo de trabalho seja concluído mesmo se a etapa de marcação automática falhar.

   ![Configure o fluxo de trabalho Ativo de atualização do DAM para adicionar a etapa de tag inteligente e selecionar avanço do manipulador](assets/smart-tag-step-properties-workflow2.png)


   *Figura: Configure o fluxo de trabalho Ativo de atualização do DAM para adicionar a etapa de tag inteligente e selecionar avanço do manipulador*

   Para marcar os ativos quando eles forem carregados independentemente de a marcação inteligente estar ativada nas pastas, selecione **[!UICONTROL Ignorar sinalizador de tag inteligente]**.

   ![Configure o fluxo de trabalho Ativo de atualização do DAM para adicionar a etapa de tag inteligente e selecione ignorar sinalizador de tag inteligente](assets/smart-tag-step-properties-workflow3.png)


   *Figura: Configure o fluxo de trabalho Ativo de atualização do DAM para adicionar a etapa de tag inteligente e selecione ignorar sinalizador de tag inteligente*

1. Clique em **[!UICONTROL OK]** para fechar a etapa do processo e salve o fluxo de trabalho.

>[!MORELIKETHIS]
>
>* [Gerenciar tags inteligentes](managing-smart-tags.md)
* [Visão geral e como treinar tags inteligentes](enhanced-smart-tags.md)
* [Diretrizes e regras para treinar o Serviço de conteúdo inteligente](smart-tags-training-guidelines.md)

